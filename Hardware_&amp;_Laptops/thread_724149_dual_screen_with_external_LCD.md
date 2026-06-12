---
title: "dual screen with external LCD"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by napsy on 2008-03-14
Hello.

I have a laptop with resolution 1280x800 and an external LCD 19" monitor with 1280x1024 maximum resolution.

The laptop has intel gma x3100 graphics chip and if I try to create the virtual screen with xrandr I get the following error:
> 
$ xrandr --output VGA --below LVDS --rate 60 --mode 1280x1024
xrandr: screen cannot be larger than 1280x1280 (desired size 1280x1824)


Here is the output of xrander with no arguments:
> 
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0     59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)


I'm running Hardy with the latest updates, so Xorg-core is 1.4 and xserer-xorg is 7.3.

Please help.

---

### Post by yarox on 2008-04-01
Hi,  I'm running Ubuntu Gutsy on a Macbook Santa Rosa (1280x800) and my external LCD is also 19'' (1280x1024). I had the same issue with dual monitors, so I think this could help.

The thing here is the the virtual screen resolution to be used. Your xrandr output says you want a 1280x1824 resolution, but actually, your maximum is 1280x1280. So, in your **xorg.conf** look for the **Section "Screen"** and once there, in the **SubSection "Display"** add this: **Virtual 1280 1824** . Restart your X session, type  **xrandr --output VGA --below LVDS** in your terminal and I think you're done :)

That worked for me but, if you still having problems, this links may help:[INDENT][http://ubuntu-tutorials.com/2007/10/25/dual-monitor-setup-help-1280x800-1440x900/](http://ubuntu-tutorials.com/2007/10/25/dual-monitor-setup-help-1280x800-1440x900/)
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)[/INDENT]

---

