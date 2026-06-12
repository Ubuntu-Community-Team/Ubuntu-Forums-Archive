---
title: "automated lower case file names on VFAT"
date: 2008-10-06
forum: General Help
---

### Post by ymartin59 on 2008-10-06
To answer the following archived thread [http://ubuntuforums.org/showthread.php?t=483857](http://ubuntuforums.org/showthread.php?t=483857)

The vfat driver provides options to control how short names (old 8.3 DOS, upper case only) are created and displayed. A flag since winnt indicates if the shortname is lower case or upper case - internal details are available at  [http://www.win.tue.nl/~aeb/linux/fs/fat/fat-1.html](http://www.win.tue.nl/~aeb/linux/fs/fat/fat-1.html)

So to get CVS directories right or any filename shorter than 8 characters created with only upper (or lower) cases, you have to add "shortname=winnt" (default value is "lower") in mount options of your vfat file system in /etc/fstab.

Then, according to the way existing files have been created, it may be necessary to delete and create them again - in case of CVS, do a fresh checkout. Mixed-case file names are not affected because a long name is created for them.

For details, you can refer to Linux kernel Documentation/filesystems/vfat.txt   [http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt) and also man mount and search for "shortname" keyword.

---

### Post by akos.maroy on 2010-03-04
but how would I make ubuntu / gnome use the shortname=lower option automatically on all vfat mounts?

---

