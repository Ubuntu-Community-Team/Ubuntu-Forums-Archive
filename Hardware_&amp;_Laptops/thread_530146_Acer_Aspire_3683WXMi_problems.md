---
title: "Acer Aspire 3683WXMi problems"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by Azraeli on 2007-08-20
I have been using Ubuntu for a few months now, but there are just a couple things that have become problems for me recently.

Firstly I have no sound through the headphone jack anymore. I managed to get the sound working but for some reason it stopped working a couple days ago.

Secondly the integrated webcam won't work. lsusb shows that it's type is ID 5986:0100 but I have not been able to find a way to make it work. It appears to me that the problem is getting the webcam to turn on, since the computer recognises it. Camera programs show a USB camera connected but it won't work.

If anyone could help fix these problems it would be greatly appreciated.

---

### Post by nosrednaekim on 2007-08-20
could you paste your "lspci" so we can see what sound card you have?

---

### Post by unixhead on 2007-08-20
I have exactly the same problems with 3683.

> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


---

### Post by Azraeli on 2007-08-23
Yeah that's the same as mine.

A problem just popped up... I put my computer into sleep mode, and when i turned it back on the touchpad refuses to work...

---

