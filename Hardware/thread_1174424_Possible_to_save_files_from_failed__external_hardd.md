---
title: "Possible to save files from failed  external harddive?"
date: 2009-05-30
forum: Hardware
---

### Post by tocilog on 2009-05-30
I have a 500GB western digital harddrive that failed on me. I tried plugging it into different computers but i get the same results. ubuntu sees the drive but it cant mount it, saying "no media in drive." when i go to properties it gives me nothing. 

lsusb
```
Bus 001 Device 009: ID 1058:0400 Western Digital Technologies, Inc. External HDD
Bus 001 Device 008: ID 1058:0600 Western Digital Technologies, Inc. 
Bus 001 Device 007: ID 1058:0500 Western Digital Technologies, Inc. hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The western digital drive is listed here.

fdisk -1
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc88cc88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96409640

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001    c  W95 FAT32 (LBA)

```

sda is my system drive. sdb is my data drive. here I *think* the external drive is sde, but it's only listed as 250GB instead of 500GB.  

So the pc sees the drive, i just can't access it at all. Any help is appreciated.

---

