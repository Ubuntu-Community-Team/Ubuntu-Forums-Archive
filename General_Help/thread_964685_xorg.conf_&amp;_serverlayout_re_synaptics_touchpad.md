---
title: "xorg.conf &amp; serverlayout re: synaptics touchpad"
date: 2008-10-31
forum: General Help
---

### Post by johanhartman on 2008-10-31
I've recently been trying to configure the synaptics touchpad on my laptop as described in this [post]("http://ubuntuforums.org/showthread.php?t=960251"). For this purpose I have been scrutinising my xorg.conf file and I have found that while the InputDevice section for the touchpad is correct, it is linked in a different ServerLayout section as all the other input devices. I don't think there is anything wrong with that but, quoting the [man pages for xorg.conf]("http://www.linuxmanpages.com/man5/xorg.conf.5x.php");
> A ServerLayout section is considered "active" if it is referenced by the -layout command line option or by an Option "DefaultServerLayout" entry in the ServerFlags section (the former takes precedence over the latter). If those options are not used, the first ServerLayout section found in the config file is considered the active one.
...looking at my xorg.conf file (relevant bits are bold and italic);
```
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

[I][B]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"on"
EndSection[/B][/I]

Section "InputDevice"
         Identifier "aiptek"
         Driver "wacom"
         Option "Device" "/dev/input/aiptek"
         Option "Type"   "stylus"
         Option "USB"    "on"
         Option  "TopX"          "0"
         Option  "TopY"          "0"
         Option  "BottomX"       "10000"
         Option  "BottomY"       "6250"
         Option  "MaxX"          "10000"
         Option  "MaxY"          "6250"
EndSection
[I][B]
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"aiptek"	"SendCoreEvents"
#	Inputdevice	"stylus"	"SendCoreEvents"
#	Inputdevice	"cursor"	"SendCoreEvents"
#	Inputdevice	"eraser"	"SendCoreEvents"
EndSection[/B][/I]

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

[I][B]Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection[/B][/I]
```

Please correct me if I'm wrong but it seems that the ServerLayout section at the bottom would be inactive, going by the man pages anyway.

If this is the case then my problem could probably be solved by simply linking the InputDevise section for the synaptics touchpad to the bigger ServerLayout Section...

Comments please, I am not sure if I understand this topic completely.:confused:

---

