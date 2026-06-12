---
title: "Need two spare HDD's inside PC to auto-mount upon boot."
date: 2008-09-24
forum: General Help
---

### Post by Roasted on 2008-09-24
My current /etc/fstab.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=882ebefa-daea-4453-b514-95a5e1502193 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=a3f52684-6915-4e41-bfb7-8cb9bcd72ef4 /home           ext3    relatime        0       2
# /dev/sda2
UUID=9397ac6b-b51b-433e-8857-bf765234cd6c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



My current fdisk -l


jason@jason-hardy:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa74ba74b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+  83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825        3948      996030   82  Linux swap / Solaris
/dev/sdb3            3949        5772    14651280   83  Linux
/dev/sdb4            5773       30515   198748147+  83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43e0877d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          62      497983+   5  Extended
/dev/sdc2              63       30515   244613722+  83  Linux
/dev/sdc5               1          62      497952   82  Linux swap / Solaris
jason@jason-hardy:~$ 



I need sdc2 and sda1 to auto-mount upon boot.

How can I achieve this?

---

