---
title: "Second display's workspace overlays first one"
date: 2015-01-19
forum: Hardware
---

### Post by Ratatwisker on 2015-01-19
Hi,

I'm using xubuntu 14.10 on my laptop (ThinkPad E525) and have an external monitor connected. For example one standard configuration - external display right of built in - looks like this (xrandr output):
```
VGA-0 connected 1280x1024+1366+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4
```
However, I noticed that the contents of the two displays overlap in the middle by two pixels. That is, on the external display I can see the two right most columns of the laptop's display. Which annoys be obviously. Using xrandr I moved the external display two pixels to the right which fixes the visible overlay:
```
xrandr --output VGA-0 --mode 1280x1024 --pos 1368x0 --output LVDS --mode 1366x768 --pos 0x0
```.
I guess it has something to do with 1366 (laptop's resolution) is not divisible by 8 and 1368 is.

Unfortunately this introduces another annoying problem: if the displays are aligned at the top, there is extra space at the bottom of the laptop's screen reaching all the way down to 1024, where then my launcher bar is located so it becomes inaccessible for me. Aligning the displays at the bottom, the launcher bar works fine again and, to my surprise, the task bar at the top is also at it's proper location. However, there is still extra space at the top of the laptop's display. That frequently causes my mouse cursor to miss when I want to switch to another window for example.

Maybe there are more xrandr options I'm missing which might help me deal with this problem or other workarounds? Any suggestions?

---

