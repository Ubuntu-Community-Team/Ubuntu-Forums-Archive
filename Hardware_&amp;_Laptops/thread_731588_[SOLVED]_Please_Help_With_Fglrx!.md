---
title: "[SOLVED] Please Help With Fglrx!"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by harshil102 on 2008-03-22
i really need help with my computer and fglrx.

my problem is pretty much that with the new fglrx 8.3, at boot after the ubuntu boot thing i just get a black screen (after some flickers). I have installed with Envy, with the Ati installer and manually, but all have given the same unfortunate result. I even tried a reinstall of ubuntu but it didnt help either. I then started using the driver from the restriceted driver manager for a temporary solution, but because of their performance, i really couldent use them so i tried fglrx 8.2 then 7.12 then 7.11. Only 7.11 worked all the other versions did the same thing (black screen)! I never upgraded beyond the 7.11 driver before (because my hard drive deid around the time of release of the 7.12 drivers and i didnt get another drive untill about 2 weeks ago) so i dont know if this problem has come up with my current installations or if the same thing would have happened before the hard drive died.

My Specs:
OS:Gutsy Gibbon & XP Pro
Abit VI7 Mobo
P4 2.4Ghz @ 2.93Ghz CPU
X1600PRO AGP Graphics Card
Western Digital 160GB SATA Drive
Maxtor 120GB IDE Drive

My xorg.conf (used same for all drivers):
```
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"	"1440x900"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```


Please please please if you can help please do so, i really want to use the new drivers as people are getting really good results with them compared to the older drivers.

---

### Post by Distro Jockey on 2008-03-22
You could try adding the following section to your xorg.conf
```
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by harshil102 on 2008-03-22
uh yea i will try that tomorrow DJ because it is pretty late and i am tired right now

thanks for the help!!!

---

### Post by harshil102 on 2008-03-22
I tried adding the "glx" module to xorg, but it unfortuenetly didn't help. I also tried removing the overlay options in the "Device" section (just to try it out), but it did nothing.

Thanks anyway

---

### Post by harshil102 on 2008-03-22
I SOLVED IT!!!!!!

I AM SO HAPPY TO FINALLY BE ABLE TO USE THIS DRIVER!!!

for anyone else having this problem, i fixed it by setting my AGP Aperture Size to 256MB in the BIOS. My cad has 512MB of on board RAM so i am guessing that you have to set it to 1/2 the size of the RAM on the graphics card its self.

---

