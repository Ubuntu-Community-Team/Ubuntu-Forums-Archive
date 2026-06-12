---
title: "Panning of screen and mouse in virtual desktop"
date: 2009-03-03
forum: Hardware
---

### Post by Termo on 2009-03-03
I have a IBM Thinkpad X41 with and intel i915 graphics driver. The resolution on my laptop is 1024x768, and should be kept that at all times. But I want to be able to have a higher resolution on the VGA output when I use my computer at work. (and they should be mirrored)

I can do so with xrandr, but the problem is that the mouse will only move in the area visible on the laptop (i.e. the 1024x768 from the top left corner)

I've tried to turn off the LVDS (laptop screen) by xrandr, but I'm still only able to use the mouse in the top left area of my screen. The gnome top bar and windows shows and moves fine in the whole area ?!?

I'm thinking that maybe I need to set up in either Compiz or gnome so that the mouse and/or screen should pan around in the whole virtual screen...

xrandr
```

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1280 x 1024
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       44.2 +   85.0     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)

```

xorg.conf (kept simple)
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver "intel"
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
SubSection "Display"
  Virtual              1280 1024 
EndSubSection

EndSection

```

---

### Post by Termo on 2011-01-29
Solved.

It turned out to be a matter of me using Synergy software to control mouse on the laptop (client side). So a restart of Synergy with the new size of desktop solved the problem :)

---

