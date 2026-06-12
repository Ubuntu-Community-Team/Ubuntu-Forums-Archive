---
title: "ATI Radeon 9800 Pro &amp; Ubuntu"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by Maelstrom65 on 2005-04-29
I'm running a P4 2.6Ghz on an Asus P4P800 Deluxe mainboard with 2Gb RAM and an ATI 9800 Pro AGP vidcard.  I installed Ubuntu over a week ago and ran into a major foul-up with my MBR on that drive which finally sorted itself out in the last 24 hours.  After not being able to boot to any operating system (Had XP and Ubuntu on the same drive), I can now boot to Linux.  I ended up reinstalling windows on another drive.  Even then, no operating system would boot on the old drive until last night when suddenly, Grub kicked in and let me boot to Linux.

Anyhow, my problem is two-fold at this juncture.  

Part1:  When I boot Ubuntu normally and GDM starts, I just have enough time to type in my login and password and then GDM restarts...over and over and over...ad infinitum.  So, I boot to Recovery, type in my root password, and then type "gdm" to start Gnome.  That works.  No constant restarting.  If after signing in as root and then su'ing over to my normal account, GDM starts just fine.  Any ideas as to why it constantly restarts when I try and boot normally?

Part 2:  Is there any updated drivers for my ATI card that will allow me to span my desktop across 2 monitors?  I see on ATI's site that they have linux drivers that will do just that, but they were written for Fedora and SUSE and are in a RPM package.   Does anyone know if they will work in Ubuntu and if so, how do I install them on my machine?  If not, are there any other drivers that will work?

Thanks in advance for any assistance offered.

Cheers

---

### Post by odix on 2005-04-29
[QUOTE=Maelstrom65]Part1:  When I boot Ubuntu normally and GDM starts, I just have enough time to type in my login and password and then GDM restarts...over and over and over...ad infinitum.  So, I boot to Recovery, type in my root password, and then type "gdm" to start Gnome.  That works.  No constant restarting.  If after signing in as root and then su'ing over to my normal account, GDM starts just fine.  Any ideas as to why it constantly restarts when I try and boot normally?[/QUOTE]
It looks like there was not only a problem with the MBR, maybe the rest of the disk isn't ok at all.

[QUOTE=Maelstrom65]Part 2:  Is there any updated drivers for my ATI card that will allow me to span my desktop across 2 monitors?  I see on ATI's site that they have linux drivers that will do just that, but they were written for Fedora and SUSE and are in a RPM package.   Does anyone know if they will work in Ubuntu and if so, how do I install them on my machine?  If not, are there any other drivers that will work?[/QUOTE]
The open source driver also support dual monitor(type: "man radeon" in the console or terminal), if you want to install the ati binary driver (it's not written for Fedora and SuSE, it's only in rpm format), try [this](http://www.ubuntuforums.org/showthread.php?t=22496)  thread.

odiX

---

