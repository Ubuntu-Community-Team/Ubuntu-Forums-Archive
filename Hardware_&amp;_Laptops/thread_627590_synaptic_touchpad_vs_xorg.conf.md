---
title: "synaptic touchpad vs xorg.conf"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by tzg6sa on 2007-11-30
Hi!

I am a really new linux user. I have problems with my touchpad too (I want to disable the clicking by tapping). 
BUT in my xorg.conf there are nowhere the string "synaptics" (the xorg.conf-s in every topic has this string). Altough my "device manager" (sorry I use a not english version) says that I have a synaptics touchpad.
All I have as InputDevice: Generic Keyboard, Configured Mouse, stylus, eraser and cursor.
So - I dont have my touchpad there
     - there are many strange names. (stylus for example)

I have installed qsynaptics. It says that I need to install the synaptics driver and I have to enable X shared memory config in XF86Config. (btw I don't find any file called XF86Config :( )

Is it installed? Should I install it? How could I disable it?

Thanks!
Zoli

---

### Post by tinycamp on 2007-11-30
could you post the contents of /etc/X11/xorg.conf ?

---

### Post by tzg6sa on 2007-11-30
Of course!

I hope it helps you to find the solution! :)

[FONT="Microsoft Sans Serif"][FONT="Lucida Console"]Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hu"
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
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
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
	Option		"Composite"	"0"
EndSection

Section "Module"
	Load		"glx"
EndSection[/FONT][/FONT]

---

### Post by tinycamp on 2007-11-30
xorg must be detecting the touchpad with the "configured mouse" section, try adding one of this inside the section:

for disabling tapping and scrolling:

```
TouchPadOff 2

```

for disabling one, two and three finger tapping:

```
TapButton1 0
TapButton2 0
TapButton3 0
```

---

### Post by tzg6sa on 2007-11-30
It was funny! :)
I did it, and after that I have got some error messages:

[FONT="Microsoft Sans Serif"]FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071130195409
FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device
[/FONT]
After that I checked the xorg.conf. And What a wonder! I have soon a "Synaptics Touchpad" device!

What is not funny: I can not update it with "sudo dpkg-reconfigure -phigh xserver-xorg" :( I always become the messages above.
Maybe a reason: I have to boot my linux on my notebook with the switch "acpi=off". (I donno why, I just noticed it.)

How could I update xorg.conf?

Thanks!
Zoli

---

### Post by nick_h on 2007-11-30
Edit it using:
```
gksudo gedit /etc/X11/xorg.conf
```

For qsynaptics you need to add the line:
```
Option    "SHMConfig"    "True"
```

---

### Post by tzg6sa on 2007-11-30
Hi!

The solution was that I had to reboot my computer.
Now with qsynaptics my touchpad works fine. 

Problem is solved! Thanks!
Zoli

---

### Post by tinycamp on 2007-11-30
youre welcome!

---

