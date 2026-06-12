---
title: "Two graphic cards two screens"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by christooss on 2005-08-21
I m wondering is it posible to have one agp and one pci graphic card in same computer and than two screens pluged in. 

Will this work in Ubuntu

If yes how can I make it work?

---

### Post by foolsh on 2005-08-21
yes its should be not problem but you will have to edit your /etc/X11/xorg.conf file manually 
this can get tricky for newbies 
i have three video cards one agp and two pci cards
works great!
you will have to use the command # lspci
to see where your cards are asigned
here the "important bits" of my xorg.conf
-----------------------------------------------------
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
Section "Device"
	Identifier	"matrox1"
	Driver		"mga"
	BusID		"PCI:1:0:0"
EndSection
Section "Device"
	Identifier	"matrox2"
	Driver		"mga"
	BusID		"PCI:1:1:0"
EndSection
####################################################################################
Section "Monitor"
	Identifier	"DELL E773s"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection
Section "Monitor"
	Identifier	"mag1"
	#Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-100
EndSection
Section "Monitor"
	Identifier	"mag2"
	#Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-100
EndSection
#####################################################################################
Section "Screen"
	Identifier	"Screen0"
	Device	"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"DELL E773s"
	DefaultDepth	16
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
Section "Screen"
	Identifier	"Screen1"
	Device		"matrox1"
	Monitor		"mag1"
	DefaultDepth	16
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
Section "Screen"
	Identifier	"Screen2"
	Device		"matrox2"
	Monitor		"mag2"
	DefaultDepth	16
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
#############################################################################

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	Screen		"Screen1" LeftOf "Screen0"
	Screen		"Screen2" LeftOf "Screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option "Xinerama" "on"
	Option "Clone" "off"
EndSection

----------------------------------------------------------------
good luck with this :grin: 
 having more than one monitor makes working with any app 100% greater

---

### Post by christooss on 2005-08-21
Thanks I will try this soon. I think it wont be a problem.

---

### Post by christooss on 2005-08-28
Maybe you can help me with this

[http://ubuntuforums.org/showpost.php?p=322179&postcount=8](http://ubuntuforums.org/showpost.php?p=322179&postcount=8)

---

