---
title: "[SOLVED] Is there a command line to show a list of hardware?"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by jmagick07 on 2007-07-15
Like what type of sound card, video card, dvd rom drive, hard drive, etc. I have in my computer.  Basically a list of all the specs?

I tried looking on here [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) but couldn't find any command for what I wanted.

---

### Post by w4ett on 2007-07-15
lspci     All PCI connected chipsets....Motherboard, video etc.

lsusb    All usb connected devices

also check:

[http://www.computerhope.com/unix/uls.htm](http://www.computerhope.com/unix/uls.htm)

---

### Post by Pitbull11188 on 2007-07-15
sudo lshw

---

### Post by jmagick07 on 2007-07-15
thanks guy, those worked great

---

