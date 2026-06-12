---
title: "How do I get Ubuntu 11.04 to recognise my external hard drive"
date: 2011-05-17
forum: Hardware
---

### Post by firefox834 on 2011-05-17
**Its on NTFS, all my flash drives and mobile phones connect instantly**

---

### Post by doas777 on 2011-05-17
with the drive plugged in, please post back the output of 
```
sudo fdisk -l
```

---

### Post by firefox834 on 2011-05-17
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c3e49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18693   150145024   83  Linux
/dev/sda2           18693       19458     6142977    5  Extended
/dev/sda5           18693       19458     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16d3d9c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

---

### Post by doas777 on 2011-05-17
I'm guessing that /dev/sdb1 is your external?  a 320GB NTFS partition?


try this:
```
sudo mkdir /media/external
sudo mount -t ntfs-3g /dev/sdb1 /media/external

```after that, does your drive appear in /media/external ?

this may be of some use to you:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by firefox834 on 2011-05-17
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by doas777 on 2011-05-17
> **firefox834 said:**
> Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
you can try the command with /dev/sdb as the error message suggested, but my guess is that that won't work either.

how long has it been since you ran chkdsk /f on this volume from a windows system? i'd try it and see if that doesnt clear up your issue in ubuntu.

---

