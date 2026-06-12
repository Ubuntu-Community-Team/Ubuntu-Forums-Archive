---
title: "screen resolution"
date: 2014-10-01
forum: Hardware
---

### Post by stmcc on 2014-10-01
I have an acer lcd 17" monitor. I am using ubuntu 12.04

I can get the native 1440x900 resolution by these comands.

 cvt 1440 900 60
xrandr --newmode "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900

mac@HOME:~$  xrandr 
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192 
VGA1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1440x900       59.9* 
HDMI1 disconnected (normal left inverted right x axis y axis) 
DP1 disconnected (normal left inverted right x axis y axis) 
HDMI2 disconnected (normal left inverted right x axis y axis) 
DP2 disconnected (normal left inverted right x axis y axis) 
mac@HOME:~$ 

this works fine until I reboot.then it reverts to the original

mac@HOME:~$  xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192 
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis) 
DP1 disconnected (normal left inverted right x axis y axis) 
HDMI2 disconnected (normal left inverted right x axis y axis) 
DP2 disconnected (normal left inverted right x axis y axis) 
mac@HOME:~$

---

### Post by stmcc on 2014-10-10
I solved the problem 
go to this web site :[http://anhe51.wordpress.com/2012/01/30/change-resolution-of-unknown-monitor-in-ubuntu-11-10/](http://anhe51.wordpress.com/2012/01/30/change-resolution-of-unknown-monitor-in-ubuntu-11-10/)
Ubuntu 12.04 now boots to 1440x90 each time .

---

