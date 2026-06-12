---
title: "driver radeon 9250 ubuntu 7.10"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by mauror58 on 2007-12-08
hello,I'm a new ubuntu 7.10 user,I wuold like to install a driver for my radeon 9250 video card because I can't reduce my video resolution on 1024x768,everytime I try to lower it from1280x1024 to 1024x768, the screen looses it's horizontal sync.I think It's because of the vesa driver.Here's my xorg.conf thanks in advance
mauro 

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL E196FP"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"DELL E196FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by rmemm on 2007-12-08
I would be suprised if it was a vesa problem.  That driver should work with almost anything -- but maybe.  If you need to tweak the sync settings there are tools to do that but I've never done it.

For the ATI cards -- you have the following driver choices -- "ati" which is open source, and "fglrx" which is the binary driver and has wider range of hardware support.  

I have an X1600 card and vesa worked find.  For me I found "ati" did not support my card but it might support the 9x series.  I've recenlty configured the "fglrx" driver and it also works for me -- only advantage -- I can now run 3D games with acceleration.

To setup fglrx I used the howto:  [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I use dapper actually -- but I think there are other howtos on the same site as well.

One thing to note -- backup the xorg.conf first -- the fglrx installer tends to modify it and it's good to have something to go back to.

Rob

---

### Post by rmemm on 2007-12-08
One thing I forgot to mention -- "ati" is in the standard repositories, but "fglrx" is in the restricted set so you need those enabled in synaptic for fglrx.

Rob

---

### Post by mauror58 on 2007-12-08
thank you rob I'll try what you suggested me and let you know
mauro

---

### Post by mauror58 on 2007-12-18
well I found out that my motherbord doesn't support 4x agp so I lowered it to 1x on bios and finally could reduce resolution
thanks the same rob

---

