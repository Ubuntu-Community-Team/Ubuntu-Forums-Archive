---
title: "Can't mount NTFS partation"
date: 2009-03-16
forum: Hardware
---

### Post by gujumax on 2009-03-16
I"m trying to mount my NTFS partation and it keep saying its corrupt.  Is there anything else I can try beside mount and ntfsfix.  I havent tried chkdsk yet because users say it could be dangerous.

root@earth:/etc/network# mount -t ntfs /dev/sdc1 /backup -o force
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

root@earth:/etc/network# ntfsfix /dev/sdc1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

fdisk -l

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0e068b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS


Did I really lose this drive?

---

### Post by ddrichardson on 2009-03-17
If you have a windows CD then yes, use it to boot to a repair console and:```
fixboot
fixmbr
chkdsk /f c:
```
Or try the utilities with [system rescue cd]("http://www.sysresccd.org/Main_Page").

---

### Post by colau on 2009-06-27
> **gujumax said:**
> I"m trying to mount my NTFS partation and it keep saying its corrupt.  Is there anything else I can try beside mount and ntfsfix.  I havent tried chkdsk yet because users say it could be dangerous.

root@earth:/etc/network# mount -t ntfs /dev/sdc1 /backup -o force
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

root@earth:/etc/network# ntfsfix /dev/sdc1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

fdisk -l

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0e068b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS


Did I really lose this drive?

[ntfs-3g]("http://ubuntuforums.org/showthread.php?t=1168719&highlight=mount+ntfs")
See post 10.

---

