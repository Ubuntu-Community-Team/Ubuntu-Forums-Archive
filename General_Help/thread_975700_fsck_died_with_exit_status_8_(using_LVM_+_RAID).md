---
title: "fsck died with exit status 8 (using LVM + RAID)"
date: 2008-11-08
forum: General Help
---

### Post by marcog on 2008-11-08
I have tried installing Intrepid with LVM and MD RAID 1. During boot fsck fails, halting the boot process. If I ignore the error and let it continue (using Ctrl+D) it boots as though everything were just fine. This is obviously a bad thing, as the file system is not being checked and the journal not being recovered.

I have included the fsck logs below. It seems that fsck completes successfully on /dev/mapper/vol0-home, but fails on /dev/mapper/vol0-root . Running a read-only fsck on /dev/mapper/vol0-root identifies some minor issues (incorrect block count [off by 7] and such).

Anyone got any bright ideas? Thanks in advance!

/var/log/fsck/checkfs :

```
Log of fsck -C3 -R -A -a 
Fri Nov  7 15:31:04 2008

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
/dev/mapper/vol0-home: recovering journal
/dev/mapper/vol0-home: clean, 15283/13107200 files, 6916638/52428800 blocks
fsck died with exit status 8

Fri Nov  7 15:31:05 2008
----------------
```

/var/log/fsck/checkroot :

```
Log of fsck -C3 -a -t ext3 /dev/mapper/vol0-root 
Fri Nov  7 15:31:04 2008

fsck 1.41.3 (12-Oct-2008)
/dev/mapper/vol0-root: clean, 142220/3276800 files, 1154414/13107200 blocks

Fri Nov  7 15:31:04 2008
----------------
```

---

