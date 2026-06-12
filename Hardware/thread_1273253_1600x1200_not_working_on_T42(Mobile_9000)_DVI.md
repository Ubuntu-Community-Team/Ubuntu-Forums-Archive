---
title: "1600x1200 not working on T42(Mobile 9000) DVI"
date: 2009-09-23
forum: Hardware
---

### Post by oversky on 2009-09-23
I installed Ubuntu 9.04 on IBM T42 with ATI Mobile 9000 chipset. 
The T42 is connected to an external monitor, Dell 2007FP, through DVI cable.
The native resolution of 2007FP is 1600x1200.

I set up dual monitors with build-in System/Preferences/Display.
The display panel detected the 2007FP, and showed that it can work on 1600x1200 mode.
However, the external monitor turned to power saving 
 while I changed the display mode. In the mean time, T42 screen works. 

The dual monitors mode works OK when I lower the resolution of 2007FP to 1280x1024, 1152x864, or 1024x768. Then, I turned off T42 monitor in the display panel, and turned 2007FP to 1600x1200, still not working. Therefore, I think this should be due to the video driver, not the configuration.

I googled dual monitor setup, and found there is a bug in kernel 2.68.28, then I upgraded kernel to 2.68.30. However, not luck here. Following is information given from  xrandr with 1152x864 mode.

[B] Screen 0: minimum 320 x 200, current 2176 x 864, maximum 2176 x 1632
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 367mm x 275mm
   1600x1200      60.0 +
   1280x1024      75.0     60.0  
   1152x864       75.0* 
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
LVDS connected 1024x768+1152+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
[/B]
Any suggestion?

---

