---
title: "Sapphire Radeon 9600XT (ATi chipset) Dual-Head Almost done!"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by wr3ck on 2007-05-21
Hi there! The newbie here got his screens to both work together! But it haven't been easy, cause I don't have much experience in Linux, and less with Ubuntu and Gnome (I used to be on OpenSuSE 10.2 with KDE)
Here's my computer:
ASRock k7S41GX 1.0
AMD Athlon 2000+ XP
512mo Ram @ 333mhz (Kingston)
Sapphire Radeon 9600XT (Ati chipset) 256mo AGP 8X
Viewsonic G-773 + Sony Trinitron Multiscan 200sx (I hate this one)
LG DVD Writer
IBM Deskstar (ide) 20G (For root system) @ 7200rpm
Seagate (ide) 160G (For windows and data storage) @ 7200rpm
Logitech Cordless USB desktop
PCI Usb hub (Because onboard USB doesn't work anymore)

Well enough talk, I'm here to post my (almost) successful xorg.conf and to ask you guys some questions about it:
```
Section "Files"
#	FontPath	"/usr/share/fonts/X11/misc"
#	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbVariant"	"multi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option  	"XAANoOffscreenPixmaps" "true"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600] Secondary"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option  	"XAANoOffscreenPixmaps" "true"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Viewsonic"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Sony"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"Viewsonic"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600] Secondary"
	Monitor		"Sony"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Multihead"
	Screen		"Screen0"
	Screen		"Screen1" rightof "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama"        "on"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```
Okay now, questions part:

Question #1
It works, but I had to manually switch my two screen plugs behind the comp. because screen #1 was on my right, and I use that monitor only for watching videos while I work because it's very blurred (like an old tv set). Isn't there a way to get a "screens switch" without unplugging them? because when I'll get back to Windows, I will have the same problem (main screen on the sh*tty monitor).

Question #2
I can see a line shadow slowly going up in my first screen, and another one going down on my second. Is there a way to make them disappear ?

Question #3
How can I get two separate desktops showing the same wallpaper? without editing every wallpaper that I have. I did edit my favorite one in Gimp (made a larger image and pasted the same image beside) But it's quite annoying to do. As you can see above, I did put Xinerama on (while I tought it could resolve the problem) but of course, it didn't.

Question #4
My mouse pointer on my second screen doesnt appear. It's a big transparent green square instead. Why?

Well thanks for your helpful forum (which helped me alot in getting into this first step) and i will wait for your answers.

---

