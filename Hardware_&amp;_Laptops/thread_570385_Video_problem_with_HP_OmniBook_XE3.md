---
title: "Video problem with HP OmniBook XE3"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by joanetpics on 2007-10-08
Hello,
I'm new to Ubuntu and I have installed a 7.04 on a HP OmniBook XE3 laptop.
It's been difficult because I wasn't able to see anything so I had to use the "alternate" version and install in text mode.
When the installation have completed I had to reconfigure the xorg.conf and change "i810" driver to "vesa" driver just to see something.
Now I have a very small screen with a large black frame around. The resolution is just 640x480 and I cannot change it.
I've tried to use the 915resolution program but it doesn't work. This is the message when I try to run it:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 35758086

Can anyone help? Thanks a lot!

...
joanet

---

### Post by overdrank on 2007-10-09
> **joanetpics said:**
> Hello,
I'm new to Ubuntu and I have installed a 7.04 on a HP OmniBook XE3 laptop.
It's been difficult because I wasn't able to see anything so I had to use the "alternate" version and install in text mode.
When the installation have completed I had to reconfigure the xorg.conf and change "i810" driver to "vesa" driver just to see something.
Now I have a very small screen with a large black frame around. The resolution is just 640x480 and I cannot change it.
I've tried to use the 915resolution program but it doesn't work. This is the message when I try to run it:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 35758086

Can anyone help? Thanks a lot!

...
joanet

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by joanetpics on 2007-10-09
Hello Overdank,
Here is the result. Hope you can help ;-)

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 03)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)

---

### Post by ljonesj on 2007-10-09
try this in terminal sudo apt-get install xserver-xorg-video-intel hope it works for you

---

