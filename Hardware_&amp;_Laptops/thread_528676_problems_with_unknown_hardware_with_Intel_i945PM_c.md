---
title: "problems with unknown hardware with Intel i945PM chipset"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by Guyver1 on 2007-08-18
Hi,

currently dual booting on my new Alienware m9750 laptop.

Spec:
Display: 17" WideUXGA 1920 x 1200 LCD with Clearview Technology - Stealth Black 
Operating System: Genuine Windows® XP Professional UK with SP2 - English 
TV Tuner: None 
Processor: Intel® Core&#8482; 2 Duo Processor T7600 2.33GHz 4MB Cache 667MHz FSB 
Graphics Processor : Dual 512MB NVidia® GeForce&#8482; Go 7950 GTX - SLI Enabled 
Memory: 2GB Dual Channel DDR2 SO-DIMM at 667MHz - 2 x 1024MB 
System Drive: Single Drive Configuration - 160GB 7200 RPM SATA 
Optical Drive: 8x Dual Layer DVD+/-RW / 24x CD-RW Combo with Nero Software 
Sound Hardware: Intel® High-Definition Audio (24-bit, 192Khz) with surround sound 
Keypad: Mobile Keypad - English 
Wireless Network Card: Internal Intel® Wireless 4965 a/b/g/Draft-N Mini-Card 
Communications: Integrated 10/1000Mb Gigabit Ethernet & 56K V.92 Modem 
Floppy Drive: USB Floppy Drive 
Bluetooth: Integrated Bluetooth® Device 

Motherboard uses the i945PM chipset that has a 82801GHM (ICH7-M DH) southbridge.

Problem i'm getting is that half the motherboard related components dont get recognised in Ubuntu meaning i have lots of unknown devices showing up and i cant get SLI working for my 2 GFX cards. 

heres my Windows XP device list followed by my ubuntu device list:

[IMG]http://www.guyver1.net/stuff/windows_devices.jpg[/IMG]

[IMG]http://www.guyver1.net/stuff/linux_devices.jpg[/IMG]

you can see that some of the PCI exress root ports are missing, one of which is the SLI link which allows the system to show the 2 GFX cards linked which allows SLI to work properly.

when i follow the advice here: [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/chapter-25.html)

/sbin/lspci | grep -i vga

i only get 1 GFX card listed instead of 2.

are there a full set of Intel drivers for linux for this chipset? as it seems the inbuilt support for this chipset in Feisty is lacking alot.

cheers

---

### Post by Guyver1 on 2007-08-22
bump.

anybody?

---

