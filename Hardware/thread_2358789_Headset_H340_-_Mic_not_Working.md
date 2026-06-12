---
title: "Headset H340 - Mic not Working"
date: 2017-04-17
forum: Hardware
---

### Post by douglas-rauber on 2017-04-17
Hello!

I have a Logitech USB Headset, a few days ago, i have returned to XUbuntu (from windows). But, the mic not working.
I have this output:

```
cat /proc/asound/cards 
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xc4310000 irq 52
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc4314000 irq 51
 2 [H340           ]: USB-Audio - Logitech USB Headset H340
                      Logitech Inc. Logitech USB Headset H340 at usb-0000:00:14.0-4, full speed



```

I have changed input volume on pavucontrol, but, only the internal MIC capture sound. And its very ugly for google talk calls.

[http://i.imgur.com/o9vTJc9.png](http://i.imgur.com/o9vTJc9.png)

Can anyone help me?

Thanks!

DRauber

---

