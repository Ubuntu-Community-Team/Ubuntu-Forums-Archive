---
title: "Best driver for eVGA Nvidia AGP 6200 card and Ubuntu 12.04.4"
date: 2014-04-03
forum: Hardware
---

### Post by Scotsilv on 2014-04-03
I am salvaging an old Celeron D 352 XP machine for casual use.  Specs below.  I installed Ubuntu 12.04.4.

I had problems with the nouveau driver and an Nvidia 6200 card (details below):  on boot, sometimes the menu text characters would appear scrambled and blurred, and on shutdown a rapidly scrolling, repetitive list of text error messages about nouveau and "cache error" occurred - for about 5-10 seconds of rapid scrolling before shutdown occurred.

So I installed Nvidia driver 173.14.39 via the "additional drivers" utility and all seems OK - except for an apparent slight video sluggishness compared to XP, and the message in the Nvidia utility's "X server display configuration" section:  "*Unable to load X Server Display Configuration page: The NVIDIA X driver on ps6002:0.0 is not new enough to support the nvidia-settings Display Configuration page*."
[B]
Is 173.14.39 the best driver for the card?  Is it possible to use more recent Nvidia drivers, such as *331.49*. Release Date: 2014.2.18?  (The 6200 is not mentioned in its supported chips).[/B]

----------------------

Specs:

Video card: 

**EVGA 256-A8-N341-LX GeForce 6200 256MB 64-bit DDR AGP 8X Video Card             **
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130233](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130233)
[B]
Computer - Microcenter Powerspec 6002 Celeron D 352[/B] machine, 2Gb RAM, with these lspci specs:

                        [FONT=FreeSans][SIZE=2]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] LPC Controller (rev 36) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1) [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]mr352@ps6002:~$  [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]mr352@ps6002:~$ sudo /sbin/lsmod | grep nvidia [/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]nvidia               8118113  34  [/SIZE][/FONT]

---

### Post by Scotsilv on 2014-04-03
So I just ran the "additional drivers" utility again, and it presented the options to install ver. 173 and vers. 304 and 304 [updates].

I installed 304.116 and it works, also have the X server display config item in the Nvidia widget working.

Is it necessary to run the "additional drivers" utility more than once to get the best recommendations?  It did not present these options yesterday.

---

