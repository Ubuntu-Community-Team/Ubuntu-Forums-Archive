---
title: "Intel HD Graphics 3000 on Asus N55SF"
date: 2012-04-03
forum: Hardware
---

### Post by sodoww on 2012-04-03
Hi! Recenty I bought the Asus N55SF laptop with Intel Core i7-2670QM(Intel HD Graphics 3000 inside). Shortly after I had installed the Ubuntu 11.10 I realised that it seems to be partially blind to my internal graphic card. I'm ignoring the fact that Ubuntu doesn't see my Nvidia GT 555M either, cause I don't need to use it on Linux anyway.

There's a list of few details of my problem:
- I had to append "nomodeset" to the Grub booting command to install/run Ubuntu
- No additional drivers visible to check on the "Additional Drivers" program
- "Monitor: Unknown" with 1280x1024/77hz(Can't change anything there), when I have 1920x1080 monitor with 60Hz refreshing rate

-PCI Devices-
Host bridge		: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
PCI bridge		: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
VGA compatible controller		: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
Communication controller		: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
USB Controller		: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
Audio device		: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
PCI bridge		: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode])
USB Controller		: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
ISA bridge		: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
SATA controller		: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
SMBus		: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
VGA compatible controller		: nVidia Corporation Device 1247 (rev ff) (prog-if ff)
Network controller		: Intel Corporation Centrino Wireless-N 1030 (rev 34)
USB Controller		: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
Ethernet controller		: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

- I've tested this issue on other Linux distros(Ubuntu 11.04, Mint 12 x64, Mint 12 x86 and even on Fedora 16:() same problem everywhere
- My mouse is blinking like hell when moving :P

I heard from my friend that he had a similar problem which he solved when he installed KDE desktop for Ubuntu (not Kubuntu!), but I got used to Gnome style so it's not a solution to me. Thanks all in advance!

PS. Of course I've been looking for an answer for a quite long time, but with no results
PS2. Although I'm using Linux for few years I still feel like a newbie in this system so please, be patent to me:)

---

### Post by Mark Phelps on 2012-04-04
The Hybrid Graphics is the core of the problem because Linux distros simply do not handle that well.

As to Additional Drivers, you won't see anything for Intel cards because that only applies to AMD and Nvidia chipsets.

---

### Post by sodoww on 2012-04-04
Yep, I know it, but is there any possible way to make my Ubuntu to fully use my Intel HD 3000 graphic card(3D acceleration, graphical effects in Gnome, etc.)?

---

