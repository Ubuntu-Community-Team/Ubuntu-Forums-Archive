---
title: "ubuntu screen resolution external vga screen"
date: 2012-03-14
forum: Hardware
---

### Post by louisJ on 2012-03-14
Hi

I have plugged a VGA external screen (Lg flatron W2242T,  1680x1050 ) on my thinkpad t400 with Ubuntu 11.10...but I can't get Ubuntu (using Fn+F7) to display the right resolution for this screen...
Can you help me?

thanks

Here xrandr result: 
```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900       60.1*+   59.9     49.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9 +   60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9* 
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  

```

---

### Post by louisJ on 2012-03-15
PS: I can get the right resolution for the external screen with this command
xrandr --output VGA1 --mode 1680x1050

but I loose it at each reboot...is there a way to keep it?

---

### Post by louisJ on 2012-03-18
youhou!! is there someone here?

---

