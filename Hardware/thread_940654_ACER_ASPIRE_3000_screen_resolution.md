---
title: "ACER ASPIRE 3000 screen resolution"
date: 2008-10-07
forum: Hardware
---

### Post by dallas000 on 2008-10-07
I need help with changing my screen resolution. i have seen some of the other posts but nothing helps and i dont want to end up with a blank screen from changing to the wrong res. i know it is capable of doing 1280x800 and that is what i want.

i have tried what i have seen on other forums
sudo dpkg-configure xserver-xorg

but that just does something with my key board

i am a bit new to this so please be gentle hehe but i did get my wireless working and that was an amazing thing. the laptop is blazing fast with ubunto and i love it i just want a little more.

i am also unable to add the visual effects for some reason but i think there is a decent graphics card in this old laptop of mine

thanks

---

### Post by overdrank on 2008-10-07
> **dallas000 said:**
> I need help with changing my screen resolution. i have seen some of the other posts but nothing helps and i dont want to end up with a blank screen from changing to the wrong res. i know it is capable of doing 1280x800 and that is what i want.

i have tried what i have seen on other forums
sudo dpkg-configure xserver-xorg

but that just does something with my key board

i am a bit new to this so please be gentle hehe but i did get my wireless working and that was an amazing thing. the laptop is blazing fast with ubunto and i love it i just want a little more.

i am also unable to add the visual effects for some reason but i think there is a decent graphics card in this old laptop of mine

thanks

Hi and welcome, what is the model of the graphics card? You can find the model by using the command lspci in the terminal located under applications accessories. Look for VGA. It sounds like you need the drivers for your graphics card and as for the desktop effects you may look at the FAQ's link in my signature.

---

### Post by dallas000 on 2008-10-09
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


thats what i got when i did that

---

### Post by overdrank on 2008-10-09
> **dallas000 said:**
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
[COLOR="Red"]01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

[/COLOR]
thats what i got when i did that

To change your resolution you may try using the command ```
gksu displayconfig-gtk
```

---

### Post by dallas000 on 2008-10-10
it still says its limited to 1024x768

i know that i can get 1200x800

i also would like to enable the desktop effects

thanks for the help

---

### Post by surfsup73 on 2010-06-14
I would like to install the graphics card drivers on my system.

I am trying to get the hardware acceleration to work. (example is that Google Earth only works in opengl software emulation; so slow)

How do I install the video driver for the following system:
============================================
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (r
ev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Soun
d Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev
 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev
 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Et
hernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.
11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address 
Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 
PCI/AGP or 662/761Gx PCIE VGA Display Adapter
=====================================================

I have the SiS driver for Windows XP that came with the laptop.

Please help.

Surfsup73

---

### Post by eddier on 2010-06-14
I,m assuming you have an Aspire 3000?

Have you upgraded the memory,default installation is only 256Mb.

AS the graphics chip uses shared system memory this may well be your problem. Upgrade if possible to 2Gb.

Windows Drivers are no good for linux. Sis Drivers are supplied via Xorg.

eddie

---

### Post by surfsup73 on 2010-06-14
I have the maximum memory available installed.  Are there any drivers that will improve the performance of my video card?

Thanks for you help.

---

