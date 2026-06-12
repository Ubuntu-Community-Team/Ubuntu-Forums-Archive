---
title: "Using the tablet mode on Toshiba Tecra M4"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by magicplayr2000 on 2007-10-28
Hi all, I just installed Gutsy Gibbon on my Toshiba Tecra M4.  One of the things keeping me from making the permanent switch from Windows is my need to have the tablet pen working.  I found some help in this topic: [http://ubuntuforums.org/showthread.php?t=107552](http://ubuntuforums.org/showthread.php?t=107552) that helped me find my pen (ttyS0).  I tried copy/pasting the xorg.conf file into mine, and changing the device locations, but it's not actually doing anything.  I was wondering if anyone could give me some help on getting this working.  Thanks!

EDIT:  Sorry, I'm an idiot.  I forgot to uncomment the three lines in the xorg.conf that specifically say "un-comment if using a wacom tablet."  I uncommented those and it works :-D

---

### Post by sitka on 2007-11-15
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection


that isn't commented out in my /etc/X11/xorg.conf 

my tablet worked fine in fiesty...    didn't even have to mess w/ anything in feisty  

how can i get it working?

---

