---
title: "No &quot;Input Devices&quot; section in xorg"
date: 2009-01-07
forum: Hardware
---

### Post by raj9786 on 2009-01-07
Hi I was trying to follow the directions posted on this thread [http://ubuntuforums.org/showthread.php?t=271052](http://ubuntuforums.org/showthread.php?t=271052) about disabling the touchpad while typing. But upon opening up the xorg.conf, I find that there is no "Input Devices" section in it. I am running a Dell Inspiron 1520 with 8.10 ibex. My xorg looks like this:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

That is the entire thing (minus the comments at the top). touchpad is working fine. Why is the reason for this? I would really like to disable the touchpad while typing since it is very sensitive so even if I brush with while typing, the cursor moves away and clicks on something else. Its rather annoying. Any help is appreciated.

---

### Post by raj9786 on 2009-01-09
bump

---

### Post by Ahadiel on 2009-01-09
This should work on Ubuntu aswell. [http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Stopping_the_mouse_from_clicking_while_typing](http://wiki.archlinux.org/index.php/Touchpad_Synaptics#Stopping_the_mouse_from_clicking_while_typing)

---

### Post by raj9786 on 2009-01-11
What is a .xinitrc file and how do I edit it? I did a search on the forums but I couldnt find what I was looking for. Thanks.

---

