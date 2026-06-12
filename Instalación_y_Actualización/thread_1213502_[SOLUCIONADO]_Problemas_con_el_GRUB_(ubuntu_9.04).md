---
title: "[SOLUCIONADO] Problemas con el GRUB (ubuntu 9.04)"
date: 2009-07-14
forum: Instalación y Actualización
---

### Post by Andresinho on 2009-07-14
Buenas, he tenido algunos problemillas instalando Ubuntu 9.04 especialmente en el caso que una vez que términa la instalación no corre el GRUB.

Les explico com más detalles:

Tengo un computador de proce AMD64 y dentro de un disco duro de 80GB que tiene una partición de Windows XP le instale en un espacio vacío esta versión de Ubuntu. Una vez que termina toda la instalación sin ningún problema y se renicia el computador comienza a cargar windows imaginandome que la instalación jamás le hizo nada al MBR. Por lo cual me gustaría ayuda en este tema.

Lamentablemente ahora estoy lejos del computador por lo cual no puedo darles detalles pero si es muy necesario se los daré.

Gracias de ante mano.

---

### Post by Carlos C on 2009-07-15
Por favor ingresa a ubuntu con el LiveCD y abre el terminal. Escribe el siguiente comando:
```
sudo fdisk -l
```
copia acá lo que te salga.
Saludos.

---

### Post by Andresinho on 2009-07-16
Disculpen por mi retraso, pero ya solucioné el problema, ahora descubrí un problema que de verdad me tiene acomplejado y tiene que ver con la temperatura de la CPU. Pero abriré otro tema para esto.
 
Una explicación para aquellos que les pase, cuando se tienen dos discos duros, uno IDE y otro SATA, por alguna razón el grub se instala obviamente en el sda que sería el SATA (aunque el ide igual lo nombra como "sd"). Así que aunque las particiones las hagan en el disco IDE (o secundario) e incluso en la BIOS tengan como primer boteo el IDE (o secundario) el grub se instalará en el sda.
 
A lo mejor suena obvia la explicación pero prefiero darla igual, uno nunca sabe. CT plz.
 
Y gracias.

---

