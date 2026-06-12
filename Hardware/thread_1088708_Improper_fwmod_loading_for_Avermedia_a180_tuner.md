---
title: "Improper fw/mod loading for Avermedia a180 tuner"
date: 2009-03-06
forum: Hardware
---

### Post by znice on 2009-03-06
Hey all, I'm new to this forum.  I am having issues with my Avermedia a180 in 8.10.  I have posted about this in the Mythbuntu forum, but had no help and it has since occurred to me that this really probably belongs in "Ubuntu>>>Hardware and Laptops".  The issue seems to fundamentally be that the normal saa7134 module is being loaded instead of the saa7134-dvb module.  This is occurring in spite of my having blacklisted that module.  If I try to manually remove it after boot with "modprobe -r saa7134" or with "modprobe -f -r saa7134" I get "FATAL: module in use".  I have followed the directions at [http://www.jnewcastle.com/blog/2006/...a180-on-ubuntu](http://www.jnewcastle.com/blog/2006/...a180-on-ubuntu).  For good measure, I have also added a copy of the nxt2004 firmware file to /lib/firmware/[kernel #] per Cresho's advice(this is in addition to /lib/firmware, which is where everybody else seems to think the file ought to go).  I really am going nuts over this.  It has consumed about a good ten hours of my time that should have been committed to more virtuous activities.  I have a pvr-150 in my box that works great.  If I can't find a fix, this card will just go up on ebay and subsidize an HDhomerun, but I hope it doesn't come to that.
"dmesg | grep saa" shows me:
```
[   10.176878] saa7130/34: v4l2 driver version 0.2.14 loaded
[   10.177347] saa7134 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.177353] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 18, latency: 64, mmio: 0xdffffc00
[   10.177359] saa7130[0]: subsystem: 1461:1044, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.177369] saa7130[0]: board init: gpio is 10400
[   10.328016] saa7130[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   10.328025] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   10.328032] saa7130[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 00 10 00 00 00 00
[   10.328040] saa7130[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   10.328047] saa7130[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   10.328054] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328061] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328068] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328076] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328083] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328090] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328098] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328105] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328112] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328120] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328127] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.328530] saa7130[0]: registered device video1 [v4l2]
[   10.328791] saa7130[0]: registered device vbi1
[   10.339556] saa7134 ALSA driver for DMA sound loaded
[   10.339583] saa7130[0]/alsa: saa7130[0] at 0xdffffc00 irq 18 registered as card -2
```

and "lspci | grep saa" shows me:
```
saa7134_dvb            27532  0 
saa7134_alsa           20000  0 
saa7134               147796  2 saa7134_dvb,saa7134_alsa
ir_common              48900  3 cx88xx,bttv,saa7134
videobuf_dma_sg        20612  6 cx8800,cx88xx,bttv,saa7134_dvb,saa7134_alsa,saa7134
videobuf_dvb           12932  1 saa7134_dvb
videobuf_core          26628  6 cx8800,cx88xx,bttv,saa7134,videobuf_dma_sg,videobuf_dvb
dvb_core               86272  2 saa7134_dvb,videobuf_dvb
snd_pcm                83204  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
videodev               41344  6 cx8800,cx88xx,bttv,saa7134,tuner,ivtv
compat_ioctl32          9344  4 cx8800,bttv,saa7134,ivtv
v4l2_common            19840  8 cx8800,bttv,saa7134,wm8775,cx25840,tuner,ivtv,cx2341x
tveeprom               20228  4 cx88xx,bttv,saa7134,ivtv
i2c_core               31892  14 cx88xx,bttv,lirc_i2c,nvidia,saa7134_dvb,saa7134,tuner_simple,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,v4l2_common,tveeprom
snd                    63268  12 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```
I'd really appreciate some advice.  I am losing my mind with this one.

---

