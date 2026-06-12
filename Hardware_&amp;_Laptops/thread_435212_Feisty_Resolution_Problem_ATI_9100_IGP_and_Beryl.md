---
title: "Feisty Resolution Problem ATI 9100 IGP and Beryl"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by nimes on 2007-05-06
Hi,
I installed Feisty and Beryl on my ASUS M6R Laptop. Everything works fine with the screen resolution 1024x768.
My only problem is, when I change the screen resolution to 1280x800 (which is the real resolution) problems occur. Graphics and mouse pointer become corrupted but the system does not hang. I think the problem is in buffering. When I move mouse pointer, the icons under the pointer are displayed correctly but the other parts of the screen are dynamically mixed. While rotating the cube the left and right sides of the screen becomes mixed with some parts of the opposite side.

Maybe the problem is in managing and addressing the display memory routines. 

Does anyone know how can I fix it?

---

### Post by ozgurcakmak on 2007-08-20
Problem roots from our beloved X server. Pull up a console and write:
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down until you see:
```
Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
```
this.

Which means, it may be different in your computer though, this monitor`s default depth is 24 bits. So Scroll down until you see Depth 24 mode and change the line to:

```
SubSection "Display"
		Depth		24
		Modes		**"1280x800"** "1024x768" "800x600" "640x480"
	EndSubSection
```
Save and exit and restart x server [Ctrl+alt+backspace]
Voila!

---

