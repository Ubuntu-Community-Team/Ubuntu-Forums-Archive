---
title: "Ubuntu 8.04 - Wireless won't connect - Help please"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by Kerrileigh on 2009-05-08
Hi, installed Ubuntu 8.04 Hardy last night.  It all installed ok but it won't recognise my dlink wireless DWA-547 network card.  It's only giving me options for a wired connection or point to point connection.  I am using my other pc atm which is at the other end of the house.  Can anyone please help me on how to get it to recognise wireless.  Thanks :)

---

### Post by RedSingularity on 2009-05-08
Put lspci in terminal and post the output

---

### Post by Kerrileigh on 2009-05-08
kerri@pc2:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:06.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

---

### Post by RedSingularity on 2009-05-08
Install MADWIFI following [this](http://www.stchman.com/ath_drv.html) guide.

---

