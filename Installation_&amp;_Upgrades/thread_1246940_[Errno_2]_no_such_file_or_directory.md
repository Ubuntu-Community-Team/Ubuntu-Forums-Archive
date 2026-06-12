---
title: "[Errno 2] no such file or directory"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by balroggamer on 2009-08-22
Twice, I've gotten the following message when trying to install Ubuntu 9.04 desktop edition:
 
[Errno 2] no such file or directory '/rofs/usr/share/icons/HighContrastLargePrintInverse/36x36'
 
I've done a CD check - it passed with no errors...
 
Any suggestions? 
 
-- Bob T.

---

### Post by VMC on 2009-08-22
> **balroggamer said:**
> Twice, I've gotten the following message when trying to install Ubuntu 9.04 desktop edition:
 
[Errno 2] no such file or directory '/rofs/usr/share/icons/HighContrastLargePrintInverse/36x36'
 
I've done a CD check - it passed with no errors...
 
Any suggestions? 
 
-- Bob T.

I've never seen that error before. Is "rofs" read only file system?
What is the ISO name or is this a 'shipit' cd? Where did you download it. Also what specs are you pc and is this an install to internal hard drive.

---

### Post by balroggamer on 2009-08-22
I downloaded the ISO from the main site: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
 
I'm installing it on an older Dell desktop system: Dimention L933 - Pentium III,  256K ram, internal hard drive, Intel 810 graphics.
 
-- Bob T.

---

### Post by jerrrys on 2009-08-22
if you have a working install navigate to **SynapticPackageManager** (thru System>Admin) and check to see if this package is installed

[ATTACH]125835[/ATTACH]

or open up a terminal (Accessories>Terminal) and enter 

**sudo apt-get install gnome-accessibility-themes**

see if that takes care of it

---

