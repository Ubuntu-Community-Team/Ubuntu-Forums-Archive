---
title: "Ubuntu 14.04 won't use second video card"
date: 2015-10-11
forum: Hardware
---

### Post by Joe_DePalma on 2015-10-11
Hi all! Been a while since I've posted.  Was able to figure out the three monitor issue I had last time around with Ubuntu 12.04.  Upgraded to a Lenovo W500 (Intel Core 2 Duo T9900 3.07 GHz, 8 GB RAM) and a dual hard drive setup (64 GB SSD /root and 320 GB WD Black /home) with switchable graphics.  I have been trying to get the three monitor support on this laptop.  I've been crawling around the forums for a while but a lot of the info is _***very old***_ and no longer relevant to more current versions of Ubuntu.  

I dock the laptop in the Lenovo 2503 Advanced Dock, which has a 1X PCI-e slot for precisely this purpose.  I installed a older ATI Radeon HD 4650 x16 PCI-e card I pulled from an old desktop and the computer recognizes it:  

jdepalma@jdepalma-ThinkPad-W500:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV635/M86 [Mobility Radeon HD 3650]
0d:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730 PRO [Radeon HD 4650]

When I go to ARandR to try and initialize the monitor I have hooked up to the card's DVI out, it is not there.  The monitor recognizes that it is hooked up as it went into power save.  I'd be curious to know if anyone has a suggestion.  It may be that the tech is too old but I honestly do not know.  Do I have to enable it somehow via its hardware address?  Thanks in advance.

---

