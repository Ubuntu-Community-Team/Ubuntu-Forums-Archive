---
title: "Problem Mounting HDD on Linux Desktop 13.10"
date: 2013-10-29
forum: Hardware
---

### Post by jamie_starr2 on 2013-10-29
Hey guys, I've only just installed Linux 13.10 today, and I'm brand new to the OS. I keep getting a problem with my secondary HDD.

 The facts:
 128GB SSD Partition
 Windows on 60GB
 Linux on 30GB
 3GB spare for w/e.

 I then have a 1TB Western Digital Caviar Blue dynamic HDD, partitioned into 3 main sections (but they're a bit split up due to a repartitioning issue - see photo)

 The 'Stuff' partition I can access from Linux, but the 'Games' and 'Spare' partitions give me this message every time I try and mount:

[COLOR=#003366]Error mounting system-managed device /dev/sdb2: Command-line `mount "/mnt/622CFFFC2CFFC8D5"' exited with non-zero exit status 12: Failed to read last sector (590368767): Invalid argument[/COLOR]
[COLOR=#003366]HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,[/COLOR]
[COLOR=#003366]   or it was not setup correctly (e.g. by not using mdadm --build ...),[/COLOR]
[COLOR=#003366]   or a wrong device is tried to be mounted,[/COLOR]
[COLOR=#003366]   or the partition table is corrupt (partition is smaller than NTFS),[/COLOR]
[COLOR=#003366]   or the NTFS boot sector is corrupt (NTFS size is not valid).[/COLOR]
[COLOR=#003366]Failed to mount '/dev/sdb2': Invalid argument[/COLOR]
[COLOR=#003366]The device '/dev/sdb2' doesn't seem to have a valid NTFS.[/COLOR]
[COLOR=#003366]Maybe the wrong device is used? Or the whole disk instead of a[/COLOR]
[COLOR=#003366]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]
 Being a complete newbies, I have no idea what to do, can you help?

---

### Post by jamie_starr2 on 2013-10-29
[http://www.techspot.com/community/attachments/untitled-png.77296/](http://www.techspot.com/community/attachments/untitled-png.77296/)

---

