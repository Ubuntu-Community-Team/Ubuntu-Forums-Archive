---
title: "Problem with TV/FM Tuner"
date: 2009-11-20
forum: Hardware
---

### Post by adijumi on 2009-11-20
I am new to Ubuntu (9.10) and Linux. I just succeeded getting trough an installation on my old computer. But I can't get my TV/FM card working. I tried all TV card programs.  It's about 7 years old analog card.
            I just found how to find hardware details - so here they are.

*-multimedia
                description: Multimedia controller
                product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: a
                bus info: pci@0000:01:0a.0
                version: d0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=40 mingnt=16
                resources: irq:18 memory:e6001000-e60017ff

I guess it's not even correctly detected as Tv tuner, but as some sort of audio card.
So, what should I do next.

---

### Post by adijumi on 2009-11-20
I found some more info with dmesg

[   10.147030] saa7130/34: v4l2 driver version 0.2.15 loaded
[   10.147351] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   10.147360]   alloc irq_desc for 18 on node -1
[   10.147363]   alloc kstat_irqs on node -1
[   10.147374] saa7134 0000:01:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18
[   10.147384] saa7133[0]: found at 0000:01:0a.0, rev: 208, irq: 18, latency: 32, mmio: 0xe6001000
[   10.147394] saa7133[0]: subsystem: 17de:7136, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.147425] saa7133[0]: board init: gpio is 40
[   10.147434] IRQ 18/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.296025] saa7133[0]: i2c eeprom 00: de 17 36 71 10 28 ff ff ff ff ff ff ff ff ff ff
[   10.296040] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296052] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296064] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296075] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296087] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296098] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296110] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296121] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296133] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296145] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296156] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296168] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296179] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296191] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296202] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.296217] i2c-adapter i2c-2: Invalid 7-bit address 0x7a
[   10.297135] saa7133[0]: registered device video0 [v4l2]
[   10.297169] saa7133[0]: registered device vbi0
[   11.473404] saa7134 ALSA driver for DMA sound loaded
[   11.473426] IRQ 18/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.473463] saa7133[0]/alsa: saa7133[0] at 0xe6001000 irq 18 registered as card -2

---

