# VIGENERE-CIPHER
## EX. NO: 4
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.


STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.


STEP-3: Repeat this process for all 26 rows and construct the final key matrix.


STEP-4: The keyword and the plain text is read from the user.


STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.


STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.


STEP-7: The junction character where these two meet forms the cipher character.


STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Function to encrypt a message using Vigenere Cipher
void encrypt(char text[], char key[], char result[]) {
    int textLen = strlen(text);
    int keyLen = strlen(key);
    int i, j = 0;

    for (i = 0; i < textLen; i++) {
        if (isalpha(text[i])) {
            char base = isupper(text[i]) ? 'A' : 'a';
            result[i] = ( (text[i] - base) + (toupper(key[j % keyLen]) - 'A') ) % 26 + base;
            j++;
        } else {
            result[i] = text[i]; // keep spaces/punctuation
        }
    }
    result[i] = '\0';
}

// Function to decrypt a message using Vigenere Cipher
void decrypt(char text[], char key[], char result[]) {
    int textLen = strlen(text);
    int keyLen = strlen(key);
    int i, j = 0;

    for (i = 0; i < textLen; i++) {
        if (isalpha(text[i])) {
            char base = isupper(text[i]) ? 'A' : 'a';
            result[i] = ( ( (text[i] - base) - (toupper(key[j % keyLen]) - 'A') + 26 ) % 26 ) + base;
            j++;
        } else {
            result[i] = text[i]; // keep spaces/punctuation
        }
    }
    result[i] = '\0';
}

int main() {
    char text[1000], key[100], enc[1000], dec[1000];

    printf("Simulation of Vigenere Cipher\n");
    printf("Enter the message: ");
    scanf("%[^\n]", text);   // read full line including spaces
    getchar();
    printf("Enter the key: ");
    scanf("%s", key);

    for (int i = 0; i < strlen(key); i++) key[i] = toupper(key[i]);

    encrypt(text, key, enc);
    printf("Encrypted text : %s\n", enc);

    decrypt(enc, key, dec);
    printf("Decrypted text : %s\n", dec);

    return 0;
}

```

## OUTPUT

<img width="385" height="296" alt="Screenshot 2025-09-03 100616" src="https://github.com/user-attachments/assets/fe414714-9453-4dd3-ba52-50c83102c445" />




## RESULT
The program is executed successfully
