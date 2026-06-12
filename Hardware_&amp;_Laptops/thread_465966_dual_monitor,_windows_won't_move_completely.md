---
title: "dual monitor, windows won't move completely"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by cursief on 2007-06-06
hi,

i managed to get dual monitor sort of working on my system at work. The problem however is that when I try moving windows to my second monitor, the windows won't move completely onto the second monitor. It's like there is some "hidden  toolbar" (which isnt) on the right keeping it from moving. 

Strange thing is that my mouse pointer can get anywhere on the monitor and even windows xp under vmware can use the screen to it's fullest. I've never seen anything like it. Also I can not place icons or move files over to the second screen. Anyone has any idea?

here is the xorg.conf:

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"us"
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


# intel graphics card

Section "Device"
	Identifier	"Intel Graphics"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"LG1"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Right Screen"
	Device		"Intel Graphics"
	Monitor		"LG1"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0	
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


# ATI graphics card

Section "Device"
	Identifier	"ATI Radeon"
	Driver		"ati"
	BusID		"PCI:3:2:0"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"LG2"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Left Screen"
	Device		"ATI Radeon"
	Monitor		"LG2"
	DefaultDepth	24
	
	SubSection "Display"
		Viewport	0 0
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
		Viewport	0 0
	EndSubSection
EndSection



Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0		"Right Screen" 0 0
	Screen		1		"Left Screen" RightOf "Right Screen"
#	Screen 	1	"screen1" RightOf "screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
	Option "Clone" "off"
EndSection

---

### Post by qwerkus on 2007-06-06
May sound stupid, but it worked for me: have to tried pushing the "auto config" button at your monitor AFTER everything (desktop) loaded ?

---

### Post by cursief on 2007-06-06
Hi, i did do autoset on the monitor (i did however tried it again just to make sure haha). 

It's not that the monitor only shows part of the screen (my mouse (pointer) is quite happy with the amount of space and can crawl into any corner), it's that the windows just aren't able to move completely (in this case) to the right and moving an icon onto it snaps those back to the first screen.

---

### Post by cursief on 2007-06-08
does anybody have any idea? It's nice that the two screens work but it's really useless at the moment

---

### Post by crocowhile on 2007-10-10
I am having exactly the same problem with ubuntu 7.10
I also have an Intel graphic card and an old ATI, as in your configuration.
Possibly something wrong with the combination of those two.

---

### Post by cursief on 2007-10-10
> I am having exactly the same problem with ubuntu 7.10
I also have an Intel graphic card and an old ATI, as in your configuration.
Possibly something wrong with the combination of those two.

I've switched to KDE (kubuntu) which does not have this problem. So my guess it's GNOME doing something wrong with this setup! So for me the only way to fix it was to switch to Kubuntu, i've found out that it is not a bad switch in any case :) but that is a personal choice. :lolflag:

I still hope someone can find out what it is, cause it is frustrating.

---

