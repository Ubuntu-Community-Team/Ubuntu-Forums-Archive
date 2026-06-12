---
title: "Western Digital ext. hard drive not recognized"
date: 2010-01-06
forum: Hardware
---

### Post by w1av on 2010-01-06
Hi,

I have a DUAL BOOT system, WinXP and Ubuntu 8.04.....everythings cool except I cannot get my ***Western Digital "My Book" external hard drive*** to be recognized in Ubuntu.  It is a USB 500GB drive. Works fine in Windows and I cannot figure out why it wont work in Ubuntu. My small USB flash drives work fine and other usb hardware. Please help!!!

---

### Post by Guitar John on 2010-01-06
I don't really know if this makes a difference, but what file system is the external formatted to?

---

### Post by mtbsoft on 2010-01-06
Check your log files, you may find that it is being detected but not being automatically mounted.  I had similar problems with my own 2Tb MyBook on earlier versions of Linux.

---

### Post by Sef on 2010-01-07
> I don't really know if this makes a difference, but what file system is the external formatted to?


That will not make a difference.

> I have a DUAL BOOT system, WinXP and Ubuntu 8.04....

1) Have you plugged it into more than one usb port?

2) I have a 1 gb My Book, and it is detected in [Lucid Lynx]("http://cdimage.ubuntu.com/releases/lucid/alpha-1/").   You could download the Live CD and run it to see if it detects it.   Lucid is the next LTS which is to be stable in April 2010.  Currently it is alpha 1, so not recommended for installing.

---

### Post by Joel Barnes on 2010-02-06
I had the same problem until I realized that the USB cable to the drive had wiggled slightly loose. Learned a lot about mounting drives while troubleshooting it though.

Probably just me.

---

