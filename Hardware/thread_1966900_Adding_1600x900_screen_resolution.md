---
title: "Adding 1600x900 screen resolution"
date: 2012-04-27
forum: Hardware
---

### Post by tahunasky on 2012-04-27
Hi,

I have just installed ubuntu 12.04 under VMWare on my laptop - HP elitebook 8560.
I can not get it to use a screen resolution of 1600x900. I have tried adding it with xrandr following instructions i have found on here but i doesnt work.. all i get is a > prompt.

xrandr output:

Screen 0: minimum 1 x 1, current 1440 x 900, maximum 8192 x 8192
Virtual1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.0 +   60.3  
   2560x1600      60.0  
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   1920x1200      59.9  
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9* 
   1280x960       60.0  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1280x768       59.9  
   1024x768       60.0  
   640x480        59.9  
Virtual2 disconnected (normal left inverted right x axis y axis)
Virtual3 disconnected (normal left inverted right x axis y axis)
Virtual4 disconnected (normal left inverted right x axis y axis)
Virtual5 disconnected (normal left inverted right x axis y axis)
Virtual6 disconnected (normal left inverted right x axis y axis)
Virtual7 disconnected (normal left inverted right x axis y axis)
Virtual8 disconnected (normal left inverted right x axis y axis)



ubuntu 11.10 worked find, and detected the default resolution.

why isnt 1600x900 in the resolution list as its a default size of alot of laptops screens ?

thanks

---

### Post by FiFE on 2012-04-27
This helped me: [http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768](http://askubuntu.com/questions/37411/screen-resolution-stuck-at-1024x768)

---

### Post by tahunasky on 2012-04-27
Thanks FiFE...

And for anyone else who might be having the same problem I got it to work doing this:

xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

xrandr --addmode Virtual1 "1600x900_60.00"

xrandr --output Virtual1 --mode "1600x900_60.00"

---

### Post by davidgutu on 2012-11-06
Thanks. Worked amazingly :)

---

### Post by davidgutu on 2012-11-07
You may need to add this in ```
/etc/gdm/Init/Default
``` before initialization (prety much at the top) to make sure it's run every time you start.

---

