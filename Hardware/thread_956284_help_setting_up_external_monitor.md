---
title: "help setting up external monitor"
date: 2008-10-23
forum: Hardware
---

### Post by dabd on 2008-10-23
Hi,

I tried using xrandr to setup my external monitor at the correct resolution.
My laptop (fujitsu amilo si1520) display controller Intel Corporation Mobile 945GM has a resolution of 1280x800.

My external monitor has a maximum resolution of 1440x900 and I would like to set up a dual monitor with the external monitor set to 1440x900 and the laptop to 1280x800.

I tried to use xrandr and follow this excellent tutorial, but unfortunately the site seems to be down since the past 12 hours or so. [www.thinkwiki.org/wiki/Xorg_RandR_1.2](www.thinkwiki.org/wiki/Xorg_RandR_1.2)

My laptop has a DVI connector and I have to use a converter from the external monitor VGA output.

Here is the output for xrandr -q.  If I try xrandr --output TMDS-1 --mode 1440x900 this changes my laptop screen resolution instead of the external monitor.  Aren't the external monitor settings listed as TMDS-1?  Why do I get a VGA connected listing besides the TMDS-1?


```
dabd@qbit:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2048 x 2048
VGA connected (normal left inverted right x axis y axis)
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       59.9*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected (normal left inverted right x axis y axis)
   1440x900       59.9 +   75.0  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
TV disconnected (normal left inverted right x axis y axis)

```

This are the relevant sections from my xorg.conf.  I added the Display SubSection with Virtual 2048 2048, as I started following the xrand tutorial mentioned above, but the site has been down and I couldn't finish it.

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		   Depth	24
		   Modes	"1440x900"
		   Virtual	2048 2048
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Thanks in advance.

---

### Post by dabd on 2008-10-23
I've been scouring the web looking for a solution to my problem, and here [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) it says that intel drivers don't support sdvo output.

Could someone please confirm this information?

If intel drivers for 945GM don't support sdvo/dvi output is there some workaround for configuring my external monitor?

Thanks.

---

