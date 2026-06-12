---
title: "HP Compaq 8510w cdrom not working (Fiesty Fawn)"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by DaBump on 2007-08-15
Hallo there. I recently purchased a new HP Compaq 8510w notebook. I noticed yesterday, that when I insert a cd, ubuntu does nothing. Does not even mount the cd. I then tried to mount the medium myself, and I got the following:

> mount: special device /dev/scd0 does not exist

I've got a feeling that the cdrom connects to the mainboard in a funny way. Does anybody have any ideas whats wrong here, I'll attach the lspci and lsusb results here:

lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile HECI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 040c (rev a1)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 03)
02:06.3 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 10)
03:00.0 USB Controller: NEC Corporation USB (rev 43)
03:00.1 USB Controller: NEC Corporation USB (rev 43)
10:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)


lsusb:
> Bus 009 Device 001: ID 0000:0000  
Bus 008 Device 002: ID 12d1:1001  
Bus 008 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Thanks for the help!
Martin

---

### Post by DaBump on 2007-08-20
Anybody?

---

### Post by marlus on 2007-08-20
Hi, I don't know about the 8510W but I have a 6710b and there the same problem is solved
with:

modprobe piix

To make it permanent add piix to /etc/modules

hope it helps

---

### Post by DaBump on 2007-08-22
Hi Marlus, this worked perfectly. What I did in the meantime was to add the 'all_generic_ide' option to the kernel options (When booting using grub), which also solved the problem.

Thanks again,
Martin Coetzee (South Africa)  :KS

---

