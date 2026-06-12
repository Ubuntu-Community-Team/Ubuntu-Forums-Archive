---
title: "cdrom1"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by jjbergdolt on 2005-07-22
I have 2 cdroms installed on my system a reader and a burner.
The reader (cdrom) is displayed on my desktop but not the burner (cdrom1).
How to get it displayed?
The Device Manager lists everything correctly.
There is a /dev/cdrom1 file.

---

### Post by adwait on 2005-07-22
If the drive is not listed only on the desktop, it simply means there is not short cut to it. Right click and click on "Add a Custom Launcher". Name it whatever you want, and in the command type 
nautilus /media/cdrom1

---

