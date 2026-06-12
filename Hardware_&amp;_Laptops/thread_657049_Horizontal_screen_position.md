---
title: "Horizontal screen position"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by penman242 on 2008-01-03
I  know there are a lot of posts on this but none of them (I have found) are fixing my particular problem.

I have a dual-boot and when I boot into ubuntu the screen is positioned too far to the left.  I have intel integrated graphics in a dell and a compaq V710.

I have no auto adjust feature.

Here are pertinent sections of my xorg.conf:
```

Section "Device"
	Identifier	"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"COMPAQ V710"
	Option		"DPMS"
	HorizSync 30-75
	VertRefresh 50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
	Monitor		"COMPAQ V710"
	DefaultDepth	24
	SubSection "Display"
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Any help would be greatly appreciated!

---

### Post by jeremytaylor on 2008-01-03
Try using xvidtune. Once you've fiddled with the settings until it looks right it can spit out a modeline that you can then copy and paste into your xorg.conf file.

Jeremy

---

### Post by penman242 on 2008-01-03
Thank you for that quick reply.

When I start xvidtune and click auto, as shown here:

[http://www.xfree86.org/3.3.6/QuickStart6.html](http://www.xfree86.org/3.3.6/QuickStart6.html)

then click right (or left), I get:

Invalid Mode Requested - Sorry you have requested a mode-line that is not possible, or supported by your hardware configuration.

Am I doing something wrong?  Thanks again.

Edit:  same thing happens with gksudo xvidtune

---

