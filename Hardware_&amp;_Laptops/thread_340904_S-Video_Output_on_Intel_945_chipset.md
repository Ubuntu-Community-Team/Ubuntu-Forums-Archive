---
title: "S-Video Output on Intel 945 chipset"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by Valhalla on 2007-01-17
Does anyone know how to enable the s-video output on on Intel 945GM chipset. I've tried using the i855-crt utility and another i810rotate. Both fail to recognize that I have video cards, even though I'm using the i810 driver in xorg. I assume something is wrong, because when I simply plug the s-video card into the jack nothing happens. Doh! ](*,) Anyway, any help would be appreciated. Thanks in advance.

---

### Post by groggyboy on 2007-01-18
S-video on intel chipsets is a known shortcoming, at least on the forums.
I started [this thread]("http://www.ubuntuforums.org/showthread.php?t=141031") almost a year ago.  [This thread]("http://ubuntuforums.org/showthread.php?p=1766202") and [this thread]("http://www.ubuntuforums.org/showthread.php?t=161033") are two others that tried to address intel chips and s-video.  Unfortunately, no one has found a good, working solution (that I'm aware of).

Back in December, motin suggested that someone should start a wiki page for this, with all the half-baked solutions that people had come up with, as an attempt to create a feasible way of getting s-video working.

I gave up a while back, but I think I may try tweaking around with it again.  I haven't tried my laptop's s-video in edgy or feisty, so I don't know if things have changed with the latest drivers.

Sorry for the non-answer, but it's the best I've got.  Maybe someone else will see this thread and help us out...
](*,)

---

### Post by discord on 2007-02-13
its too bad with open source drivers and all you think you would be able to get the svideo working. Espically since the driver supports it. could you email me if you ever get it working. Its hard with video stuff because it seems like we should figure out how to get it working and report bugs but i always seem to get involved in a fruitless effort. I would like to work on some bug team for this issue but I'm not aware of one.

---

### Post by featherking on 2007-02-13
Not sure if anyone cares but i got this working with my i945 chipset (i810 driver) : Svideo(two desktops), Dual Monitors(single desktop), and Dual Monitors(two desktops) i will post my xorg.conf if you would like, i also have a small script to switch between the different configurations. Also, i do use beryl but i had to switch to metacity for all these to work..

---

### Post by brettr on 2007-02-13
Hey, could you go ahead and post that config, i wouldn't mind seeing it.

---

### Post by featherking on 2007-02-14
Okay so prepare for a long post, i guess you could call it a how-to it works for me anyways..

[SIZE="3"]How To: Svideo/Dual Monitor(xinerama)/Dual Monitor(cloned desktop) on i945 (i810) driver[/SIZE]

I have a little script that i use to switch inbetween the different xorgs that i have set up.

[SIZE="2"][COLOR="SandyBrown"]STEP ONE[/COLOR][/SIZE]
run this to create this script:
```
sudo gedit /usr/bin/switchmon
```

then paste the following into the open gedit window:
```
#!/bin/sh
#
#FeatherKing Xorg.conf Rotater Script
#(partially modified from someone else sorry i dont remember who)
#
#
cmd=${0##*/}                              # Command's basename
msg="\n\tUsage: $cmd [1|2|3|4]\n\t\t1 = single monitor\n\t\t2 = S Video\n\t\t3 = Dual Monitor\n\t\t4 = Clone Desktop"

if [ $# -lt 1 ]; then
	echo $msg
	exit 0
fi 
if [ $1 = "3" ]; then
	echo -e "\nChanging to Dual Monitor mode"
	sudo cp /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
	echo
	exit 2
fi
if [ $1 = "4" ]; then
	echo -e "\nChanging to Cloned Desktop mode"
	sudo cp /etc/X11/xorg.conf.clone /etc/X11/xorg.conf
	echo
	exit 2
fi
if [ $1 = "2" ]; then
	echo -e "\nChanging to S-Video mode"
	sudo cp /etc/X11/xorg.conf.svideo /etc/X11/xorg.conf
	echo
	exit 2
elif [ $1 = "1" ]; then
	echo -e "\nChanging to single monitor mode"
	sudo cp /etc/X11/xorg.conf.single /etc/X11/xorg.conf
	echo
	exit 1
else
	echo "Invalid Number" $msg
	exit 0
fi

```

then save and exit. we need to make that file executable so it can do its job:
```
sudo chmod +x /usr/bin/switchmon
```

Now we need to create the different xorg.conf files that we will switch between
[COLOR="Red"]*note*[/COLOR] You will probably have to edit the resolution values in these files to match whatever you are
trying to get, i just use my laptop so im limited to 1280x800 but some people might have bigger monitors or whatever[COLOR="Red"]*/note*[/COLOR]

[SIZE="2"][COLOR="SandyBrown"]STEP TWO[/COLOR][/SIZE]

We will copy the xorg.conf to a different named file so we can switch back to it when not using svideo:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.single
```

Now we create the svideo version of the xorg:
```
sudo gedit /etc/X11/xorg.conf.svideo
```

paste the following into that window:
[COLOR="Red"]*note*[/COLOR] You may want to copy only from the "Section 'Device'" line and below depending on your hardware, if you have a different mouse or something just make a copy of your current xorg.conf and save it as xorg.conf.svideo and then replace from the Device line below in your file with what ive posted here [COLOR="Red"]*/note*[/COLOR]
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO" # "COMPOSITE"
	Option "ConnectedMonitor"	"TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"TV"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		0 "LCD"
	Screen		1 "TV" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```
then save and close the file

Now we create another xorg file for using a cloned desktop (useful for connecting to a projector):
```
sudo gedit /etc/X11/xorg.conf.clone
```

Again, paste the following (and again from the device line and below if you want):
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load    "dbe"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"Intel"
	Driver		"i810"
	Option    "MonitorLayout" "CRT,LFP"
	Option    "Clone" "true"
	Option    "DevicePresence" "true"
	Option		"UseFBDev"		"true"
	BusID		"PCI:0:2:0"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Option 		"AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

```
then save and close the file

Now we create an xorg for using dual monitors as one desktop(using xinerama):
```
sudo gedit /etc/X11/xorg.conf.dual
```

Again, paste the following:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```
save the file and close

[SIZE="2"][COLOR="SandyBrown"]STEP THREE[/COLOR][/SIZE]
Now we should have 4 different xorg.conf files:
xorg.conf.single
xorg.conf.dual
xorg.conf.clone
xorg.conf.svideo

The script we created at the beginning will switch between these, the xorg.conf.single is the file that you were currently using when you started. To switch between them its very simple:
from the terminal run
```
switchmon
```

And it displays the script usage parameters, for example running:
```
switchmon 2
```
will swap out your current xorg.conf with the svideo xorg.conf,

now press Ctrl+Alt+Backspace to reboot X (this will close any open programs beware) and upon reboot you should now be able to plug in your svideo cord (or hookup another monitor, or a project or whatever xorg.conf you wanted to switch to)

[COLOR="Red"]*note*[/COLOR] turn off beryl/compiz before switching between xorg files, i could never get it to work using anything but metacity [COLOR="Red"]*/note*[/COLOR]

[COLOR="Red"]*note2*[/COLOR]Also, sometimes after switching between two many xorg right in a row (i.e. running switchmon 1, then restart x, then switchmon 2, then restart x, then switchmon 4, then restart x, etc) for me sometimes X would just give an error about not being able to start, in these cases i could only get back into X by rebooting, just FYI [COLOR="Red"]*/note2*[/COLOR]

Hopefully this helps someone, im no Xorg expert so i will try to answer any problems that will probably arise but this works for me after many days of hunting obscure settings from the forums.. Please let me know if it works/doesnt and maybe i have a typo somewhere.

Good luck

-The King

---

### Post by discord on 2007-02-17
hey thats great you got it working. Right now I would like to be able to press the keyboard shortcut on my e1505 to switch to my external display. That works at the moment but I can't seem to get it to function at the monitor's resolution 1680x1050.. I have already added the appropriate modes to my video bios via 915resolution but I still cannot just use the external lcd by itself with the key toggle. Can you help me figure it out?

---

### Post by featherking on 2007-02-18
maybe post your xorg.conf from the 'Device' section and down and maybe we can look at it, as i said im no expert but maybe others here will see and help too, but post it and see whats happens

---

### Post by chronniff on 2007-02-19
you are a life saver, this is the only way I have have gotten it to work on my intel 915, thank you so much!!

---

### Post by jaypeasy on 2007-02-19
Thanks! :) 

Works pretty well. Only one issue still bugging me. When I run the dual monitor mode, I can't drag a window all the way onto the second screen. No matter what I do, a strip of the window is stuck on my primary screen. The primary screen is my laptop, running at a widescreen 1280x800 and the external screen runs at a conventional aspect ratio, with res 1024x768.

Any ideas?

---

### Post by featherking on 2007-02-20
I wrote up an actual 'How To' for this and it is posted [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=361124") perhaps it is worded a little better.. Post there if any of you have success/problems with my post

---

### Post by Ferret-Simpson on 2007-08-20
I just have problems with dual head. Will test your scripts, then report back.

---

### Post by wieman01 on 2007-08-21
> **Ferret-Simpson said:**
> I just have problems with dual head. Will test your scripts, then report back.
Not sure what the problem is, but S-Video works out of the box in Feisty. Ubuntu has considerably improved here.

---

### Post by rolibalicas on 2007-11-30
Too bad that improvement isn't carried over in Gutsy... The howto doesn't seem to work in Gutsy. Is there any edit needed for that one? Would surely want to know. Thanks!

---

