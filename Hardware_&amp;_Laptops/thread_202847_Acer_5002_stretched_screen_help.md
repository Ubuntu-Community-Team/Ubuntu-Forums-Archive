---
title: "Acer 5002 stretched screen help"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by usfour on 2006-06-24
Hi, 

I've installed Dapper Drake onto my Acer 5002 WLMI.  It's a great laptop running WinXP.  The graphics are well proportioned for the wide screen.  When I run it in Ubuntu, the graphics are stretch and disproportionate.  Can anyone help me please?

Thanks in advance for any help I can get on this.

---

### Post by nolongerlivecd on 2006-06-24
Umm... download proprietary ATi drivers.

---

### Post by usfour on 2006-06-24
[QUOTE=nolongerlivecd]Umm... download proprietary ATi drivers.[/QUOTE]

Does the Acer 5002 use ATI Graphics?  I don't know what the driver is.

:confused:

---

### Post by evil_elman on 2006-06-24
open up a terminal and write 'lspci' without the quotes. Look for something that says 'VGA compatible controller' and see what else it says on that line.

Or... Just copy and paste all of it so we can have a look at it. 

If my memory serves me right it's either Xpress200 or Mobility X700 in that thing...

---

### Post by usfour on 2006-06-24
[QUOTE=evil_elman]open up a terminal and write 'lspci' without the quotes. Look for something that says 'VGA compatible controller' and see what else it says on that line.

Or... Just copy and paste all of it so we can have a look at it. 

If my memory serves me right it's either Xpress200 or Mobility X700 in that thing...[/QUOTE]

Per your request.  Here it is...  Thanks.

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

---

### Post by usfour on 2006-06-25
The results from the above gave the clue that my graphics card is SIS.  Did some google and executed the following command.

sudo dpkg-reconfigure xserver-xorg

Picked 'SIS' for graphics card
Picked 1280x800 for resolution

The rest unchanged.  

And it all worked!!!  Thanks for the help above.

---

