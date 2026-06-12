---
title: "mount cdrom and dvd"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by gosh on 2006-01-09
Hi,
I have two cd/dvd players in my system, but I can't mount/reach any of them.
When I put a cd in one of them, nothing happens.

fstab gives:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

There is however no /dev/hdd or /dev/hdc

dmesg doesn't show hdd or hdc either

---

