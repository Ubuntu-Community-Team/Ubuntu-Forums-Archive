---
title: "(Another)SATA hard drive not recognised"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by chandru on 2005-05-06
Hi,

I have been trying to install hoary on an AMD64 machine(AMD64 distribution). Everything  is detected except for the sata hard disk.

The drive is Seagate ST3200822AS. I think the motherboard is ATI(but I can't find out).

All usb drives, card readers and dvd drives are picked up.I can get the system up using a livecd but there is no hard disk detected.

lspci shows
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:11.0 IDE interface: ATI Technologies Inc: Unknown device 437a
0000:00:12.0 IDE interface: ATI Technologies Inc: Unknown device 4379
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 04)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70
0000:02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 05)
0000:02:01.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)
0000:02:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

Any help will be appreciated.

Thanks

Chandru

---

### Post by chandru on 2005-05-06
Sorry to reply to my own post. 

The motherboard is MS 7093 with ATI SB400 chipset. Apparently chipset is supported under the sata_sil driver from kernel version 2.6.11. 

It appear I need to wait for the next release or probably breezy experimental

Thanks.

---

### Post by jtc970 on 2005-07-06
[QUOTE=chandru]Sorry to reply to my own post. 

The motherboard is MS 7093 with ATI SB400 chipset. Apparently chipset is supported under the sata_sil driver from kernel version 2.6.11. 

It appear I need to wait for the next release or probably breezy experimental

Thanks.[/QUOTE]
 Im havin the same problem, I only have the sata drive and it's not being recognized :(
SHould I got and buy a new motherboard? It doesnt seem like ATI is much for linux

---

