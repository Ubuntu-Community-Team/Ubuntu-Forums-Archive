---
title: "Problemas con lectora de DVD"
date: 2008-10-03
forum: Hardware
---

### Post by sdm_cacto on 2008-10-03
Tengo una Laptop (Dell Inspiron 1521) corriendo Hardy.
El problema es que desde hace unos dias no me detecta la lectora de DVD, no se bien por que (porq constantemente estoy toqueteando cosas) pero ni siquiera se me abre la bandeja, cosa q si pasa antes de iniciar el Sistema Operativo.
Posteo mi /etc/fstab por si ayuda

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=02a65ec1-8779-4631-88ca-40ece8aeb16a /               ext3    relatime,errors=remount-ro 0 1
# /dev/sda3
UUID=080861f1-9a0f-4604-8a4a-1786676b424a /home           ext3    relatime        0       2
/dev/sda1   /windows        ntfs    defaults,umask=007,gid=46         0       1
# /dev/sda4
UUID=88581254-a1c2-47df-bc9e-0a1b830dbbbb none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8   0       0


ademas:

> 
sergio@sergio-laptop:~$ sudo mount /dev/hda
mount: el dispositivo especial /dev/hda no existe


PD: tampoco me bootea windows.

---

### Post by Mauro22 on 2008-10-03
:confused:


Probaste con un livecd? o sea, si te bootea con la lectora...


A veces no la reconoce o no la reconoce para nada??

---

