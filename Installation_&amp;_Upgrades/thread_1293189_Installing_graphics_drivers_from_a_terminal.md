---
title: "Installing graphics drivers from a terminal"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by Xyldor on 2009-10-16
I have recently switched from windows to linux. Initially, I installed xubuntu on my eeePC901 and now I want to install Ubuntu 9.04 on my desktop.

When I use a live CD I have to select safe graphics mode, otherwise the desktop freezes and often doesn't display properly. Once in to the desktop (Gnome) in safe graphics mode I can select 
System-Administration-Hardware Devices
then activate the Nvidea accellerated graphics driver (Version 180)

When I install Ubuntu to the hard drive and try running it, the screen goes blank (with a movable arrow cursor) after the login is achieved. There does not appear to be any way to select safe graphics mode. I can switch to a terminal window (alt-ctl-F1) and have run 
sudo apt-get update
& sudo apt-get dist-upgrade
without effect.

I suspect the graphics card driver is not installed but I dont know how to install it from a terminal.
How do you either enter ubuntu in safe graphics mode, or load the Nvidea graphics driver from a terminal?


The graphics card is a GE7800GT,
Mother board Gigabyte GA-K8NF-9
Processor Athlon 64
Ubuntu Jaunty Jackalope (9.04)

Oh, and Mandriva installs OK first time. But I would prefer to use Ubuntu.

---

### Post by wojox on 2009-10-16
Here you go, worked for me for nvidia 173.***:[HowTo: NViDIA 185.18 Drivers in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1125400")

Just download the driver for 180.*** and follow those instructions.

---

### Post by Xyldor on 2009-10-17
Not much luck I'm afraid.
I installed 180.60 from *[http://uk.download.nvidia.com/XFree86/Linux-x86/180.60/NVIDIA-Linux-x86-180.60-pkg1.run](http://uk.download.nvidia.com/XFree86/Linux-x86/180.60/NVIDIA-Linux-x86-180.60-pkg1.run)* and it reported as installed (after all the kernel compiling, etc) 

I tried it, resulting in just a blank screen after the login

Had to remove temp1 and freetype from modules in xorg.conf to make 
**grep -n "^(EE)" /var/log/Xorg*log** report no errors,

**grep -i "nvidia\|NVRM" /var/log/syslog** gave no indication anything was wrong

Trying to uninstall using
[B]sudo nvidia-uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-all[/B] 
also resulted in a blank screen after login


The only way I have found so far to get onto the desktop is through the LIVE CD by selecting Safe Graphics Mode..

How do I do this for the installed version ?

---

### Post by Xyldor on 2009-10-17
Help please. I'm getting desperate. I need to install Ubuntu but it wont work from the hard drive. It only works from the Live CD in  safe graphics mode.

I dont want to have to revert to mandriva but I may have to if this isnt sorted soon.

I cant believe a major distribution like Ubuntu is missing an important function like safe graphics mode for its installed version.

---

