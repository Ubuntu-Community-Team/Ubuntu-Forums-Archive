---
title: "Only extended partition misaligned"
date: 2012-08-26
forum: Hardware
---

### Post by shane84 on 2012-08-26
Only one extended partition is misaligned. This partition is split into three logical partitions (each correctly aligned), one containing my windows C drive, on with Ubuntu installed, and one with the cache. Since the logical partitions are aligned correctly, will this still affect the hard drive performance or do I need to go through the trouble of repartitioning and reinstalling everything? My hard drive is a hitachi and uses 4K byte sectors. 

Thanks!!

This is the output of fdisk -lu /dev/sda
> Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa6486ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409662  1420908543   710249441    f  W95 Ext'd (LBA)
Partition 2 does not start on physical sector boundary.
/dev/sda3      1420908544  1464936447    22013952    7  HPFS/NTFS/exFAT
/dev/sda4      1464936448  1465145343      104448    c  W95 FAT32 (LBA)
/dev/sda5          409664   601706495   300648416    7  HPFS/NTFS/exFAT
/dev/sda6       601708544  1404332031   401311744   83  Linux
/dev/sda7      1404334080  1420908543     8287232   82  Linux swap / Solaris


---

### Post by linrunner on 2012-08-26
Hi,

the alignment of the extended partition doesn't matter at all. Only partitions containing data (primary, logical) are important

---

### Post by shane84 on 2012-08-26
> **linrunner said:**
> Hi,

the alignment of the extended partition doesn't matter at all. Only partitions containing data (primary, logical) are important

Thank you! I am glad I do not go through the trouble of fixing this!

---

