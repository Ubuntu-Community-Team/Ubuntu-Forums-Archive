---
title: "USB Problems"
date: 2008-05-15
forum: Hardware
---

### Post by derek72 on 2008-05-15
I'm running 8.04 and my USB drivers seemed be installed, but nothing happens when I plug in a device. Here are my specs:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)


HELP!!!!!!!!!!

---

### Post by pacrep on 2008-05-15
When usb device plugged in try this: ```
lsusb
``` to see if the device is listed.

If nothing appears then you might need to find a work around for your ports.

---

### Post by derek72 on 2008-05-15
When I use lsusb all I get it is a listing of the ports. Any device attached is not shown. What kind of work around is possible?

---

### Post by elamd on 2008-05-15
I'm having the same issue.

Devices were working fine a few days ago.

The kernel is telling me this when I plug in my mouse:

> May 15 10:17:06 Valerian kernel: [ 1712.968063] usb 1-1: new low speed USB device using uhci_hcd and address 3
May 15 10:17:07 Valerian kernel: [ 1713.144520] usb 1-1: configuration #1 chosen from 1 choice
May 15 10:17:07 Valerian kernel: [ 1713.160804] input: Acrox USB & PS/2 Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input12
May 15 10:17:07 Valerian kernel: [ 1713.202197] input,hidraw0: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:1d.0-1
May 15 10:17:08 Valerian kernel: [ 1714.169512] usb 1-1: USB disconnect, address 3
> elam@Valerian:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

---

### Post by derek72 on 2008-05-15
Mine never worked in either 7.10 or 8.04. Although my SD card reader worked once I upgraded to 8.04

---

