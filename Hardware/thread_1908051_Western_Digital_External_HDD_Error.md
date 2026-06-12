---
title: "Western Digital External HDD Error"
date: 2012-01-12
forum: Hardware
---

### Post by qd50 on 2012-01-12
I'm pretty new to Ubuntu and have a problem connecting my 2Tb Western Digital hard drive via USB to my laptop running Ubuntu 11.10. I keep getting the error message:

[SIZE="1"]Error mounting: mount exited with exit code 12: Failed to read last sector (3907027119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/SIZE]

The hard drive contains my media and works fine with my desktop running Windows 7. Other posts on here regarding WD HDD's recommend formatting the drive - is there a fix that allows me to keep my data?

---

