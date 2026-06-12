---
title: "MediaDirect trouble with partitions"
date: 2008-05-07
forum: Hardware
---

### Post by Dontpanic.its42 on 2008-05-07
I am working on a XPS m1330, and I dual boot Ubuntu HH 64bit with WinVista. As expected, I pressed the dreadful MediaDirect button and I got the blue screen. After rebooting, I have not had any (apparent) issues in the functioning of both OSs, but "fdisk -l" reads

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   385478656   390719487     2620416    c  W95 FAT32 (LBA)
/dev/sda2          241664    21213183    10485760    7  HPFS/NTFS
/dev/sda3   *    21213184   221431799   100109308    7  HPFS/NTFS
/dev/sda4       221440021   390719487    84639733+   f  W95 Ext'd (LBA)
/dev/sda5       385478656   390719487     2620416   dd  Unknown
/dev/sda6       221440023   221568479       64228+  83  Linux
/dev/sda7       221568543   229376069     3903763+  82  Linux swap / Solaris
/dev/sda8       229376133   252814904    11719386   83  Linux
/dev/sda9       252814968   385463609    66324321   83  Linux

Partition table entries are not in disk order

while "cfdisk" gives
> FATAL ERROR: Bad primary partition 0: Partition ends in the final partial cylinder

I intend to use VirtualBox to run my Vista partition from Linux, so I would like to clear this mess before going after that. Any help will be appreciated.

Cheers

++ New to Ubuntu, new to the forum, apologies if I am in the wrong place

---

