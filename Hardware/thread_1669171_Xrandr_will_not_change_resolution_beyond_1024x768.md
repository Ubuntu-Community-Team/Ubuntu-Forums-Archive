---
title: "Xrandr will not change resolution beyond 1024x768"
date: 2011-01-17
forum: Hardware
---

### Post by Polymuter on 2011-01-17
While using the default Radeon driver for my ATI Radeon HD 4550 I cannot get xrandr to change the output resolution beyond 1024x768.  Xrandr does somewhat change the resolution yet my monitor still displays at 1024x768.  So the end result is my desired resolution (i.e. 1280x768 or 1360x768) squeezed to fit a 1024x768 viewing area.  It is beyond my knowledge to accurately describe my situation technically so I'll attach an image representing my issue and write the process I use to change the resolution via xrandr.

**Query modes:**
```

scott@vivi:~> xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)

```[B]Create modeline using cvt:
[/B]```

scott@Vivi:~> cvt 1360 768
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

```[B]Add mode:
[/B]```

scott@Vivi:~> xrandr --newmode "1360x768"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

scott@Vivi:~> xrandr --addmode VGA-0 "1360x768"

```[B]Change resolution:
[/B]```

scott@Vivi:~> xrandr --output VGA-0 --mode "1360x768"

```After I change the resolution is when I get the problem.  The attached image displays what I see after I issue the command (I had to re-size it with Gimp because screenshots display 1360x768 perfectly).

I am currently using openSUSE 11.3, but the openSUSE community forums seems to have some database issues and I cannot login.  Since I recently switched from Ubuntu 10.10 due to very similar issues I hope this can somehow be resolved here with your help.

*Note: I get the same results using my on board Intel graphics chip.

Thanks in advanced.

---

