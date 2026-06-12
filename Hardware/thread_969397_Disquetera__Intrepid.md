---
title: "Disquetera  Intrepid"
date: 2008-11-03
forum: Hardware
---

### Post by erdosain9 on 2008-11-03
Hola.  El tema es que no encuentro el icono de la disquetera en lugares y no puedo montarla.  He buscado y no encuentro la solución.
 Por ejemplo me sale esto en una terminal al intentar montarla:
mount /media/floppy0
mount: el dispositivo especial /dev/fd0 no existe

o esto 

mount /media/floppy
mount: el dispositivo especial /dev/fd0 no existe

Al mirar este archivo: sudo gedit /etc/fstab
me sale esto:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=465b137d-7358-4985-9f0d-b03ba170d779 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9df5c98a-68a7-4619-aa4f-73a728234df7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Lo que me hace suponer que está bien... pero bueno, yo soy muyyy nuevo.
Si alguien me da una mano para poder acceder a la disquetera!!!
Gracias!

---

### Post by erdosain9 on 2008-11-04
mmm,alguna idea??????

---

### Post by faktorqm on 2008-11-04
Creo que deberias hacerlo con el siguiente comando:

```
sudo mount -t auto -o rw,user,noauto,exec,utf8 /dev/fd0 /media/floppy0
```

Si no te anda postea la salida. Salu2!

---

### Post by EnriqueK on 2008-12-22
Para montar  la disquetera para la presente sesión
sudo modprobe floppy

Para montar siempre la disquetera
sudo gedit /etc/modules
añadir una linea: floppy

---

