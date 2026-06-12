---
title: "sound &quot;loop&quot; with es1869 in feisty"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by danmbox on 2007-08-05
Hi, whatever sound I to play on my ES1869 card (snd-es1869.ko), the first frame loops. E.g. when I play the ALSA "Front Left" sound,

aplay /usr/share/sounds/alsa/Front_Left.wav

I hear "Front, Front, Front" etc.

The IRQ, DMA and I/O port settings seem to be correct. Edgy used to work (though I had to configure manually IIRC), Feisty does not. This is a Compaq Armada 1700.

Thanks!

---

### Post by LDRoamer on 2007-08-20
I have a compaq Armada 1750 with the ES1869 chip and have not been able to get it working with Feisty. I tried quite a few things before finally giving up. I have started using a usb sound card. It doesn't use the builit in speakers for my laptop but it does work (although I did have to do a bit of configuring to get it working properly).

---

