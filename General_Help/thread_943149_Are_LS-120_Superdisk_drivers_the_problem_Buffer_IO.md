---
title: "Are LS-120 Superdisk drivers the problem? Buffer I/O error with 1.44 meg floppy"
date: 2008-10-09
forum: General Help
---

### Post by MaxIBoy on 2008-10-09
In both Ubuntu server and a Debian net-install, trying to mount a floppy which was inserted into a Superdisk drive gave this error:
```
Buffer I/O error on device fd0, logical block 0
``` repeated a few times, with some other cryptic stuff about superblocks and boot sectors. Mounted as msdos or as vfat, it does the same thing. Setting the filesystem as "auto" in fstab doesn't work either. 

The floppy contains ethernet drivers (obviously critical to the computer's future role as a print server.)


The superdisk is connected to an IDE port. I suspect that the builtin drivers which the OS is trying to use are unsuited to that kind of hardware. Could that be the problem?

---

### Post by cariboo on 2008-10-10
Have a look at this page here:

[http://paulbristow.net/main/2002/02/02/ide-floppy/](http://paulbristow.net/main/2002/02/02/ide-floppy/)

Jim

---

### Post by MaxIBoy on 2008-10-10
Copied by hand:
```
max@ubuntu:/mnt$sudo mount -t vfat /dev/fd0 /mnt/floppy
mount: block device /dev/fd0 is write-protected, mounting read-only
```
*Extremely long pause, during which the drive doesn't light up or make any noise
```
[ 8652.7145871] FAT: unable to read boot sector
mount: /dev/fd0: can't read superblock
```

And if you think I'm going to hand-copy the output of a ls -a in /dev, you're crazy. However, fd0 is in there.

---

### Post by MaxIBoy on 2008-10-11
Hate to do this, but... bump.

Do I have a bad floppy? I think maybe I might have some old floppies lying around I could use to test the drive with, should I try that?

---

### Post by MaxIBoy on 2008-10-15
Really hate to do this, but... bump.

---

