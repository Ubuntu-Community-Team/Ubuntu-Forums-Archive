---
title: "Second Avermedia A161 card not registered"
date: 2010-02-18
forum: Hardware
---

### Post by missingtale on 2010-02-18
Hi,

I am having trouble getting a second Avermedia tuner card registered on my system. I am currently running Jaunty and have 2 identical Avermedia A161 cards installed primarily for myth. I have both cards in the machine but only the first one gets registered and detected. If I take either card out of the machine the other gets detected and works fine.

I am sure this is some thing small but fundimental that I have missed durring config, any help would be much appreciated.

I think this is the relevant messages which I read as the first card gets detected correctly and the second card does not.

```

[    9.528739] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[    9.528751] saa7134 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[    9.528756] saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 18, latency: 64, mmio: 0xfbeff800
[    9.528762] saa7133[0]: subsystem: 1461:2c00, board: AVerMedia TV Hybrid A16AR [card=99,insmod option]
[    9.528925] saa7133[0]: board init: gpio is 2b600
[    9.529037] input: saa7134 IR (AVerMedia TV Hybrid as /devices/pci0000:00/0000:00:08.0/0000:01:09.0/input/input6
[    9.587179] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[    9.587192] HDA Intel 0000:00:07.0: PCI INT B -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[    9.587252] HDA Intel 0000:00:07.0: setting latency timer to 64
[    9.686738] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 17
[    9.686751] nvidia 0000:04:00.0: PCI INT A -> Link[LNED] -> GSI 17 (level, low) -> IRQ 17
[    9.686757] nvidia 0000:04:00.0: setting latency timer to 64
[    9.687874] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    9.840024] saa7133[0]: i2c eeprom 00: 61 14 00 2c 00 00 00 00 00 00 00 00 00 00 00 00
[    9.840033] saa7133[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[    9.840040] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 03 01 08 ff 00 a3 ff ff ff ff
[    9.840047] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840054] saa7133[0]: i2c eeprom 40: ff 32 00 c0 86 1e ff ff ff ff ff ff ff ff ff ff
[    9.840061] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840068] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840076] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840083] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840090] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840097] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840104] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840111] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840118] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840125] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.840131] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.948092] tuner' 2-0043: chip found @ 0x86 (saa7133[0])
[    9.954785] tda9887 2-0043: creating new instance
[    9.954789] tda9887 2-0043: tda988[5/6/7] found
[    9.981095] tuner' 2-0060: chip found @ 0xc0 (saa7133[0])
[    9.981164] tea5767 2-0060: type set to Philips TEA5767HN FM Radio
[    9.989016] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.991264] tea5767 2-0060: type set to Philips TEA5767HN FM Radio
[   10.024314] saa7133[0]: registered device video0 [v4l2]
[   10.024334] saa7133[0]: registered device vbi0
[   10.024352] saa7133[0]: registered device radio0
[   10.036399] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 16
[   10.036412] saa7134 0000:01:0a.0: PCI INT A -> Link[LNKC] -> GSI 16 (level, low) -> IRQ 16
[   10.036417] saa7133[1]: found at 0000:01:0a.0, rev: 209, irq: 16, latency: 64, mmio: 0xfbeff000
[   10.036423] saa7133[1]: subsystem: 1461:2c00, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.036467] saa7133[1]: board init: gpio is 2a600
[   10.232089] tuner' 3-0043: chip found @ 0x86 (saa7133[1])
[   10.232158] tda9887 3-0043: creating new instance
[   10.232160] tda9887 3-0043: tda988[5/6/7] found
[   10.256088] tuner' 3-0060: chip found @ 0xc0 (saa7133[1])
[   10.256155] tea5767 3-0060: type set to Philips TEA5767HN FM Radio
[   10.312022] saa7133[1]: i2c eeprom 00: 61 14 00 2c 00 00 00 00 00 00 00 00 00 00 00 00
[   10.312031] saa7133[1]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   10.312039] saa7133[1]: i2c eeprom 20: 01 40 01 02 02 03 03 01 08 ff 00 a3 ff ff ff ff
[   10.312047] saa7133[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312055] saa7133[1]: i2c eeprom 40: ff 32 00 c0 86 1e ff ff ff ff ff ff ff ff ff ff
[   10.312063] saa7133[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312071] saa7133[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312079] saa7133[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312087] saa7133[1]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312095] saa7133[1]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312103] saa7133[1]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312111] saa7133[1]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312118] saa7133[1]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312127] saa7133[1]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312135] saa7133[1]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312142] saa7133[1]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.312520] saa7133[1]: registered device video1 [v4l2]
[   10.312545] saa7133[1]: registered device vbi1
[   10.317318] saa7134 ALSA driver for DMA sound loaded
[   10.317350] saa7133[0]/alsa: saa7133[0] at 0xfbeff800 irq 18 registered as card -2
[   10.317767] saa7133[1]/alsa: saa7133[1] at 0xfbeff000 irq 16 registered as card -1
[   10.345579] dvb_init() allocating 1 frontend
[   10.488781] tuner-simple 2-0061: unable to probe Philips TD1316 Hybrid Tuner, proceeding anyway.<6>tuner-simple 2-0061: creating new instance
[   10.488787] tuner-simple 2-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   10.488792] DVB: registering new adapter (saa7133[0])
[   10.488795] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...

```

---

