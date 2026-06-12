---
title: "NEC MultiSync LCD2010"
date: 2011-11-29
forum: Hardware
---

### Post by mmrooker on 2011-11-29
I have run into this issue with both Ubuntu 10.04.02 and 11.10.01. I cannot get the system to recognize the monitor and allow me to set the resolution correctly. I have tried other monitors, and the system quite happily recognizes and sets the appropriate resolution for them, so I know the video is at least working properly. I have nothing but issues however when trying to use either an NEC MultiSync LCD2010 or an NEC MultiSync LCD2000, and cannot get the system to allow me to display higher resolutions than 800x600.  

Is there a switch I need to throw on the kernel or a driver I need to add that will force these monitors to respond correctly? I doubt the issue is in the monitor itself, as they display perfectly when booting in Windows.

lscpi output is as follows:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

xrandr -q output is:
960x600        60.0  
960x540        60.0  
800x600        60.0*    56.0  
768x576        60.0  
720x576        60.0  
856x480        60.0  
800x480        60.0  
720x480        61.0  
640x480        60.0  
400x300        60.0  
320x240        61.0  
1024x768_60.00   59.4  
1280x1024_60.00   59.9  
1024x768_75.00   74.9  
1280x1024_75.00   74.5  

The 1280x1024 and 1024x768 modes were added with xrandr --newmode and xrandr --addmode commands based upon the outputs provided when using the cvt 1024 768 (60 and 75) and cvt 1280 1024 (60 and 75) commands. The system however gives me an error if I try to use any of these by commanding it xrandr --output default --mode (and any of the last four modes).

Any help would be appreciated.

---

### Post by rchennau on 2012-03-11
Attached is my Xorg.conf.

I simply added the following line

Modes      "1280x1024" "1280x960" "1024x768" "832x624" "800x600"

---

