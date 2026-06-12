---
title: "Still trying to set HP laptop to native resolution"
date: 2012-02-27
forum: Hardware
---

### Post by redss on 2012-02-27
I have a HP Pavillion dv6500 laptop. I read somewhere online that the graphics card is a "383MB NVIDIA GeForce 8400M GS with DirectX 10" (but somewhere else online said Intel X3100)

When I boot ubuntu live USB, the video is all screwed up (out of sync?) but I managed to get it to boot with better video using the nomodeset boot option.

But now the problem is that the resolution is set at 1024x768 which is not the native resolution of the laptop's native 1280x800 resolution.

So I performed the following steps to add the native resolution:
> cvt 1280 800 
    xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
    xrandr --addmode default 1280x800_60.00

But when I try to switch to that resolution in the monitor preferences, I get the following message:
> The selected configuration for displays could not be applied
could not set the configuration for CRTC 262
I assume this has to do with the nomodeset boot option I used.  How can I get this working in the native resolution?

---

### Post by redss on 2012-02-28
Anybody?

---

