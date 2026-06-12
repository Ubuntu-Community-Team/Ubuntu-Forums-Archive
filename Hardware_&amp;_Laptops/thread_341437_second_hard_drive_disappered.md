---
title: "second hard drive disappered"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by Chemist on 2007-01-18
I switch my PC on for the first time in about 4 days and when I tired to view my second internal hard drive i noticed that all the folders locked. I re-booted and the hard drive was no longer visible. I've checked the fstab and its still listed in there but when I look in qtparted the hard drive shows up as no file structure. It used to be ext3 but its blank. I know I can re-format but I'd really like to recover the data. Does anybody know any good tools for recovering data and how I'd go about sorting this mess out??

Thanks

---

### Post by john_spiral on 2007-01-18
try: 

**sudo fschk /dev/device name**

use the below command to find your device name:

sudo fdisk -l

---

### Post by Chemist on 2007-01-18
> will@will-desktop:~$ sudo fsck /dev/hdb
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext3: Filesystem revision too high while trying to open /dev/hdb
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

i've tried 

> sudo e2fsck -b 8193 /dev/hdb 

but the same error appears

---

### Post by john_spiral on 2007-01-20
Try booting off a modern live CD like Knoppix version 5.1 or even Ubuntu 6.1, might mean your filesystem is too new for the version of **fschk**? 

If Knoppix gives the same error looks like your 'filesystem superblock is corrupt'.

Give it a try.

---

### Post by Chemist on 2007-01-22
i've managed to get it to reckonise the drive but but now i get this

> e2fsck: Filesystem revision too high while trying to open /dev/hdb
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)

Any ideas??

---

