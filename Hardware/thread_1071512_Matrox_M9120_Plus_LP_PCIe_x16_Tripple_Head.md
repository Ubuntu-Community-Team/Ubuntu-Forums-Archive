---
title: "Matrox M9120 Plus LP PCIe x16 Tripple Head"
date: 2009-02-16
forum: Hardware
---

### Post by IanWood on 2009-02-16
Hi, 

In my work machine I have a Matrox M9120 Plus LP PCIe x16 video card. This has recently been changed from an older Matrox card so that I could have 3 screens. 

With the older Matrox card I was able to run dual head using xinerama. 

Using the beta driver from the Matrox site, released 3 Feb 2009, the best I am able to get is all three screens cloned, I am not able to have them independent. I have followed the readme from Matrox but every time I try to have independent screens X fails to start.

Does anyone know how to configure the xorg.conf to work with 3 screens?

Hope someone can help.

Best regards,

Ian

---

### Post by IanWood on 2009-02-26
UPDATE- 
Since physically ordering the screens correctly I have managed to get the screens working independently showing their own desktops. 

However I am not able to acheive them appearing as one large desktop. 

Whenever I enable Xinerama X doesn't load and a failsafe xorg.conf is put in place. 

Can someone please suggest a way to get the 3 screens to have a single large desktop?

Here is my xorg.conf.

Thanks in advance, 

Ian

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"MonitorLeft"
EndSection

Section "Monitor"
	Identifier	"MonitorMiddle"
EndSection

Section "Monitor"
	Identifier	"MonitorRight"
EndSection

Section "Device"
	Identifier	"VideoCard0"
	Driver		"m9x"
	BusID		"PCI:1:0:0"
	Screen 		0
        Option          "Independent"

EndSection

Section "Device"
	Identifier	"VideoCard1"
	Driver		"m9x"
	BusID		"PCI:1:0:0"
	Screen 		1
        Option          "Independent"
EndSection

Section "Device"
	Identifier	"VideoCard2"
	Driver		"m9x"
	BusID		"PCI:1:0:0"
	Screen 		2
        Option          "Independent"
EndSection

Section "Screen"
	Identifier	"ScreenLeft"
	Device		"VideoCard0"
        Option          "monitor-mon0" "MonitorLeft"
        DefaultDepth 24
EndSection

Section "Screen"
	Identifier	"ScreenMiddle"
	Device		"VideoCard1"
        Option          "monitor-mon1" "MonitorMiddle"
        DefaultDepth 24
EndSection

Section "Screen"
	Identifier	"ScreenRight"
	Device		"VideoCard2"
        Option          "monitor-mon2" "MonitorRight"
        DefaultDepth 24
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
	Screen		"ScreenLeft"
	Screen		"ScreenMiddle" RightOf "ScreenLeft"
	Screen		"ScreenRight"  RightOf "ScreenMiddle"
      #  Option	        "Xinerama"	"true"
EndSection

---

### Post by IanWood on 2009-09-15
I used randr in the end, with the virtual clause

[https://wiki.ubuntu.com/X/Config/Multihead](https://wiki.ubuntu.com/X/Config/Multihead)

---

