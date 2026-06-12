---
title: "Trouble mounting HPFS/NTFS drive from USB Adapter"
date: 2010-03-05
forum: Hardware
---

### Post by skr0gg on 2010-03-05
Can't mount HPFS/NTFS drive.

Commands read:

skr0gg@MyNE-01:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f41a506

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15918   127861303+   7  HPFS/NTFS
/dev/sda2           15919       28984   104952645    5  Extended
/dev/sda5           15919       28447   100639161   83  Linux
/dev/sda6           28448       28984     4313421   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2173bf3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           1        9729    78148161    7  HPFS/NTFS
skr0gg@MyNE-01:~$ sudo mount -s -t ntfs /dev/sdc2 /media/sdc2
NTFS signature is missing.
Failed to mount '/dev/sdc2': Invalid argument
The device '/dev/sdc2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Any help is greatly appreciated.

---

### Post by skr0gg on 2010-03-05
Tried the following: (with responses)

skr0gg@MyNE-01:~$ sudo mkdir /media/sdc
skr0gg@MyNE-01:~$ sudo mount -s -t ntfs /dev/sdc /media/sdc
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
skr0gg@MyNE-01:~$ sudo mount -t ntfs /dev/sdc /media/sdc
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
skr0gg@MyNE-01:~$ sudo mount -t hpfs/ntfs /dev/sdc /media/sdc
mount: unknown filesystem type 'hpfs/ntfs'
skr0gg@MyNE-01:~$ sudo mount -t hpfs /dev/sdc /media/sdc
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

skr0gg@MyNE-01:~$ sudo mount -t ntfsprog /dev/sdc /media/sdc
mount: unknown filesystem type 'ntfsprog'
skr0gg@MyNE-01:~$ sudo mount -t ntfs-3g /dev/sdc /media/sdc
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
skr0gg@MyNE-01:~$ sudo mount -t ext /dev/sdc /media/sdc
mount: unknown filesystem type 'ext'

---

### Post by coffeecat on 2010-03-05
> **skr0gg said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           1        9729    78148161    7  HPFS/NTFS
skr0gg@MyNE-01:~$ sudo mount -s -t ntfs /dev/sdc2 /media/sdc2
**NTFS signature is missing.**
Failed to mount '/dev/sdc2': Invalid argument
**The device '/dev/sdc2' doesn't seem to have a valid NTFS.**
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


I've taken the liberty of emboldening the relevant bits. It looks as though there's something wrong with the filesystem. First step would be to do a chkdsk on that drive from Windows. There are Linux tools for NTFS, but NTFS is a Microsoft filesystem and it's best to use Windows for diagnosis and repair of NTFS.

Interesting that the one and only partition is sdc2. What happened to partition #1?

---

### Post by skr0gg on 2010-03-05
Thank you...  I tried loading with Win and the drive won't mount there either, but if I boot from the drive it tells me to run chkdsk...  I would, if I could get it to mount as slave.  BTW it's a laptop drive.  Anyway, it's neither here nor there anymore.  Higher took it and is going to rebuild...  Thanks and Blessed Be.

---

