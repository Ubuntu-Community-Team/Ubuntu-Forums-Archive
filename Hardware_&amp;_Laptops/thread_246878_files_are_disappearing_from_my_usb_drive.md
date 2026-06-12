---
title: "files are disappearing from my usb drive"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by fstevens on 2006-08-29
I am moving files from Ubuntu (Dapper) to a fat32 usb drive.  When I unplug the usb drive the files disappear when I plug the drive back in again ... any help would be great!

---

### Post by funchords on 2006-08-29
I wonder if the files are being buffered. 

Before removing the drive, try 

**sudo sync**

then 

**sudo umount /dev/sda1** (or whichever device)

---

