---
title: "Why Gusty not automatic mount SD/MMC on first login ?"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by YUMYUM9x on 2007-10-28
my laptop is acer aspire 5583 nwxmi.

use 7.04 can automatic mount SD/MMC Card but when i use 7.10 it can't automatic mount my SD card

it need to out put/in agian before mount :(

```
s$ lspci
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by YUMYUM9x on 2007-10-28
and dmesg | tail

> s$ dmesg | tail
[  984.564000] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  984.564000] usb 1-2: USB disconnect, address 4
[  984.676000] usb 1-2: new low speed USB device using uhci_hcd and address 5
[  984.872000] usb 1-2: configuration #1 chosen from 1 choice
[  984.920000] input: HID 04d9:0499 as /class/input/input8
[  984.920000] input: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1d.0-2
[ 8962.076000] tifm0 : demand removing card from socket 0:1
[ 8962.880000] tifm_core: MMC/SD card detected in socket 0:1
[ 8963.004000] mmcblk0: mmc0:b368 UD    975360KiB 
[ 8963.004000]  mmcblk0: unknown partition table

---

