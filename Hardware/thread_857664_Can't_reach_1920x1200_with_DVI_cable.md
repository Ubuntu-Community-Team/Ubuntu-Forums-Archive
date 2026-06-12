---
title: "Can't reach 1920x1200 with DVI cable"
date: 2008-07-12
forum: Hardware
---

### Post by mozartatplay on 2008-07-12
Hi

I'm running hardy with a samsung 245t monitor and an NVIDIA fx 5500 display card but I can only reach 1600x1200 with the DVI cable yet I can reach 1920x1200 with the old analog VGA cable.

It doesn't matter what I happen to set in my xorg.conf file, it appears hardy uses a program called "xrandr" to detect what resolutions are possible and basically simply ignores all the available resolutions that were entered in the xorg.conf file. 

The problem is xrandr can't detect the 1920x1200 resolution when I have the DVI cable plugged in. Any iedas?

---

### Post by cprofitt on 2008-07-12
> **mozartatplay said:**
> Hi

I'm running hardy with a samsung 245t monitor and an NVIDIA fx 5500 display card but I can only reach 1600x1200 with the DVI cable yet I can reach 1920x1200 with the old analog VGA cable.

It doesn't matter what I happen to set in my xorg.conf file, it appears hardy uses a program called "xrandr" to detect what resolutions are possible and basically simply ignores all the available resolutions that were entered in the xorg.conf file. 

The problem is xrandr can't detect the 1920x1200 resolution when I have the DVI cable plugged in. Any iedas?

Might be a detection issue... I have a similar problem with one of my monitors being on a VGA cable. I had to manually edit the xorg.conf file and force the resolution and refresh.

---

