---
title: "WD My Book &quot;read only&quot;"
date: 2008-08-10
forum: Hardware
---

### Post by beezlebozo on 2008-08-10
I can't write to the external HD, here's my current /etc/fstab

[I][INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=011a1fc9-d68e-47fa-a7d3-768e0b086dd0 /               ext3    relatime,errors=remount-rw 0       1
# /dev/sda5
UUID=874960be-5070-4903-a869-fd93d43d5aeb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/INDENT][/I]

I have tried chmod and chown.  It is a fat32 drive.

---

