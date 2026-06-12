---
title: "problem with swap"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by anirup on 2009-05-11
i have two swap partitions.1st one is on my first harddisk and it is
**/dev/sda9** and second one is on my second harddisk **/dev/sdb7**.**i may have made some changes to etc/fstab because of which neither of the swap partition ****mounts**.**there was no prob during installation.it was only after i made some changes.can i rectify this problem?**

[B]anirupdutta@HCL:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf464f464

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         985     7911981    b  W95 FAT32
/dev/sda2             986        4869    31198230    f  W95 Ext'd (LBA)
/dev/sda5             986        2050     8554581    b  W95 FAT32
/dev/sda6            2051        3617    12586896    b  W95 FAT32
/dev/sda7            3618        4191     4610623+   b  W95 FAT32
/dev/sda8            4192        4815     5012248+  83  Linux
/dev/sda9            4816        4869      433723+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1f21661

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9535    76589856    c  W95 FAT32 (LBA)
/dev/sdb2            9536       19456    79690432+   f  W95 Ext'd (LBA)
/dev/sdb5            9536       18459    71681998+   b  W95 FAT32
/dev/sdb6           18460       19383     7421998+  83  Linux
/dev/sdb7           19384       19456      586341   82  Linux swap / Solaris
[/B]

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=0de56ce4-82e3-4049-b939-40ac24437728 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=90e7ab63-d6e3-4f42-af1c-e935ae4d1a16 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/B]

---

### Post by logos34 on 2009-05-11
You only need one swap.

There's only one entry in fstab (sda9). Maybe the UUID changed, which is why it's not mounting.

check

> sudo blkid

and edit if different

Seems they're a little small too

what does 

> free -m

show?

---

### Post by anirup on 2009-05-11
**thank u.i changed the uuid and it works all right now.**

---

