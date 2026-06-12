---
title: "FAT32 Storage drive not recognized"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by Cpl.Punishment on 2009-01-02
Hello,

I would like to be able to save data to my storage drive from Ubuntu. When I first installed it I saw all 3 hard drives and formated the storage drive as Fat32. 

I have 3 hard drives; 1 with Ubuntu 8.10, 1 with winxp and 1 storage drive formated as Fat32. Ubuntu recognizes all but the storage drive. Under Places and Computer it shows 300.1 GB Media, CD Rom and Filesystem. 

Here is what FSTAB shows:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=07a87831-01da-46f4-b92c-033e609f16d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=7f93ef14-45a5-439e-a801-4f2e44d4a627 /home           ext3    relatime        0       2
# /dev/sdc5
UUID=0FC2-FE88  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=2de21df3-d94d-4d27-883e-00a41ae2c75c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Your help is appreciated.

---

