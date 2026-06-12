---
title: "Can I change LCD resolution without scaling?"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by SamuelScarano on 2008-03-13
Hi, does anyone know how to reduce the display resolution in X without having it automatically scale to fit the LCD screen?

Scaling looks bad on LCDs. What I would like is to crop off the bottom 26 rows of my screen without having X scale the remaining 998 to fit the screen vertically, so that a logical pixel is still the same height as a physical pixel.

"Why would you want to do *that*?" you ask. Well, here's the long explanation, just in case you're interested. I have a laptop PC (Dell Dimension D520) with a built-in 1400x1050 display, and a regular external 1280x1024 LCD monitor. I'm using XRandR to put the external display above the laptop. It's a great setup, and XRandR works fine. The virtual display height would be 1024 + 1050 = 2074, but the driver won't enable hardware acceleration for more than 2048 lines, so to stay within that limit I let the two physical displays overlap by 26 pixels. So with this setup, xrandr -q says:

VGA connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
[snip]
LVDS connected 1400x1050+0+998 (normal left inverted right) 0mm x 0mm
[snip]

The overlap is surprisingly annoying, because a maximized window on either display shows up -- just a little bit -- on the other. So I would rather set the top display to 1280x998 (without the ugly scaling).

If anyone can tell me how to do this, that would be awesome.

By the way, as this is my first post, I just want to say that Ubuntu is fantastic, and I'm really impressed that, aside from this one issue, I can run it on my laptop without sacrificing any significant capabilities of the hardware.

Sam

---

