---
title: "VGA output to External Monior"
date: 2014-04-08
forum: Hardware
---

### Post by xcon2 on 2014-04-08
I am using a laptop and found that if I use a standard VGA cable, the external monitor is recognized and outputs at 1280x1024. If I use a longer 25 foot cable, the display shows as unknown and only outputs to 1024x768. How can I fix this? 

```
xrandr -qScreen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
eDP1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



```
```
lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)



```

---

### Post by TheFu on 2014-04-08
Use a shorter cable
or
Use a higher quality cable
or
Use a display booster device of some sort
or
switch to HDMI.

All things that you've probably already considered.

---

