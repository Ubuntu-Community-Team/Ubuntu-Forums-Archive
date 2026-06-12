---
title: "Corrupt hard disk is unerasable!"
date: 2009-02-15
forum: Hardware
---

### Post by DigiTan on 2009-02-15
Or would that be "inerasable?"  Anyway, I have a harddrive that got corrupted by a WinXP SP3 upgrade (forgot to turn off antivirus).  I have the contents of this drive backed up on 2 other hard disks, so if I have to erase the entire drive, that's fine.

The problem is, Ubuntu can't read, write or boot off this disk in any way.  Any time I try to view its contents or partitions with GParted, Fdisk, or even the console, it causes those programs to hang endlessly.  Neither Windows nor Ubuntu can boot off it in their normal modes.  When doing ntfsfix, I got this...

```
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume : Invalid argument
FAILED
Attempting to correct errors... FAILED
Failed to startup volume : Invalid argument
Volume is corrupt. You should run chkdsk.
```

I tried: **sudo dd if=/dev/zero of=/dev/sdb**
and: **sudo dd if=/dev/sda of=/dev/sdb**

...and both froze.  (I could tell because the HDD light never stays on, like with a succeful dd operation).  All I want is this disk erased.  Why won't it work?

---

### Post by hansdown on 2009-02-15
System rescue disk might work.

[http://www.sysresccd.org/wiki/index.php?title=Download.en.php&redirect=no](http://www.sysresccd.org/wiki/index.php?title=Download.en.php&redirect=no)

---

