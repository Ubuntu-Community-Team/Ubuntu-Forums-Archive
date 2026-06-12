---
title: "big external har disk - impossible to mount"
date: 2011-01-05
forum: Hardware
---

### Post by andreaconsole on 2011-01-05
It's a 2TB WesternDigital HD. It works fine on Windows7, but when I try to mount on kubuntu 10.10 it says:
 
"org.freedesktop.Hal.Device.Volume.UnknownFailure: Failed to read last sector (3907027119): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup yet, or it was not setup correctly (e.g. by not using mdadm --build ...), or a wrong device is tried to be mounted, or the partition table is corrupt (partition is smaller than NTFS), or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/sdb1': Invalid argument The device '/dev/sdb1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"

I tried ntfsfix, but it didn't report any error
I tried manual mount (sudo mount /dev/sdb1 /mnt/temp) with same result
this is the output of fdisk -l:

"Disco /dev/sdb: 2000.4 GB, 2000396746752 byte
255 testine, 63 settori/tracce, 243201 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x0003c302

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953513560    7  HPFS/NTFS
"
any suggestions?
thanks

---

### Post by andreaconsole on 2011-01-06
I made a scan with windows7 chkdsk /f. The result was:
"The second ntfs boot sector is unwriteable".
Formatting the drive is the one solution I have?

---

### Post by Fafler on 2011-01-06
That or do a complete surface scan. I don't know if ntfsfix can do that in conjunction with badblocks. Remember to do the non destructive write test, otherwise it won't remap bad sectors automatically.

But if you have to possibility to reformat, it's probably the best solution.

---

### Post by andreaconsole on 2011-01-06
thanks for your answer!
Even if it's not an ubuntu topic anymore, to help anyone could have the same problem, this is the solution that worked for me:
(I found it on an other forum, I don't remember where)

using window7:

1) make a new partition on the hd, I made a 1GB one
2) format the partition ntfs
3) chkdsk /f the new and the old partition: they should not have error anymore
4) delete new partition and extend the old one to the whole hd
5) chkdsk /f again and everything should be ok!

---

