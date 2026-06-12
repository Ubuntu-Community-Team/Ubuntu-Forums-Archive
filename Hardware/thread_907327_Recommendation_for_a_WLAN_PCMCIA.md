---
title: "Recommendation for a WLAN PCMCIA?"
date: 2008-09-01
forum: Hardware
---

### Post by amityak on 2008-09-01
Hello People

im running ubuntu 8.04 on an Amilo PRO 2035v machine
(Fujitsu-Siemens), lspci attached to the end of this post.

because im too tired of struggling with my BC4813 wireless chip i've decided to try my luck with a wireless PCMCIA which will hopefully give better results. 

Are there any compability issues i should take into account before buying one? does anyone have positive expiriences?

i found on ebay (germany) the following cards, id be happy to know if someone had success with one of them:

1. WLAN Adapter PCMCIA,108M Atheros Chip eXtended Range (30€)
2. TP-Link WLAN 54Mbit PCMCIA Karte Atheros Chipset (16€)


any many other variations of the same chipset

thank ya all

and to my lspci:::::::::::

```

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

---

### Post by IntuitiveNipple on 2008-09-01
amityak, I don't want to put you off the PCMCIA/CardBus alternative but there's one other, possibly more elegant solution, too.

Most internal WiFi cards are either mini-PCI or mini-USB and come in a *standard* form-factor. They plug into a socket on the circuit board like memory chips do.

If you determined the form-factor and interface of the internal BCM4813 card in the laptop (either through research, or more reliably, by opening the laptop, you could buy a replacement internal adapter that has a chipset supported by kernel drivers, and just plug it in.

For example, I recently replaced a mini-PCI 802.11b Hermes I chipset that uses the antiquated non-WPA2 orinoco driver with an Intel iwl3945 802.11a/b/g which works perfectly. It cost about US$50 and is well worth it for the convenience.

---

