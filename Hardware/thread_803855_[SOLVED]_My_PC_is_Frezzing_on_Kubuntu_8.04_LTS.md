---
title: "[SOLVED] My PC is Frezzing on Kubuntu 8.04 LTS"
date: 2008-05-22
forum: Hardware
---

### Post by nettobr on 2008-05-22
Hi everyboby,

On Kubuntu 7.10, only Firefox 2.0.0.12 was freezing my PC.

Now, on Kubuntu 8.04 LTS my PC is freezing on any application, even on pacience card game.

I Think it's due to Video Board installed - I had to install the generic Driver (Safe Mode) because the video board automaticaly recognized just did a mess on my monitor.

My PC has a Gigabyte VM900 M.Board, 1 Gb Ram and onboard VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
Monitor Sony HSM-75

Has anybody seen this problem???

Other: USB only works if I set CMOS to 1.1 USB Support.

Thanks from Brazil,

Nettobr

lspci says:
lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:05.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
vieira@vieira-desktop:~$

And lsusb says:
lsusb
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 2001:3c00 D-Link Corp. [hex] DWL-G122 802.11g rev. B1 [ralink]
Bus 001 Device 001: ID 0000:0000

---

### Post by nettobr on 2008-05-26
Hi Everybody,

I think problem is solved by installing the VGA driver from Via Linux.

Thanks from Brazil,

NettoBr

---

### Post by nettobr on 2008-05-28
Really solved.

Thanks from Brazil,

NettoBr

---

