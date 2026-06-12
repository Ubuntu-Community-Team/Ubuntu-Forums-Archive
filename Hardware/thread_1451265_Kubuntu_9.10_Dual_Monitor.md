---
title: "Kubuntu 9.10 Dual Monitor"
date: 2010-04-10
forum: Hardware
---

### Post by freshtoast on 2010-04-10
Hi guys,

Does anybody have any pointers on how I get an extended desktop working on Kubuntu 9.10? (ATI x700)

I can get it mirrored quite easily - System settings > Display > Size and Orientation.

But if I click on multiple monitors I get: *"This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration."*

So, I run ```
xrandr -q
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1152x864       60.0
   1024x768       60.0*
   800x600        60.3
   640x480        59.9
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 330mm x 210mm
   1280x800       60.1*+
   1280x720       59.9
   1152x768       59.8
   1024x768       59.9
   800x600        59.9
   640x480        59.4
DVI-0 disconnected (normal left inverted right x axis y axis)

__________________________________________

So, I run the following:

```
xrandr --output VGA-0 --off
```

```
xrandr --output LVDS --auto --output VGA-0 --auto --right-of LVDS
```

And I get told that "xrandr: screen cannot be larger than 1280x1280 (desired size 2304x800)"

So I have manually creates an xorg.conf file, and added "Virtual 2304 800" so the relevant section reads:
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	Virtual 2304 800	
EndSection

Restarted the computer, but I still get the same result... any pointers?!

---

