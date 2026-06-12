---
title: "915resolution on 1920 widescreen"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by FredTech on 2007-02-22
I have a Dell latitude X1 and I'm using 915resolution to get the correct screen resolution (1280x768). I'd like to connect an external 23" monitor (hp f2304) and I've managed to get 1920x1200 resolution by using the 915res. hack. But the text and image quality is blurry and weird. I've tried different 915resolution modes with various results, but never managed to get a clear and sharp image.

I did make this work on Dapper Drake, but never on Edgy. Now I've installed Feisty Fawn to see if that made any difference. So far with no luck.

Here's my xorg.conf

```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	74.56
	VertRefresh	60
	Modeline	"1920x1200" 193.25 1920 2048 2256 2592  1200 1201 1204 1242 -HSync +Vsync
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1280x768"
	EndSubSection
	SubSection "Display"
		Depth		32
		Modes		"1920x1200" "1280x768"
	EndSubSection
EndSection
```

At the moment I'm using this command for 915resolution
```
915resolution 4d 1920 1200 24
```

It gives the correct resolution, but with blurry/unclear image quality. I have no idea where the error is. Anyone else with experience on this?

---

### Post by dotman on 2007-03-07
I think your problem is that WUXGA exceeds the amount of lines of resolution that the X1's Intel GMA 900 can actually provide. I actually own one of those and lets face it, it was never meant to power a 24" screen. But since you are overriding its default maximums, it is attempting to stretch the image to fit your parameters. My only suggestion would be to try installing Intel's drivers with the mode setting feature, but still i don't think you are going to get exactly what you want out of it.

---

### Post by Laen on 2007-03-23
I had a similar problem with a 20.1'' widescreen at 1680x1050. Managed to get it to work with 915resolution, but everything was blurry. Another good pointer that something wasn't right was the fact that whenever I try to automatically readjust the image with the monitor auto button it would say something to the extend of "Adjusting image... Try 1680x1050 for best effect." It was a funny statement, having in mind that that was the actual resolution set anyway.

I got the solution from another post, which however I can't quote right now as I couldn't find it straight away.
Someone suggested adding your values in the 915resolution config file which was (I think) /etc/defaults/915resolution. My values there were set to auto, so I'm guessing such is the case with you also. Just replace them with your desired resolution and depth and reboot.

Hopefully that does it.

---

