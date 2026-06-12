---
title: "No hard drive after failed installation"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by pure life on 2009-03-04
I recently attempted to install Ubuntu onto internal harddrive #2 (set up as slave). The install failed and when i logged back into windows, only my C: showed up in My Computer. The one where I tried to install is nowhere to be found. Any help??

---

### Post by taurus on 2009-03-04
Windows cannot access or view ext3 filesystem.  So if you want to access your second harddrive, you either need to use gparted from Ubuntu LiveCD to format it back to ntfs/fat32 or install fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/) in windows first.

---

### Post by pure life on 2009-03-04
Thanks! So in order to do that, all i will need to do is insert the Live CD and there will be the option to reformat it back to NTFS/FAT32?

---

