---
title: "Nvidia-glx update and aftermath...Toshiba M35-S359"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by kumpooterjooser on 2005-05-30
Before the nvidia-glx update...
1. some movies in fullscreen mode are shaky/fuzzy
2. Cross Office and its installed applications work fine.
3. Terminal access by Ctrl-Alt-F1 --> F6 works fine.

After performing the following steps 

1. sudo apt-get install nvidia-glx
2. sudo nvidia-glx-config enable

and changing drivers in xorg.conf from 'nv' to ''nvidia' ...

Results...
1. Display is more crisp/contrasted. Looks good
2. Movies in fullscreen arent shaky anymore.
3. Cross Office does not install any more applications. Wont give 
any error either.
4. Terminal access through Ctrl-Alt-F1 -->F6 isnt possible anymore. All I get is 
a blank screen filled with random green squares/rectangles.
5. On machine shutdown I dont get the messages like 'Sending TERM signal'...all 
I see is the same green/black screen and the laptop powers down.
6. The same green/black screen is seen with X restart (Ctrl-Alt-Backspace). X 
restarts fine but for sometime the screen is black/green.

If I roll back the nvidia-glx update Cross Office and all other things are back 
to working state.

Here is my machine configuration.
Graphic card: nvidia GeForce FX Go5200...
Screen resolution: 1280*800@60
Laptop: Toshiba M35-S359

Has anyone else seen this issue or am I missing some setting ?

Thanks

---

### Post by ::DoGG:: on 2005-05-30
About those black screens when dropping to shell - for me it looks like you video card is sending then output to another device (if you have laptop probably to monitor or to lcd) What is your default display in xorg.conf, are you able to switch the video output through some specia key combination ( like fn+F4 on my presario)??

---

### Post by kumpooterjooser on 2005-05-31
[QUOTE=::DoGG::]About those black screens when dropping to shell - for me it looks like you video card is sending then output to another device (if you have laptop probably to monitor or to lcd) What is your default display in xorg.conf, are you able to switch the video output through some specia key combination ( like fn+F4 on my presario)??[/QUOTE]


Special key combination doesnt work. Of the 12 function keys, only 3 work. Screen 
brightness up/down and hibernation.

Thanks


here is the xorg.conf code.
```
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	30-60
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go 5200]"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by moment on 2005-06-03
I have a M35-S359 as well and I don't have these problems you mentioned. I sugest you reinstall the nvidia drivers.

---

### Post by moment on 2005-06-21
This is a small HOWTO install ubuntu on a Toshiba M35-S359 that I have recently made. I hope it helps you.

[http://qols.ph.ic.ac.uk/~ho1/toshiba-M35.html](http://qols.ph.ic.ac.uk/~ho1/toshiba-M35.html)

---

