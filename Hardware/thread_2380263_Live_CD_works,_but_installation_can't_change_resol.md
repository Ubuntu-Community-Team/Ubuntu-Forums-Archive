---
title: "Live CD works, but installation can't change resolution! Lubuntu 17.10"
date: 2017-12-15
forum: Hardware
---

### Post by sciemulo on 2017-12-15
Hey, I ran the Live CD for Lubuntu 17.10 and everything worked great. I was able to change the resolution to 800x600, which is where I need it for my VGA to HDMI converter to work properly.

After installing the system, I'm limited to only 1280x1024. I have no idea why this would be. It should be the same graphics support as the Live CD, shouldn't it?

lshw -c video tells me my card is:
Matrox Electronics Systems Ltd.
Millennium G550

xrandr tells me:
On the Live CD:
minimum: 640x480 ... maximum: 1280x1024
On the installed system:
minimum: 1280x1024 ... maximum: 1280x1024

Everything else is identical in both systems.

I even tried setting my resolution in the Live system to 800x600 as I installed, both with and without updates and proprietary drivers - same result.

Any help would be greatly appreciated. Thank you.

---

### Post by sccman on 2017-12-15
Have you tried installing graphics drivers on the installed system?

---

