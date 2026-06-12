---
title: "Avermedia m115 Hybrid TV-Card in Aspire 9813 wkmi"
date: 2009-09-04
forum: Hardware
---

### Post by zeroXcool on 2009-09-04
Hi ;) At first sorry for my bad english ;)

I'am working since two Days now to get my TV-Card (Avermedia m115 Hybrid) to work. I got it running now but (thx google) but there are still a major Problem, with the Tuner I think ;)

Now I hope someone here can help me ;)

The following Informations are correct:
```
* Notebook: Acer Aspire 9813wkmi
* Ubuntu: 9.04
* Kernel: 2.6.28-15-generic ("uname -r")
* TV-Card: Avermedia M115 Hybrid
* Composite1 works in tvtime
* watching Analog-Cable-TV doesn't work in tvtime (tvtime-scanner says "no signal" all the time)
```

The following Information I hope are correct:
```
* The TV-Card need the Module "saa7134" with the Options "card=138 tuner=37"
* The Tuner needs the Firmware "/lib/firmware/xc3028-v27.fw"
```

dmesg says after "sudo modprobe saa7134 card=138 tuner=37":
```
[10887.631669] saa7130/34: v4l2 driver version 0.2.15 loaded
[10887.631777] saa7133[0]: found at 0000:09:04.0, rev: 209, irq: 16, latency: 64, mmio: 0xd2005000
[10887.631791] saa7133[0]: subsystem: 1461:a836, board: Avermedia M115 [card=138,insmod option]
[10887.631884] saa7133[0]: board init: gpio is effffff
[10887.773779] cx25843.c: starting probe for adapter saa7133[0] (0x90000)
[10887.824111] saa7133[0]: i2c eeprom 00: 61 14 36 a8 00 00 00 00 00 00 00 00 00 00 00 00
[10887.824135] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[10887.824156] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c0 ff ff ff ff
[10887.824177] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824198] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[10887.824219] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824240] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824261] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824282] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824302] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824323] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824344] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824365] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824386] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824407] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.824427] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[10887.836155] tuner 3-0061: chip found @ 0xc2 (saa7133[0])
[10887.844066] tuner-simple 3-0061: creating new instance
[10887.844074] tuner-simple 3-0061: type set to 37 (LG PAL (newer TAPC series))
[10887.870047] saa7133[0]: registered device video1 [v4l2]
[10887.870098] saa7133[0]: registered device vbi0
[10887.884812] saa7134 ALSA driver for DMA sound loaded
[10887.884866] saa7133[0]/alsa: saa7133[0] at 0xd2005000 irq 16 registered as card -2
```

There are no Problems or did I miss something ?

It would be great if someone could give me some Hints on how to get the Tuner (Analog-Cable-TV) working.

Thanks to everyone who has read so far ;)

---

### Post by zeroXcool on 2009-09-08
UPDATE:
I think i've found a solution, I just need the correct Firmware "xc3028-v27.fw" is not the one I need...

So can anybody tell me where/who to get/extract it from AverM115.sys ?

thx

---

### Post by skotos on 2009-11-02
Well, I have an Acer Aspire 9815WKMi and up to 9.04 inclusive I have not been able to properly run the TV tuner. Now, after installing Karmic from scratch a few more hardware issues have arosen (the webcam does not work anymore) and I am investigating.  To get and extract the firmware you can follow the instructions provided [here]("http://linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028")

HTH!

Maybe [this]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/278656") and [this!!]("http://ubuntuforums.org/showthread.php?t=1021879&highlight=xc3028") are of interest too.

---

