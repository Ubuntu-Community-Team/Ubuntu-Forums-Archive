---
title: "Surface testing of a hard drive, to mark bad sectors unuseable?"
date: 2013-01-13
forum: Hardware
---

### Post by scruffyeagle on 2013-01-13
I have an external 1TB hard drive, which I'm positive has some bad sectors in one of its partitions. I use it under both Windows & Linux, and neither seems to have isolated the defects & marked those places of the drive's surface unuseable. I remember seeing an option for doing surface testing & marking of bad sectors, but I don't remember for sure whether it was under Windows or Linus. Anyway, I can't find it now... Is there a utility in Linux that can do this task for me? TIA!

---

### Post by ahallubuntu on 2013-01-13
What does S.M.A.R.T. say?  Install GSmartControl to check if you haven't already and look at the Attributes for this drive.

Modern hard drives automatically mark bad sectors unusable (the drive firmware handles it) and replace bad sectors with spares.  A 1TB drive should have a few hundred spares.  If you have more bad sectors than that, you should probably replace the drive, anyway.

If S.M.A.R.T. shows any Pending Sectors, you can try zeroing the drive with something like Darik's Boot and Nuke (DBAN) - [www.dban.org](www.dban.org) .  (Do a quick erase to do only one pass, probably all you need for this.)  Sometimes this will get the drive firmware to reallocated spare sectors for them and you can use the drive again, albeit with caution to make sure more sectors don't fail.

If S.M.A.R.T. shows reallocated sectors and no pending sectors, you don't need to do anything - the firmware has already marked the bad ones "do not used" and reallocated spares to replace them.

---

### Post by sudodus on 2013-01-13
You can use smartctl from smartmontools in linux to get a S.M.A.R.T. health test.

Linux ext file systems:

Use ```
sudo e2fsck -f /dev/sdxy
``` booted from another drive to check the file system for logical errors.

Use 
```
sudo e2fsck -c /dev/sdxy
``` and
```
sudo e2fsck -c -c /dev/sdxy
``` (read-write) to test the device in order to find any bad blocks

from ```
man e2fsck
```
```
-f
    Force checking even if the file system seems clean.
```
```
-c
    This option causes e2fsck to use badblocks(8) program to
    do a read-only scan of the device in order to find any
    bad blocks. If any bad blocks are found, they are added
    to the bad block inode to prevent them from being
    allocated to a file or directory. If this option is
    specified twice, then the bad block scan will be done
    using a non-destructive read-write test. 
```

Windows FAT and NTFS file systems:

Use ```
chkdsk /f X:
``` for file system errors and
```
chkdsk /r X:
``` to locate and mark bad sectors

From ```
chkdsk /?
```
```
/f - fixes errors on the disk
/r - Locates bad sectors and recovers readable information (implies /f)

```

Use ***ddrescue*** to save what can be saved from a failing drive.
Read the excellent description and tutorial in ```
info ddrescue
```

---

### Post by tgalati4 on 2013-01-13
```
sudo fsck -cc /dev/sda1
```

Make note of the list of badblocks that are found and perform it once a year (or sooner) to compare the list.  If it continues to grow, then change the drive.

---

### Post by scruffyeagle on 2013-01-20
> **ahallubuntu said:**
> Install GSmartControl

Will do. Thanks!

I'll be getting back to this thread in a while, after I've done some work w/ GSmartControl & smartmontools.

Thanks to all, for the replies!

---

