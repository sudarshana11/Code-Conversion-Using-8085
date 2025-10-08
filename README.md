# Code-Conversion-Using-8085
## Aim:
## To write 8085 microprocessor programs for converting:
1.	Hexadecimal to ASCII
2.	ASCII to Hexadecimal
## Apparatus Required:
•	Laptop with an internet connection
## Program 1: Hexadecimal to ASCII Conversion
```
; HEX to ASCII conversion
; Input at 2050H (00–0FH)
; Output at 2051H

        LDA 2050H      ; Load hex digit
        CPI 0AH        ; Compare with 0AH (decimal 10)
        JC  NUM        ; If < 0AH → it's 0–9
        ADI 37H        ; For A–F → Add 37H
        JMP STORE

NUM:    ADI 30H        ; For 0–9 → Add 30H

STORE:  STA 2051H      ; Store ASCII result
        HLT
```
## Algorithm:
1.	Load the hexadecimal number from memory location 4200H.
2.	Mask the upper nibble and check if it is less than 10H.
3.	If it is less than 10H, add 30H to convert it to ASCII.
4.	If it is greater than 10H, add 37H to convert it to ASCII.
5.	Repeat the process for the lower nibble.
6.	Store the ASCII equivalent in memory location 4300H and 4301H.
## Output:
•	The ASCII equivalent of the hexadecimal number will be stored in 4300H (upper nibble) and 4301H (lower nibble).
<img width="663" height="373" alt="image" src="https://github.com/user-attachments/assets/a089a449-e606-455f-b747-088b54be29ba" />


## Program 2: ASCII to Hexadecimal Conversion
```
; ASCII to HEX conversion
; Input at 2050H
; Output at 2051H

        LDA 2050H      ; Load ASCII
        CPI 3AH        ; Compare with '9'+1 = 3AH
        JC  DIGIT      ; If < 3AH → 0–9
        SUI 37H        ; For A–F → Subtract 37H
        JMP STORE

DIGIT:  SUI 30H        ; For 0–9 → Subtract 30H

STORE:  STA 2051H      ; Store HEX result
        HLT
```
## Algorithm:
1.	Load the first ASCII digit from memory location 4200H.
2.	Convert it to hexadecimal by subtracting 30H (if it's a number) or 37H (if it's a letter A-F).
3.	Load the second ASCII digit from memory location 4201H and repeat the process.
4.	Combine the upper and lower nibbles to form a hexadecimal number.
5.	Store the result in memory location 4300H.
## Output:
•	The hexadecimal equivalent of the ASCII input will be stored in memory location 4300H.
<img width="663" height="373" alt="image" src="https://github.com/user-attachments/assets/f55669ab-4753-4fdb-b905-0712e4c7ec04" />

## Result:
The 8085 microprocessor successfully converts hexadecimal numbers to ASCII and vice versa, storing the results in memory.
