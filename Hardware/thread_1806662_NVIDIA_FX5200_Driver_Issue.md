---
title: "NVIDIA FX5200 Driver Issue"
date: 2011-07-18
forum: Hardware
---

### Post by pitbwv on 2011-07-18
I've been having this trouble for over a year now and can't seem to find any solution to my problem on the Ubuntu forms or google. I have a Dell Demision 8300 P4 2.8Ghz, 1GB RAM, 84GB HDD. My problem is with the NVIDIA GeForce FX 5200 card with 128MB RAM. I stated off in Ubuntu Maverick Meerkat and now working under Natty Narwhal. So far every time I install the driver (173) recommended from the Additional Hardware Wizard or manually from NVIDIA site I reboot my computer start normally pass POST into the GRUB loader. A few seconds later my screen goes black then the monitor kicks into power save mode. The only was to restart the computer is by hard shutdown. No sound, keyboard, mouse. I'm currently using the Experimental 3d driver provided by the community but I would like to use the full function of the card to learn Blender. Has anyone also had this problem and has anyone found a solution???? I have tried working with the xconfig.org settings, manual tweaking and ton's of idea's from the community. I'm pretty good with computers (from Win 3.11 to XP/Vista) and just now really getting settled into Linux. Any help is APRECIATED!!!!
 
Thank.
B.

---

### Post by CMOS4081 on 2011-07-18
Is this card AGP or PCI? It comes in both so thats why I am asking besides your motherboard has an AGP 8x slot according to Dell's specs. [http://support.dell.com/support/edocs/systems/dim8300/sm/specs.htm#1102218]("http://support.dell.com/support/edocs/systems/dim8300/sm/specs.htm#1102218")
Is your BIOS set to match your video card? PCI or AGP. Old Dell desktops have either AUTO, Onboard or PCI as options.

Nvidia driver for your card is the one you selected. 
"173.14.30 Certified"

Try removing any additional cards from your system and see what happens. It could be your power supply might be on the low end. 

Is this a dual boot system running Windows, and does it work?

I seen this happen when people use the PCI version of the card with another video card or onboard while using Windows. The onboard must be disabled so the addon is seen as the primary video adaptor to the OS.

run a lspci as root and post the results if you can.

---

### Post by pitbwv on 2011-07-18
It is a 8x AGP Card.  No Onboard Video, BIOS is up to date using 128MB on AGP.  No other Video source is listed in BIOS/ No other Video Cards installed.  I'm not duel booting on this computer.  There is a driver issues with this card since WinXP Sp3 came out.  Microsoft pushed an update to one of the drivers components and caused BSOD every time.  MS and NVIDIA no longer support the Card so they wont fix the bug in Windows.  Here is the output of lspci:

00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by BlueAngel-CPT on 2012-01-04
I found this thread browsing the net, hoping for a solution to my problem. I've got a very similar problem to yours. Have you managed to find a solution as yet?

I've also got the Nvidia FX 5200 card and the machine was happily working in 10.10 Maverick Meerkat (restricted drivers working,3d enabled,compiz working) when I (foolishly) decided it was time to upgrade my Ubuntu installation. Upgrading from 10.10 -> 11.04 caused the driver to stop working, so I had to revert to the default open source nouveau driver, which caused screen resolution issues. I'd hoped that the issue would be fixed in 11.10, so I upgraded to that as well, but no.

If anyone knows how to get this working in Ubuntu 11.04 or 11.10 that would be fantastic!

---

### Post by crazy bird on 2012-01-04
Try updating your nvidia driver with the x-swat PPA, [click here]("http://ubuntuforums.org/showpost.php?p=11583627&postcount=2") to read how to do it.

---

### Post by Sverige_Torsten on 2012-01-04
[http://ubuntuforums.org/showthread.php?t=1904230](http://ubuntuforums.org/showthread.php?t=1904230)

Try that. It is a fresh 11.10 install, so you probably would like to backup your stuff first.

---

