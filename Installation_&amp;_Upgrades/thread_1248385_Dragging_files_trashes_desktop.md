---
title: "Dragging files trashes desktop"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by albanach on 2009-08-24
I updated Ubuntu 8.10 to 9.04 on my Packard Bell Easynote laptop, and since then, if I try to drag a file from one location to another, the display is completely distorted.  A trail of icons is left behind the mouse movement, the items on the taskbar disappear, and the rest of the screen is just a graphical mess.  

Below is a copy of the relevant section of my xorg.conf file.

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
				Modes	"1280x800"
			EndSubSection
EndSection

Any help much appreciated

---

### Post by stlsaint on 2009-08-24
what type of graphics card driver are you using? ubuntu's or proprietary?

---

### Post by albanach on 2009-08-26
I am using the Ubuntu driver. The adapter is VIA S3G.

Thank you

---

