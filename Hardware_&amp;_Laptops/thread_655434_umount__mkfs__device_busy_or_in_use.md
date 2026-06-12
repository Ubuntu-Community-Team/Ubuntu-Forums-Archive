---
title: "umount / mkfs / device busy or in use"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by xover on 2008-01-01
I have tried to create filesystems on 7.10 with a WD passport and a Seagate Desktop 500GB with no avail. I am able to create them on CentOS5, but when i try to do so on gutsy i get device is busy or in use.

it is not mounted and there are no processes accessing files on the disk.

i have 4 others dics that i can happily create file systems on in a different enclosure.

Rich
fdisk -l

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux

root@pc:~# umount /dev/sdc1
umount: /dev/sdc1: not mounted

root@pc:~# fuser /dev/sdc
root@pc:~# fuser /dev/sdc1
root@pc:~# 

root@pc:~# mkfs.xfs /dev/sdc1
mkfs.xfs: cannot open /dev/sdc1: Device or resource busy

root@pc:~# mkfs.ext3 /dev/sdc1
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdc1 is apparently in use by the system; will not make a filesystem here!

---

