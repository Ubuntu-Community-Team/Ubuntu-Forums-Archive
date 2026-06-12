---
title: "Ubuntu 8.04 x64 and Sil3512 SATA Raid Controller problem"
date: 2010-07-19
forum: Hardware
---

### Post by acidrop on 2010-07-19
Hi!

I have a box with Sweex Sil3512 chipset SATA Raid controller and 2 WD 1TB Green SATA2 disks.
I have dual-boot Ubuntu 8.04 x64 Kernel 2.6.24-27
and Win7 x64bit.
Windows can identify the RAID1 mirror set correctly as it shows 1hd on local disk management.
Ubuntu however ond DiskParted it shows 2 hds /dev/sda and /dev/sdb with the same partition structure.
My question is:
Does it recognize the RAID1 mirror set correctly if it shows 2 hds instead of 1 like on Win?
Is there any other driver i should try?

Some data:

root@ubuntu:~# lspci | grep Sil
04:01.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

root@ubuntu:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb41069e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5115    41086206    7  HPFS/NTFS
/dev/sda2            5116      121601   935673795    5  Extended
/dev/sda5            5116       10230    41086206    7  HPFS/NTFS
/dev/sda6           10231       13770    28435018+  83  Linux
/dev/sda7           13771       14054     2281198+  82  Linux swap / Solaris
/dev/sda8           14055       47014   264751168+   7  HPFS/NTFS
/dev/sda9           47015       60801   110744046   83  Linux
/dev/sda10          60802      121601   488375968    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x108f45ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5115    41086206    7  HPFS/NTFS
/dev/sdb2            5116      121601   935673795    f  W95 Ext'd (LBA)
/dev/sdb5            5116       10230    41086206    7  HPFS/NTFS
/dev/sdb6           10231       13770    28435018+  83  Linux
/dev/sdb7           14055       47014   264751168+   7  HPFS/NTFS
/dev/sdb8           47015       60801   110744046   83  Linux
/dev/sdb9           60802      121601   488375968+   7  HPFS/NTFS
/dev/sdb10          13771       14054     2281198+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44434255

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         974     7823623+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(60, 254, 63) logical=(973, 254, 63)

---

### Post by dino99 on 2010-07-19
recheck bios settings and select ahci mode

---

### Post by acidrop on 2010-07-20
This is a pci controller not onboard on motherboard.
It has a Bios option which you can create/delete an array 
but not to setup AHCI mode.

---

### Post by tallthom on 2011-01-19
I have the Silicon Image Sil3512 as well with the same issue.  Has anyone seen/heard of any updates to the situation? 

The raid devices are not being detected.  It looks like there are drivers for the Red Hat / Fedora Community, so wondering if anyone has heard of things for Ubuntu.

Would like to try out RAID 0/1 on my backup server.  The version I'm on is 10.04.

---

