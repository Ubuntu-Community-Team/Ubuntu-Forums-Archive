---
title: "My screen (Samsung SyncMaster 923nw) is not properly recognized in Ubuntu"
date: 2009-07-18
forum: Hardware
---

### Post by ldigital on 2009-07-18
I've searched the forum, but couldn't find the answer, so here's my question. 
I installed Ubuntu 9.04 on my PC. 
I installed the drivers for my graphics card, an Nvidia Geforce2 MX 100/200, but there's a problem. My screen, Samsung SyncMaster 923nw, is not properly recognized by Ubuntu and will only work in 640x480 with or without the Nvidia driver. 
In Windows XP, I always used 1280x960 without any problems, and i want that same resolution in Ubuntu. 
Does anyone know a solution for this problem? Thanks in advance!

My PC:
- Processor: Intel Pentium 4 2.8GHZ          
- Memory: 1 GB
- Graphics: Nvidia Geforce2 MX 100/200
- Screen: Samsung SyncMaster 923nw

lspci output:
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)


---

### Post by willem.deboer on 2009-07-18
I have exactly the same problem since today after installing a new LCD-monitor.

Ubuntu 9.04
Graphics: NVIDIA Geforce FX5200
Screen: Philips 190CW9

What's the cure?

---

