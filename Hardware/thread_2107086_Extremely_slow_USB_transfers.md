---
title: "Extremely slow USB transfers"
date: 2013-01-21
forum: Hardware
---

### Post by skinnypeteyo on 2013-01-21
I have been experiencing an ongoing problem with my ubuntu install that is driving me crazy.  I have a few external usb hard drives hooked up to my PC that are getting very slow transfer speeds.  At one point I had windows xp installed on this same PC and my transfer speeds were fine, so I know its not a hardware problem. 

Typically if I'm transferring something from the internal hard drive to the external or vice versa, I top out at speeds around 1 mb/s.  BUT if I transfer something from a samba share on my home network to one of the external drives, I get better speeds--around 1.5 mb/s.

I initially thought the problem was the fact that my external was formatted NTFS.  However I reformatted it as ext4 and I'm experiencing the same problems. 

I am using an old motherboard: an ECS [RS482-M754]("http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=1&DetailID=537&MenuID=24&LanID=9").  I thought it might have been an issue with the on-board USB, so I purchased a USB 2.0 PCI card.  But I get the same slow transfer speeds whether it is plugged into the PCI card or the onboard USB ports.  I've also tried enabling and disabling the "Legacy USB support" option in my BIOS, but no change.  

Both of my external  hard drives are USB 2.0.  I have tried plugging it into all of the different USB ports on my computer without any change. I hook up the same hard drives to my netbook running Ubuntu 12.10 and I get 30 mb/s transfer speeds.  

I was running 32 bit Ubuntu 12.04 on this computer.  I just changed to 64 bit Lubuntu 12.10 but I am experiencing the same problem.  

I have also tried messing with the "pci=routeirq" and "pci=noacpi" options in my GRUB configuration, but I still get the same slow transfer speeds.

In short, I'm banging my head against a wall and would greatly appreciate any help with this problem.  

Here is my lsusb output:

```
Bus 001 Device 003: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 005 Device 002: ID 15d9:0a33 Trust International B.V. Optical Mouse
Bus 005 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

* Note * At this point my external hard drive was plugged into the PCI usb 2.0 card, and not the onboard USB.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Radeon HD 4350]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]
02:01.0 USB controller: NEC Corporation USB (rev 44)
02:01.1 USB controller: NEC Corporation USB 2.0 (rev 05)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

