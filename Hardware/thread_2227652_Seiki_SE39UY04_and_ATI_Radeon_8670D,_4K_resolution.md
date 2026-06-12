---
title: "Seiki SE39UY04 and ATI Radeon 8670D, 4K resolution but low refresh rate?"
date: 2014-06-03
forum: Hardware
---

### Post by Ryan_Freebern on 2014-06-03
I recently set up a Seiki 39" 4K LCD connected to the HDMI output of an ATI Radeon 8670D. According to the 8670 [specs]("http://www.amd.com/en-us/products/graphics/desktop/oem/8670"), it should support full 4K resolution (3840x2160) at a 30Hz refresh rate. However, I'm only getting 14Hz, and no matter what I try, I can't get it to go higher than that.

I've tried the open-source fglrx driver, ATI's catalyst drivers (both stable version 14.4 and beta 14.6). I've tried calculating and setting dozens of modelines via xrandr by hand. I'm not sure what else to try.

Here's the xrandr output:
```
[FONT=arial]Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 16384 x 16384
DFP1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 854mm x 481mm
   3840x2160      13.8*+
   2048x1536      13.8  
   1800x1440      13.8  
   1856x1392      13.8  
   1792x1344      13.8  
   1920x1200      13.8  
   1920x1080      60.0     50.0     59.9     60.1     50.0     24.0     60.0     24.0  
   1600x1200      13.8  
   1776x1000      50.0     59.9     50.0     24.0     60.0  
   1680x1050      60.0     50.0     59.9     24.0     24.0  
   1400x1050      60.0     50.0     59.9     24.0     24.0  
   1600x900       50.0     59.9     24.0  
   1280x1024      60.0     50.0     59.9     24.0     24.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0     50.0     59.9  
   1024x768       75.0     70.1     60.0  
   1152x648       50.0     59.9  
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3  
   720x576        50.1     50.0  
   800x480        72.2     75.0     60.3  
   720x480        60.1     60.0     60.1     59.9  
   640x480        75.0     72.8     59.9[/FONT]
```

Any suggestions would be greatly welcome. While 30Hz isn't great, 14Hz is barely usable.

Thank you!

---

