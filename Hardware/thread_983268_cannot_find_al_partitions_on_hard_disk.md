---
title: "cannot find al partitions on hard disk"
date: 2008-11-15
forum: Hardware
---

### Post by linx-fan on 2008-11-15
Hi,
I have installed ubuntu 8.10 amd64 version on a SATA 500GB disk.
I partitioned the disk into 200, 150, 148 & 2GB (swap)
Mounted 200GB on / and installed the OS.

Now every thing working fine but I could not see, access the 150GB and 148 GB space.

I did not remember whether i formatted this space or not.
Let me know how I can regain this space.

System Spec

Processor: AMD phenom $X 9950
Motherboard : gigabyte MA790GP-DS4h
HArd Drive: Seagate 500GB SATA

thanks

---

### Post by cdtech on 2008-11-15
Can you post the output of:
```
sudo fdisk -l
```
You may need to use the "gparted" application to format those.

---

### Post by linx-fan on 2008-11-15
Hi,
Ic ould see the partitions now. output is here
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac7e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24899   200001186   83  Linux
/dev/sda2           24900       43573   149998905   83  Linux
/dev/sda3           43574       43822     2000092+  82  Linux swap / Solaris
/dev/sda4           43823       60801   136383817+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49f449f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6276    50411938+  83  Linux
/dev/sdb2            6277       10442    33459206+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb3           10442       19058    69205185    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb4           19058       19457     3211960+   7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sdb5            6526       10442    31456561+  83  Linux
/dev/sdb6            6277        6525     2000061   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf64ef64e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3243    26043885    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2            3243        6506    26215528+   7  HPFS/NTFS
/dev/sdc3            6507        9729    25888747+   7  HPFS/NTFS

I will use gparted and check

---

### Post by linx-fan on 2008-11-15
> **cdtech said:**
> Can you post the output of:
```
sudo fdisk -l
```
You may need to use the "gparted" application to format those.

Thanks a lot.
gparted did a wonder

---

### Post by cdtech on 2008-11-15
congrats.....:guitar:

---

### Post by petterwr on 2009-10-31
Hope someone is able to help me too with this issue. Here is my output for sudo fdisk -l:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4a4e4a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/sda2   *        1217        2432     9767520    7  HPFS/NTFS
/dev/sda3            2433       14267    95064637+   5  Extended
/dev/sda4            7297       14267    55994526    c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeffce093

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdc: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders
Units = cylinders of 16002 * 512 = 8193024 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1955    15641929    c  W95 FAT32 (LBA)

When I run sudo gparted I got the following message:

======================
libparted : 1.8.8
======================
Can't have overlapping partitions.

And in the main window the whole disk is just one gray block.

Background info:
I used to have 5 partitions on my hd, one for me, one for my partner, one win 2k, one win xp and one as a common file archive.

Decided to get ubuntu on it and merged all except for the archive and win xp. Now ubuntu worked fine but I couldnt boot xp. So i used som old disktools I had laying around and got a warning that I should never use the tool again, serious error. After that the Ubuntu boot cd couldnt find any partitions.
After that nothing worked, so I reinstalled xp and it could still see and access the archive and the old xp partition, but nothing else. Thats where I am now.

Wondering if I should just backup all essentials and then reformat the whole harddisk.. anyone got any other suggestions?

---

