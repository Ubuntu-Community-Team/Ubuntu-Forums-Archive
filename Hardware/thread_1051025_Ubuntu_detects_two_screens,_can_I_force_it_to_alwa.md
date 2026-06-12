---
title: "Ubuntu detects two screens, can I force it to always use one of them?"
date: 2009-01-26
forum: Hardware
---

### Post by mesh2005 on 2009-01-26
Ubuntu detects two screens: the laptop screen and the external one. The problem is they are both of different resolution, so screen mirroring results in very poor resolution on the external display. 

Can I force Ubuntu to always use the external display and ignore the laptop screen? Here is the output of lspci | grep VGA:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

Thank you.

---

### Post by nixscripter on 2009-01-26
Please post the contents of the **/etc/X11/xorg.conf** file, which is what controls the display stuff.

---

### Post by mesh2005 on 2009-01-28
Thank you for your reply. Here are the contents of the xorg.conf:
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1680 1818
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"intel"
EndSection

---

### Post by nixscripter on 2009-01-28
I don't know if you can force it to use **only** the external screen, but I think I can solve your resolution problem.

There are two things involved. The first has to do with this line:

```

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
**Virtual 1680 1818**
EndSubSection
EndSection

```

That says "my screen, across all my monitors, is 1680 x 1818". If you make that bigger, then the resolution of all your monitors is less constrained.

The second thing has to do with the way your external monitor is configured. THe resolutions allowed can sometimes be found in the output of this command: ```
xrandr -q
```

See if there is one in there you want, and I can help you switch to it.

---

### Post by mesh2005 on 2009-01-28
Here is the output of "xrandr -q":

> VGA connected 1680x1050+0+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      75.0     60.0     60.0  
   1440x900       59.9  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected 1024x768+0+768 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0 +
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9 

I wanna use the best possible resolution for the VGA connected monitor, any ideas?

Thank you.

---

### Post by nixscripter on 2009-01-28
Alright, let's try switching the VGA monitor's resolution.

1. Open up Screen and Graphics under Ubuntu Menu -> System -> Administration menu.
2. Screen 1 should be the internal screen, which is the laptop. That should be at 1680 x 1050, and have the "Default screen" radio button selected. Screen 2 should be the external monitor, at 1024 x 768.
3. Change screen 1's resolution to 1280 x 1024, then select screen 2 and radio button  "Secondary Screen", and "Mirror default screen".
4. Hit OK.

If it doesn't work, just wait 15 seconds, and the old settings will revert.

Let me know what happens.

---

### Post by mesh2005 on 2009-01-28
There are no default screen checkbox or secondary screen checkbox, is that normal?

---

### Post by mesh2005 on 2009-01-28
You know what, I found a why to stop the laptop screen. Simply, I set its resolution to "Off". Now, I can use my external screen as the default one :)

Thank you.

---

### Post by nixscripter on 2009-01-28
Well... okay. That's odd. But if you did fix your problem, that's good.

Please mark the thread as solved (under the thread tools menu).

---

