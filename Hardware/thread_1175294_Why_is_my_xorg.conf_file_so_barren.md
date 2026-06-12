---
title: "Why is my xorg.conf file so barren?"
date: 2009-06-01
forum: Hardware
---

### Post by keh7d on 2009-06-01
Hi I just installed the latest version of Kubuntu on a Dell XPS M1330. I am having problems with my touchpad (it wont let me disable tap-click) and my media buttons (they dont work). I've read I should install gsynaptics (did it) or just edit my xorg.conf file. Problem is, I dont have anything regarding my touchpad in which to edit. Shouldn't my xorg.conf file have more in it? It is as follows:

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


Thanks for any advice.

---

### Post by SunnyRabbiera on 2009-06-01
More modern versions of xorg need less information, as its supposed to be more efficient then having lots of entries.
Me I never liked touchpads so I cannot help you much, I always use a mouse with my laptop.

---

### Post by Yellow Pasque on 2009-06-01
X.org uses HAL/evdev for input device detection: [http://wiki.archlinux.org/index.php/Xorg_input_hotplugging](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging)

---

