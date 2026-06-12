---
title: "usb/network drive"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by AlanR8 on 2007-12-02
I have a Freecom 500 gig network drive. No problems with mounting it via samba but I find the transfer rate slow.

The drive has a USB port as well and a couple of weeks ago I just plugged it in to the laptop and all was well. it mounted and copied across very fast.

Subsequently I've reinstalled Kubuntu Gutsy and the drive is not visible via the USB cable. That said, if I go into System Settings/Advanced then Disk and file systems it shows up there and the mount point is given as /proc. Navigating there gives a list of folders but I can't find the drive contents.

Any thoughts?

---

### Post by prodezigner on 2007-12-02
If your connecting via USB try:

sudo apt-get autofs ntfs-3g

If the drive is NTFS that should fix the problem... after the packages install just plug it back in, if that doesn't work, just post back.

---

### Post by AlanR8 on 2007-12-02
Tried that no joy. Should have mentioned the drive seems to be running a Linux OS of sorts, instant on

---

### Post by AlanR8 on 2008-01-31
Bump..........

Driving me nuts!

---

### Post by AlanR8 on 2008-02-14
Bump......bump!!!!!!!

Anyone?

---

### Post by AlanR8 on 2008-03-01
Quadruple BUMP!!!! :) :) :)

---

