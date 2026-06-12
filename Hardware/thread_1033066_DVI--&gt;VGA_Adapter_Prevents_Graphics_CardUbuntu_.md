---
title: "DVI--&gt;VGA Adapter Prevents Graphics Card/Ubuntu from Recognizing Monitor+Correct Res."
date: 2009-01-07
forum: Hardware
---

### Post by Liquid 2 on 2009-01-07
The title basically sums up my issue.

My card is an Nvidia 6800 and my monitor is a Viewsonic Q19wb.  The native resolution of the monitor is 1440x900, but Ubuntu 8.1 (Ibex) won't allow me to set the correct resolution, forcing me to use a very hard to look at stretched resolution.

I've tried editing xorg.conf (everything from adding modelines to making a Display subsection with the correct resolution to telling my graphics card to ignore EDID information) and using an old driver with no avail.  
The person who helped me on #ubuntu@freenode thinks the DVI adapter which I use to connect my graphics card (which only outputs in DVI) to my monitor (which only takes VGA) is the root of the issue.

I'm currently back on the default xorg.conf, but I think I have copies of most of what I tried, if anyone thinks that it might help them/me.

Any ideas?  Thanks.

---

### Post by Liquid 2 on 2009-01-07
Bump.  

Any help would be greatly appreciated, since this issue is making my desktop nearly unusable. Thanks!

---

### Post by Liquid 2 on 2009-01-08
Ba-da-bump.

---

### Post by Liquid 2 on 2009-01-08
Anyone out there?

---

### Post by Liquid 2 on 2009-01-09
Bump.

---

### Post by Andy-N on 2009-01-09
I am having the same problem as well. I have an intel card with a DVI-> VGA converter which then goes into the monitor.

It shows up as this:

```

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2432 x 1024
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1600x1024      60.2  
   1280x1024      75.0     60.0     60.0  
   1440x900       75.0     59.9     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0* 
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  

```

And as two monitors in the "Screen Resolution App".

Still looking into it... I'll report back if I find anything.

---

### Post by svestka on 2009-03-29
I have similar problem. I've solved it with the following script:

```

#!/bin/bash
xrandr --newmode  "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --verbose --addmode VGA "1440x900_60.00"
xrandr --output VGA --mode 1440x900_60.00

```

If you need another mode, this may help you too:
```
cvt XXXX YYYY
```
where XXXX YYYY is your resolution.


Hope I helped and sorry for my English, bye :)

---

