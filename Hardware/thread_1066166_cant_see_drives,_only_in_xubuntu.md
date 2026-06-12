---
title: "cant see drives, only in xubuntu"
date: 2009-02-10
forum: Hardware
---

### Post by dreken105 on 2009-02-10
i cant seem to mount any of my internal hard drives in xubuntu. when i load up a ubuntu session the drives are there, but this is only hardware so ubuntu runs too slow when im running multiple programs. how can i mount these drives? here is the sudeo fdisk -l output:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd31fd31f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1567    12586896    c  W95 FAT32 (LBA)
/dev/sda2            1568        9964    67448902+   f  W95 Ext'd (LBA)
/dev/sda5            1568        9964    67448871    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ec23040

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16709   134215011    7  HPFS/NTFS

---

