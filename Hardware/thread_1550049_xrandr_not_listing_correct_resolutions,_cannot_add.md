---
title: "xrandr not listing correct resolutions, cannot add new"
date: 2010-08-10
forum: Hardware
---

### Post by gleslie07 on 2010-08-10
**Well, while trying to fix that problem my motherboard seems to have died on me.  Unfortunately, I cannot pursue this any further for the moment.**

Hello.  I'm running Ubuntu Studio 10.04, and I'm trying to get my nVidia 6150SE card running correctly.  I've spent the better part of the day trying to install the nVidia driver, and I finally accomplished that, and now I have a new problem.  The nVidia Settings panel does not list the correct resolution of my monitor (1280x1024), and neither does xrandr -q, the return of that being:
```
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0 
```

So I went ahead and followed another thread about adding the correct resolution via xrandr, I ran "cvt 1280 1024" which returned:
```
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```

I then ran "xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync" and "xrandr --addmode default "1280x1024_60.00""

Everything seemed to be going smoothly until I tried to change to that resolution in the Xfce4 Display Settings panel, and nothing happened.  So I ran "xrandr --output default --mode 1280x1024_60.00", my screen flashed for a quarter of a second, and I was returned:
```
xrandr: Configure crtc 0 failed
```

Is there a way to get my system running the right resolution?  Between this and my bcm43xx driver (fixed this morning, thank god), I've been at this since yesterday morning and I'm about brain dead.

Thanks!
graham

---

