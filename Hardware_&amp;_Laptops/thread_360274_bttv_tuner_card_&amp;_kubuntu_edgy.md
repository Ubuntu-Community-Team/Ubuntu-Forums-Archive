---
title: "bttv tuner card &amp; kubuntu edgy"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by brandon_r87 on 2007-02-12
Hi,

I just installed Kubuntu Edgy and want to get MythTV running, but first I have to take care of my bttv card, which isn't working. In XawTV I just get a black screen, no matter what my settings are.  With dmesg, I can see an unknown card and also mine (Aimslab VHX, card=14, tuner=2).  Why is it in there twice, and would this be stopping me from using it?

```
$ dmesg | grep bttv && dmesg | grep tuner

[   68.136904] bttv: driver version 0.9.16 loaded
[   68.136909] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   68.136952] bttv: Bt8xx card found (0).
[   68.136977] bttv0: Bt848 (rev 18) at 0000:03:00.0, irq: 233, latency: 32, mmio: 0x52000000
[   68.136989] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   68.137017] bttv0: gpio: en=00000000, out=00000000 in=00ff3fff [init]
[   68.141340] bttv0: using tuner=-1
[   68.141343] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   68.143465] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   68.145596] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   68.147719] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   68.149947] bttv0: registered device video0
[   68.149977] bttv0: registered device vbi0
[  435.843808] bttv0: unloading
[  480.146236] bttv: driver version 0.9.16 loaded
[  480.146241] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  480.146637] bttv: Bt8xx card found (0).
[  480.146706] bttv0: Bt848 (rev 18) at 0000:03:00.0, irq: 233, latency: 32, mmio: 0x52000000
[  480.146821] bttv0: using: Aimslab Video Highway Xtreme (VHX) [card=14,insmod option]
[  480.147293] bttv0: gpio: en=00000000, out=00000000 in=00ff3fff [init]
[  480.149791] bttv0: using tuner=2
[  480.149840] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  480.152039] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  480.154239] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  480.192204] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  480.259929] bttv0: registered device video0
[  480.260011] bttv0: registered device vbi0
[  480.260081] bttv0: registered device radio0
[  480.260158] bttv0: PLL: 28636363 => 35468950 .. ok
[ 1371.283548] bttv0: unloading
[   68.141340] bttv0: using tuner=-1
[  480.149791] bttv0: using tuner=2
[  480.226322] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  480.226327] tuner 0-0060: chip found @ 0xc0 (bt848 #0 [sw])
[  480.226537] tuner 0-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles)
```

---

