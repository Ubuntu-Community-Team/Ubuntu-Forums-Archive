---
title: "how to get intel graphics card working?"
date: 2008-09-10
forum: Hardware
---

### Post by Slenkar on 2008-09-10
Hi

I have tried to turn direct rendering on to no avail.
I am using an intel graphics card
I added some lines to my xorg.conf file but it doesnt work

here is the whole file:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"i810"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "GLcore"
	Load  "freetype"
EndSection

Section "DRI" 
Mode 0666 
EndSection

---

### Post by Slenkar on 2008-09-10
anyone?

---

### Post by phidia on 2008-09-10
The Ubuntu video [wiki]("https://help.ubuntu.com/community/Video") is your best source for setting your card up. You will need to identify which card you have.
> lspci | grep VGA
If you have problems with the guide please post any error messages and/or what exactly you observe.

---

### Post by Slenkar on 2008-09-11
I followed the guide for Ubuntu 8.04 - (the one that I have)

I changed my xorg file as it said 
and it works now
(although, it still says direct rendering is disabled in glxinfo!)

THANKS

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "GLcore"
	Load  "freetype"
EndSection

Section "DRI" 
Mode 0666 
EndSection

Section "Device"
  Identifier  "Configured Video Device"
  Driver      "Intel"
  Option      "NoAccell"      "0"
  Option      "DCC"           "1"
  Option      "DRI"           "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

