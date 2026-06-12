---
title: "Resolution problems with Mobile GM965/GL960 Integrated Graphics Controller"
date: 2011-12-07
forum: Hardware
---

### Post by sajuukkhar on 2011-12-07
Hey guys


I have a Mobile GM965/GL960 Integrated Graphics Controller on my laptop.  


I updated from 10.10 to 11.10 and my screen resolution has been cut back to 1280x800 and can't do 1920x1080 with my second screen any more.  I can't recall how to get the drivers to work (or change them) to fix this problem.  

Any help would be appreciated alot alot :)

---

### Post by sajuukkhar on 2011-12-07
I just did a total reformat and it still doesn't come up with the resolutions that it did in 10.10.  I think it has something to do with the driver.  Any suggestions for the aforementioned graphics chip?

---

### Post by sajuukkhar on 2011-12-08
So I did 

xrandr -q

and outputted 

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       59.9 +
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
  1280x1024_60.00 (0xbe)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

But that's all I got, I have no idea how to redo this.  Apparently I can do this by making my own Xorg file but that didn't work too well.

---

