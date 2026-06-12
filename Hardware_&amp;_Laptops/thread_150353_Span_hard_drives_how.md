---
title: "Span hard drives? how?"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by navilon on 2006-03-25
I am constantly adding more drives to my machine and i would like to know the best way to do this if i wish to have the drives spaned

---

### Post by soce_32 on 2006-03-25
LVM - Logical Volume Manager

[http://sourceware.org/lvm2/](http://sourceware.org/lvm2/)

You can lose data by setting up LVM, so read up, backup and test on new drives/partitions before going all out.

---

### Post by navilon on 2006-03-25
mostly because of a hard drive failure, correct?

---

### Post by soce_32 on 2006-03-26
LVM docs generally suggests that you run pvcreate for the entire disk, but you can do it for a group of partitions.  pvcreate destroys data on disks/partitions.  You have to then create volumes, and create a new filesystem on the volume.

If you don't backup you stuff, or move it around creatively, you will lose data when you setup LVM.

---

### Post by navilon on 2006-03-27
What would you reccomend for backing up arround 600 MB on a budget. Tapes?

---

### Post by puddpunk on 2006-03-27
[QUOTE=navilon]What would you reccomend for backing up arround 600 MB on a budget. Tapes?[/QUOTE]

600mb? CDRW mate :)

---

