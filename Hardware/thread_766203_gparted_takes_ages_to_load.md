---
title: "gparted takes ages to load"
date: 2008-04-25
forum: Hardware
---

### Post by potatan on 2008-04-25
Hi,

Whenever I run gparted from a terminal, it takes maybe 10-15 minutes to finish scanning the disks - is this normal?  I have four hard disks and a number of partitions scattered around them (which I intend to tidy up!), but the load time of gparted seems excessive.

Output from fisk -l :

```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74bfade6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10410    83618293+   7  HPFS/NTFS
/dev/sda2           10411       19536    73304595   83  Linux
/dev/sda3           19537       19929     3156772+   f  W95 Ext'd (LBA)
/dev/sda5           19537       19929     3156741   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6256c92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c703c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff8eff8e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

```

Many thanks.

---

### Post by potatan on 2008-04-27
This problem is resolved now after I upgraded to 8.04 - not sure why it was a problem to begin with, but gparted now takes about 1.5 minutes to load.

---

