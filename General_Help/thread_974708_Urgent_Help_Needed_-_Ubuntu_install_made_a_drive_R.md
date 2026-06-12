---
title: "Urgent Help Needed - Ubuntu install made a drive RAW??"
date: 2008-11-07
forum: General Help
---

### Post by gohanssjn on 2008-11-07
So, I installed Ubuntu to sdb2, and when the computer restarted, sba1 went from NTFS to RAW in Vista.  Ubuntu LiveCD sees the drive as NTFS, but says it is unusable.

Any ideas?  Any way to get the data off???

---

### Post by gohanssjn on 2008-11-07
And here's an odd thing:  if I give the drive it's old name "Storage" the litte yield sign goes away in GParted, but then it has an error when commiting the change.

---

### Post by gohanssjn on 2008-11-07
Sigh, tried to repair and get this as well:

GParted 0.3.8

Libparted 1.8.9

Check and repair filesystem (ntfs) on /dev/sdb1  00:00:00    ( ERROR )
     	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 2048
end: 767051775
size: 767049728 (365.76 GiB)
check filesystem on /dev/sdb1 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sdb1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sdb1' as NTFS failed: Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).

---

