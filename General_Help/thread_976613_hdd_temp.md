---
title: "hdd temp"
date: 2008-11-09
forum: General Help
---

### Post by rusty_jones on 2008-11-09
```
 sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d3f1d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29646   238131463+  83  Linux
/dev/sda2           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1193

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    b  W95 FAT32

Disk /dev/sdc: 32.3 GB, 32346472448 bytes
255 heads, 63 sectors/track, 3932 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3933    31588351+   c  W95 FAT32 (LBA)
```

This is my print out for sudo fdisk -l
```
 localhost 7634
|/dev/sda|WDC WD2500KS-00MJB0|33|C|
```

This is my print out for "nc localhost 7634" What happened to sdb and sdc?


Rusty

---

