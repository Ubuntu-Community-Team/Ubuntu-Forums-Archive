---
title: "Cannot mount:"
date: 2008-11-07
forum: Hardware
---

### Post by gangsterbill02 on 2008-11-07
Invalid mount option when attempting to mount the volume 'TRANSFORMERS_D1'.

This is the error I get when trying to mount a blue ray "Transformers." Any answers? 

This is my /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f345bac0-ed44-432a-b85c-81fb9e207e16 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d02e526a-ca64-44ae-b372-a533439360e4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I am running Ubuntu 8.04 64 bit.

---

### Post by kidders on 2008-11-09
Hi there,

I could be wrong, but afaik, "utf8" is not a supported mount option for UDF filesystems.

---

