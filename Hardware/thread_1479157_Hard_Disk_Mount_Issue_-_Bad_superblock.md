---
title: "Hard Disk Mount Issue - Bad superblock"
date: 2010-05-10
forum: Hardware
---

### Post by ZootHornRollo on 2010-05-10
Hi,

I am trying to mount a second HD but am running into problems :

I am trying to mount /dev/sdb1 as /media/backup

```
musicbox@musicbox-desktop:~$ sudo fdisk -l
[sudo] password for musicbox: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be48b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        3040     9767520   83  Linux
/dev/sda3           60607       60801     1566337+  82  Linux swap / Solaris
/dev/sda4            3041       60606   462398895   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001fb5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 1002 MB, 1002438656 bytes
65 heads, 32 sectors/track, 941 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         942      978928    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 64, 32) logical=(941, 18, 32)

```

```
musicbox@musicbox-desktop:~$ sudo mkdir /media/backup
musicbox@musicbox-desktop:~$ sudo mount /dev/sdb1 /media/backup
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
musicbox@musicbox-desktop:~$ dumpe2fs /dev/sdb | grep superblock
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Permission denied while trying to open /dev/sdb
Couldn't find valid filesystem [COLOR="Red"]superblock[/COLOR].

```

---

