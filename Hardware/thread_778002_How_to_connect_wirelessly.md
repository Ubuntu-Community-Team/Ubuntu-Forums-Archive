---
title: "How to connect wirelessly?"
date: 2008-05-01
forum: Hardware
---

### Post by antwolf on 2008-05-01
I'm not only new to Ubuntu, I'm also kinda new to computer's, so please go easy with me. What I'm asking for is a step by step on how to connect wirelessly. I've been going through the forums here and what I've been seeing so far is to go to terminal and to apply commands. I don't know how this is done and where to go to begin to try. No problems connecting to the Internet wired. I thank you in advance.

My laptop is an HP Pavilion dv2000. If you need more information please let me know.

---

### Post by antwolf on 2008-05-02
It's been 23 hours, 15 views, and no replies. Thanks for making me feel welcome.

---

### Post by mariner09 on 2008-05-03
Well, don't get brash in your 1st bump, that's not going to get you far.

You have Ubuntu installed, so you got to the internet somehow.

Usually there's a tool running by default in the upper right corner called NetworkManager.  If it looks like 4 bars, then you're connected to wireless.  If it looks like 2 PCs, then you're not.  A simple left-click on the icon will show a list of available access points.  Click one and if it's open, you should connect.  You can't do both ethernet and wireless at the same time, so it's one or the other.

Let us know how you make out...

---

### Post by Ayuthia on 2008-05-03
> **antwolf said:**
> I'm not only new to Ubuntu, I'm also kinda new to computer's, so please go easy with me. What I'm asking for is a step by step on how to connect wirelessly. I've been going through the forums here and what I've been seeing so far is to go to terminal and to apply commands. I don't know how this is done and where to go to begin to try. No problems connecting to the Internet wired. I thank you in advance.

My laptop is an HP Pavilion dv2000. If you need more information please let me know.From the Terminal, can you post your lspci -nn information?  It will help us figure out what wireless card you have.  HP has been using Intel, Broadcom, and Atheros cards.

---

### Post by poboxjosh on 2008-08-15
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
08:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

---

### Post by kspncr on 2008-08-15
You can try this thread: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

Should work on an HP Pavilion dv2000.

---

