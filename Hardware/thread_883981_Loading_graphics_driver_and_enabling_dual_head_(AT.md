---
title: "Loading graphics driver and enabling dual head (ATi 7500)"
date: 2008-08-08
forum: Hardware
---

### Post by henbjo on 2008-08-08
Hello.

I've been searching around for some time now for solutions on how to enabling some sort of dual head head mode for utilizing my current dual screen setup, or even my living room HDTV as an external monitor, but I have some initial problems with my gfx card not being recognized.

I have this old [_[COLOR="Blue"]Compaq Evo N800v[/COLOR]_](http://h18000.www1.hp.com/products/quickspecs/11077_na/11077_na.html) with an 1.8 GHz Intel P4 CPU, 256 megs of RAM and an ATi Mobility Radeon 7500 gfx card, and it's running Xubuntu (Hardy) pretty flawlessly.

My problem is that when I open my **xorg.conf** file, and am about to edit it, it's only configured with what seems to me to be generic values for everything, and when i run the **dpkg reconfigure xserver-xorg** it only asks me to define values regarding the keyboard input device.

I guess the problem is that my gfx card isn't being recognized, and I will have to persuade X oh so gently to do that and load the radeon driver for it, before I can even start thinking about the dual head problem. Unfortunately I'm pretty new to xubuntu and Linux, so I don't really know where or how to do this. I have been using Mac OS X for a long time though, so I'm pretty familiar and comfortable with using the terminal, and I'm guessing I have to inject my card and vendor ID-s somewhere.

Here's how the **xorg.conf** looks like:
```

# xorg.conf (X.Org X Window System server configuration file)
#
[.......]

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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

Anyone care to point the n00b in the right direction? :confused: O:)

Thanks in advance for any help! :)

---

### Post by Waaib123 on 2008-08-24
I have the same issue. Anyone out there able to help please do.

---

