---
title: "ASUS DRW-24B1ST not detected after boot"
date: 2011-08-03
forum: Hardware
---

### Post by h82bu on 2011-08-03
Hi,
I must give the classic newbie apology (I'm new to linux, I've had a relatively easy time learning new things, but have a long way to go. I'm currently stuck, I've done some browsing and tried some things to no avail).

Problem: I cannot access any cds/dvds when I place them in my optical drive. 

My rough interpretation: Kubuntu 11.04 is not detecting my ASUS DRW-24B1ST dvd burner. 

Background: I currently have a dual boot set up with Win 7 and Linux.  The cd/dvd drive is detected by windows without any problems.  When I boot to the bios, it detects the cd/dvd drive without any problem.  When I boot to linux, I no longer have a usable cd/dvd drive.

Feeble attempts: I looked into this issue and figured it was a problem with mounting the device, so I gave my best shot at manually mounting the device, but the more I tried that route, the more it looked like the device was just not being detected. 

I found one post in the desktop incompatibility post that looked like someone else had problems with this cd/dvd burner, but I've also read people that had it working out of the box.

Without providing too much more useless info, I'll wait to see if someone can help guide me along the right path to diagnosing my problem, hopefully enlightening me along the way.

PS (not sure of the appropriateness/helpfulness). I ran lspci and here was the output:

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
05:00.0 PCI bridge: Device 1b21:1080 (rev 01)
06:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
07:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
09:00.0 SATA controller: JMicron Technology Corp. JMB362 AHCI Controller (rev 10)

Thank you for your time!
Craig

---

### Post by Andy0 on 2011-12-15
^ Bump

Same issue on a new build. 

Ubuntu 10.10
Mobo: Gigabyte GA-Z68X-UD3H-B3 Socket 1155
Main chipset: Intel Z68
Secondary chipset: Marvell 88SE9172 (DVD Drive connected here)
DVD Drive: ASUS DRW-24B1ST

---

