---
title: "Avermedia tv tuner &quot;no signal&quot;"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by valentin.dumitran on 2007-02-21
Hi,

I'm not able to use my Avermedia AverTV GO 007 in Edgy. I installed the driver and tvtime sees my card, but I get a "no signal" error. It works fine in windows, so it's not a hardware problem.

dmesg shows:
```

[17179593.016000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179593.016000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (
level, low) -> IRQ 10
[17179593.016000] saa7130[0]: found at 0000:00:0a.0, rev: 1, irq: 10, latency: 3
2, mmio: 0xde000000
[17179593.016000] saa7130[0]: subsystem: 1461:d109, board: Avermedia AVerTV GO 0
07 FM [card=57,insmod option]
[17179593.016000] saa7130[0]: board init: gpio is 10000
[17179593.016000] input: saa7134 IR (Avermedia AVerTV GO as /class/input/input3
[17179593.192000] saa7130[0]: i2c eeprom 00: 61 14 09 d1 ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.192000] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.192000] saa7130[0]: i2c eeprom 20: 13 02 ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.192000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.192000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.192000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.192000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.192000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff
[17179593.232000] tuner 1-0061: chip found @ 0xc2 (saa7130[0])
[17179593.284000] tuner 1-0061: setting tuner address to 61
[17179593.596000] saa7134 ALSA driver for DMA sound loaded
[17179593.596000] saa7130[0]/alsa: saa7130[0] at 0xde000000 irq 10 registered as
 card -1

```
And lspci shows:
```
00:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

```

I also tried xawtv but I only see a black screen. Google didn't provide very much help with my problem and I'm hoping I'll find someone who can help me.

---

