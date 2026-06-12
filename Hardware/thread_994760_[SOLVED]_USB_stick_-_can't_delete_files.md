---
title: "[SOLVED] USB stick - can't delete files"
date: 2008-11-27
forum: Hardware
---

### Post by oygle on 2008-11-27
I can't delete files on my KINGSTON USB stick (4 Gb). Ubuntu says it is a 'read-only' system.

The mount command shows this ..

> /dev/sdd1 on /media/KINGSTON__ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

Any clues please ?

---

### Post by oygle on 2008-11-27
Seems somehow Ubuntu got itself in a knot. Unmounted the USB stick, then mounted it, and it is now okay, I can delete files, and also copy files from the HDD to the stick (overwrite).

---

### Post by johntayler on 2008-11-27
It looks some odd, but it is true. Check the file system of your hard drive and of your USB stick. If both have the same file system, it will be formated.

Tayler

---

### Post by oygle on 2008-11-28
The file system on the hard drive is ext3 , and the file system on the USB stick is vfat (it was formatted on an XP computer).

If I have any probs copying or deleting to the USB, I just unmount/mount and all is well again.

Used the USB to get some digi pics printed today, it would be interesting to format the USB to ext3 and then copy some pics and see if the pics can be recognised/printed (on a Fuji printing system).

---

