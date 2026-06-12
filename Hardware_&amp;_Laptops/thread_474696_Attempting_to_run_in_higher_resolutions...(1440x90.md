---
title: "Attempting to run in higher resolutions...(1440x900)"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by Tekee on 2007-06-15
Last night I spent many hours googling fixes to this, and while I got a few, one of the suggestions apparently screwed up my .xorg file and I had to find a fix to get back into graphical log-ins (I'm a new user, so bear with me).

Does anyone have an elaborate tutorial of getting Ubuntu to run in the resolution I need? Again, I'm running 1440x900 widescreen, and I have an ATI graphics card. Thanks!

---

### Post by mikewhatever on 2007-06-15
Have you tried editing your xorg file without screwing it up? Simply add the required resolution to the already existing ones, save and exit, then hit Ctrl+Alt+Backspace to restart X.

---

### Post by Tekee on 2007-06-15
Yes, I actually looked at it right now and it's set to do 1440x900...although the screen resolutions I can choose from in 'System' are something like 1152x864 and 1024x780.

---

### Post by Tekee on 2007-06-15
Figure I'd at least show you the .xorg file as well:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	60-70
	VertRefresh	70-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon Xpress200"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection
```

---

### Post by mikewhatever on 2007-06-15
This is odd. I've done just that several times yesterday and it worked. Another way to do it is > sudo dpkg-reconfigure xserver-xorg
Hopefully the default options will work. You may also want to check out what to expect [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
Backup the existing file with the following
> sudo cp /ect/X11/xorg.conf /ect/X11/xorg.conf_backup

---

### Post by lamadredelsapo on 2007-06-15
I think you should do the following to set your screen at 1440x900@60Hz:

Open a terminal window and execute the following command

```
gtf 1440 900 60
```

You should get something similar to this:
```
# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

```

Backup your xorg.conf file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Copy de output of the gtf command to the "Monitor" section of your xorg.conf file and the following to the "Screen section"
```
SubSection     "Display"
        Depth       24
        Modes      "1440x900_60.00"
    EndSubSection
```

Save your xorg.conf file, logout and restart your X with Ctr+Alt+Back space

You should have your desired resolution working

---

### Post by stchman on 2007-06-15
> **Tekee said:**
> Last night I spent many hours googling fixes to this, and while I got a few, one of the suggestions apparently screwed up my .xorg file and I had to find a fix to get back into graphical log-ins (I'm a new user, so bear with me).

Does anyone have an elaborate tutorial of getting Ubuntu to run in the resolution I need? Again, I'm running 1440x900 widescreen, and I have an ATI graphics card. Thanks!

look to see if there is a /etc/X11/xorg.conf.bak file.  A lot of times apps will backup this file.

If not then download Envy for which Ubuntu you have and go to the recovery mode.  Make sure you have an internet connection.

Type envy -t

Select Uninstall the ATI driver

Let it do its thing and reboot back into recovery mode.

Type envy -t again

Select Install the ATI driver

Let it do its thing again.  Reboot and you should be able to get back into Gnome.  Envy updates the xorg.conf file.

Hope this helps.

---

### Post by jpangamarca on 2007-06-16
I tried this to set the screen resolution at 1152x864@60Hz (with the correct values, of course) but I couldn't:

Originally posted by ***lamadredelsapo ***
> I think you should do the following to set your screen at 1440x900@60Hz:

Open a terminal window and execute the following command

Code:

gtf 1440 900 60

You should get something similar to this:
Code:

# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

Backup your xorg.conf file

Code:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

Copy de output of the gtf command to the "Monitor" section of your xorg.conf file and the following to the "Screen section"
Code:

SubSection     "Display"
        Depth       24
        Modes      "1440x900_60.00"
    EndSubSection

Save your xorg.conf file, logout and restart your X with Ctr+Alt+Back space

You should have your desired resolution working

What I did was:

```
user@machine:~# gtf 1152 864 60
# 1152x864 @ 60.00 Hz (GTF) hsync: 53.70 kHz; pclk: 81.62 MHz
  Modeline "1152x864_60.00"  81.62  1152 1216 1336 1520  864 865 868 895  -HSync +Vsync

```

Instead of getting 1152x864@60Hz, I get ***1152x768@55Hz*** (where does that come from???), and it doesn't look any pretty. I can use 1152x864@60Hz under Windows. What am I missing? I removed the following section of code from the "Monitor" section (xorg.conf) because it didn't make any difference:

```

HorizSync	30.0 - 55.0
VertRefresh	50.0 - 120.0

```

My xorg.conf file is:

```

====================================================
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
	Option		"XkbLayout"	"es"
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
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	DefaultDepth	24	
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864_60.00"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
====================================================

```

I also tried to use DefaultDepth 16 instead of 24. but it didn't work either...

Please help me. Thanks.

---

