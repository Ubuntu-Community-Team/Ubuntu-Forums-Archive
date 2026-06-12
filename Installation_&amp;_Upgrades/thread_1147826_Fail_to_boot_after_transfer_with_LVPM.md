---
title: "Fail to boot after transfer with LVPM"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by saka on 2009-05-03
Hi
I have ubuntu 8.10 installed inside windows after i transfered to a separete partition using LVPM it failed to boot it says " partition could not be mounted " 
this is the output of 
sudo fdisk -lu :
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69b2a27a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   158722047    77824000    7  HPFS/NTFS
/dev/sda3       158722048   312578047    76928000   83  Linux

---

