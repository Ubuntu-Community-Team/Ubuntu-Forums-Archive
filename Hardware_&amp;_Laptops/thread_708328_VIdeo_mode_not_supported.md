---
title: "VIdeo mode not supported"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by archeryguru2000 on 2008-02-26
I'm having some... issues with my Gutsy installation.  I have recently upgraded from Dapper (of which, I had zero problems, just decided to keep up with technology) to Gutsy.  I have an Acer Aspire 3003LCi laptop with a broken monitor (don't ask, long story).  Needless to say, I am running with an external monitor.  When I first installed Gutsy I was using an older monitor.  But now I am trying to run on a newer model (another Acer monitor) and I keep getting a message of "Video mode not supported".  That's it, no login menu, no fuzzy screen, nothing!  I am currently using the Gutsy live CD in "Safe Graphics Mode" to write this message.  Any suggestions would be greatly appreciated!

Also noticed that everybody else posts their xorg.conf file... so here's mine.

----------------------------------------------------------------------
Section "Files"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
	InputDevice	"Synaptics Touchpad"
EndSection
----------------------------------------------------------------------------------

~~archery~~

---

### Post by archeryguru2000 on 2008-02-26
bump

---

### Post by archeryguru2000 on 2008-02-26
bump

---

### Post by archeryguru2000 on 2008-02-26
will nobody help!

---

### Post by archeryguru2000 on 2008-02-29
[SIZE="3"]OK, I decided to ditch the current install and try to re-install Gutsy.  However during the installation procedure I noticed that there was this error message popping up every now and then (during the boot-up scroll messages) that stated something of the following:
[FONT="Fixedsys"][SIZE="4"]
bcm43xx: Error: Microcode "bcm4xx_microcode5.fw" not available or load failed
[/SIZE][/FONT]
Confused as to what that meant, I decided to abandon Gutsy altogether and resort back to Dapper (which worked fine).  HOWEVER during the Dapper installation... that same error message appeared!  Now I'm beginning to wonder if I have something internally wrong with my laptop.

Does anybody have any suggestions?  I'm open to trying (almost) anything to get this to work!

Sincerely,
~~archery~~[/SIZE]

---

