---
title: "cfdisk /dev/sda FATAL ERROR: Bad logical partition 6: enlarged logical partitions ove"
date: 2014-07-17
forum: Hardware
---

### Post by gallay-charles on 2014-07-17
I am currently trying to build a LinuxFromScratch System. For that purpose I need to partition my disk. I want to use cfdisk but I got this error. Does someone know why ?

Here is my fdisk -l output :

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000712f7


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   488488959   244141056    7  HPFS/NTFS/exFAT
/dev/sda3       488491006   976771071   244140033    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       960618496   976771071     8076288   82  Linux swap / Solaris
/dev/sda6       488491008   960618495   236063744   83  Linux


Partition table entries are not in disk order
```

Thanks for you help

Charles

---

### Post by ajgreeny on 2014-07-17
More details are needed as your thread title has been foreshortened by the forum and does not give all the error details.

If there is no data you need to keep in the partitions, I would suggest you start again, and because I am a bit fussy, put all the partitions in disk order; I just like things neat and tidy, though I accept that it is not really important.  However, a clean start may allow you to get rid of the error.

---

