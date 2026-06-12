---
title: "how to set resolution to 1024*768? (s3 prosavage)"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by mistamcgoo on 2006-08-24
when i installed kubuntu dapper on my acer aspire 1300, i
had to use the safe graphics mode to boot the live cd properly.
So my video driver was set to vesa, now i searched around a bit
and i changed the driver to savage. after rebooting, everything seems to work, but the resolution is stuck to 640*480(just the center of the screen being used with a big black border around it), while with the vesa driver i get 1024*768, which it is supposed to be. 
i tried to change the resolution in system settings->display, but
there's only 640*480 as a choice, i can't move the slider to the right.
Is it possible that the monitor setting is involved in this? 
it's set to default plug and play monitor, while this is actually a laptopscreen, to what should i change this?  

can anyone help me set the correct resolution with the savage driver/monitor? all help would be very greatly appreciated:), ive been messing on this for a while

this is from my xorg.conf

Section "Device"
	Identifier	"S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

### Post by daller on 2006-08-25
Have you tried using dpkg-reconfigure xserver-xorg?

Run:

sudo dpkg-reconfigure xserver-xorg

...just follow ALL the steps, and ask questions, if you are i any kind of doubt!

DPKG-RECONFIGURE should help you setup everything properly... (Including detecting gfx and monitor!)

---

### Post by GreyMane on 2006-08-25
Try to find the horizontal and vertical refreshrates for your monitor. They should be found in your technical desc. for the monitor.
In your xorg.conf add (after taking a backup copy) and after "DefaultDepth 24"

Monitor "Generic Monitor"
DefaultDepth 24
HorizSync minsync-in-manual - max-sync-in-manual
VretRefresh minrefresrateinmanual - maxrefresrateinmanual

Restart the X-server w. ctrl+alt+backspace
Editing a configuration file w. a text editor is not particulary userfriendly but should do the trick.

The interface is the application
/GM

---

### Post by mistamcgoo on 2006-08-25
Thank you for the information, it seems to have solved my problem :)

i have 1024x768 now, and according to xorg.conf and system settings in kde, 
my card is recognized correctly. kde and the apps work a lotfaster than with the vesa driver too. 

during the process it asked me how much ram i wanted to give to the card, i selected 64 mb, is that ok? This laptop had only 265 mb ram when i got it 
but i added 512 mb (144 pins pc133 ram)So it should have plenty to spare.

edit : it works even better than i expected :), i just installed and ran the 3ddesk and xdesktopwaves apps and they run smooth :)

---

