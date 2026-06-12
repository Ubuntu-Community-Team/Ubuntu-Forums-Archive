---
title: "Bad pixelation on 2560x1440 display"
date: 2013-02-09
forum: Hardware
---

### Post by papalagi on 2013-02-09
hi everybody

i've just bought a SAMSUNG S27A850D monitor, capable of 2560x1440 resolution

i attached the HDMI output from my Acer 5742g notebook using an adaptor

unfortunately the computer has an Optimus NVIDIA GT540M, and i use Bumblebee

the monitor is recognised and the EDID read, but the maximum resolution in the settings is 1920x1200

adding a New Mode with xrandr i can get the full resolution:

```
xrandr --newmode "2560x1440_60.00"  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
xrandr --addmode HDMI-0 "2560x1440_60.00"
xrandr --ouput HDMI-0 --mode "2560x1440_60.00"

```

unfortunately the display is badly pixelated and looks like the RGB subpixeling goes wrong (see the attached picture)

the fonts are very small, smaller than the change in resolution can justify

do you have an idea of what can go wrong?

cheers!

[ATTACH]231177[/ATTACH]

---

