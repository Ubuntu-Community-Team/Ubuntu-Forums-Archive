---
title: "Corrupted root inode on ext3 RAID - data recovery"
date: 2008-08-22
forum: General Help
---

### Post by Peevish on 2008-08-22
I've recently had some issues with my file systems.  I rebooted [as I do once in a while, despite running Linux], and it booted into a recovery console, as one of my file system's was not clean.

The file system in question is a RAID10 [4x250] setup with an ext3 partition on it.  The array builds successfully.  The fsck fails with the error message: "The root inode is not a directory".  I'm not all that fluent with Linux in general, so I resort to asking questions like this.  Is there any way to recover my data ?

My system is a Gigabyte GA-P35-DS3R, e8400, 4GB DDR2 800, XFX 8800GT, everything's at stock speeds [I know, what kind of geek am I ?].  The drives in question are Seagate 250GB SATA IIs.  The system boots fine if I remove the array in question from the fstab, but I can't see any way to recover the data on it.  I have limited backups [perhaps 60% of the data], but they are not organized, and I'd rather not have to re-organize them again.

Any ideas ?

---

