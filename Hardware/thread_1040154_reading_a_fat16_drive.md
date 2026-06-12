---
title: "reading a fat16 drive"
date: 2009-01-15
forum: Hardware
---

### Post by bschultzjames on 2009-01-15
I have a usb stick formatted in fat16 and want to recover a few files off of it.


Two questions:
1.  Do I need a driver to read fat16 in ubuntu?
2.  How can I reformat it to fat32 or ext3?


thanks!

---

### Post by taurus on 2009-01-15
Chances are when you plug it in, it would be automounted so you don't have to do anything.  Otherwise, you can mount it by hand from a terminal.

And if you want to reformat it, use gparted in System -> Administration (install it if you don't have it).  Remember to unmount it first before you can format it.

---

