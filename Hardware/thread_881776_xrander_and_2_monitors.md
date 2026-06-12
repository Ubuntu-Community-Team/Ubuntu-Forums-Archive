---
title: "xrander and 2 monitors"
date: 2008-08-06
forum: Hardware
---

### Post by kovalenko on 2008-08-06
I read following thread
[http://ubuntuforums.org/showthread.php?t=869915&highlight=xrandr](http://ubuntuforums.org/showthread.php?t=869915&highlight=xrandr)

With help of following script I can get my second monitor working:
```
#!/bin/bash
laptop="1280x800" #laptop resolution

current=$(xrandr | grep '*' | awk '{print($1)}')

if [ "$laptop" == "$current" ]

then 
	xrandr --output LVDS --mode 1280x800 --output VGA --mode 1280x1024 --right-of LVDS
else 
	xrandr --output VGA --off --output LVDS --auto
	
fi

exit 0
```

If you have asus laptop you can add path to this script to **action** variable in /etc/apci/events/asus-video and button fn-f8 will work as it should.


But I'm having problems with 2 monitors. Here you can see screenshot of my descktop:
[http://web2proxy.net/screenshot.png](http://web2proxy.net/screenshot.png)
My laptop resolution is 1280x800, second monitor (SyncMaster 970p) 1280x1024 and there is (left, bottom) area that I can't see.

At right there is another strange area, perhaps it's end of the virtual desktop with 3D acceleration enabled. As it's explained here:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

[QUOTE]Note that the maximum supported size of the virtual desktop for the Intel 945GM series of chipset with 3D acceleration enabled, is 2048x2048. The virtual screen can be larger but DRI will be disabled./QUOTE]

Is it possible to make right area work as usual without "special effects"? And on switching I want panels stay at laptop's display. I can drag them back, but it's not convenient to do that each time.

lspci | grep -i graphics:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

xrandr -q
```
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 1024
VGA connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       59.9*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
```

---

