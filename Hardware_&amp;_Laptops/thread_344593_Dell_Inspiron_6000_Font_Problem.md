---
title: "Dell Inspiron 6000 Font Problem"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by LeoF on 2007-01-23
Dear all;

I'm running XUbuntu on a Dell Insprion 6000 laptop computer. I love Ubuntu, but I'm having a horrible time with the fonts. I have tried to do stuff I've found on the web, but it looks like every time I do something, it ends up worse, the fonts are really fuzzy.

Would anyone in the community be able to help with this matter?

Thanks and best regards,

LeoF

Here are some relevant parts of my xorg.conf file:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by mikewhatever on 2007-01-23
Try providing more info. Are the fonts fuzzy in every application? What have you tried or found on the web?

---

### Post by LeoF on 2007-01-23
Hello, Mike;

Yes, fonts are generally fuzzy. Including menus, etc. I'm now using DejaVu Sans Condensed, at 8 points with anti-aliasing, hinting and subpixel hinting from the "User Iterface Settings".  In bash, I'm using monospace 8 without anti-aliasing.

Whatever I did from the web, I undid already, so we're at step 0.

Please let me know if you need more info.

Best,

Leo

---

### Post by asbesto on 2007-05-12
Same problem: after installing some x11 fonts, my Monospace 8 become  
unreadable like here:

[IMG]http://spatof.org/asbesto/fontporcodio.jpg[/IMG]

playing with anti aliasing and font rendering setting doesn't help.

It seem something strange was installed !!!

:confused: :confused: :confused: :confused: 

Can anyone help ?

---

