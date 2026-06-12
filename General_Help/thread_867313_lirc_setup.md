---
title: "lirc setup"
date: 2008-07-22
forum: General Help
---

### Post by deep-z on 2008-07-22
Hello!

I have Ubuntu 8.04 with JETWAY (bt878) chipset card, but my remote control is not working. Infrared remote control window shows a warning at Configuration test section with text: 

> Remote control daemon is not running. Cannot test buttons.

Tried to run lircd manually and got this, when accessing Infrared remote control tool in system preferences:

```
$ sudo lircd -n
lircd-0.8.3pre1[7033]: lircd(userspace) ready
lircd-0.8.3pre1[7033]: accepted new client on /dev/lircd
lircd-0.8.3pre1[7033]: could not get file information for /dev/lirc
lircd-0.8.3pre1[7033]: default_init(): No such file or directory
lircd-0.8.3pre1[7033]: caught signal
Terminated

```

In my dmesg output card is detected (I'm also able to access tv tuner via tvtime app) like this:

```
$ dmesg | grep btt
[   46.879989] bttv: driver version 0.9.17 loaded
[   46.880001] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   46.880574] bttv: Bt8xx card found (0).
[   46.880644] bttv0: Bt878 (rev 17) at 0000:02:04.0, irq: 19, latency: 32, mmio: 0xe0000000
[   46.880673] bttv0: using: Modular Technology MM201/MM202/MM205/MM210/MM215 PCTV, bt878 [card=23,insmod option]
[   46.880720] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[   46.882064] bttv0: Modtec: Unknown TunerString: 
[   46.882071] bttv0: tuner type=18
[   46.882077] bttv0: i2c: checking for Bt832 @ 0x88... not found
[   46.882668] bttv0: i2c: checking for Bt832 @ 0x8a... not found
[   46.883259] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   46.896115] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   47.344086] bttv0: registered device video0
[   47.344143] bttv0: registered device vbi0
[   47.344173] bttv0: PLL: 28636363 => 35468950 .. ok

```

What steps are needed for lircd to get it working?
Any help would be great. :) ...

---

