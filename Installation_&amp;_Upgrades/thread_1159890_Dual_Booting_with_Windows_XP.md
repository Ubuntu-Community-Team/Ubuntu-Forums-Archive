---
title: "Dual Booting with Windows XP"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Ecstatic23 on 2009-05-15
Installing Jaunty on my friends laptop.

Specs:
80GB Hard Drive
1GB RAM
C & D Drive.

XP is installed on the C drive and he wishes to install Jaunty on the D drive.

Will this erase files on the D drive or slow down performance in anyway?

Thanks!

---

### Post by Mark Phelps on 2009-05-16
> **Ecstatic23 said:**
> XP is installed on the C drive and he wishes to install Jaunty on the D drive.

Will this erase files on the D drive or slow down performance in anyway?

Thanks!
Understand what your saying but Ubuntu doesn't use "C" and "D" drives, which means, whichever drive you want to install Ubuntu to can not be formatted as NTFS (for windows).  So, the first thing you will need to do is remove the "D" drive using the Ubuntu LiveCD Partition Editor.

You can then install to the unformatted space.

The install will overwrite the MBR but when done, you should have a GRUB menu with entries for Ubuntu and for Windows.

---

### Post by x33a on 2009-05-16
as mark explained, there are no such drives in ubuntu.

if you have data on D drive, first defragment that drive. then resize that drive, and convert the rest of the space to ext3 (linux file system, needed for ubuntu).

then you can install ubuntu on that space, and have a dualboot system with grub as the bootloader.

---

### Post by erixoltan on 2009-05-16
You can also try Wubi, which will let you run the Ubuntu installation right inside Windows.  This might make it easier.

[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)

---

