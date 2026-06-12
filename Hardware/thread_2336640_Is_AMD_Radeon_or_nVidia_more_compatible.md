---
title: "Is AMD Radeon or nVidia more compatible?"
date: 2016-09-09
forum: Hardware
---

### Post by PenguinLust on 2016-09-09
I tried to look at what *looks *like a very comprehensive resource, like [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia) but it seems very old. What tends to be more compatible these days? I'm thinking of either Radeon HD 6850 or nVidia GeForce GTX 550.

---

### Post by gordintoronto on 2016-09-10
I have never had a problem with my Nvidia.

---

### Post by pqwoerituytrueiwoq on 2016-09-10
both of those cards should run just fine on the current version of ubuntu
the only amd drives are the open source ones now
the only issue i have had with nvidia (closed source driver) is if i turn my TV (only monitor via HDMI) off the system forgets it there and will not use it when it turns back on without sending a command over ssh to it to tell it to use that display, i got so annoyed with this i set a button up on my raspberry pi to do this
that command is [FONT=courier new]DISPLAY=":0.0" xrandr --output HDMI-0 --auto[/FONT]

---

