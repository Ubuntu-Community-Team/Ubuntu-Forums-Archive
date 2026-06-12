---
title: "unable to see my sata hdd in ubuntu in Compute-File browser"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by pbraju123 on 2009-07-26
hi,

I am new to ubuntu. Recently I have made my system dual boot : Windows XP and ubuntu.. I have 2 hdd : one is 40GB IDE drive and other one is SATA 160GB hdd.
after installation I am not able to see my 160GB sata hdd in file browser. other drive is vissible . This is the fdisk dump :
:/$ sudo fdisk -l
\
Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf314f314

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            2436        4870    19559137+   f  W95 Ext'd (LBA)
/dev/sda5            2436        4870    19559106    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d3a878f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

i can see the sata drive here but in in file browser it is not vissible.
Please help me resolve this issue. one more thing, in disk usage analyser I can see the 160GB drive.

---

