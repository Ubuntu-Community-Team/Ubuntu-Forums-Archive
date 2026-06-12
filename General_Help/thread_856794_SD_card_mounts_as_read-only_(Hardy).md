---
title: "SD card mounts as read-only (Hardy)"
date: 2008-07-11
forum: General Help
---

### Post by jmwyatt on 2008-07-11
Cannot use SD card as it give message "Read Only." Tried unmount and remount. No luck. Tried CHMOD. No luck. Anyone else encountered this problem? Solved it? Thanks!

---

### Post by Ptero-4 on 2008-07-11
use fsck -t vfat -a on it. This is the equivalent of the windoze scandisk tool.

---

### Post by jmwyatt on 2008-07-11
Here is the result:

fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /media/KINGSTON:Is a directory

---

### Post by jonlemur on 2008-07-12
I think you should be able to mount it (after unmounting it) for read/write by doing something like ```
mount -o rw /dev/SDDISK /media/disk
```That's not quite the right syntax, and you'll have to replace SDDISK with where your sd card is (I think it's in /dev).  You may also have to specify the filesystem type.  But I hope at least the -o rw may help mounting it read/write.

You can "man mount" for more information on it.

---

### Post by Ptero-4 on 2008-07-15
> **jmwyatt said:**
> Here is the result:

fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /media/KINGSTON:Is a directory

The fsck is done on the block device (/dev/*)

---

### Post by leona on 2011-01-23
Was there any fix for this?
I get the same problem with 10.04 now.
Sometimes it mounts fine, other times it tells me its read only.
What is going on?

---

### Post by leona on 2011-01-23
> **Ptero-4 said:**
> use fsck -t vfat -a on it. This is the equivalent of the windoze scandisk tool.

Arr, this fixed my problem too, must have been a file system error that prevents the system from mounting it, you know it would be so much better is Ubuntu provided better user feedback, if it say "Unable to mount Read/Write due to file system error" you could then do something about it, but it just says nothing until you try to copy something onto it, then it just gives you "Error, Disk Read only", which isn't very helpful! :(

---

