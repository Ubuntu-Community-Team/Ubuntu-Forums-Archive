---
title: "Disable &quot;Panel fitting&quot; on widescreen laptops"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by thetor on 2007-09-04
Is there any way to disable the panel fitting feature on widescreen laptops with intel graphics?

Panel fitting is usually enabled by default, and makes the picture stretch to fill the screen even when using a 4:3 screen resolution. When playing games I often have to use 4:3 resolutions, but the picure looks terrible when stretched to fill a 16:10 screen.

I believe you can set set panel fitting behavior in the BIOS on some laptops, but not on mine. The intel driver on windows is also able to control panel fitting behaviour. There are three options:
- Stretch to fill the entire screen, no matter which screen resolution is used.
- Enlarge to the maximum size possible without changing the aspect ratio of the picture (4:3 resolutions are shown with black bars on the right and left sides)
- Keep 1:1 pixel mapping (all resolutions lower than the maximum one are shown inside a black frame)

Any help is greatly appreciated, as the default setting is extremely annoying.

---

### Post by ryanVickers on 2007-09-04
I'm not sure how do do this in Linux, but in windows, with my nVidia card, I can pick "no scaling" (just shows whatever it's set to in the middle of the screen), "scaling but keep aspect ratio" (this is what you want - scales it to full size but stops when one of the borders reaches the edge of the screen; best size without distortion), and "full scaling" (stretches it to fit no matter what - ugly on incorrect sizes and shapes! :))

---

### Post by ryanVickers on 2007-09-04
[This]("http://www.ubuntugeek.com/fix-for-widescreen-resolutions-for-intel-display-cards-in-ubuntu-feisty.html") may come in useful!

---

### Post by thetor on 2007-09-07
Thanks for your input.

> **ryanVickers said:**
> I'm not sure how do do this in Linux, but in windows, with my nVidia card, I can pick "no scaling" (just shows whatever it's set to in the middle of the screen), "scaling but keep aspect ratio" (this is what you want - scales it to full size but stops when one of the borders reaches the edge of the screen; best size without distortion), and "full scaling" (stretches it to fit no matter what - ugly on incorrect sizes and shapes! :))
This confirms my experiences. The Windows Intel driver has the same settings, and I assume Windows ATI drivers do, too.

> **ryanVickers said:**
> [This]("http://www.ubuntugeek.com/fix-for-widescreen-resolutions-for-intel-display-cards-in-ubuntu-feisty.html") may come in useful!
Yes, this is the driver I am currently using. Unfortunately I haven't found any information about scaling or panel fitting.

Surely there must be some way to do this in Ubuntu, when it's so easy in Windows? I have understood that Intel is being regarded as fairly dedicated to providing Linux support for their products. I find it hard to imagine that such an obvious feature is missing from their own open source driver!

---

### Post by droid8622 on 2007-10-03
the same trouble! wen i play q3 640x480 resulution it fits all the screen ;(

---

