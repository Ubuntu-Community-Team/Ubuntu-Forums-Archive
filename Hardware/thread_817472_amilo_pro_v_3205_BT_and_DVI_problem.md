---
title: "amilo pro v 3205 BT and DVI problem"
date: 2008-06-03
forum: Hardware
---

### Post by Ciberjohn on 2008-06-03
Dear All.
I'm kind of new to this OS, been using it in a production environment since 7.10. Totally replaced windows. Only, since I upgraded from 7.10 to 8.04 I'm having some troubles, most fixed and worked arround, only two small ones to debug/correct.

1st » Used to use a lot Bluetooth transfer from my nokia N70 (pictures, videos etc). Now it only says " can't connect ". To do so, I was used do start manually Applications » Accessorys » Blue tooth File Sharing. A new antenna appears on the tray and all went well, untill my upgrade.

The other issue it's the eternal double screen issue. I really need to workaround this, cause in fact the only thing that can really make me return to Windows it's this two issues. I need to make several presentations in work and I'm using a friends laptop to do so....

I work at an ISP (we are extremly used to other distros), but concerning my personal case, I use Ubuntu, my wife to and my older daughter (edubuntu). Even the web servers I maintain, monitoring tools like FMS NAGIOS SYSORB etc, I started to use UBUNTU. But, this two "simple" issues from an plain regular user point of view, I'm not being able to solve :-( Any help/suggestion would bee very kindly appreciated.

ciberjohn@PRT-CIBERJOHN:~$ lsusb
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 0000:0000


ciberjohn@PRT-CIBERJOHN:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

