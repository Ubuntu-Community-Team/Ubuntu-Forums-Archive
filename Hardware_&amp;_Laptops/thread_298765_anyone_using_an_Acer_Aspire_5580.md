---
title: "anyone using an Acer Aspire 5580?"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by mert on 2006-11-13
Over the weekend I found that Circuit City is selling the aspire 5580 for $999.  Looks like a pretty good deal to me so I'm thinking of getting one.  Does anyone use one of these with ubuntu?  I've been searching all morning and I can't find a report with this exact model but I did find reports of similar models that work pretty well with ubuntu or other linux distros.  I just want to check with others in this form in case anyone happens to have this model, to see if their hardware is working. 
cheers
mert

---

### Post by oddin85 on 2007-04-11
Everything works with a fresh install of Edgy except
1280 x 800 resolution - fix by installing 915resolution from synaptics
sound comes out of headphones but not the speakers
5 in 1 card reader doesn't read my memory stick
web cam doesn't work

i've been busy so i haven't had time to look for a fix to all of the issues yet, i've only had ubuntu on it for a few days

---

### Post by oddin85 on 2007-05-09
I installed Feisty the day it released, here's what i have working, what's partially working, and what's not working :-)

Working:
[INDENT]1280x800 resolution
[INDENT]Fix by typing "sudo apt-get install 915resolution" in the console
then log out with control alt backspace[/INDENT][/INDENT]
[INDENT]trackpad
[INDENT]Fix by editing /etc/X11/xorg.conf
first backup xorg.conf "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak" if anything goes wrong, boot from a live cd and replace the the new xorg.conf with the backup
open xorg.con "sudo gedit /etc/X11/xorg.conf
scrol to Section "InputDevice" Identifier "Configured Mouse"
add after InputDevice EndSection for Configured Mouse
```
Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "on"
EndSection
```
then find:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice "Synaptics Touchpad" // add this line here, but don't add my comment
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```
[/INDENT][/INDENT]
[INDENT]Intel Core2 Duo Processor works, shows up as 2 cores, no special action necesary[/INDENT]
[INDENT]Graphics card works without any special action (beryl looks nice without any special configuration, that's why i'm saying this)[/INDENT]
[INDENT]CD burning works, no special action needed (burning DVDs may work too, haven't checked, but it shows up as an option)[/INDENT]
[INDENT]Wireless and LAN both work, no special action required[/INDENT]
[INDENT]Mic works, no special configuration[/INDENT]

Kinda Working:
[INDENT]Camera kinda works with camorama, haven't had a chance to mess with it, but it works with the colors inverted :-([/INDENT]
[INDENT]Quick launch buttons work, can be assigned to shortcuts, the Euro button doesn't work, neither does the $ near it [/INDENT]
[INDENT]Sound comes out only from headphones, not built in speakers :( [/INDENT]

Not Working: (because i haven't been looking for fixes, cuz i've been busy)
[INDENT]5 in one Reader[/INDENT]
[INDENT]s-video[/INDENT]
[INDENT]vga output (haven't checked)[/INDENT]
[INDENT]the light on the quick launch email button[/INDENT]

Problems I've Had:
[INDENT]Sometimes randomly, programs appear to freaze, but the cpu indicator shows that it's all IOWait, then after a few seconds there's an audible click from the hard drive and the programs unfreeze and the cpu usage goes back to almost nothing :confused: [/INDENT]
[INDENT]There's a lag on start up, where the progress bar just stops moving, then keeps going after a while, this also happens on my friend's computer (HP with Ubuntu Feisty), so this may not be specific to this computer[/INDENT]

I don't remember where i got the fixes for the issues i've had, but it's on the ubuntu forums, sory for no URL to them

---

### Post by oddin85 on 2007-05-25
yay! I have sound!
it was apparently working from the beginning...

i just added a volume control applet to a panel and selected for it to control the surround under HDA alsa that controls the speakers, and add another one to control the headphonesHDA alsa front

^_^ i'm happy with sound now :D

also fixed the lag on start up: fixed it by commenting out the eth1 in /etc/network/interfaces


[http://www.opocot.com/ubuntu-feisty-sound-problem-solved/]("http://www.opocot.com/ubuntu-feisty-sound-problem-solved/")
and [http://ubuntuforums.org/showthread.php?p=2637781]("http://ubuntuforums.org/showthread.php?p=2637781")

---

### Post by oddin85 on 2007-06-13
from here: [http://ubuntuforums.org/showthread.php?t=361124]("http://ubuntuforums.org/showthread.php?t=361124")

i now have s-video working :-)

i didn't use the exact procedure from there, but these are my xorg.conf files:

xorg.conf (default)
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"LCD"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"LCD"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

xorg.conf with s-video
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"LCD"
	Driver		"i810"
	Option "MonitorLayout"	"TV,LFP"
	Screen 0
	BusID		"PCI:0:2:0"
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
	HorizSync	28-64
	VertRefresh	43-60
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
	Screen		1 "TV" LeftOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection
```

just switch between the two to either go back to default or s-video :-)

s-video works! yay! \\:D/

---

### Post by oddin85 on 2007-08-25
yay! :popcorn:
VGA output! ^_^

xorg file for vga (2 screens)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dbe"
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
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"LCD"
	Driver		"i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0	
	BusID		"PCI:0:2:0"
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
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

and code for vga with cloned output :-)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"LCD"
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
	Device		"LCD"
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
	Option 		"AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

```

same url as the one for s-video

---

### Post by oddin85 on 2007-09-15
SD Cards in the built in reader :-)

From here: [http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html]("http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html")

```
sudo gedit /etc/modules
```

just add:
```
tifm_sd
tifm_core
tifm_7xx1
```

---

### Post by funnypanks on 2007-09-21
did you ever get the freezes to stop?!?! its really driving me up the wall, i have the same laptop.

---

### Post by neoyahuu on 2007-10-16
nice posts oddin85. :KS :KS :KS
i got same laptop Aspire 5580. Seem Ubuntu is the best. 
After Ubuntu, i tried mandriva and now slackware.. Love to hear many things on aspire 5580 works.
:guitar:

---

### Post by oddin85 on 2007-11-03
I think the freezes are related to heat issues, I've noticed that in air conditioned areas it won't freeze as often, and if it's frozen and I lift it up so it can get more air, it'll unfreaze within a few seconds

in vista, the fan is always full blast, and  i've never seen it freeze (non-windows related)
xp sometimes freezes but fan isn't at max speed all the time

i haven't been able to find something that will let me control the fan in ubuntu (i don't care if it's noisy if it means it won't freeze)

i've been too busy w/ school to look for a solution, so in the mean time i'll stick to air conditioned areas :)

---

### Post by sjafri on 2007-11-25
I using Aspire 5580 also, Aspire 5585WXMi for spesific, I had same problem for over heating, it's look like the fan never kick ups if the laptop got heated, that way I want to know how manually speed change this fan speed, any program in ubuntu to speed up the fan?. how ?
and other problem If I using extended apperance it's "freez" thing happen more quick, maybe it heat problem related. I think if this heat can be solve, ubuntu will run smoth in this laptop.
My laptop spec
Intel core 2 duo T7200 2.0 Ghz, 667 Mhz FSB, 4 MB L2 cache
Geforce Go 7300
2 GB DDR2 Mem

---

### Post by oddin85 on 2007-12-26
:confused:

i got a chill mat for christmas, and my computer still freezes may not be a heat issue after all :(
My computer is nice and cold now, but still freezes. ARG!

---

### Post by funnypanks on 2007-12-28
oddin i know how u fix the freezes since i have the same laptop. u have to have windows to flash the dvd drive to sc03. i did this about 3 months ago so i don't have links/files anymore look around online for the files. good luck.
just so u can b sure, after a freeze do a dmesg and ull see something there about ur dvd drive. this is 100% ur issue there is no way that it is anything else. after flashing to sc03 both feisty and gutsy no longer freeze. have fun!

---

### Post by oddin85 on 2008-01-20
THANK YOU SOO MUCH! :grin:

I did what you suggested, and googled for the SC03 firmware and installed it using the instructions found here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg435655.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg435655.html)

so far no freezes!

thanks again! :-D

---

### Post by Jeffrey S. Antonio on 2008-03-17
Does it work just as well having XP also installed like the garden variety dsktop:confused:

---

### Post by oddin85 on 2008-04-11
I haven't used XP in a long time. but since this is a firmware issue, I think XP shouldn't freeze either after flashing the DVD drive :-)

---

