---
title: "unmounting USB key drive kills read/writes on other USB device"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by lazyfirecloud on 2007-12-17
Hello,
I've been having an odd issue in which my external hard drive stops responding after I unmount my USB key drive.
I have a 500 GB external hard drive which is always on and plugged in.  Currently it is mounted from command line (usually fstab takes care of it) after unmounting it from nautilus as it does that automatically when I plug it in.  I've noticed that if I plug my USB key drive (automounted by nautilus) then unmount it, all read/writes stop from my external hard drive and it stops responding.  Then I have to unmount it and remount it.  It does unmount successfully so it didn't get unmounted when I unmounted the USB key drive.  All processes running using the data from external hard drive die saying the drive is not available for read/write.
How do USB devices work in Ubuntu?  Is there something weird going on here?

---

### Post by lazyfirecloud on 2007-12-20
Anyone?
It would really be nice to be able to copy data onto my USB key drive while running processes using data on my external hard drive.

---

### Post by Jakadinho on 2007-12-31
I have the same problem and unfortunately no solution :(

---

