---
title: "Help debugging dual monitors on intel integrated graphics"
date: 2017-09-12
forum: Hardware
---

### Post by bhouse2 on 2017-09-12
I recently built a new PC with no separate graphics card and loaded Ubuntu on it. I am unable to figure out how to get both of my monitors working on it though. I have one monitor connected to the DVI port on my motherboard and that works fine. However, the second monitor, which I had to buy a DVI <-> VGA adapter for because my motherboard only has one DVI, isn't working. When I plug it in, nothing displays, and my first monitor starts flickering pretty badly. 

Setup:
CPU: Intel Core i3-7100
Mobo: MSI B250M PRO-VD
Monitors: Dell U2415 (Each with an HDMI -> DVI cable, one with the DVI <-> VGA adapter on the end)

xrandr output with both monitors plugged in:
```

Screen 0: minimum 320 x 200, current 3840 x 1200, maximum 8192 x 8192
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-1 connected 1920x1200+1920+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-3 disconnected (normal left inverted right x axis y axis)

```

I don't know why that shows a DP-1 connected, since they are both HDMI.

Any tips on where to start debugging? I don't even know what the culprit is here (Graphics, monitor, vga->dvi adapter...). Would I save a lot of hassle if I just bought a cheap video card that had two DVI ports?

---

