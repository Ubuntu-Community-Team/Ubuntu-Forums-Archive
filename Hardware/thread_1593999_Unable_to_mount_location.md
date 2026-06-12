---
title: "Unable to mount location"
date: 2010-10-11
forum: Hardware
---

### Post by raw157 on 2010-10-11
Alright, so I'm dual booting between 7 and Ubuntu 10.10

I have a 1 TB drive, with movies and music on it. I cannot access it inside Ubuntu. 
I get...

[B]Unable to mount location

Error mounting: mount exited with exit code 12: Failed to read last sector (204799): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

[/B]Ideas?
Thanks,
raw

---

### Post by efflandt on 2010-10-11
Are you sure that sda1 is your Win7 partition?  Many Win7 systems have a boot partition first.  On my Dell system sda1 is a utility partition, sda2 is the recovery partition originally marked as the boot partition, and Win7 is actually on sda3.

What is the output of **sudo fdisk -l** (small L)?

---

### Post by raw157 on 2010-10-11
And no I'm not positive, I'm pretty new to ubuntu land

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf07cca6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976761528+  42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41e541e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16908   135807543+   7  HPFS/NTFS
/dev/sdb2           16908       19458    20481025    5  Extended
/dev/sdb5           16908       17394     3905536   82  Linux swap / Solaris
/dev/sdb6           17394       18610     9764864   83  Linux
/dev/sdb7           18610       19458     6808576   83  Linux

---

### Post by raw157 on 2010-10-13
Bumpy

---

### Post by redwaldmcmanus on 2010-10-13
Hello!
That seems to be saying your 1tb is a "Smart File System", which I've not come across before.

Under windows, how does it say your disk is formatted?
You can view this in my computer, right clicking on your drive and looking in the properties

---

### Post by raw157 on 2010-10-13
It's formated as NTFS.

It's a WD green drive. When I installed it inside windows it gave me some issues, and the bios would recognize it, but "My Computer" wouldn't. I've got that resolved, but now onto this issue.

---

### Post by raw157 on 2010-10-16
bump.
Ideas?

---

### Post by raw157 on 2010-10-24
I really would like to get this fixed.. anyone?

Bump.. one last time.

---

