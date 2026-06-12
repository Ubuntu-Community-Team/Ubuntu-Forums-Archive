---
title: "Can't access raid partition"
date: 2014-06-30
forum: Hardware
---

### Post by geoffmen on 2014-06-30
I have these two disks with RAID arrays I need to recover important data from. It's from a LaCie NAS and its fileserver is *nix-based. I have been trying to load the data partitions to recover deleted files, I just can't get the partitions to mount. I knew nothing of RAID arrays two days ago and have been struggling for several hours reading stuff all over the place trying to troubleshoot this.

Here are some outputs that might explain where I'm at:


[FONT=system]**[B]$ ****disktype /dev/sdb2**

[/B]--- /dev/sdb2
disktype: Can't open /dev/sdb2: Permission denied
[B]
**$ sudo disktype /dev/sdb2**
[/B]
--- /dev/sdb2
Block device, size 929.6 GiB (998145953280 bytes)
Linux RAID disk, version 0.90.0
  RAID0 set using 2 regular 0 spare disks
  RAID set UUID A1DB68CE-2D6B-D26F-FF38-2745F5635918 (Reserved)
XFS file system, version 4
  Volume name ""
  UUID F3686720-B310-4DA4-8A30-95D45D0E1B9F (DCE, v4)
  Volume size 1.816 TiB (1996291702784 bytes, 487375904 blocks of 4 KiB)
[B]
$ sudo mdadm --examine /dev/sdb2[/B]
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : ce68dba1:6fd26b2d:452738ff:185963f5
  Creation Time : Wed Dec 31 19:00:22 1969
     Raid Level : raid0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 4

    Update Time : Mon Oct  8 13:05:35 2012
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 955b3c07 - correct
         Events : 85

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2

**$ sudo mdadm --examine /dev/sdc2**
/dev/sdc2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : ce68dba1:6fd26b2d:452738ff:185963f5
  Creation Time : Wed Dec 31 19:00:22 1969
     Raid Level : raid0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 4

    Update Time : Mon Oct  8 13:05:35 2012
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 955b3c19 - correct
         Events : 85

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2

**$ sudo disktype /dev/sdc2**
--- /dev/sdc2
Block device, size 929.6 GiB (998145953280 bytes)
Linux RAID disk, version 0.90.0
  RAID0 set using 2 regular 0 spare disks
  RAID set UUID A1DB68CE-2D6B-D26F-FF38-2745F5635918 (Reserved)**$ sudo mount -t xfs -o ro /dev/sdb2 /mnt/raid/**
mount: /dev/sdb2: can't read superblock

**$ sudo mount -t xfs -o ro /dev/sdc2 /mnt/raid/**
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**$ dmesg | tail**
[ 1941.553136] sdb2: rw=32, want=3899007232, limit=1949503815
[ 1941.553148] XFS (sdb2): Mounting Filesystem
[ 1941.553218] attempt to access beyond end of device
[ 1941.553219] sdb2: rw=32, want=1949505665, limit=1949503815
[ 1941.553220] XFS (sdb2): metadata I/O error: block 0x74331880 ("xlog_bread_noalign") error 5 numblks 1
[ 1941.553222] XFS (sdb2): empty log check failed
[ 1941.553223] XFS (sdb2): log mount/recovery failed: error 5
[ 1941.553242] XFS (sdb2): log mount failed
[ 2405.020317] XFS (sdc2): bad magic number
[ 2405.020334] XFS (sdc2): SB validate failed with error 22.[/FONT]

---

### Post by Silkefot on 2014-07-01
There was a good articale in Linux Journal  [Recovery of RAID and LVM2 Volumes | Linux Journal]("http://www.linuxjournal.com/article/8874") on the second page they are doing the raid recovery. I have the same problem only on my system the --examine doesn't give anything...

---

