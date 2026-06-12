---
title: "[SOLVED] Reformating a hard drive from a Mac for Ubuntu"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by waggygee on 2007-05-05
I have a hard drive with Windows XP on it in my computer now and I took another out of my old Mac. How can I remove all the infomation off that drive so I can install linux on it?

---

### Post by Mike T on 2007-05-05
You should try putting it in the PC and install Ubuntu  from the Live CD.   When you get to the screen asking where to put Ubuntu, use the option to set up partitions manually.  Then find the Mac formatted hard drive and delete any partitions on it.  Finally, set up a ext3 partition for the file system, but leave some room for a linux swap partition.  I use a 2GB swap partition on my system, but YMMV.

---

### Post by waggygee on 2007-07-01
Ok... this was a bit of a dumd question.... I was still new to the whole thing...

---

