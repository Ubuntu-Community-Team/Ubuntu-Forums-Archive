---
title: "ATI AIW 9600 128meg 2003 can this card work in 9.04????"
date: 2009-10-29
forum: Hardware
---

### Post by chrisginger26 on 2009-10-29
Hi Guys 

I am trying to install an ATI All in Wonder 9600pro with 128meg ram on ubuntu 9.04.

I have it working with a resolution of 1280x1024(5:4) 0hz refresh rate.

This is the card with a square looking dvi port that has an adapter cable going out two female vga cables I'm trying to get it working with a pair screens but at the moment I can't resolution/refresh rate using the open source driver that is installed with ubuntu (xserver-xorg-video-ati and xserver-xorg-video-radeon). Nothing shows up in the restricted hardware drivers window and when I follow the instructions on the ati site and install its driver the ati software says that there is no device installed.

Here is the output from lspci 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:10.0 SCSI storage controller: Adaptec AIC-7850 (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

Is this card compatible with 9.04???

Not sure what to do next can anyone help 
 
thanx

chris

System Ubuntu 9.04 
kernal 2.6.28-11-generic
GNOME 2.26.1

Memory 1002.7Mib
Processor: Intel(R) Pentium(R) 4 CPU 2.66GHZ

Hard disk 250gig

---

### Post by chrisginger26 on 2009-10-30
Hi Guys 

I now realise that this card is incompatible with 9.04 and I have gone back to 8.10 in an effeort to get it working after doing so I have now got the drivers working and both screens displaying the desktop.

My next question is is there a way to get this card to produce one desktop accross both screens for use with gimp etc (palettes tools etc on one screen image on the other and the moose traveling between the two)??

I have done this in the past with mac os but there does not seem to be an option in the ati catalyst to do this?

Can anyone help with ??

thanx again 

chris

---

