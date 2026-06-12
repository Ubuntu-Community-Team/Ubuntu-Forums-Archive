---
title: "Tv tuner - problems"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by becali2us on 2006-11-02
I have this tv tuner:
[http://www.directron.com/vsltv7131rf.html](http://www.directron.com/vsltv7131rf.html)
and I can't use it. I have ubuntu 6.10 instaled on my system.
lspci:
> 
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
02:0b.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)

dmesg:
> 
[17179594.916000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179594.916000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179594.916000] saa7133[0]: found at 0000:02:0b.0, rev: 208, irq: 11, latency: 66, mmio: 0x40000000
[17179594.916000] saa7133[0]: subsystem: ffff:ffff, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179594.916000] saa7133[0]: board init: gpio is 40
[17179595.052000] saa7133[0]: i2c eeprom 00: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179595.052000] saa7133[0]: registered device video0 [v4l2]
[17179595.052000] saa7133[0]: registered device vbi0
[17179595.096000] saa7134 ALSA driver for DMA sound loaded
[17179595.096000] saa7133[0]/alsa: saa7133[0] at 0x40000000 irq 11 registered as card -1


If some one coluld help me setup this tv tuner...:-k

---

### Post by becali2us on 2006-11-24
Nobody?

---

