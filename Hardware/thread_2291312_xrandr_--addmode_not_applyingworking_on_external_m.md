---
title: "xrandr --addmode not applying/working on external monitor"
date: 2015-08-19
forum: Hardware
---

### Post by mhp_pmh on 2015-08-19
Hi all,

I've got a problem with my external monitor. The resolution is not detected correctly, it's a FHD screen but the maximum is "1024x768" via VGA. So I added FHD resolution manually with:

```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 "1920x1080_60.00"

```

now I can select this resolution in the settings. But then The screen goes black for about 2 seconds and it reverts to the old resolution (but the dialog with the countdown is shown). 
Same problem with 
```
xrandr --output VGA1 --mode "1920x1080_60.00"
```.
I also tried the same with 1280x720 resolution with the same result.

I'm using a laptop with a Nvidia GeForce GT520M and an Intel i5 graphics. I disabled the nvidia graphics (in nvidia-settings set to "Intel (Power Saving Mode)". With this one I got even more problems).

if you need any more information please tell me.

Regards

---

