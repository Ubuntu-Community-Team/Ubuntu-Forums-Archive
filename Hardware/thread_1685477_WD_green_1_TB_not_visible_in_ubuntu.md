---
title: "WD green 1 TB not visible in ubuntu"
date: 2011-02-10
forum: Hardware
---

### Post by krepperk on 2011-02-10
Hi
I recently installed ubuntu 10.10 and ubuntu can't see one of my hard drives. It is a WD green 1TB, it shows up in bios but not in the OS. This is what the fdisk -l looks like:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e22a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   82  Linux swap / Solaris
/dev/sda2            1216        8511    58592257    5  Extended
/dev/sda5            1216        8511    58592256   83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51aa4d3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182402  1465136128    7  HPFS/NTFS

So two hdd show up but not the third. I have also screwed up my windows installation so i can't boot into that, haven't even been able to reinstall it..
Any suggestions?

---

