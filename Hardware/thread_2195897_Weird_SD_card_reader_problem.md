---
title: "Weird SD card reader problem"
date: 2013-12-27
forum: Hardware
---

### Post by Ertai87 on 2013-12-27
Hi all!  I have a strange problem with my SD Card reader.  When I put the SD card into the reader once, it works fine.  Then I remove it and attempt to put it in again, and the computer simply refuses to recognize it.  I have no idea what the cause of this is.  Here's some output for you guys to analyze:

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

dmesg:

```

[16216.412117] r852: detected xD writeable card in slot
[16216.716106] No NAND device found
[16217.107461] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.109657] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.122375] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.171459] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.176002] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.186450] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.299532] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.303900] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16217.315962] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16235.487438] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16235.493775] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16235.559611] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16235.570040] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16235.621835] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16235.635735] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16235.687792] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16265.741649] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16265.754125] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16265.807661] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16265.867764] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16265.870169] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.
[16265.882899] mmc0: Got command interrupt 0x00030000 even though no command operation was in progress.

```

The SD card reader appears to be working, but then randomly cuts out for some reason.  Using a newly store-bought SD card appears to make the reader work again for that card, but then that card also works only once or twice before the reader won't recognize it either.  Also, all cards I've tried so far are SDHC cards; I don't own any regular SD cards to test it with.  I am also using standard-size SD cards and no funny business with expanders.

Any ideas?

---

### Post by Ertai87 on 2013-12-27
Apparently I googled everything but the one thing I needed to Google.  I found a patchwork solution in the last post on this thread, but if there is a more permanent solution I'd like to hear about it, which is why I'm leaving this thread marked unsolved.

Temporary solution: [http://ubuntuforums.org/showthread.php?t=1611491&page=3](http://ubuntuforums.org/showthread.php?t=1611491&page=3)

---

