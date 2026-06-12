---
title: "fsck failing (exit status 8) after software updates"
date: 2008-09-24
forum: General Help
---

### Post by re5et on 2008-09-24
I am receiving the following error message on startup"


[INDENT]
* Checking file systems...
fsck 1.40.8 (13-Mar-2008)
/dev/sde1 is mounted.  e2fsck: Cannot continue, aborting.
[/INDENT]

I am then asked to repair the file system manually.  I am dumped into a maintenance shell, where I attempt fsck, but of course it cannot continue because of the mounted disk.  I attempt to unmount /dev/sde1, and receive the message "umount: /dev/sde1: not mounted".  Where do I go from here?

---

### Post by rsambuca on 2008-09-24
If you have any live linux CD, you can boot from there and run fsck -f on the sde1 partition.

---

