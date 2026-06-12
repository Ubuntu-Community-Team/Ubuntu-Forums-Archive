---
title: "Sound card not detected on HP Pavilion N5150"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Super TWiT on 2007-12-28
I can't get the sound recognized on an older laptop.  It's an HP Pavilion N5150.  It runs full Ubuntu Gutsy pretty well, except there is no sound on it.  I am willing to compile a custom kernel/module.  I just don't know if this card is even supported.  Here's the output from lspci. ```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1420
00:04.1 CardBus bridge: Texas Instruments PCI1420
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia video controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:08.1 Communication controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```
I think the sound card is the ESS Technology ES1988 Allegro-1 (rev 12).  However, I am not certain.  If anyone could tell me if there's a way to get the sound working, please let me know.

---

