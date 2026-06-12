---
title: "[strong]Install ATI Catalyst 9.8 failed, need help.[/strong]"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by Nathan.zhu on 2009-08-21
Hi, I try to install ATI Catalyst 9.8 in my laptop (ThinkPad R400 series). It use ATI HD 3470 graphic card.
Download package ati-driver-installer-9-8-x86.x86_64.run
```
sudo a+x ati-driver-installer-9-8-x86.x86_64.run
``````
sudo sh ati-driver-installer-9-8-x86.x86_64.run
```Get ATI install interface follow next, get done, no error.
rebuild xorg.conf file
```
sudo aticonfig --initial
```get below xorg.conf configure file.
> 
Section "ServerLayout"
   Identifier     "aticonfig Layout"
   Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
   Identifier   "Configured Monitor"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section "Device"
   Identifier  "Configured Video Device"
EndSection

Section "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver      "fglrx"
   BusID       "PCI:1:0:0"
EndSection

Section "Screen"
   Identifier "Default Screen"
   Device     "Configured Video Device"
   Monitor    "Configured Monitor"
EndSection

Section "Screen"
   Identifier "aticonfig-Screen[0]-0"
   Device     "aticonfig-Device[0]-0"
   Monitor    "aticonfig-Monitor[0]-0"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
   EndSubSection
EndSection
reboot computer.
get black screen. don't show anything.
have to reboot again. go to recovery mode to fix graphic.
So, this time I'm get failed again, before try it on 9.7 version. it's samed.
Where is my wrong or need another step to setting something let it work?
Please help me, really thanks, thanks.

---

### Post by Nathan.zhu on 2009-08-22
nobody can help me?

---

### Post by Mark Phelps on 2009-08-22
There is an option with the drivers to build distro-specific packages.  When I used to use the restricted drivers, I found that tended to work better.  You would have to read the installation instructions for the details on how to do that.  But when done, you simply install the .debs.

---

### Post by humphreybc on 2009-09-03
I have the same problem, see this thread:

[http://ubuntuforums.org/showthread.php?p=7891047#post7891047](http://ubuntuforums.org/showthread.php?p=7891047#post7891047)

and this one:

[http://ubuntuforums.org/showthread.php?t=1256983](http://ubuntuforums.org/showthread.php?t=1256983)

---

