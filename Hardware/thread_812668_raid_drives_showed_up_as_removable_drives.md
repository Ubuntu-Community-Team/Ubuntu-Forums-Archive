---
title: "raid drives showed up as removable drives"
date: 2008-05-30
forum: Hardware
---

### Post by LenzM on 2008-05-30
I'm not sure when it happened, but 2 (of 4) of the drives in my RAID array are now on my desktop and in the places menu as removable media.  All 4 of them are mounted in /media/ as disk, disk-1, disk-2 and disk-3 with 700 permissions.  `sudo ls /media/disk*` gives nothing, gparted sees them as an unknown file system with the raid flag.

I'm afraid that something might write to the devices and mess up the array.  I'm also unsure about unmounting the drives.  Does anybody know what's going on?

---

