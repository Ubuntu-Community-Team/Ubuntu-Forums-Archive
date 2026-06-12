---
title: "How can I increase the monitor resolution of my netbook?"
date: 2009-05-03
forum: Hardware
---

### Post by DeepSeaNautilus on 2009-05-03
I have ubuntu 8.10 installed on an acer aspire one. I have connected an external screen to the netbook's vga port, but the resolution is very low and I don't know how to change it because in the system>screen resolution application, the highest resolution available is 800x600, which is my current resolution.

```
$ lspci | grep -i 'graphics'
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

$ cat /etc/X11/xorg.c
Section "Device"
	Identifier	"Configured Video Device"
	Option	"MonitorLayout" "LVDS,VGA"
	Option	"Clone" "True"
	Option	"AccelMethod" "EXA"
	Option	"MigrationHueristic" "greedy"
	Option "CacheLines" "1980" 
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 1600 x 1600
VGA connected 800x600+0+0 (normal left inverted right x axis y axis) 410mm x 257mm
   1440x900       59.9 +   75.0     59.9     60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      75.0     60.0     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 800x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0 +
   800x600        60.3* 
   640x480        59.9

```

 How can I change the resolution of the external screen only to those displayed by the xrand command and how can I configure the monitor and the screen separately?

I think this can be solved by editing the xorg.conf to the proper configuration, but I am not sure how to configure it properly, can anyone tell me how to configure this file to solve my problem or if there is any other way to fix this? Thanks in advance

---

### Post by DeepSeaNautilus on 2009-05-03
OK, I am answering myself so others can benefit. Reading the xrandr man page I found that It does not only inform about the valid screen resolutions, but can also change the resolution for a specified screen and many other operations. If the desired resolution is already registered, simply type:
xrandr --output <screen> --mode <resolution>

Worked great for me :), and works much better than it does in windows xp (just like the wifi adapter by the way) even when I tried with all the available resolutions.

---

