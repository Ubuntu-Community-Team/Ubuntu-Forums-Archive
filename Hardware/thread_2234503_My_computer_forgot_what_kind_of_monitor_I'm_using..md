---
title: "My computer forgot what kind of monitor I'm using..."
date: 2014-07-15
forum: Hardware
---

### Post by stretch4 on 2014-07-15
I installed Xubuntu and the default display settings were perfect. In the display settings it was listed as "19' EMA" (It's an emachines monitor) and the resolution set to 1366x768, which is it's native res.

I was installing some software when my computer suddenly went to a black screen with a little blinking _ in the corner. Nothing I did could get a response except ctrl_alt_F1 which showed something about crash reporting and then back to black.

So, I restarted the computer, and now the resolution's wrong. When I open the display settings, the monitor is listed as "default" and 1366x768 is no longer listed as a resolution option.

How can I get it to recognize the monitor correctly again?

I suppose some hardware info might be handy:
```
stretch@Z-Xubuntu:~$ sudo xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 1024
default connected 1280x800+0+0 0mm x 0mm
   1280x1024      50.0     51.0  
   1280x960       52.0  
   1280x800       53.0* 
   1280x720       54.0  
   1152x864       55.0     56.0     57.0     58.0  
   1024x768       59.0     60.0     61.0  
   960x600        62.0  
   960x540        63.0  
   840x525        64.0     65.0     66.0  
   832x624        67.0  
   800x600        68.0     69.0     70.0     71.0     72.0  
   800x512        73.0  
   720x450        74.0  
   680x384        75.0     76.0  
   640x512        77.0     78.0  
   640x480        79.0     80.0     81.0     82.0  
   576x432        83.0     84.0     85.0     86.0  
   512x384        87.0     88.0     89.0  
   416x312        90.0  
   400x300        91.0     92.0     93.0     94.0  
   320x240        95.0     96.0     97.0  
stretch@Z-Xubuntu:~$

```

[COLOR=#696969]PS: 1366x768 seems to be a pretty common resolution. Shouldn't it be included in the default modes?[/COLOR]

---

### Post by stretch4 on 2014-07-15
Problem solved.
I switched from Nvidia's proprietary driver to the open-source X.org driver.
Why didn't I think of that sooner...?

---

