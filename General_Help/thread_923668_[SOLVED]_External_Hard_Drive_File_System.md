---
title: "[SOLVED] External Hard Drive File System"
date: 2008-09-18
forum: General Help
---

### Post by CrusaderAD on 2008-09-18
When clicking the properties on an external hard drive, it says the file system is msdos. When I run a backup to this drive, it renames certain files (Folder would be %sjhgolder). Do I have to format this external drive to a more compatible file system? If so how?

---

### Post by leef on 2008-09-18
not sure about this but I've had the same issues in the past, I think it's some limitation in the fat filesystem, if you need windows compatibility I would say it might be good to go with a more modern filesystem like ntfs. If not I would go with a killer filesystem like reiserFS (ok perhaps that was in bad taste).

---

### Post by CrusaderAD on 2008-09-18
I thought that maybe the issue. Got any good recommendations for a format program?

---

### Post by leef on 2008-09-18
Personally, I would go with either ext3 or reiserFS but if you need something more specific wikipedia has a comparison chart of the various file systems available;

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

just make sure the one you choose to use is supported by the kernel (which the ones I mentioned earlier are)

---

### Post by scouser73 on 2008-09-19
> **leef said:**
> Personally, I would go with either ext3 or reiserFS but if you need something more specific wikipedia has a comparison chart of the various file systems available;

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

just make sure the one you choose to use is supported by the kernel (which the ones I mentioned earlier are)

I would suggest that you use reiserFS, as if you make it ext2 or ext3 it uses a portion of the HDD's space. To format I use Gparted, it's in the repos, and is very effective.

---

### Post by mcduck on 2008-09-19
> **scouser73 said:**
> I would suggest that you use reiserFS, as if you make it ext2 or ext3 it uses a portion of the HDD's space. To format I use Gparted, it's in the repos, and is very effective.

..all filesystems use a portion of the disk space..

If you are talking about the 5% reserved to root on Ext2/3, that's something you can freely adjust or completely disable. ;)

Ext works better if you need to access the disk in Windows or OS X, I haven't seen any ReiserFS drivers for them.

---

### Post by mb_webguy on 2008-09-19
As far as cross-compatibility between Windows and Linux, I'd go with NTFS.  Linux's support for NTFS seems more solid than Window's support for ext2 or ext3 through the third-party drivers.  Besides, Ubuntu now supports NTFS out of the box, whereas you have to install those third-party drivers for Windows to read ext2/ext3.

As to programs to format the drive, I'd go with GParted.  If you want to format NTFS using GParted, you'll need to install the ntfsprogs package first.

---

### Post by CrusaderAD on 2008-09-19
When I open Gparted with sudo, everything is greyed out... how do I unlock it?

---

### Post by CrusaderAD on 2008-09-19
Never mind, it's cause they were mounted. Thanks for all the great replies!

---

