---
title: "Montar partición EXT3"
date: 2009-01-26
forum: Hardware
---

### Post by Ropoo on 2009-01-26
Hola. Tenía una partición NTFS, pero la formateé y ahora tiene EXT3.
El problema es que no se monta, no puedo acceder.
[IMG]http://img145.imageshack.us/img145/4013/capturahdno3.gif[/IMG]

Mi fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=014a10c7-e803-4768-a6f0-036f36958ef8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=243dc110-1692-415e-8fbf-207c770ae0f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


**_Edit:_**

Perdón por mi novatez, solo tenía que editar el fstab y agregar la siguiente linea:
> /dev/sdb1 /media/Datos ext3 rw,user 0 0
***El problema ahroa es que no puedo escribir dentro de la partición.***

Gracias de antemano.

**_Edit2:_**

Problema solucionado, solo tenía que darle permisos. 
Gracias a Google,

---

