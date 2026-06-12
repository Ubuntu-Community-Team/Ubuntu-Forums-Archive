---
title: "Fresh install of ubuntu 9.10, but wireless doesn't work anymore"
date: 2010-03-16
forum: Hardware
---

### Post by jtso8 on 2010-03-16
I reinstalled ubuntu onto my laptop.  I first installed ubuntu 9.04 and my wireless card was found.  Everything worked fine and even when i upgraded to 9.10 my internet would not work once i restarded.  After a quick restart everything worked fine.  When i did a fresh install of ubuntu 9.10 my wireless driver was not found.  Does anyone have any ideas what is going on here.

---

### Post by devildoc5 on 2010-03-16
What kind of comp?  What kind of wireless card?

---

### Post by jtso8 on 2010-03-17
I have a dell inspirion 1501.  I"m not sure about the wireless card but i thinks its a wireless 1505 draft 802.11n WLAN mini-card.

---

### Post by 2hot6ft2 on 2010-03-17
Open a terminal
Applications > Accessories > Terminal
and run
```
lspci
```
That's LSPCI in lower case, and post the results.

---

### Post by jtso8 on 2010-03-17
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

---

### Post by norseman-has-a-laptop on 2010-03-18
ndiswrapper insall package offline look it up

---

### Post by devildoc5 on 2010-03-18
The other option that worked for me (ndis wrapper and fw-cutter didnt)  would be to download the b43 and b43 legacy drivers to a thumb drive, then place them into the appropriate folder.  I cant honestly remember what it was anymore, but I found the tutorial on here.  Think it was at ubuntu wiki.  Cant seem to find the web address either, but it shouldn't be too hard to locate.  Just try "b43 driver offline ubuntu wiki" and it should bring it up fro myour favorite search engine...Good Luck!

---

### Post by jtso8 on 2010-03-19
i know of other ways of making my wireless card to work, but its just really weird that 9.10 cannot find the drivers for it.  Do they every delete drivers from the database.  I"m just trying to figure what what different about 9.10 from 9.04

---

