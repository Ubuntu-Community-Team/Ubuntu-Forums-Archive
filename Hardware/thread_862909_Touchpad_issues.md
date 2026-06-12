---
title: "Touchpad issues"
date: 2008-07-17
forum: Hardware
---

### Post by niglch on 2008-07-17
I just got my Dell XPS M1530 and I tried using the Ubuntu live CD (8.04) to see if I would be lucky enough to have it work out of the box. Although everything else is working fine to my knowledge, the touchpad seems to have issues. If I try to move the mouse, it jumps around and left and right clicks very rapidly basically at random. Is there any special driver that I need to install or is it possibly just incompatible. The touchpad is simply specified as a "Dell Touchpad".

---

### Post by sergiom99 on 2008-07-18
please post the output of:
lspci
lsusb

to see if there's more hardware info there.

---

### Post by niglch on 2008-07-18
Ok, here's the output that I got:
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000
```
I can't really make much of it myself but hopefully someone will. Also, sometimes the touchpad will respond OK but will move extremely slowly (even at the fastest setting) but I was only able to reproduce this once. Also, sometimes it won't respond at all.

---

### Post by niglch on 2008-07-19
Maybe I should be more specific about the problem. On the Hardy Heron live CD when I try to use the touchpad it doesn't even respond for the most part (nothing happens when I use the buttons or try to move my finger across the pad). Occasionally when using the touchpad, the mouse rapidly and randomly jumps around and clicks on stuff. Usually the result is a bunch of new folders getting scattered across my desktop or programs getting randomly opened if the mouse so happens to jump onto the applications bar. I've searched around the forums and on Google and can't seem to find anyone with quite the same problem. It's kind of strange because the M1530 is the same model laptop that I know Dell pre-installs Ubuntu on (although I bought it with Vista) so I expected it to pretty much work out of the box. So much for that idea...

---

