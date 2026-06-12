---
title: "Partition problem dualboot 64studio/hardy"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by Ouia on 2009-03-02
Hello there,

I must be tantalizing close to a solution, but I have too little knowledge of linux to make the last final step.

I installed ubuntu 8.04 64bit  a few days ago, after which I installed 64studio on another partition(sda3).

by changing the menu.lst file I managed to load 8.04 first instead of 64studio.

But this still leaves with the problem that 64studio doesn't boot at all. it stops at:

```
Check root= bootarg cat /proc/cmdline
      or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/sda3 does not exist.  
Dropping to a shell!

BusyBox .......  ........ commands.

/bin/sh: can't access tty; job control turned off
```


I did some search for information and got this:

sudo fdisk -lu
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41413535

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976960844   488480391   83  Linux
/dev/sda2       976960845  1002343544    12691350   82  Linux swap / Solaris
/dev/sda3      1002343545  1953520064   475588260   83  Linux
```

grub> geometry (hd0)
```

geometry (hd0)
drive 0x80: C/H/S = 121601/255/63, The number of sectors = 1953525168, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
```

ls /dev/disk/by-uuid/ -alh
```
total 0
drwxr-xr-x 2 root root 100 2009-03-01 07:37 .
drwxr-xr-x 5 root root 100 2009-03-01 07:37 ..
lrwxrwxrwx 1 root root  10 2009-03-01 07:37 23931ce7-2522-42d3-9e3d-13887475de06 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-03-01 07:37 9351427c-9801-4546-9503-3643d1108f88 -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-03-01 07:37 f1287190-73b6-418f-afd1-65655a07119f -> ../../sda1
```

64studio:etc/fstab  (sda5 was a swap partition that I removed afterwards)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

```
Hardy etc/fstab :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f1287190-73b6-418f-afd1-65655a07119f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=9351427c-9801-4546-9503-3643d1108f88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

Does anybody has an idea on how to proceed from here on?

Thanks in advance.

---

### Post by Ouia on 2009-03-03
bump

---

