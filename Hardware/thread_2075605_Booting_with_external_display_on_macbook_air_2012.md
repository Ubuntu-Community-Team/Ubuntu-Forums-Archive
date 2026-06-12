---
title: "Booting with external display on macbook air 2012"
date: 2012-10-24
forum: Hardware
---

### Post by agb32 on 2012-10-24
Hi,
I have a macbook air 2012 (5,1), and find that if I boot with an external display plugged in, then the laptop screen itself does not come on, and although is detected, only options for a lower resolution are given.
This happens with both precise and quantal.

If I wait until the greeter screen before plugging in the monitor, then all is fine, and I get dual monitors as expected.

Any suggestions?

Thanks...

---

### Post by Julas on 2012-11-26
I run into the same problem. I tried updating the drivers from the following PPA:
[https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

but nothing changed. Did you manage to fix it?

---

### Post by agb32 on 2012-11-26
Hi,
no, still haven't fixed it...
I currently just try to remember to unplug the external before booting.

---

### Post by skierpage on 2013-02-12
oops

---

### Post by skierpage on 2013-02-12
Me too (MacBook Air, Ubuntu 12.04 and now 12.10). Very annoying. Same workaround. [FONT=Courier New]sudo lshw[/FONT] reports I have a MacBookAir5,2.

I have several other problems with my MBA: the backlight shuts off but then immediately turns back on when I close the lid, Xorg locks up twice a week (cursor follows the mouse but nothing else updates), occasionally display hangs coming out of standby. It all might be related to switching between extended desktop on an external display and the built-in display only.

---

