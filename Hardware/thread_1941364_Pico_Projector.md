---
title: "Pico Projector"
date: 2012-03-15
forum: Hardware
---

### Post by hazardcell on 2012-03-15
I am having a problem trying to get my pico projector working. I have an Optoma PK301 that has a mini-HDMI input which is connected to the HDMI output on my Compaq CQ50-104AU running Debian Squeeze (6.0.4). The laptop seems to detect the projector because when I run xrandr I get:

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS-1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-D-1 connected 1280x720+1280+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1280x720       60.0*+   60.0     50.0  
   1280x800       59.8  
   1024x768       60.0  
   800x600        60.3  
   720x576        50.0  
   720x480        59.9  
   640x480        60.0 

```

But for some reason I can't get any output on the projector. I noticed that the laptop detects the HDMI port as a DVI-D port but from what I understand that shouldn't matter because a DVI-D signal is still a valid HDMI signal. Anyone know what the problem might be?

---

