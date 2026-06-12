---
title: "Ubuntu on a toshiba laptop- wireless"
date: 2010-06-10
forum: Hardware
---

### Post by kaze11 on 2010-06-10
I'm trying to install ubuntu solely on a toshiba satelite L100-179.
All seems to work fine except for the internet. Plugging it in works but the wireless doesn't, it doesn't seem to recognize the wireless adapter built into the mb.
Any clue how to figure this out?- even advice on how to find out what model wireless adapter I'm looking for the drivers for would help as frankly I haven't a clue.

---

### Post by roger_1960 on 2010-06-10
Hi

Can you post the ouput from > lspci

(Type this in the terminal window and press return)

This should indicate your wireless adapter

---

### Post by kaze11 on 2010-06-10
It seems to be running rather slow actually...think it may be missing its other drivers too, dang.




00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
gary@gary-laptop:~$

---

### Post by roger_1960 on 2010-06-10
Hi again Gary

The Broadcom BCM4318 has lots of posts relating to it.  Suggest you do a search for it in these forums and look at what comes up.

---

