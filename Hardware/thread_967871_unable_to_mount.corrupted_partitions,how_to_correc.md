---
title: "unable to mount.corrupted partitions,how to correct?"
date: 2008-11-02
forum: Hardware
---

### Post by ramthegreatcv on 2008-11-02
[SIZE=3]**Output of fdisk -l**[/SIZE]

```
[ram@ubuntu:~$ sudo fdisk -l
[sudo] password for ram: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3270    26218080    7  HPFS/NTFS
/dev/sda3           14351       14593     1951897+  82  Linux swap / Solaris
/dev/sda4            3271       14350    89000100    f  W95 Ext'd (LBA)
/dev/sda5            3271       12042    70461058+   7  HPFS/NTFS
/dev/sda6           12043       13190     9216000   83  Linux
/dev/sda7           14066       14350     2289231    b  W95 FAT32
/dev/sda8           13191       14065     7028406    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/dm-0: 49 MB, 49319424 bytes
74 heads, 14 sectors/track, 92 cylinders
Units = cylinders of 1036 * 512 = 530432 bytes
Disk identifier: 0x45440072

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   ?           1           1           0   42  SFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 73, 15) logical=(0, 0, 1)
Partition 1 has different physical/logical endings:
     phys=(256, 73, 14) logical=(4145721, 24, 4)

Disk /dev/dm-1: 26.8 GB, 26847313920 bytes
255 heads, 63 sectors/track, 3264 cylinders
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

Disk /dev/dm-2: 72.1 GB, 72152123904 bytes
255 heads, 63 sectors/track, 8771 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 2344 MB, 2344172544 bytes
255 heads, 63 sectors/track, 284 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System

Disk /dev/dm-4: 7197 MB, 7197087744 bytes
255 heads, 63 sectors/track, 874 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-4p1   ?       48437      119493   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(48436, 183, 40)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(119492, 104, 7)
Partition 1 does not end on cylinder boundary.
/dev/dm-4p2   ?       10501      131013   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10500, 111, 30)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(131012, 158, 28)
Partition 2 does not end on cylinder boundary.
/dev/dm-4p3   ?      116395      236907   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(116394, 188, 12)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(236906, 234, 25)
Partition 3 does not end on cylinder boundary.
/dev/dm-4p4   ?      179626      179629       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(179625, 87, 47)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(179628, 203, 42)
Partition 4 does not end on cylinder boundary.
Partition table entries are not in disk order
```[SIZE=3]**my /etc/fstab**[/SIZE]

```
ram@ubuntu:~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ac8b6125-ddb6-4f99-859c-e3ef2a8e2a91 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d25fbb5d-a444-4a2e-adf1-fb8299615f58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5     /media/Data    ntfs-3g defaults 0 0
/dev/sda2    /media/Windows    ntfs-3g defaults 0 0
/dev/sda7    /media/Backup    vfat defaults 0 0
/dev/sda8    /media/Extra    vfat defaults 0 0


```

---

### Post by thestig_992 on 2008-11-03
How did the partitions become corrupted?
I just had a problem where windows screwed up my partitions, so it had the same error when fdisk doesnt think that its a partition tbale. (solved this litterally minutes ago)
I couldnt see any data, then i deleted all the weird partitions and created one big one. *NOTE: I do not recommend doing this, because i didnt really know what i was doing. Check with someone more knowledgeable than me first. Just giving out ideas...*

---

### Post by feng85jie on 2008-11-03
[Air Filter](http://www.chinafengjie.com/air-filter/)Ruian Fengjie Auto parts manufacture CO.,LTD is a company specilized in Filter and Filter components service.

---

### Post by ramthegreatcv on 2008-11-03
yeah its true,windows ntfs has some problem(thats what i got when i visited their support site).it occurs when there is some data transfer.

its suggested that i run chkdsk,but i has not been able to rectify my problem .i think its because windows partition itself is corrupt.
but i can't understand why fat32 partitions (that are not corrupt) are not mounting.

---

### Post by ramthegreatcv on 2008-11-04
[LIST=1]
[*]my bootable disks are not able to boot(both XP,ubuntu).even though the dvd drive and CDs themselves are working fine when checked in an OS(both XP,ubuntu).
[*]Ubuntu (or for that matter mandrake) when run from an USB drive are able to detect all my drives and mount them.
[*]Ubuntu when run from harddisk still has the problem
[*]Windows XP is able to mount all the drives.
[/LIST]

---

