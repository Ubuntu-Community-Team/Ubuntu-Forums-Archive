---
title: "Mounting Existing NTFS Raid Device with dmraid"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by Bozni on 2007-10-18
Hello all.

I'm new to Ubuntu and am in need of assistance. 

I'm running Gutsy on an IDE 40gb HD and Windows XP on 2 250gb SATA drives using an Intel Software RAID.  

I've been reading all I can about getting the RAID mounted in Ubuntu but haven't had much luck.

_Here's my fdisk readout:_

bozni@bozni-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5f8d5f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x058a0589

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488392033+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77f5156b

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/dm-0: 500.1 GB, 500118061056 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x058a0589

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       60802   488392033+   7  HPFS/NTFS

Disk /dev/dm-1: 500.1 GB, 500113442304 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
 

_Here's my dmraid raid device readout:_

bozni@bozni-desktop:~$ sudo dmraid -r
/dev/sdb: isw, "isw_jbifjjgg", GROUP, ok, 488397166 sectors, data@ 0
/dev/sdc: isw, "isw_jbifjjgg", GROUP, ok, 488397166 sectors, data@ 0


_I'm able to activate the device in the /dev/mapper directory: _

bozni@bozni-desktop:~$ sudo dmraid -ay -v
RAID set "isw_jbifjjgg_RAID_Volume0" already active
INFO: Activating GROUP RAID set "isw_jbifjjgg"
RAID set "isw_jbifjjgg_RAID_Volume01" already active
INFO: Activating partition RAID set "isw_jbifjjgg_RAID_Volume01"
bozni@bozni-desktop:~$ 

_However, when I attempt to mount, this happens:_

bozni@bozni-desktop:~$ sudo mount dev/mapper/isw_jbifjjgg_RAID_Volume0 /media/sdb1
mount: special device dev/mapper/isw_jbifjjgg_RAID_Volume0 does not exist

I KNOW that file exists but for some reason it is saying it doesn't.  I'm very confused and very frustrated and would appreciate whatever help I can get.

---

### Post by Bozni on 2007-10-18
I'm pulling my hair out here!!!  Anyone know anything about this at all?

---

### Post by Bozni on 2007-10-18
Please.....?

---

### Post by psusi on 2007-10-18
You are missing the leading /

---

