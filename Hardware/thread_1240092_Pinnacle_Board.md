---
title: "Pinnacle Board"
date: 2009-08-14
forum: Hardware
---

### Post by RobiMaso on 2009-08-14
I have a Pinnacle PCTV-Pro board used for video analogic acquisition.
I used it untill Ubuntu 8.10.
Now I have upgrated my Ubuntu to 9.04 and the programs I used with that board  (KDETV e XAWTV) doesn't found the board.
The  kernel log seems ok.

[   10.921110] bttv: driver version 0.9.17 loaded
[   10.921115] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.921172] bttv: Bt8xx card found (0).
[   10.921187] bttv 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.921197] bttv0: Bt878 (rev 17) at 0000:04:00.0, irq: 16, latency: 64, mmio: 0xdefff000
[   10.921253] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   10.921256] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
[   10.921284] bttv0: gpio: en=00000000, out=00000000 in=00fffbdf [init]
[   10.921341] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   10.921612] bttv0: pinnacle/mt: id=2 info="PAL+SECAM / stereo" radio=yes
[   10.921615] bttv0: tuner type=14
[   10.921618] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   10.995290] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   10.995912] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   11.209957] bttv0: registered device video0
[   11.210034] bttv0: registered device vbi0
[   11.210105] bttv0: registered device radio0
[   11.228321] bttv0: PLL can sleep, using XTAL (35468950).
[  693.557783] bttv0: PLL: 35468950 => 28636363 .. ok

Thanks for the answers.

---

### Post by osinghrathore on 2009-08-14
Have you installed V4L ..?

---

### Post by RobiMaso on 2009-08-15
Yes I installed v4l.

Thanks.

---

