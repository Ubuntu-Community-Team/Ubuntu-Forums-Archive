---
title: "Screen resolution problems, please help"
date: 2008-06-26
forum: Hardware
---

### Post by selador88 on 2008-06-26
I've been having trouble with my screen resolution. When I have a fresh install, the screen is detected fine and I get the correct resolution. However, if I do anything at all that changes the xorg configuration settings, the screen resolution goes back down to 800x600. I've been backing up the xorg.conf file before I change anything, but the screen resolution remains low even after I revert to the backup. Also, a new file is created, xorg.conf.failsafe, and that appears to be what my laptop is using instead of the xorg.conf file. 

I have a Dell Inspiron 5150 laptop, and the graphics card is an Nvidia GeForce FX Go5200. I just upgraded to 8.04, and I've never had a problem with the screen resolution before.

This is my orginal xorg.conf file:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection


The only thing I added to it was the line Option “RenderAccel” “true” under the Screen section.

Any help would be appreciated, as the only way I've been able to fix this is to do a clean install.

---

### Post by niyonk on 2008-06-26
Hi have you tried system -> administration -> hardware drivers? :)
Then enabling the video card from there.

---

### Post by peakshysteria on 2008-06-26
> **niyonk said:**
> Hi have you tried system -> administration -> hardware drivers? :)
Then enabling the video card from there.

I agree. If you haven't enabled the driver try to do so.

In terminal:
```
sudo displayconfig-gtk
```
And adjust the resolution.
(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others):)

---

### Post by selador88 on 2008-06-26
I was able to get the screen resolution back to 1024x768, but then it completely re-writes the xorg.conf file so that the changes I was trying to make are erased anyway. All I really want to be able to do is hook my laptop up to a projector so that I can watch movies...any ideas?

---

### Post by peakshysteria on 2008-06-26
Have you installed the graphics card driver? If so, how did you install it and are you sure it's running properly?

---

