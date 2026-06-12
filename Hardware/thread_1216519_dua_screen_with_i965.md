---
title: "dua screen with i965"
date: 2009-07-18
forum: Hardware
---

### Post by Kouran-sama on 2009-07-18
heya,
im trying to get my external monitor and my laptop monitor to work in 9.04. i have an i965 graphics device and the monitor is connected to the vga. i can switch between the two monitors and if i set the resolution to 1680x1050 (which is the one on my external monitor) i can even switch on the laptop monitor (1400x1050) and see a cloned image,.. sure about 200 pixels are missing on the left side because of the resolution. what i wanted to to is extend the desktop to the notebook screen to put im-windows there or stuff like that. i tried it with xrandr:

```

xrandr --output VGA --left-of LVDS

```

the only output was that my desired resolution would be 3080x1050 (which is correct) but the resolution can't be higher than 1680x1680. and finally it does nothing.

any ideas?
thanks in advance
tom

---

