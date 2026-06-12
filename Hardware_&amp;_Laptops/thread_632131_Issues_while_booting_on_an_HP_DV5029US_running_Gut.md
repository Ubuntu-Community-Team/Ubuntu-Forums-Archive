---
title: "Issues while booting on an HP DV5029US running Gutsy 7.10"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by firemagican2845 on 2007-12-05
Hey all I'm fairly new with Ubuntu and I'm having an issue I can't seem to find out how to fix.

When I start up the system and it gets through GRUB and the kernel starts to load I get a few messages and then a black screen. I never see the Ubuntu Splash Screen either. Once it goes into this black screen I have to hit CTRL + Alt + F1 to make it continue the system start up or it sits there for hours. Heres the system info and the messages.

System Info:

Model: HP DV5029US
Processor: AMD Turion 64
Ubuntu Version: Gutsy 7.10 32 Bit
Graphics Card: ATI Raidon Xpress 200m
Ram: 1024MB

Messages:

> Starting Up...
[0.000000<---These numbers are always random]PCI: Cannot allocate resources to region 7 of Bridge 0000:00:05.0
[0.000000<---These numbers are always random]PCI: Cannot allocate resources to region 8 of Bridge 0000:00:05.0
Loading please wait...
[0,000000<---These numbers are always random]8139CP 0000.06:06.0 This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[0.000000<---These numbers are always random]8139CP 0000:06:06.0 Try the "8139too" driver instead.

So anyone have any idea whats going on? I figure its the ATI Card Driver. I can't use Compiz effects at all. 



---

### Post by firemagican2845 on 2007-12-05
bump for the morning crew :P

---

### Post by firemagican2845 on 2007-12-05
I guess this is an issue with 7.10. I did a reinstall with 7.04 and the problem went away. 

~Fire

---

### Post by Yellow Pasque on 2007-12-05
Good to hear you got it fixed, but I wonder what it was.
> This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Sounds like it has something to do with your Network card/chip (Realtek 8139). For posterity's sake, can you do:
```
sudo update-pciids; lspci
``` and post the output? Thx.

---

### Post by firemagican2845 on 2007-12-06
Sure thing. Here it is.

> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Though keep in mind this is from 7.04 now. Not from 7.10 where I had the error.

---

### Post by Yellow Pasque on 2007-12-06
> Though keep in mind this is from 7.04 now. Not from 7.10 where I had the error.
That's ok. Your hardware's still the same.

Thanks for that. It looks like your network card is indeed an 8139, so I'm guessing that the PCI error caused that problem. Hopefully, no one has to deal with this error.

---

