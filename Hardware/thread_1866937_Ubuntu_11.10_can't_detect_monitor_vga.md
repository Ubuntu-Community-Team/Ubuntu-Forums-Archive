---
title: "Ubuntu 11.10 can't detect monitor vga"
date: 2011-10-22
forum: Hardware
---

### Post by Philip Marlowe on 2011-10-22
i was on ubuntu 11.04, now i am on ubuntu 11.10 (no upgrade, but brand new installation):
my tv doesn't recognise anymore my laptop (through vga cable): it just sees it only at the beginning (root menu), but when ubuntu 11.10 starts my tv says "no signal".
never had problem on ubuntu 11.04 with that...
i've an hp pavillion dv6000.
this is my output on terminal typing lspci:

diego@diego-HP-Pavilion-dv6000-GB190EA-ABZ:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

is it solvable? thanks

---

### Post by Philip Marlowe on 2011-10-22
is that such a stupid question? anybody had the same problem or have any ideahow to solve it? thanks!

---

### Post by seicean on 2011-10-24
> **Philip Marlowe said:**
> i was on ubuntu 11.04, now i am on ubuntu 11.10 (no upgrade, but brand new installation):
my tv doesn't recognise anymore my laptop (through vga cable): it just sees it only at the beginning (root menu), but when ubuntu 11.10 starts my tv says "no signal".
never had problem on ubuntu 11.04 with that...
i've an hp pavillion dv6000.
this is my output on terminal typing lspci:

diego@diego-HP-Pavilion-dv6000-GB190EA-ABZ:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

is it solvable? thanks

same issue here. 

I have an Acer P223W and ubuntu 11.10 doesn't recognise it via VGA out. 

still waiting for a reply

---

### Post by _Smiler_ on 2011-10-25
It would be really nice if either of you could let us know how you solved 
the issue: I'm completely ](*,)!!

---

### Post by Philip Marlowe on 2011-10-26
that's how i did solve it:
instead of installing the 11.10 directly i did install back the version i had not problem with (you can find old releases of ubuntu on the site) and then i did the upgrades step by step as described on the ubuntu wiki documentation up to the 11.10: everything is working fine now! it's a long process but it works, hope it will help ciao!

---

### Post by newnews on 2012-01-05
I have same problem. First it cannot detect dual monitors. After I spend a few time by searching the answer in internet, now both monitors are working. HOwever, it still cannot detect the correct resolution of my Dell monitor. 11.04 has no such problem. The new version 11.10 is not user friendly and hangs many times on my PC. I am going to switch back to 11.04

---

