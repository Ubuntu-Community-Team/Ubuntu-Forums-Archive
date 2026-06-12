---
title: "Problem with DMA"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by stevediraddo on 2007-02-25
Hi, I have a problem with enabling DMA in Ubuntu 6.06. I am no n00b, keep this in mind :P

I followed all instructions and tweaked the hdparm settings, and all settings are applied without problem. My harddrive is hda, and my DVD-rom is hdc. When I run the settings I get:

```
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

/dev/hdc:
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
```

both are using DMA mode 66 (Ultra DMA Mode 2). The harddrive jumped to 20MB/s after applying the settings but for the DVD I fail to get buffered transfer speeds higher than 600kb/s, which basically rapes DVD playback. 

This is a Toshiba Satellite A10 with an Intel 855 chipset. Oddly enough it works perfect on my Satellite A70, which has an ATI chipset.

---

### Post by dalee on 2007-02-25
Hi,

Just kind of a guess, but shouldn't unmaskirq    =  0 (off), be unmaskirq = 1 (on)

---

### Post by stevediraddo on 2007-03-20
I solved the problem. Had nothing to do with the IRQ settings, turned out the DVD Drive just has a fault and needed to be replaced. Everything works peachy now.

---

