---
title: "Como hago para acceder a un disco externo?"
date: 2009-01-31
forum: Hardware
---

### Post by DrKenobi on 2009-01-31
Hola!

Mi familia compro un disco externo. Como la PC principal de la casa es una iMac, siguieron las instrucciones del manual y lo setearon para Mac (ni idea que hicieron, yo no estaba en casa).

Si yo conecto el disco a cualquier Mac, con USB, no hay problema. Pero cuando lo conecto a mi Xubuntu, solo puedo leer y copiar archivos del disco externo a mi PC, pero no puedo "subiir" ningun archivo. Como que solo tengo permitido la lectura pero no la escritura sobre este disco externo.

Alguna idea? Alguna forma de poder usarlo?

Me voy a estudiar, espero que alguien me pueda ayudar.

Gracias

---

### Post by Hei Ku on 2009-01-31
Que tipo de filesystem tiene el disco?

---

### Post by DrKenobi on 2009-01-31
no se, pero como puedo averiguarlo?

---

### Post by gmunioz on 2009-01-31
Hola drk....:

Necesitas instalar:
hfsplus hfsprogs hfsutils libhfsp0 hfsutils-tcltk disk-manager

Una vez instalados, montas el disco pulsando:

Sistema - Administración - Administrador de disco

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu. 6666 Más malo que el Diablo.**

---

### Post by DrKenobi on 2009-02-04
instale todo eso y nada...... :(
al disco siempre lo pude montar, pero no lo puedo escribir

---

### Post by NickCis on 2009-02-05
> **DrKenobi said:**
> instale todo eso y nada...... :(
al disco siempre lo pude montar, pero no lo puedo escribir

Fijate como lo monta, capas lo estas montando como read only (ro) intentalo montar como read and write (rw)...

Intentaste modificar el disco externo siendo root?
Saludos.

Edit:
Yo tengo un disco ntfs que se monta automaticamente cuando prende la pc (por eso esta configurado en /etc/fstab)
La linea que lo monta es esta: /dev/sda1 /media/disk ntfs defaults,rw,user,auto,iocharset=utf8,umask=000 0 0

Donde dice rw significa read and write si estubiese montado solo con ro, no podria modificarlo.

Si escribis mount en el terminal te da informacion de como estan montados todos los dispositivos, fijate que dice relacionado con tu disco externo

---

