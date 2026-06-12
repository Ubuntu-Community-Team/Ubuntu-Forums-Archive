---
title: "Laptop Doesn't Find Wireless Card"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by taz5005 on 2008-02-25
I'm really confused about my laptop's wireless card.  I've got a Toshiba Satellite a215-s5818

I can't seem to find it anywhere...I don't see the device as being recognized at all by Ubuntu...here's my lspci output:

```
  00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge 
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) 
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914 
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915 
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) 
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA 
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) 
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) 
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) 
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) 
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) 
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14) 
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia 
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series 
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01) 
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
```

Is there something I'm missing?  I can see the ethernet connection (and it DOES connect when plugged in), but I don't see anything about wireless...

I've followed directions on this website....
[http://my-geek-side.blogspot.com/2007/08/ubuntu-on-toshiba-a215-s4747.html](http://my-geek-side.blogspot.com/2007/08/ubuntu-on-toshiba-a215-s4747.html), but still nothing...I've even got the driver they recommended installed.  If my computer can't find the wireless card I don't think I can get anywhere else.

---

### Post by taz5005 on 2008-02-25
Could someone at least tell me if the wireless device IS actually in the list of pci devices?  If it is actually in there and someone can tell me which listing it is, then I could get farther on my own, but I don't even know if I just don't understand the listing or if it's not there at all..

---

