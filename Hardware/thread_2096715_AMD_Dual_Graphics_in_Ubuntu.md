---
title: "AMD Dual Graphics in Ubuntu?"
date: 2012-12-20
forum: Hardware
---

### Post by m3t4lm4n222 on 2012-12-20
Hi. Steam Beta has come to Linux and I am ready to make the switch BUT I have one problem. I run AMD Dual Graphics (A10-5800K + 6670) and it needs to be enabled via CCC/AMD Vision Center. Will this be possible with Ubuntu? If so..HOW?


Thank you very much :D

---

### Post by m3t4lm4n222 on 2012-12-20
Sorry for an early bump but I am highly curious. This could make or break my decision to switch.

---

### Post by m3t4lm4n222 on 2012-12-21
NOthing?

---

### Post by grahammechanical on 2012-12-21
It all depends upon the video drivers does it not? Does AMD provide a Linux version of that CCC/AMD vision control centre? Or is it part of the AMD/ATI proprietary video driver?

I would install Ubuntu in a separate partition and dual boot and test things out before you switch. I never upgrade from one version of Ubuntu to the newer version until I have proved that the new version can be set up the way I like it. You only need 10 - 15GB of disk space to test Ubuntu in this way.

You might be interested in the first post at the top of this page:

[http://www.webupd8.org/]("http://www.webupd8.org/")

Regards.

---

### Post by m3t4lm4n222 on 2012-12-21
Well I installed 12.11 Beta drivers and got into CCC but there's no section showing "AMD Dual Graphics" like there is in Windows. With 12.10 there was a CrossfireX section but it was all greyed out. + Unity wouldn't work with 12.10 for some odd reason. Neither will the ATI Binary Driver guide methods.

---

### Post by m3t4lm4n222 on 2012-12-21
Just went through a AMD provided PDF file and it says this:

> Radeon Dual Graphics requires an AMD "A" Series APU plus an AMD Radeon discrete graphics configuration and is available on WIndows 7.** Linux OS supports manual switching which requires restart of X-Server to engage and/or disengage the discrete graphics processor for dual graphics compatibility**
What does this mean???


My LSPCI says 

> austin@TrinityJames:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7660D]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:15.2 PCI bridge: Advanced Micro Devices [AMD] Device 43a2
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Turks [Radeon HD 6670]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 09)





---

### Post by v4mpiro on 2012-12-22
Hi. I don't know if it can help but i want to share with you my situation: notebook with dual ati gpu: 4200 integrated + 5650 discrete. I've never been able to use the discrete 5650 card on linux with amd proprietary drivers. I have to use windows to play games and also to watch hd videos. It seems there's no solution, switching is NOT supported. I will sell this notebook and buy forever nvidia stuff. Greetings

---

