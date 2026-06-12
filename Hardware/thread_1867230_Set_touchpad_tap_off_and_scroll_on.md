---
title: "Set touchpad tap off and scroll on"
date: 2011-10-22
forum: Hardware
---

### Post by kr0n1x on 2011-10-22
Hi, I'd like to turn off touchpad tapping while keeping vertical scroll (with right side of the touchpad) on.

And it should work at every boot, not only the current session (gsynaptics keep the options enabled just for the current session).

I tried adding:
```
Option "TouchpadOff" "2"
```
in 50-synaptics.conf (I made a copy of that file into  /etc/X11/xorg.conf.d/) but it turns off both tapping and scrolling.

I tried by adding:
```
Option "VertEdgeScroll" "true"
```
but it doesn't work.

Any suggestion? Thanks

---

### Post by kr0n1x on 2011-10-22
I tried this:

I deleted the two Options I've talked about (touchpadoff and vertedgescroll) and I've added these two instead:

```
Option "MaxTapTime" "0"
Option "MaxTapMove" "0"
```

It seems to work... it should be impossible to do a tap, right? Because by touching the touchpad the value would at least be more than 0.

If you know a better solution, I'd like to know it!

Thanks

---

