---
title: "SD Card reader not working in dell 1420"
date: 2008-12-17
forum: Hardware
---

### Post by Vandrerol on 2008-12-17
Hello, I'm a newbie having a strange problem with my internal sdcard reader.

First of all, here's my lspci

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

I'm guessing "03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)" is what I'm interested in.

Now *when I put in a card* a disk appears in my 'Computer' folder that says SD/MMC Drive, however it cannot be opened or mounted, and nothing appears in the desktop or in /media.

In fdisk -l I can only see my internal disks and my external HD, nothing else. My dmesg screams in agony when I plug in the card, this is the | tail.

```
[ 2629.070247] end_request: I/O error, dev mmcblk0, sector 0
[ 2629.070254] end_request: I/O error, dev mmcblk0, sector 8
[ 2629.070257] end_request: I/O error, dev mmcblk0, sector 16
[ 2629.070260] end_request: I/O error, dev mmcblk0, sector 24
[ 2629.072986] mmc0: Got data interrupt 0x00400000 even though no data operation was in progress.
[ 2629.072997] sdhci: ============== REGISTER DUMP ==============
[ 2629.073002] sdhci: Sys addr: 0x0fe36000 | Version:  0x00000400
[ 2629.073006] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000000
[ 2629.073013] sdhci: Argument: 0x00000000 | Trn mode: 0x00000033
[ 2629.073018] sdhci: Present:  0x01df0000 | Host ctl: 0x00000003
[ 2629.073023] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
[ 2629.073028] sdhci: Wake-up:  0x00000000 | Clock:    0x00000107
[ 2629.073032] sdhci: Timeout:  0x00000009 | Int stat: 0x00000003
[ 2629.073036] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
[ 2629.073041] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
[ 2629.073045] sdhci: Caps:     0x01e021a1 | Max curr: 0x00000040
[ 2629.073047] sdhci: ===========================================
[ 2629.076317] mmcblk0: error -84 transferring data
[ 2629.076320] end_request: I/O error, dev mmcblk0, sector 0
```

I had used the card reader with no problems before, I can't understand why it suddenly stopped working. I was playing around with the fstab for a while trying to get an mp3 player to work, but I'm very sure I left everything as it was.

Any help is appreciated.

---

### Post by Captain_tux on 2008-12-25
Bump.

---

### Post by Vandrerol on 2009-02-17
bump-bump

---

