---
title: "Xinerama almost working with fglrx, need advice"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by chaumurky on 2005-07-19
First of all, my xorg.conf:

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	SubSection "extmod"
	    Option "omit xfree86-dga"
	EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Head0"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"UseInternalAGPGART" "no"
	screen 0
EndSection

Section "Device"
	Identifier	"Head1"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
	Option		"UseInternalAGPGART" "no"
	screen 1
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Head0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Head1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	Screen "Screen1" RightOf "Screen0"
	Option		"Xinerama" "on"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Now, when I vnc from work (this is where I was when I was setting it up) I get a 2560x1024 desktop - looks good. I come home to see that both monitors look like clone mode but the mouse can move from one monitor to the other! If I maximize a window to the section I can't see it vanishes (still visible on the taskbar) and on clicking in the top right of the second monitor I can close the window (gone from the taskbar). I hope this decription makes sense. I just need my second monitor to show what I know is there! My xorg log is [downloadable here](http://carters.homeip.net/Xorg.0.log) if it provides any clues. Thanks for your time.

---

