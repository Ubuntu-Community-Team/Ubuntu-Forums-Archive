---
title: "Hard drive parameters?"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by davesbrain on 2008-01-17
I noticed that my drive parameters are different between two identical drives.  The cylinders are different.   HDA is my XP drive and HDB is Ubuntu.  I did use 'Auto' in the bios when I installed the drive.    Both are Maxtor51536H2.    
See fdisc info below:

```
davejr@davejr-desktop:~$ sudo fdisk -l

Disk /dev/hda: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc77ec77e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1867    14996646    7  HPFS/NTFS

Disk /dev/hdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000affe2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1744    14008648+  83  Linux
/dev/hdb2            1745        1826      658665    5  Extended
/dev/hdb5            1745        1826      658633+  82  Linux swap / Solaris
```

---

