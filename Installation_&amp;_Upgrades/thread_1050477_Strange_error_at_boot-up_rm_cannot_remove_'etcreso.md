---
title: "Strange error at boot-up: rm: cannot remove '/etc/resolvconf/run/interface/*'...."
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by giorgione on 2009-01-25
Hi there,

I have 2 HDD in my PC , sda and sdb. On sda I used to have Ubuntu 7.10 and Windows and on sdb I have Ubuntu 8.10 which I am using.

I got rid of 7.10 by deleting the respective partitions on sda and now I have on sda1 my old windows and sda2 in a big ext3-partition.

After these changes on sda I rebooted and got a strange error at boot time:

> rm: cannot remove '/etc/resolvconf/run/interface/*': Read-only file system /etc/rcS.d/S07resolvconf: 116: cannot create /etc/resolvconf/run/enable-updates: read-only file system

Besides this error everything seems alright. Does anyone know how so solve this problem or what consequences it has?

Thanks!


The problem is not due to the /etc/fstab. There everything is alright:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=c27db196-fce9-4baa-9a40-5568ce09e3a9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=de41aad4-0516-470a-b10b-0ef9438a9d09 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=61455f8c-e025-420b-a366-5fe1445d9430 none            swap    sw              0       0
/dev/sda2 /home/giorgione/backup                            ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by palo_m on 2009-04-29
Try to rename /etc/rcS.d/S07resolvconf to /etc/rcS.d/S38resolvconf.

See also [Bug #264165]("https://bugs.launchpad.net/bugs/264165")

---

