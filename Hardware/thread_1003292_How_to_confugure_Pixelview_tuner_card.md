---
title: "How to confugure Pixelview tuner card"
date: 2008-12-05
forum: Hardware
---

### Post by pps2009 on 2008-12-05
I have got a Pixelview tuner card ,I don't know how to configure this .......plz help

when open Xawtv i can hear noise......but no video
tvtime is saying that there is no signal

lspci gives following output

01:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


bttv modules are also loaded

:lsmod

v4l1_compat            22404  1 videodev
ir_common              48132  1 bttv
soundcore              15328  1 snd
compat_ioctl32          9344  1 bttv
i2c_algo_bit           14340  1 bttv
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
v4l2_common            19840  1 bttv
videobuf_dma_sg        20612  1 bttv
videobuf_core          26628  2 bttv,videobuf_dma_sg
btcx_risc              12552  1 bttv
tveeprom               20228  1 bttv
i2c_core               31892  4 bttv,i2c_algo_bit,v4l2_common,tveeprom

:dmesg

 16.875189] Linux video capture interface: v2.00
[   16.968046] bttv: driver version 0.9.17 loaded
[   16.968053] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   16.989457] bttv: Bt8xx card found (0).
[   16.989488] bttv 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.989505] bttv0: Bt878 (rev 17) at 0000:01:01.0, irq: 22, latency: 32, mmio: 0xfc001000
[   16.989529] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   16.989582] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[   16.992281] tveeprom 0-0050: Huh, no eeprom present (err=-6)?
[   16.992289] bttv0: tuner type unset
[   16.992295] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   16.992914] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   16.993534] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   16.994470] bttv0: registered device video0
[   16.994589] bttv0: registered device vbi0

---

