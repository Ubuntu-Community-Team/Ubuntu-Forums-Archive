---
title: "Toshiba Qosmio f30 auto eth0 missing"
date: 2009-10-21
forum: Hardware
---

### Post by micdhack on 2009-10-21
I ve installed the beta karmic on a toshiba qosmio f30. Everything works fine except the ethernet is missing. Wireless works fine but i cant connect through a wire. The wire works with another laptop that i have.
The module that is loaded is e100 and when it is loaded, on the network manager i can see the wire network menu but i have no option auto eth0 to select.
In addition i tried killing the network manager, use dhclient eth0 and various settings on /etc/networks/interfaces as eth0 inet dhcp but also static settings. Nothing worked!
Also tried to boot the kernel with noapic option and still nothing.
Any ideas?

My lspci
[code]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce Go 7600] (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
06:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
06:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:0b.3 SD Host cont[code]

---

### Post by micdhack on 2009-10-21
Turns out that the cable was incombatible with that laptop. I changed it with another and it worked perfectly.

---

