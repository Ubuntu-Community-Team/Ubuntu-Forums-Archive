---
title: "fusectl filesystem?"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by thetick1 on 2009-08-23
I rebuilt my kernel on an older laptop.  My old TP A22m with a stripped down, optimized kernel is now much more responsive then with the default Ubuntu kernel.  

Why is a FUSE filesystem created by default?  I would need it for NTFS , but I use only use FAT32 for flash drives.

I have no need for FUSE built in my kernel or as a module, so what is the function of the FUSE filesystem with the base kernel.

ie > mount -l | grep fuse
fusectl on /sys/fs/fuse/connections type fusectl (rw)

---

