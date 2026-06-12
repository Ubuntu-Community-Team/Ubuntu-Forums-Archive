---
title: "xrandr gives inconsistent results"
date: 2011-05-09
forum: Hardware
---

### Post by barley05 on 2011-05-09
I'm trying to configure samsung syncmaster b2230 monitor on a 11.04 installation. When I ran xrandr for the first time, it gave me the following result:


Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0 +
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

But now xrandr only gives the following:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  

I'm unable to select 1920x1080 resolution that I prefer because only the 4 limited choices are available for me to choose. Any help in fixing this problem is appreciated.

---

