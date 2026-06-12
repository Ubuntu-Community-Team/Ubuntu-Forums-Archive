---
title: "3rd monitor on DisplayPort - Lenovo T510 - Ubuntu 10.04 (intel graphics)"
date: 2010-07-07
forum: Hardware
---

### Post by rozmar564 on 2010-07-07
Heyya All -

I am trying to set up a 3rd monitor via DisplayPort on my ThinkPad T510.
So far no success. This is how I was trying and what I've got::
If I go to System->Preferences->Monitors I DO see the 3rd monitor. But when I turn it from Off to On and hit Apply - I get the message - "The selected configuration for screens could not be applied - could not find a suitable configuration of screens".
This is what my xrandr says
```
xxx@xxx3834ny:/www/developer/application/views$ xrandr -v
xrandr program version       1.3.2
Server reports RandR version 1.3
also
xxx@xxx3834ny:/www/developer/application/views$ xrandr -q
Screen 0: minimum 320 x 200, current 2646 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+1366+0 (normal left inverted right x axis y axis) 380mm x 300mm
   1280x1024      60.0 +   75.0* 
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
LVDS1 connected 1366x768+0+256 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+   50.0  
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
```
Can anybody give me some help on what am I suppose to do?

---

