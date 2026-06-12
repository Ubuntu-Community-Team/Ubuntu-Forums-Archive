---
title: "Dual head with 2 monitors and 2 graphic cards"
date: 2009-05-25
forum: Hardware
---

### Post by giovanni.destefano on 2009-05-25
Hello all,

I have to admit that now I am a little desperate :-(

I have 2 graphic cards and 2 monitors. I would like to have a dual head configuration with each card connected to one monitor.

In Ubuntu 9.04 I cannot find any GUI to help me (not even displayconfig-gtk) and...surprise surprise...there is no xorg.conf anymore...what happend??? :-( well, there is one but it is empty...

For sure I must have missed some super cool improvement in the technology...but I was hoping that dual head support would have improved in the meantime...

Anyway, this is the HW I have: 

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0e.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
00:0e.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
00:0f.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
00:10.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
00:10.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

Kernel 2.6.28-11-generic. I have a crappy computer as it is a Celeron 2.4 GHz with 2 GB RAM...

Given that my xorg.conf is empty...and that I have an ATI Radeon 9200 PRO, and an on board SiS card, how can I have this dual head thing working? 

Which drivers shall I install? and how do I know which drivers are currently in use for each card?

Any help is very much appreciated!

Cheers,
Giovanni

---

### Post by jmmarca on 2009-06-01
I believe that I am having the same problem, I have 2 video cards and want to work on two monitors, I could do this in windows but in ubuntu not yet :/ 

 Description of plates:  
 sudo lspci -G  | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:04.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)


 I tried to put the Xorg as follows.


Section "Device"
#    Identifier    "Configured Video Device"
    Identifier    "0 VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
    BusID        "PCI:04:04:0"
    Screen        0
EndSection

Section "Device"
#    Identifier    "Configured Video Device"
    Identifier    "1 VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
    BusID        "PCI:1:0:0"
    Screen          1
EndSection

Section "Monitor"
    Identifier    "Main Monitor"
EndSection

Section "Monitor"
    Identifier    "Second Monitor"
EndSection

Section "Screen"
    Identifier    "Main Screen"
    Monitor        "Main Monitor"
    Device        "0 VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
EndSection

Section "Screen"
    Identifier    "Second Screen"
    Monitor        "Second Monitor"
    Device        "1 VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen          1 "Main Screen"
    Screen        0 "Second Screen" RightOf "Main Screen"
    Option "Xinerama" "true"
EndSection

---

