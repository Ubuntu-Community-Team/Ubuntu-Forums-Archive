---
title: "Help with Webcam issues PLEASE!"
date: 2009-09-28
forum: Hardware
---

### Post by Archie69 on 2009-09-28
Hello all,

I have tried to resolve this issue on my own to no avail. I have an Acer Aspire 5920 and it has a Nvidia 8600GT-M w/ 512MB VRAM graphics card, and have had Ubuntu 8.04 running on it for about a year and a half with no major problems. It has a built in webcam (called the Crystal Eye) and it was working perfectly until a few weeks ago. I have recently moved to London England and need the webcam now more than I did in the past and it isn't working. I had zero issues with it when I Was back home (Canada) when using skype or msn video chats. Now that I have moved here, it no longer works.

It strikes me as odd as to why it wouldn't be working and would REALLY REALLY APPRECIATE THE HELP. PLEASE!

WHAT SHOULD I DO TO FIX THIS?

Thanks

---

### Post by i.r.id10t on 2009-09-28
run lspci and figure out what kind of cam it really is.  maybe lsusb as well.  Then post camera info and more help can happen.

---

### Post by Archie69 on 2009-09-28
So I ran Ispci and it shows this:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Hopefully that can help someone. Thanks

---

### Post by Archie69 on 2009-09-28
Sorry. Here is what it said on isusb:

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 064e:a101 Suyin Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


Anyone have any suggestions?
Anything will help

---

### Post by Archie69 on 2009-09-28
Can anyone suggest anything please?
Thanks

---

### Post by Archie69 on 2009-09-29
Anyone?
Anything?

---

