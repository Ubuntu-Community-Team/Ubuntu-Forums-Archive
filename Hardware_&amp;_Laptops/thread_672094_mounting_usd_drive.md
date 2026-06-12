---
title: "mounting usd drive"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by md5hash on 2008-01-19
my usb stick is not mounting automatically

lsusb outpu 

```
paske@x86:~$ lsusb
Bus 005 Device 009: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

fdisk -l output

paske@x86:~$ sudo fdisk -l
[sudo] password for paske:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc19ac19a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009a09e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          36      289138+  83  Linux
/dev/sdb2              37        3860    30716280   83  Linux
/dev/sdb3            3861       15433    92960122+  83  Linux
/dev/sdb4           15434       19457    32322780    5  Extended
/dev/sdb5           15434       15535      819283+  82  Linux swap / Solaris
/dev/sdb6           15536       19457    31503433+   b  W95 FAT32
```

---

