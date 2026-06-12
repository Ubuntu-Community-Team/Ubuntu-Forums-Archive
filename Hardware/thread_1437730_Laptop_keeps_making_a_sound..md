---
title: "Laptop keeps making a sound."
date: 2010-03-24
forum: Hardware
---

### Post by elektrisk564 on 2010-03-24
Hello.
My laptop, which is running Ubuntu 9.10, will periodically make a sound that sounds like someone is plugging something into a sound jack. I will try to get a recording of it, but that doesn't seem likely anytime soon.

I tried disabling my internal mic, and that didn't fix it. It makes it even when my speakers are muted, which makes me think it's because some hardware is not correctly configured. I have an HP dv6236us laptop.

Here is my lspci output. Dunno if it will help, but it can't hurt:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```Then, here's lspci -n
```
00:00.0 0600: 8086:27a0 (rev 03)
00:02.0 0300: 8086:27a2 (rev 03)
00:02.1 0380: 8086:27a6 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27b9 (rev 02)
00:1f.2 0101: 8086:27c4 (rev 02)
00:1f.3 0c05: 8086:27da (rev 02)
02:00.0 0280: 14e4:4311 (rev 01)
05:05.0 0c00: 1180:0832
05:05.1 0805: 1180:0822 (rev 19)
05:05.2 0880: 1180:0843 (rev 0a)
05:05.3 0880: 1180:0592 (rev 05)
05:05.4 0880: 1180:0852 (rev ff)
05:08.0 0200: 8086:1092 (rev 02)

```According to [this]("http://kmuto.jp/debian/hcl/") site, after having read my lspci -n log, the drivers for this hardware is missing on my system:

82801G (ICH7 Family) PCI Express Port 1
82801G (ICH7 Family) PCI Express Port 2
82801G (ICH7 Family) USB UHCI Controller #1
82801G (ICH7 Family) USB UHCI Controller #2
82801G (ICH7 Family) USB UHCI Controller #3
82801G (ICH7 Family) USB UHCI Controller #4
82801G (ICH7 Family) USB2 EHCI Controller
R5C832 IEEE 1394 Controller
R5C592 Memory Stick Bus Host Adapter
xD-Picture Card Controller

Could those missing drivers be the culprit?

If I left out any important information, let me know. Thanks.

---

### Post by elektrisk564 on 2010-03-24
Please help me, if you have time.

---

### Post by elektrisk564 on 2010-03-28
Bump. Please assist me.

---

### Post by elektrisk564 on 2010-03-29
Bump.
My harddrive is made by Fujitsu, if that helps.

---

### Post by Fafler on 2010-03-29
Well, a quick and dirty hack, if you doesn't need sound anyway, would be a unconnected jack in the headphone port. But i don't know how else to fix it, except maybe to look in the BIOS?

---

