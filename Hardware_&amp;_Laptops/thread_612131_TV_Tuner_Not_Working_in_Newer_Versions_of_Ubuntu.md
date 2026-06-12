---
title: "TV Tuner Not Working in Newer Versions of Ubuntu"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by RPG405 on 2007-11-13
Hi,

Back when Ubuntu 5.10 "Breezy Badger" was out, I was able to watch TV with my computer's PCI TV tuner card. However, with the upgrade to 6.06, and subsequently to 7.04 then 7.10 (my current version), the card has not worked. I used to be able to view the TV signal in tvtime. Ever since 6.06, tvtime has displayed no signal. I have tried multiple other TV viewing programs along with specifying different input devices for tvtime. None have worked.

The details for the card are below.

```
05:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors Unknown device 0000
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at d100a000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1

```

My guess, which is very limited, is that a kernel module present in the 5.10 kernel was removed in the 6.06 kernel and never replaced (I use standard Ubuntu kernels).

---

### Post by Jose Catre-Vandis on 2007-11-13
What does dmesg tell you about your tuner (should look something like this)
> [   42.451532] saa7133[0]: found at 0000:01:06.0, rev: 208, irq: 19, latency: 32, mmio: 0xe8000000
[   42.451542] saa7133[0]: subsystem: 1043:4857, board: ASUSTeK P7131 Dual [card=78,autodetected]
[   42.451553] saa7133[0]: board init: gpio is 0
[   42.451709] input: saa7134 IR (ASUSTeK P7131 Dual) as /class/input/input4
[   42.586702] saa7133[0]: i2c eeprom 00: 43 10 57 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   42.586714] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[   42.586723] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 cb ff ff ff ff
[   42.586732] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.586740] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
[   42.586749] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.586758] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.586767] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.686616] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   42.734570] tuner 2-004b: setting tuner address to 61
[   42.774537] tuner 2-004b: type set to tda8290+75a
[   44.141331] tuner 2-004b: setting tuner address to 61
[   44.181296] tuner 2-004b: type set to tda8290+75a
[   45.502867] saa7133[0]: registered device video0 [v4l2]
[   45.503062] saa7133[0]: registered device vbi0
[   45.503250] saa7133[0]: registered device radio0

Note my card is different to yours!

---

### Post by RPG405 on 2007-11-13
dmesg produces nothing of the sort. After combing through the six hundred some line file, most lines appear in this format, simliar to this:

```
[   43.408000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.25 DST=192.168.1.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76 
```

Nothing in the output matches "saa", "7133", "video", "tuner", or "v4l2".

---

