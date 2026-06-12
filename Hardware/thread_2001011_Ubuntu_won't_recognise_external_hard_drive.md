---
title: "Ubuntu won't recognise external hard drive"
date: 2012-06-10
forum: Hardware
---

### Post by Th3Blaze on 2012-06-10
The format is unknown in GParted, so I'm hoping I just need to install something to fix it.
Anyway, here's some info.

Fdisk -l
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029ff5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *  1045463040  1250263039   102400000   83  Linux
/dev/sda2            2046  1045463039   522730497    5  Extended
/dev/sda5            2048    23437311    11717632   82  Linux swap / Solaris
/dev/sda6        23439360  1045463039   511011840   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe562914b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   234438655   117218304    6  FAT16

```

lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 1bcf:0c31 Sunplus Innovation Technology Inc. Serial-ATA bridge
Bus 002 Device 004: ID 05ac:1003 Apple, Inc. Hub in Pro Keyboard [Mitsumi, A1048]
Bus 002 Device 005: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 002 Device 006: ID 05ac:020c Apple, Inc. Extended Keyboard [Mitsumi]

```


dmesg | tail
```
[  464.865507] sd 8:0:0:0: [sdb] Write Protect is off
[  464.865515] sd 8:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  464.872509] sd 8:0:0:0: [sdb] No Caching mode page present
[  464.872516] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  464.887878] sd 8:0:0:0: [sdb] No Caching mode page present
[  464.887885] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  464.912249]  sdb: sdb1
[  464.932994] sd 8:0:0:0: [sdb] No Caching mode page present
[  464.933002] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  464.933009] sd 8:0:0:0: [sdb] Attached SCSI disk

```

The device I'm looking for(the external hard drive) is sdb1 and the "Sunplus Innovation Technology Inc. Serial-ATA bridge"

I have worked out that it is something like this ```
Code:
sudo mkdir /media/drive

Code:
sudo mount -t vfat /dev/sdb1 /media/drive 
```

But it comes up with the error ```
sudo mount -t vfat /dev/sdb1 /media/drive
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

So I think I just need to find out what to put instead of the vfat, "apparently" the drive is FAT16, but I don't see why it's working. So does anyone know the option for FAT16 instead of FAT32 ?

Just need help with this, then I think that's it ```
sudo /usr/bin/udisks --mount /dev/sdb1
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
It contains alot of important information, and I REALLY, don't want to lose it. Any advice ?

---

### Post by ahallubuntu on 2012-06-10
Can we assume you've already tried it without any option, letting the mounter figure out the format:

sudo mount /dev/sdb1 /mnt 

?

FYI, this has nothing to do with your problem, but don't use /media to mount stuff manually - that's where Nautilus mounts stuff.  Use /mnt instead.

---

### Post by sudodus on 2012-06-10
Maybe there is the exFAT file system on the USB drive.

- Can you check that in a Windows computer?

- You can try according to this link
[[COLOR="Red"]_http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm_[/COLOR]]("http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm")

---

### Post by Th3Blaze on 2012-06-10
```
mary@Mercury:~$ sudo mount /dev/sdb1 /mnt 
[sudo] password for mary: 
mount: you must specify the filesystem type

```

Nope no use there.

I think the problem is where the vfat part is. I should be putting something else there instead (sudo mount -t vfat /dev/sdb1 /media/drive)

And i'm doing that now sudodus

---

### Post by Th3Blaze on 2012-06-10
Nope, no luck. The only thing I have is the vfat thing, so please can everyone jog their memory different inputs for that bit. Or anything at all that will mount the drive. When I boot up, the loading screen says that their is an error mountin the device, but I think this is that it thinks the device is an unknownformat, whn it is fat16

---

### Post by Th3Blaze on 2012-06-10
Any help anyone?Desperate to get this fixed..

---

### Post by Th3Blaze on 2012-06-10
[IMG]http://i.imgur.com/TJGVv.jpg[/IMG]

Sorry for the spamming, but I have a limited amount of time to complete this, so really need to press on with this as fast as I can. Anyone have any knowledge at all on mounting options such as these.

---

### Post by sudodus on 2012-06-11
> **sudodus said:**
> Maybe there is the exFAT file system on the USB drive.

- Can you check that in a Windows computer?

- You can try according to this link
[[COLOR="Red"]_http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm_[/COLOR]]("http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm")

exFAT is *not* the same as vFAT!

- Can you borrow a Windows computer to see if it can identify and mount the file system on your external drive. Did you check if the drive has the exFAT file system?

- Did you try to enable exFAT according to the link?

---

### Post by roelforg on 2012-06-11
Try without the -t vfat
This would cause mount to try to find a suitable fs on it's own, might work.
But FAT16 on a 120gb drive? Wasn't there some sort of limit preventing that?

---

