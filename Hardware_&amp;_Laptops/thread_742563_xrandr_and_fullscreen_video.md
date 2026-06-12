---
title: "xrandr and fullscreen video"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by incandenza on 2008-04-01
Hi,

I'm trying to add a 1680x1050 external LCD to my 1440x900 notebook screen (Dell Inspiron e1405 using Intel GMA945 graphics chipset).

I'm trying to set things up for when I'm primarily using the external display.  I've tried two ways: with or without doing "Ignore" "True" on the LVDS in xorg.conf.

If I do NOT ignore the LVDS, the problem is when I try to play a fullscreen video (or just maximize a window), it only goes up to the size of the smaller notebook screen (1440x900), even though I'm using the larger, external screen.  This happens whether or not I turn off the notebook screen by doing 'xrandr --output LVDS --off'.  (I can manually make a video window bigger but then I still have the window frame, menu bars, etc.)

If I DO ignore the LVDS, I can maximize videos just fine, but there's still one minor annoyance: the backlight of the notebook screen stays on (although no image is displayed).  I don't really want the backlight drawing power and wearing itself out while I'm not using it.  In this case turning it off with xrandr does nothing (I guess because the xorg.conf told xrandr to make this device appear nonexistent).

Any suggestions?

Thanks...

---

