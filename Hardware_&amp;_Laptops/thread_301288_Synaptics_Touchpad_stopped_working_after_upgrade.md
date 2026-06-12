---
title: "Synaptics Touchpad stopped working after upgrade"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by Migalicious on 2006-11-16
Hi, I have a Dell Inspiron 6000 and the other day my touchpad was working fine, but after I enabled to 3v1n0 repository it upgraded xserver-xorg-input-synaptics and when I rebooted my tap doesn't work, the scroll bars don't work and using the mouse via the touchpad causes it to scroll so slow it's barely usable

My whole xorg.conf
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"on"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
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
	InputDevice	"Synaptics Touchpad" "AlwaysCore"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Is there anyway I can downgrade to the ubunutu repository one or get my mouse working again?

---

### Post by K.Mandla on 2006-11-17
I don't know that this will work, because I only did it once a long time ago, but I think this was it. If you find the synaptic driver package you want, you might be able to downgrade with something like this ...

```
sudo apt-get install xserver-xorg-input-synaptics=1:0.14.6-0ubuntu3
```
That's the 0.14.6 from Edgy. Dapper's is kind of amusing. 

```
sudo apt-get install xserver-xorg-input-synaptics=1:0.14.3+seriouslythistime-0ubuntu3
```
Alternatively, you might try downloading that package from the packages.ubuntu.com site ...

[http://packages.ubuntu.com/edgy/x11/xserver-xorg-input-synaptics](http://packages.ubuntu.com/edgy/x11/xserver-xorg-input-synaptics)

And installing with 

```
sudo dpkg -i xserver-xorg-input-synaptics*.deb
```
or double-clicking on the package. Oh wait, your mouse is ... :roll:

---

### Post by Migalicious on 2006-11-17
Thank you so much, it worked.  Is there any way I can blacklist that version of that package from that repo?

---

### Post by K.Mandla on 2006-11-17
Glad I could help. :)

I believe there's a *preferences* file inside */etc/apt/*, but I've never tampered with it, so you'll have to do a little research on that one. Try the [man pages for apt-get]("http://www.die.net/doc/linux/man/man8/apt-get.8.html"), or poke around in that file to see if it makes sense. Good luck!

---

### Post by Allysan on 2007-04-29
Silly newb question here, but then I did just install Feisty last night.

I would really like to try installing this package, but after downloading the extractable files and extracting them, I have absolutely no idea where to put them such that they can actually be installed.  I'm ripping my hair out here, as the only reason I need this is to disable my Trackpoint... the thing has gotten to the point where it sticks my cursor in one corner or another and it is literally painful to get it out... you have to hold it in one spot, and that doesn't always work.  I have no command-line fears, so doing this via Terminal is fine.  Please help!

---

