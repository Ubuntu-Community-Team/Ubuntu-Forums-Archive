---
title: "problem with dvd driver definition?"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by ubunlilluz on 2006-03-05
why if in many applications (e.g. mplayer)  i define the dvd driver as /media/cdrom0 it doesn't work, but if i change the config of that application with /dev/hdd it works fine?

to help you, my fstab is: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    umask=000
/dev/hdb5       /media/hdb5     ntfs    umask=0222        0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto	0	0

---

### Post by ubunlilluz on 2006-03-06
has anybody found the same problem?

---

