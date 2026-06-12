---
title: "Resolution 800x600 Max"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by postalphil on 2007-01-25
I am running 6.10 Edgy on a gateway 400VTX laptop that has the Intel 852MG video chipset.  I have tried several ways to get the screen resolution to 1024 x 768 but have no luck.  All I have is 800 x 600 and 640 x 480.  In Windows XP I do have the 1024 x 768 runningIs there any help out there

lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)

---

### Post by _simon_ on 2007-01-25
This might be of some help:

[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

---

### Post by Garyu on 2007-01-25
```
sudo dpkg-reconfigure xorg-xserver
```
If you run this command in a terminal you can enter all sorts of info about your video card and monitor. If you have your manuals handy (or search for them on the internet like I usually do) there should be horizontal and vertical refresh rates that you can fill out for the monitor. Those things might help you get the correct resolution. 

The above command will create an automatic backup of you /etc/X11/xorg.conf file with a date and time at the end. If you are curious on how this file works you can compare the old backup with the one you made with the above command and learn how to change it manually.

Of course, you have to restart your x-server to apply the changes. If you don't want to reboot your computer, I think this is done with a
```
gdm -restart
```
in a terminal (ctrl-alt-F1), or ctrl-alt-backspace might do the trick as well when you are running the x-server.

---

### Post by postalphil on 2007-01-28
I have tried these and still I can't get 1024 x 768

---

### Post by Garyu on 2007-01-28
Maybe you can post the contents of your /etc/X11/xorg.conf

---

### Post by j0sh0 on 2007-01-28
Postalphil:
I think you may have the same problem as myself and a couple of other people I've read posts from. Unfortunately we're part of a very small minority who 915resolution doesn't work for. The only other option I can suggest at the moment is to do a search for "modesetting driver" in these forums and read the thread called "compiling the latest intel modesetting driver". I'm unable to compile the driver at the moment, I'm still waiting for a guru to reply with some help, but it seems to be my (our) last hope. Have you tried searching for a bios update for your laptop. I'm under the impression that this may help solve the problem, too.

Give that suggested thread a read and let us know how you go.

Reagards

j0sh0

---

### Post by postalphil on 2007-01-29
> **Garyu said:**
> Maybe you can post the contents of your /etc/X11/xorg.conf

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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD TFT"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"LCD TFT"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
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


$ sudo xresprobe i810
Password:
id:
res: 1024x768
freq:
disptype: lcd/lvds
depth: 16

sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller Hardware Version 0.0
memory: 12288kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid:
edidfail


The display is still 800 x 600

---

### Post by Garyu on 2007-01-29
Hmm, yeah, as far as I can see everything looks fine there. I guess j0sh0 is right and that you should try to follow the directions he gave, or just wait until someone releases some good drivers.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel)
If you look at the hardware compatibility list, your card isn't listed either. You should always check out this list when you are buying new hardware to make sure you get something which is working fine. Still, you've got 800x600, so at least you've got limited functionality. I've seen posts by ATI users who don't have any kind of graphics without tinkering with x.org settings. 

As for me, I always use nVidia cards as they usually work fine with just about anything. :)

---

### Post by marcthepunk on 2007-01-29
hey postaphil, probably you will need to have a modeline statement under the monitor section.  google modeline generator.  you may also want to look at adjusting your horizontal and vertical sync.  word of advice, make a copy of your xorg.conf file before changing values.

---

### Post by gamerteck on 2007-01-29
Check out this HOWTO...

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Might help some, I know I had an issue with a similar Intel graphics chip-set and had to force the resolution by using a modeline as **marchthepunk** suggested.

I know there is a command you can run in the terminal, to retrieve a modeline, but I can't recall what it is.

---

### Post by postalphil on 2007-01-29
> **gamerteck said:**
> Check out this HOWTO...

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Might help some, I know I had an issue with a similar Intel graphics chip-set and had to force the resolution by using a modeline as **marchthepunk** suggested.

I know there is a command you can run in the terminal, to retrieve a modeline, but I can't recall what it is.

If you do remember let me know.  I have also contacted Award for a bios update since they have aquired Phoenix Tech.

---

