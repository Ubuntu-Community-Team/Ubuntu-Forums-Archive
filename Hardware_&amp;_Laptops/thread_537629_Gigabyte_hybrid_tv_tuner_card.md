---
title: "Gigabyte hybrid tv tuner card"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by tristanjl on 2007-08-29
I am having difficulty in getting my Gigabyte TV tuner working. It is currently being identified by saa7134 as a generic/unkown card and am unable to use it with mythtv/tvtime.

The relevant dmesg output:
[   38.216828] Linux video capture interface: v2.00
[   38.463626] saa7130/34: v4l2 driver version 0.2.14 loaded
[   38.464165] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   38.464169] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   38.464177] saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 11, latency: 64, mmio: 0xdbfff800
[   38.464182] saa7133[0]: subsystem: 1458:9002, board: UNKNOWN/GENERIC [card=0,autodetected]
[   38.464190] saa7133[0]: board init: gpio is c000000
[   38.609036] saa7133[0]: i2c eeprom 00: 58 14 02 90 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   38.609045] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   38.609051] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c1 ff ff ff ff
[   38.609057] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.609063] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 50 ff ff ff ff ff ff
[   38.609069] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.609075] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.609081] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.609338] saa7133[0]: registered device video0 [v4l2]
[   38.609365] saa7133[0]: registered device vbi0
[   38.646359] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.647829] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.686558] NET: Registered protocol family 17
[   38.938121] input: PC Speaker as /class/input/input2
[   38.958196] parport: PnPBIOS parport detected.
[   38.958241] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   39.225503] Linux agpgart interface v0.102 (c) Dave Jones
[   39.399542] saa7134 ALSA driver for DMA sound loaded
[   39.399566] saa7133[0]/alsa: saa7133[0] at 0xdbfff800 irq 11 registered as card -2

---

### Post by msaliba on 2007-12-17
i allso need to get this card to work in ubuntu with any software can someone plz help

---

