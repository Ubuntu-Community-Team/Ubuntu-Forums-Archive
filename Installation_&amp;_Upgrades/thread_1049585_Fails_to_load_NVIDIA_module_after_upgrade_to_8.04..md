---
title: "Fails to load NVIDIA module after upgrade to 8.04.2"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by wjmcolorado on 2009-01-24
[FONT="Arial"]Updated to 8.04.2 
Absolutely zero problems prior (love Ubuntu!)
After re-start, received following message:
Failed to start X server (your graphical interface). It is likely that it is not set correctly. Would you like to view the X server output to diagnose the problem?
<Yes> obviously
Meat of next message:
(==) log file: "/var/log/Xorg.0.log",Time: Sat Jan 24 15:36:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed toload module "type 1" (module does not exist, 0)
(II) Module "ramdac" already built in
Fatal: Error running install command for nvidia
(EE) NVIDIA(0): Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernal module
(EE) NVIDIA(0):  ***Aborting***
(EE) Screen(s) found, but none has a usable configuration

My display adapter is a NVIDIA GeForce 6150SE nForce 430.  This is the first time I've ever encountered any problems with the system.[/FONT]

---

### Post by Will4 on 2009-01-24
try going through your text terminal after you boot by pressing Ctrl+Alt+F1 to F6

you will be asked your username and password, after that (if you have already set your /etc/apt/source.lst) 

Step 1
> sudo apt-get install nvidia-glx-new-envyif you haven't set it yet 

Step 2
> sudo gedit /etc/apt/source.lstafter it opens,  Ctrl+A to select all and then Delete. Copy the fallowing lines and paste there. After that, Ctrl+s to save and Alt+F4 to exit and then ... Step 3 (below)
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 

Step 3

> sudo apt-get update

---

### Post by wjmcolorado on 2009-01-24
Fixed. Thanks!

---

