---
title: "WQHD 2560 x 1440 resolution"
date: 2013-04-03
forum: Hardware
---

### Post by SamTzu on 2013-04-03
How can I get WQHD 2560 x 1440 resolution with dual link DVI cable.
It does not seem to work. I can only get 1900x1200.

---

### Post by gordintoronto on 2013-04-03
It might be helpful if you told people the version of Ubuntu you are using, whether you installed an Additional Driver, the brand and model of your monitor, and the brand and model of your video card. Also, run this command and paste in the line which includes "VGA":
lspci

Also, what refresh rate have you specified? "At 2560x1600 you can only do 60Hz."

---

### Post by SamTzu on 2013-04-04
I have Ubuntu 12.10.
The Software Sources, Additional Drivers sayz...
Using X.Org X server - AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)
Monitor is capable of displaying WQHD resolution (and has dual link cable.)

sami@sami:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 **VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cayman PRO [Radeon HD 6950]**
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]
07:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)

---

### Post by SamTzu on 2013-04-23
The monitor is [Dell 27" U2713HM]("http://www.dell.com/ed/business/p/dell-u2713hm/pd").

---

