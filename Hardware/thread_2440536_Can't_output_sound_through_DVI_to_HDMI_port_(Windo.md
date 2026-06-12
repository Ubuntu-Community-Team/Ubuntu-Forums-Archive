---
title: "Can't output sound through DVI to HDMI port (Windows 10 did it just fine)"
date: 2020-04-12
forum: Hardware
---

### Post by .Michael on 2020-04-12
Been up trying to figure out how to get sound to my tv from an app (Already figured out the app part, now I just need the DVI to HDMI part) and it only outputs to the monitor that has HDMI to HDMI. Is there a way to output it to the other port or is this probably a proprietary function of the video card driver?

---

### Post by CelticWarrior on 2020-04-12
Which graphics card?

---

### Post by SeijiSensei on 2020-04-12
In the past I had to use the proprietary NVIDIA driver to get sound over an HDMI connection. Never used DVI so I can't help with that. 

If you have an NVIDIA card, it's pretty easy to install the proper driver in modern Ubuntu versions. Just go to System Settings > Driver Manager and let it find the proper driver and install it on your machine. It takes a bit of time because the installer needs to compile a couple of things.

---

### Post by Tadaen_Sylvermane on 2020-04-12
I'd be double checking that myself. To my knowledge DVI has never carried audio, nor can it. There are hdmi > dvi adapters but they only carry the video. I'd be happy to be proved wrong. Your best bet would be a aux cable from headphones / sound jack into the tv somehow. Without knowing your available ports not sure. I'm certain something can be put together for it though.

---

### Post by CelticWarrior on 2020-04-12
> **Tadaen_Sylvermane said:**
> I'd be double checking that myself. To my knowledge DVI has never carried audio, nor can it. There are hdmi > dvi adapters but they only carry the video. I'd be happy to be proved wrong. Your best bet would be a aux cable from headphones / sound jack into the tv somehow. Without knowing your available ports not sure. I'm certain something can be put together for it though.

It's true the DVI standard doesn't carry audio but I've heard many years ago that it can. It has some extra pins that are generally unused so - I think - some manufacturers implemented non-standard audio channels in those pins. This non-standard may have became an unofficial standard: [https://www.cables.com/blog/does-dvi-support-audio/](https://www.cables.com/blog/does-dvi-support-audio/)

This depends on the actual hardware and, of course, drivers. The point is the assertion is plausible.

---

