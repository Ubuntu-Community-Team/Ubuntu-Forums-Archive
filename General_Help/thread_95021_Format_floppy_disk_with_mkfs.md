---
title: "Format floppy disk with mkfs"
date: 2005-11-25
forum: General Help
---

### Post by cocox on 2005-11-25
hi friends i do this for fix a bug of ubuntu floppy
i add this to mi fstab

/dev/fd0 /media/floppy0 vfat rw,user,noauto,umask=000 0 0

after that i can mount at least a disk...

now im triying to mount mi kernell on a floppy disk doing this..

mount /media/floppy0
cp /boot/vmlinuxxxx /media/floppy0
umount /media/floppy0

but when i mount my disk again there is no anyfile

so.. i try to format my disk in ext2 doing this

mkfs.ext2 /dev/fd0

after that i get this message

-------------------------------------------------------------------

cocox@techi:~$ sudo mkfs.ext2 /dev/fd0
mke2fs 1.35 (28-Feb-2004)
Cuidado: no se puede borrar el sector 2: Attempt to write block from filesystem resulted in short write
Etiqueta del sistema de ficheros=
Tipo de SO: Linux
Tamaño del bloque=1024 (bitácora=0)
Tamaño del fragmento=1024 (bitácora=0)
184 nodos i, 1440 bloques
72 bloques (5.00%) reservados para el súper usuario
Primer bloque de datos=1
1 bloque de grupo
8192 bloques por grupo, 8192 fragmentos por grupo
184 nodos i por grupo

Cuidado: no se puede leer el bloque 0: Attempt to read block from filesystem resulted in short read
Cuidado: no se puede borrar el sector 0: Attempt to write block from filesystem resulted in short write
Mientras se escribían las tablas de nodos i: 0/1
No se pueden escribir 8 bloques en la tabla de nodos i al principio de 5: Attempt to write block from filesystem resulted in short write

-------------------------------------------------------------------

here a few questions..

1. what kind of file system should i use in my floppy for copy my kernell -?
2. is there any command for know the kind of format use in my floppy disk ? (i mean view if my disk is in ext2 or vfat..)

btw .... my disk is new my floppy either ... and i already use this commands with sudo :S help plz 

:KS :KS :KS :KS

---

