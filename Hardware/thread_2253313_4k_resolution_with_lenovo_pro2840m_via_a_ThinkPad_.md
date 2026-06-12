---
title: "4k resolution with lenovo pro2840m via a ThinkPad USB 3.0 Dock and Yoga"
date: 2014-11-18
forum: Hardware
---

### Post by fungi on 2014-11-18
up until yesterday 4k screen was working great. at the login screen it is still working great.

but now when i login resolution drops to 1024x768 and 3840x2160 is not listed as an option settings.

i can work around the issue with 

```
xrandr --newmode "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync
xrandr --addmode DP1 "3840x2160_30.00"
```

but it would be nice if i could have it working out of the box again.

any ideas on where to start?

---

