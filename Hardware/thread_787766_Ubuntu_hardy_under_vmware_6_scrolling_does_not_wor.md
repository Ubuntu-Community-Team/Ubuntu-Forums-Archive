---
title: "Ubuntu hardy under vmware 6 scrolling does not work"
date: 2008-05-09
forum: Hardware
---

### Post by Encore1974 on 2008-05-09
Hello, 

I installed a fresh copy of ubuntu 8 hardy under vmware workstation 6 in windows vista but mouse scrolling didn't work. 

In my old copy of ubuntu 7, scrolling was fine so i just added the missing part in /etc/X11/xorg.conf

this is the old and new xorg.conf related to the mouse. 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
EndSection



Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option          "Protocol"      "imps/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Hope this helps. 

Encore

---

