---
title: "Mounting NTFS partition"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by yelloguy on 2009-10-26
I have Ubuntu installed in a 20GB partition on a 160 GB hard disk.  Unfortunately, the other 140GB (or so) has a bunch of files in an extended NTFS partition that I am unable to mount.  fdisk -l /dev/sdb returns this:

```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00c8c3d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  82  Linux swap / Solaris
/dev/sdb2            2551       19458   135805478    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb3             123        2550    19502910   83  Linux
/dev/sdb5            2551       19458   135805477+   7  HPFS/NTFS

Partition table entries are not in disk order

```
Can anyone help me mount the partition?  Thanks.

---

### Post by sisco311 on 2009-10-26
If you prefer the GUI to mount it:
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

If you want to mount it from the cli:

First you need create a mount point (an empty directory)
```
sudo mkdir /media/data
```
The mount it:
```
sudo mount -t ntfs -o defaults,dmask=002,umask=113,gid=46 /dev/sdb5 /media/data
```
this will mount the partition with read/write privileges for users in the plugdev group(the first user created on the system is in the group by default)

if you want to mount it at boot time, edit /etc/fstab and append it with:
```
UUID=<uuid of the partition> /media/data ntfs defaults,dmask=002,umask=113,gid=46 0 0
```

to get the UUID:
```
sudo blkid /dev/sdb5
```

---

### Post by yelloguy on 2009-10-26
Thanks so much sisco for the quick reply.  Here is what I get when I try to mount:
```

ntfs-3g: Failed to access volume '/dev/sdb5': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org

```

---

### Post by sisco311 on 2009-10-26
please post the output of:
```
sudo fdisk -l
```

and 

```
ls -al /dev/sd*
```

---

### Post by yelloguy on 2009-10-26
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d35715a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2024    16257748+   7  HPFS/NTFS
/dev/sda2            2025       19457   140030572+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00c8c3d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  82  Linux swap / Solaris
/dev/sdb2            2551       19458   135805478    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sdb3             123        2550    19502910   83  Linux
/dev/sdb5            2551       19458   135805477+   7  HPFS/NTFS

Partition table entries are not in disk order

```


```

brw-rw---- 1 root disk 8,  0 2009-10-08 14:09 /dev/sda
brw-rw---- 1 root disk 8,  1 2009-10-08 13:28 /dev/sda1
brw-rw---- 1 root disk 8,  2 2009-10-08 14:20 /dev/sda2
brw-rw---- 1 root disk 8, 16 2009-10-08 08:21 /dev/sdb
brw-rw---- 1 root disk 8, 17 2009-10-08 08:21 /dev/sdb1
brw-rw---- 1 root disk 8, 18 2009-10-26 14:50 /dev/sdb2
brw-rw---- 1 root disk 8, 19 2009-10-08 08:21 /dev/sdb3

```

---

### Post by yelloguy on 2009-10-27
Anyone?

---

### Post by supi007 on 2009-10-27
Hi All,

I have a problem I cannot mount my hard disk.
The disk is on the USB interface. I have seen info with lsusb (here you are):
```
Bus 002 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```How can I find info about my disk in /dev folder? How can I mount it?

supesz
(newby)

:KS

---

### Post by sisco311 on 2009-10-27
> **supi007 said:**
> Hi All,

I have a problem I cannot mount my hard disk.
The disk is on the USB interface. I have seen info with lsusb (here you are):
```
Bus 002 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```How can I find info about my disk in /dev folder? How can I mount it?

supesz
(newby)

:KS

Hi!

To get a better help, please start a new thread in the Absolute Beginners Talk (sub)forum:

[http://ubuntuforums.org/forumdisplay.php?f=326]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by sisco311 on 2009-10-27
> **yelloguy said:**
> Anyone?

I have no idea why /dev/sdb5 is not created.

maybe dmesg will show you the error:
```
dmesg
```
or 
```
dmesg | grep sdb
```

If you are dual booting try to check the partition for errors in Windows.

---

### Post by yelloguy on 2009-10-28
Thanks again.  Here is the output from dmesg|grep sdb command

```

[    1.198195] sd 1:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.198294] sd 1:0:1:0: [sdb] Write Protect is off
[    1.198301] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.198351] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.198630]  sdb: sda1 sda2
[    1.210050]  sdb1 sdb2 < sdb5 > sdb3
[    1.220252] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.979911] EXT4-fs (sdb3): barriers enabled
[    2.995097] kjournald2 starting: pid 281, dev sdb3:8, commit interval 5 seconds
[    2.995134] EXT4-fs (sdb3): delayed allocation enabled
[    2.997035] EXT4-fs (sdb3): mounted filesystem with ordered data mode
[   18.609104] Adding 979924k swap on /dev/sdb1.  Priority:-1 extents:1 across:979924k 
[   19.122515] EXT4-fs (sdb3): internal journal on sdb3:8

```

By the way, it was a headless box so I decided to bring it out and hook it up to a monitor yesterday and boot up Windows.  After I did that, I could access the partition and copy over the files to an external drive.

Thankfully now I don't need to do this anymore.  Maybe I will just repartition the HDD and reuse the space.  Thanks very much for your help again.

---

