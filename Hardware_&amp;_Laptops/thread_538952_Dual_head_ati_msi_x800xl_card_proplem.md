---
title: "Dual head ati msi x800xl card proplem"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by kazakx on 2007-08-30
Hi Guys,

I am struggling with some dual head configurations. I have an msi ati X800XL PCIe card. It has 2 dvi connectors. I get a graphical display on the first monitor but the second one shows nothing.

I get the following error when grep on WW of /var/log/Xorg.0.log:
(WW) RADEON: More than one matching Device section found: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found

While a lspci shows:
01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
01:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary

And my xorg.conf 
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
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary"
	Driver		"ati"
        BusID		"PCI:1:0:1"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"SyncMaster2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen 2"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary"
	Monitor		"SyncMaster2"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier   	"Dual-Head"	
	Screen		"Default Screen"
	Screen		"Default Screen 2" LeftOf "Default Screen"
	Option 		"Xinerama"
	Option 		"Clone" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection



What am i doing wrong? :(

---

### Post by f1r31c3r on 2007-09-04
Interesting i have duplicated this error last week.

can i ask is there a reason why you are usint the driver ATI and not fglrx?


also to sort this problem i know this is confusiong im still trying to figure it out but 2 difrent ways to get your 2 monitors working.

1)

add this to your xorg conf file 

Section "Device"
	Identifier "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
        BusID	    "PCI:1:0:0"
EndSection

Section "Device"
	Identifier "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)1"
	Driver      "fglrx"
        BusID	    "PCI:1:0:0"
        Screen 1
EndSection

OR

2)

Remove the second instance and just have this:

Section "Device"
	Identifier "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
        BusID	    "PCI:1:0:0"
EndSection

the option (Option	    "DesktopSetup" "horizontal") actually tells the bios on the card to initiate 2 screens.

If you dont have the ati-driver i.e. fglrx installed then install it there is howto's everywhere on installing the fglrx driver.

There is the third and most comon install and thats after the driver is installed use the:

aticonfig --initial --input=/etc/X11/xorg.conf

and then

aticonfig --dtop=horizontal --overlay-on=1

or if you prefer the dual head config

 aticonfig --initial=dual-head --screen-layout=above

as to answer the question on the PCI:1:0:1 bus device which is actually a second device it does work but puts the desktop in clone mode so everything that you do on screen one is output to screen 2 exactly makes me wounder if the busid is to do with the tv out or projector.

Im currently trying to get XGL compiz working so this busid stuff is really baffling me cause once you add (Option	    "DesktopSetup" "horizontal") the driver ignores the set instance of busid 1:0:1

i guess you could run fglrx on one and ati driver on the other ill try that and get back to you see what happens.

Option "Xinerama" you need to put it like this

Option "Xinerama" "true"

if you want it cloned then change horizontal above to clone that should get you working.

hope this helps

---

