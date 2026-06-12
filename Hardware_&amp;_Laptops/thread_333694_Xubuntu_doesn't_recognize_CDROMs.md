---
title: "Xubuntu doesn't recognize CDROMs"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by glue on 2007-01-07
Xubuntu refuses to mount my CDROMs.  As far as I can tell my fstab looks fine.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=88423dc4-42b6-4052-ae37-dbbcfa01d44e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=0d2354be-7e9b-4419-9266-9fe64ecbcdc2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows vfat umask=0000 0 0

Trying to mount at the terminal gets me a "Mount: No Medium Found" error.  If I have a problem with Xubuntu, will I likely have the same problem with Kubuntu/Ubuntu?

---

