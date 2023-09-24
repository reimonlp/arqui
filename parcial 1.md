Escribir un programa para MSX88 que, utilizando el puerto PA del PIO, reciba una cadena de 5 caracteres desde un dispositivo generico. Este dispositivo envia la cadena de a un caracter a la vez. Los caracteres se deben recibir desde el dispositivo uno por uno, esperando 10 segundos entre cada recepción. El programa debe finalizar cuando se han recibido todos los caracteres de la cadena, o cuando se presiona la tecla F10

```assembly
pa equ 30h
ca equ 32h

    org 1000h
cadena db ?,?,?,?,?

    org 2000h
        mov al, 0FFh
        out ca, al
        mov bx, offset cadena
        mov ah, 5
input:  int 6
        cmp ah, 0
        jz fin
        inc bx
        dec ah
        jmp input
fin:    int 0
        end
```