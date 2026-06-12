---
title: "Toshiba Laptop with I915GM onboard  video"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by Mikecore on 2006-04-08
Ok Im running Breezy Bager with Gnome and I have a I915GM video card everything
installed fine and I have 3d accleration. But I only get 2 screen resolutions.

1280x768 and 1024x768

I tried adding 800x600 to my xorg.conf. but I will not change screen res to that.

the laptops native screen res is 1280x768 but for gaming I would like to use 800x600
I have been looking into this online and I see there is a 915 res fix for higher res's but will this work for lower res's instead of higher ones

and why didn't the setup enable lower screen resolutions?

---

### Post by taurus on 2006-04-08
How did you add "800x600" to your /etc/X11/xorg.conf?  You can post your /etc/X11/xorg.conf here if you want.

---

### Post by Mikecore on 2006-04-08
here you go

```


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768" "800x600" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by taurus on 2006-04-08
Maybe this is a dumb question but did you restart X or even restart your system after the change?

---

### Post by Mikecore on 2006-04-08
no question is dumb and yes I did restart X

---

### Post by ZoZo on 2006-04-19
Try 915resolution: apt-get install 915resolution, and edit /etc/default/915resolution to get the resolutions you want.

---

### Post by Tom Tiger on 2006-04-20
Just to satisfy my own curiosity what Toshiba laptop are you using?  Toshiba uses different displays in their laptops.... UXga ect... my 15" toshiba goes no higher than 1024x768 while an uxga gets 1600x1200 on a 15"....  awfully small though..... but what a screen :-)

---

