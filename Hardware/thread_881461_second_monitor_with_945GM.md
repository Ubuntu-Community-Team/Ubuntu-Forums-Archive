---
title: "second monitor with 945GM"
date: 2008-08-06
forum: Hardware
---

### Post by TheMono on 2008-08-06
Hiya - 

I bought a new eee 901 - which I highly reccomend - except for this one issue. The machine will connect to another display in clone mode, but it won't allow me a second screen in the sense of one to the side of the other. 

As far as I can tell, this should be solved by adding the 'virtual' line into the xorg.conf, but it doesn't solve anything. Any ideas?

As background, to enable the second screen I'm using
xrandr --output VGA --auto --right-of LVDS
Which gives me the error that the screen cannot be larger than 1024x1024.

---

### Post by Megatog615 on 2008-08-06
Try --mode 640x480. That should get it working at least with a standard resolution. If that works, try higher resolutions with --mode.

---

