---
title: "Low resolution with nvidia-glx"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by dmix on 2007-07-08
I just set up my nForce 405 (Geforce 6100 on-board) w/ the restricted drivers manager

The screen resolution caps at 1024x768 but the card can handle 1280

Is there a way to get to 1280 with nvidia-glx?

---

### Post by pedrogl on 2007-07-08
Hi, look into your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
Search for the entry:
```
Section "ServerLayout"
...
  screen "Name of screen section"
...
EndSection
```
and then edit the screen section named "Name of screen section" or whatever name it has:
```
Section "Screen"
	Identifier	"Name of screen section"
...
	Defaultdepth	24
...
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
...
EndSection
```
Add your desired resolution as above, or simply delete/comment subsection Display and let the xserver choose the appropriate one for your hardware.

---

