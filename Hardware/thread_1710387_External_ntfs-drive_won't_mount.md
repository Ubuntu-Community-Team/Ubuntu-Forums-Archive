---
title: "External ntfs-drive won't mount"
date: 2011-03-19
forum: Hardware
---

### Post by oscar2296 on 2011-03-19
I just installed Ubuntu 10.10 64bit from Windows 7, and the most important part of my computer won't work. This is the error message I get: 

> Error mounting: mount exited with exit code 12: Failed to read last sector (1953523119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Now, I've run a chkdsk /f already on another computer, and I tried ntfsfix. I can find no other tips by searching. Please help me, I'm desperate to get this drive working, my life is on it! :confused:

EDIT: Followed advice from this thread [http://ubuntuforums.org/showpost.php?p=8515846&postcount=5](http://ubuntuforums.org/showpost.php?p=8515846&postcount=5)

---

