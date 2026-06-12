---
title: "Fakeraid ntfs_vista resize errors"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by nospoon on 2008-12-19
I'm trying to install on a a system with an intel ich9r fakeraid with a raid1 (mirror) of 2 SATA drives.  I want to dual boot with vista, which is currently the only OS installed.  I'm using the alternate installer CD, and enabling the RAID volume as per the fakeraid howto, but when I manually partition the drives, and try to resize the existing ntfs(vista) partition, I get an error:   
```

ntfsresize:  ntfsresize v2.0.0 (libntfs 10:0:0) 
ntfsresize:  Failed to startup volume: Invalid argument.
ntfsresize:  ERROR(22): opening '/dev/mapper/isw_ecggcjgbjg_Volume0' as NTFS failed: Inalid argument
ntfsresize:  the device '/dev/mapper/isw_ecggcjgbjg_Volume0' doesn't have a valid NTFS.
ntfsresize:  Maybe you selected the wrong partition?  Or the whole disk instead of a
ntfsresize: partition (eg /dev/hda, not /dev/hda1)?  This error might also occur
ntfsresize:  if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
partman:  Error running 'ntfsresize --info'

```
Thanks for your response
-nospoon

---

