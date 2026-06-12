---
title: "Wrong resolution oddity with laptop/monitor"
date: 2016-07-10
forum: Hardware
---

### Post by Bucky Ball on 2016-07-10
Hi all,

I have my laptop attached to an Acer X193HQ monitor. The monitor resolution should be 1366x768. This what I get from xrandr:

```
Screen 0: minimum 320 x 200, current 1366 x 1536, maximum 8192 x 8192
VGA-0 connected 1024x768+194+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
LVDS connected primary 1366x768+0+768 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768      59.97*+
   1280x720      59.86  
   1152x768      59.78  
   1024x768      59.92  
   800x600       59.86  
   848x480       59.66  
   720x480       59.71  
   640x480       59.38
```

These are the two screens. As you can figure, the VGA is the monitor, the other the laptop screen. The laptop screen is fine and, also clear, the monitor is not. I can't get anything beyond 1024x768_60.00. (The sizes in brackets at the end of each line would possibly describe why I getting whacky screen placement too I guess.)

So after a bit of digging, I ran this with this output as a result:

```
~$ xrandr --addmode VGA-0 1366x768_60.00
xrandr: cannot find mode "1366x768_60.00"
```

Ok. So I ran with the same as the laptop screen (ending in 59.97 instead of 60.00) and got same result with those numbers. Stumped. The screen seems to be not recognised properly (oddly enough) and in the wrong position. 

They are one above the other, that's all good, but see attachment for the output from arandr. The laptop screen, which is physically smaller than the monitor, shows the opposite and that's the way the setup looks to me and is operating. 

* The oddity. I bought this monitor for my in-laws when I built them a 'buntu system about seven years ago because I already had two of them and they were fine. As it happens, I still use my two as second monitors, one with my laptop exactly the same as I am now, and the other with my desktop which has a NVidia GTX 970. They both work fine, correct resolution, size, everything. Just boot the machine and there it is, no tweaking necessary. 

Bottom line: Laptop and second monitor working fine at home, I unplug my laptop, drive nine hours, setup my laptop and plug in an *identical* monitor - same model, make, etc. - and this. Go figure. :-k

No biggie, can live with it, but any suggestions greatly appreciated. Would prefer to be seeing things as they should be. Tnx in advance.

---

