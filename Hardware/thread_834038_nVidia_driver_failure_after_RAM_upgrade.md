---
title: "nVidia driver failure after RAM upgrade"
date: 2008-06-19
forum: Hardware
---

### Post by b-bob on 2008-06-19
I have tried searching for solutions for this problem, but have not found any working solutions.

First, my PC specs:
CPU: Intel Core2Duo T7500
GFX: nVidia 8600M GT 256MB
RAM: See below
OS:  See below

Basically, I have had massive issues with the nVidia graphics driver since upgrading to 4GB RAM. I was happily running Ubuntu 7.10 i386 for 9months or similar without any problems at 2GB RAM. I had full desktop effects, and it was very pretty.

I upgraded the RAM to 4GB and started having issues with my graphics. I have tried (in no particular order):
 - Ubuntu 7.10 i386
 - Ubuntu 7.10 AMD64
 - Ubuntu 8.04 i386
 - Ubuntu 8.04 AMD64
 - Last resort, Fedora 9 64Bit

It doesn't seem to matter which version I run, they will all run fine with the vesa driver, but will create scrambled graphics with the nVidia driver. This can be a black + rainbow login screen, or even show the initial boot POST graphics again, after the ubuntu loading graphic.

It will operate fine with just 2GB, but I need 4GB for when I do FEA, etc in Vista - I have no choice :(

I imagine that its a case of the nVidia driver trying to assign the dedicated graphics RAM in conflict with the main system RAM. I have even tried a patched kernel that is meant to fix this, but have had no success. 

Has anyone else had the same problem? Any suggestions for fixing this problem, its a real pain. Esp when the second RAM slot is under the keyboard :S 

I understand it's most likely the closed-source nVidia driver, but is there a way to change the way the kernel maps the system RAM??

Help?!?

EDIT: It may be linked to [http://ubuntuforums.org/showthread.php?t=761919](http://ubuntuforums.org/showthread.php?t=761919)

---

### Post by pietjanjaap on 2008-06-19
Wat does memtest say?

---

### Post by b-bob on 2008-06-20
Memory Tests fine..

Passes ubuntu memtest, ms vista RAM test, etc. I have also tried several different sticks. System runs vista fine with 4GB, and ubuntu fine with either one of the 2GB sticks, just not both..

---

### Post by ukripper on 2008-06-20
you need to use 64bits version to use 4GB RAM.

---

### Post by b-bob on 2008-06-20
I understand that.. I should be able to get 3.1GBish with the 32bit OS. I have the same problem with both the 32bit and 64bit versions..

---

