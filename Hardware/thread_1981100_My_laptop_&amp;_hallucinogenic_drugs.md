---
title: "My laptop &amp; hallucinogenic drugs"
date: 2012-05-16
forum: Hardware
---

### Post by Bartender on 2012-05-16
I couldn't help myself with the drugs and flashback reference.

The IT dept. gave me an old HP Compaq nc6000 laptop.  Built about 2004.  Yeah, it's old.  Pentium M proc, etc.  Nice build quality, though.

It has an ATI Mobility video chipset.  Works fine in Xubuntu, but every time I shut it down I get an acid flashback on the screen for several seconds.  The display always looks similar, in that you can discern the Xubuntu logout shapes, but the colors are always different.  The attachment doesn't do justice to the experience.  The colors are much wilder.  Remember black lights and psychedelic posters?  Yeah, that's more like it.

Anyway, not really looking for help so much as wanted to share my laptop's trippy display.

---

### Post by sudodus on 2012-05-16
> **Bartender said:**
> I couldn't help myself with the drugs and flashback reference.

The IT dept. gave me an old HP Compaq nc6000 laptop.  Built about 2004.  Yeah, it's old.  Pentium M proc, etc.  Nice build quality, though.

It has an ATI Mobility video chipset.  Works fine in Xubuntu, but every time I shut it down I get an acid flashback on the screen for several seconds.  The display always looks similar, in that you can discern the Xubuntu logout shapes, but the colors are always different.  The attachment doesn't do justice to the experience.  The colors are much wilder.  Remember black lights and psychedelic posters?  Yeah, that's more like it.

Anyway, not really looking for help so much as wanted to share my laptop's trippy display.
I have something similar with an IBM thinkpad t41 of similar age. I think the graphics mode does not support the advanced colour map necessary to show the picture properly. I run the boot in text mode, so I have edited /etc/default/grub.
```
sudo nano /etc/default/grub
``` and removed splash
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" -->
GRUB_CMDLINE_LINUX_DEFAULT="quiet"

and then run ```
sudo update-grub
```

But if you enjoy the psychedelic colours, keep the setting ;-)

---

### Post by Bartender on 2012-05-17
sudodus -
I should have explained things better.  The psychedelia only occurs while the laptop is shutting down.  During bootup nothing seems out of order.

Actually, it _is_ kind of fun to see what sort of crazy colors will appear each time :p

---

