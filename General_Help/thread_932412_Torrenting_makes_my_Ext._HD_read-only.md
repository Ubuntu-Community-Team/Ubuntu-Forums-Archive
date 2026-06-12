---
title: "Torrenting makes my Ext. HD read-only"
date: 2008-09-28
forum: General Help
---

### Post by Stoodle on 2008-09-28
For some reason, while I'm torrenting, my external hard drive will randomly become read-only and it doesn't change until I reboot (and I suppose if I mount and remount, though I haven't tried it). Why is this? I'm torrenting something huge and this is rather inconvenient especially if I want it to run at night. The hard drive is a FAT32 500GB Seagate.

---

### Post by Jeroensum on 2008-09-28
If you are downloading a file that is larger than 4GB(when downloading DVD's perhaps?), the FAT32 filesystem will be unable to cope with it and possibly crash or return some other error which makes the mount daemon remount the filesystem readonly.
I suggest reformatting the drive with a filesystem that can handle bigger files. EXT3,XFS,JFS will do niceley and if Windows compat. is an issue, nowadays NTFS is well supported by the ntfs-3g driver so it's also an option, but do the reformatting in Windows for easyness sake ;)

---

### Post by Stoodle on 2008-09-28
Are you sure NTFS-3g is good? I want compatibility across the board, meaning that if I need to, even my girlfriend's mac can sync to it. Can you give me a link with pros and cons and of certain file systems?

Edit: I wanted you guys to know there is a tool for rw in Windows for ext 3 and ext 2 filesystems! It's called IFS Drives. Check it out

---

