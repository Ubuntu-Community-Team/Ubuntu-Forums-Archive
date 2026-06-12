---
title: "Laptop Subwoofer not working."
date: 2008-09-15
forum: General Help
---

### Post by jjg5065 on 2008-09-15
Hi, I have a Lenovo Ideapad Y510, and I cannot for the life of me figure out how to get my surround sound to work. I have a built in sub and in windows I have great sound, but when working in Ubuntu, I can barely hear my music. When I type lspci into the terminal, this is what I get 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Thanks!

---

### Post by Corporal Nickel on 2008-09-15
Did you Install Drivers and make sure ubuntu is up to date? its really useful to also Google things. ;)

---

### Post by jjg5065 on 2008-09-17
I have updated my ubuntu as much as I can, including the restricted software and drivers, it still doesn't work. Most of my google search results tell me to configure alsa mixer, I'm pretty sure I did it correctly, but it still doesn't work. Anybody have any idea what I'm supposed to do?

---

### Post by sanso on 2010-07-21
any news on this? I am affected as well. No subwoofer functionality in 10.04. :(

---

### Post by treesurf on 2010-08-23
Check this thread:

[http://forums.lenovo.com/t5/IdeaPad-Y-and-U-series-Laptops/Ubuntu-Linux-Support/td-p/16842/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-and-U-series-Laptops/Ubuntu-Linux-Support/td-p/16842/page/2)

And also try installing the newest version of ALSA:
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Now, if someone could tell me how to do this on a Lenovo Y550 I'd be quite grateful!

---

