---
title: "How to mount a Windows 2nd (non-boot) SSD as 2nd drive on 14.04"
date: 2015-04-17
forum: Hardware
---

### Post by aplonis2 on 2015-04-17
So I have a Dell M6700 in which to swap OS from Win7 to Ubuntu all I do is swap the main drive (easy to do). But as Win7 there is also a 2nd SSD which I'd like also to use when booted as Linux. Here is my info on my drives. I'm presuming the last listed is the SSD I want to mount. I've tried a few things from other how-to docs peripherally related to no effect. The issues seems to be the system "HPFS/NTFS/exFAT". But I'm just guessing.

$ sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00072bd5
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   943482879   471740416   83  Linux
/dev/sda2       943484926   976771071    16643073    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       943484928   976771071    16643072   82  Linux swap / Solaris
 
Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f87a0e5
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   250066943   125032448    7  HPFS/NTFS/exFAT

$

...so then I tried this...

$ apt-get install --reinstall exfat-fuse exfat-utils

...and after that this...

$ mount -t exfat /dev/sdb1 /media/exfat
FUSE exfat 1.0.1
ERROR: exFAT file system is not found.
$

...which clearly did not work either. So, what to do?

---

### Post by weatherman2 on 2015-04-17
What is the format of your Windows partition (/dev/sdb1) ?  Are you sure it is exFat and not NTFS?  NTFS is the default filesystem for Windows disks.

If the Windows partition is NTFS, then mount it like this:

```

sudo mkdir /media/ntfs
sudo mount /dev/sdb1 /media/ntfs

```

The mount command should be able to detect the NTFS format automatically and not require the -t flag.  I almost never use it.

---

### Post by aplonis2 on 2015-04-17
> **weatherman2 said:**
> What is the format of your Windows partition (/dev/sdb1) ?  Are you sure it is exFat and not NTFS?  NTFS is the default filesystem for Windows disks.

If the Windows partition is NTFS, then mount it like this:

```

sudo mkdir /media/ntfs
sudo mount /dev/sdb1 /media/ntfs

```

The mount command should be able to detect the NTFS format automatically and not require the -t flag.  I almost never use it.

Okay, tried that...didn't work. Like so...

[FONT=courier new]$ sudo mount /dev/sdb1 /media/ntfs
mount: you must specify the filesystem type
$ sudo mount -t ntfs /dev/sdb1 /media/ntfs
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
$[/FONT]

...and, then did like asked as sda not sda1 but was also no go.

---

### Post by oldfred on 2015-04-17
Partition table says NTFS, but NTFS partitions whether bootable or not also have more boot/partition info in the partition boot sector(PBR). And the partition start & size much match the partition table.
Also partition must not have hibernated nor chkdsk flags set to be able to mount with the Linux NTFS driver.
Does Windows show it as RAW? Then the PBR is corrupted. NTFS does have a backup PBR called BS in testdisk which you can restore. Or you can use a Windows repair flash drive to run bootsect.exe.

Otherwise it just may need chkdsk which you can only run from Windows, best just to use a Windows repair flash drive or restore a Windows or move drive to a working Windows system.

---

### Post by aplonis2 on 2015-04-17
Okay, I've discovered the problem. This is a work laptop of which I write. When booted to Windows, all the drives (both C and D) are encrypted by McAfee Endpoint Encryption (which is kind of like TrueCrypt). So that is why Linux can't make sense of the second drive. I'll leave this post as a lesson for others. Thanks to you all for your assistance in my little adventure here.

---

