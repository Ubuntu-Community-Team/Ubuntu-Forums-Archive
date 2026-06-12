---
title: "DVB -S   -   saa7130 and saa7134"
date: 2009-12-11
forum: Hardware
---

### Post by lope1974 on 2009-12-11
I don't know what to do with GigabyteGT-PS700-PCI DVB-S card with chip  saa7130hl.  There is no DVB-S receiver found in MythTV backend but driver  saa7134  is loaded : 


dmesg | grep saa7130
[    6.162461] saa7130/34: v4l2 driver version 0.2.15 loaded
[    6.162928] saa7130[0]: found at 0000:03:07.0, rev: 1, irq: 21, latency: 32, mmio: 0xfdcfe000
[    6.162936] saa7130[0]: subsystem: 1458:9006, board: UNKNOWN/GENERIC [card=0,autodetected]
[    6.162952] saa7130[0]: board init: gpio is 10000
[    6.162958] IRQ 21/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.360074] saa7130[0]: i2c eeprom 00: 58 14 06 90 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    6.360082] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    6.360089] saa7130[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 08 ff 01 4c ff ff ff ff
[    6.360097] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360104] saa7130[0]: i2c eeprom 40: 50 1c 00 c0 ff 1c 01 00 ff ff ff ff ff ff ff ff
[    6.360110] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360116] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360122] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360128] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360134] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360141] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360147] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360153] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360159] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360165] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.360171] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.380005] saa7130[0]: i2c scan: found device @ 0x10  [???]
[    6.400005] saa7130[0]: i2c scan: found device @ 0x1c  [???]
[    6.430012] saa7130[0]: i2c scan: found device @ 0xa0  [eeprom]
[    6.437488] saa7130[0]: registered device video1 [v4l2]
[    6.437509] saa7130[0]: registered device vbi0
[    6.493556] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio

dmesg | grep saa7134
[    6.162920] saa7134 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.493552] saa7134 ALSA driver for DMA sound loaded

lspci -k
03:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
   Kernel driver in use: saa7134
   Kernel modules: saa7134

Does anybody know what to do?
Thanks.

---

