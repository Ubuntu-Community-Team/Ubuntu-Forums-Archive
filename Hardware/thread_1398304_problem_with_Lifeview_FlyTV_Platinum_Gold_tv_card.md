---
title: "problem with Lifeview FlyTV Platinum Gold tv card"
date: 2010-02-04
forum: Hardware
---

### Post by giora.belostotsky on 2010-02-04
all the tv watching apps say that there is no tuner,
when i type dmesg | grep saa7133 in the terminal i get this:
giora@giora-desktop:~$ dmesg | grep saa7133
[ 13.906172] saa7133[0]: found at 0000:04:01.0, rev: 240, irq: 19, latency: 32, mmio: 0xe3100000
[ 13.906185] saa7133[0]: subsystem: 5168:0214, board: LifeView FlyTV Platinum FM / Gold [card=54,autodetected]
[ 13.906218] saa7133[0]: board init: gpio is 31c00
[ 13.906415] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 14.056520] saa7133[0]: i2c eeprom 00: 68 51 14 02 ff 28 ff ff ff ff ff ff ff ff ff ff
[ 14.056539] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056556] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056573] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056589] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056606] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056623] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056639] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056656] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056672] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056689] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056706] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056722] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056739] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056755] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.056772] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 14.109638] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[ 19.228101] saa7133[0]: registered device video0 [v4l2]
[ 19.228155] saa7133[0]: registered device vbi0
[ 19.228205] saa7133[0]: registered device radio0
[ 19.235981] IRQ 19/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[ 19.236021] saa7133[0]/alsa: saa7133[0] at 0xe3100000 irq 19 registered as card -2

what should i do to make it work?
please help...

---

