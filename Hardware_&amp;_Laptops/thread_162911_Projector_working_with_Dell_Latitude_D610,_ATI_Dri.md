---
title: "Projector working with Dell Latitude D610, ATI Drivers"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by scb147 on 2006-04-19
I've searched the forums and have seen many people ask this question, but I am trying to get a projector to work with my Dell Latitude D610, running Breezy.  I have the ATI Drivers 8.24.8 installed, but I am not an expert with the xorg.conf file.  So I have no idea what I need to change.  I have the ATI Control installed, but changing the Desktop Setup to Clone Mode says I need to restart the XServer.  But restarting the XServer doesn't do anything.

Can I set it up so that I can have multiple resolutions, and the driver will pick the best one?  And can I have it so I can just change the mode with the ATI Control to get this to work?  I'd actually like to leave the Clone mode on all the time... if possible.

I have included a copy of my xorg.conf and an output from fglrxinfo. 

Any help would be greatly apprciated!

xorg.conf
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 70.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5755 (8.24.8)

```

---

### Post by gerbman on 2006-04-20
I'm assuming you're using the s-video output on your lappy. I have the Dell D810 and have been able to get dual screen working with the fglrxconfig utility. Run it with```
sudo fglrxconfig
```Help any?

---

### Post by scb147 on 2006-04-20
[QUOTE=gerbman]I'm assuming you're using the s-video output on your lappy. I have the Dell D810 and have been able to get dual screen working with the fglrxconfig utility. Run it with```
sudo fglrxconfig
```Help any?[/QUOTE]

I'm actually using the standard VGA output.  fglrxconfig always scares me cause I have no idea what most of the settings are for.

---

### Post by gerbman on 2006-04-20
[QUOTE=scb147]I'm actually using the standard VGA output.  fglrxconfig always scares me cause I have no idea what most of the settings are for.[/QUOTE]No need to be scared :-) Just back up your xorg.conf file before running fglrxconfig by doing```
cp /etc/X11/xorg.conf /where/to/put/backup/xorg.backup
```You can accept the default settings provided by fglrxconfig for everything except the dual screen set-up. Just hit enter to accept a default setting. You might have to try a couple different configurations (clone, dual-head, etc.) before finding one that suits your needs. Hit CTRL+ALT+BKSP after running fglrxconfig to test the new settings. If your session fails to start, hit CTRL+ALT+F1 to switch to a console screen and restore your xorg.conf file with```
sudo cp /where/you/put/backup/xorg.backup /etc/X11/xorg.conf
```then restart your session again.

Hope that helps.

---

### Post by scb147 on 2006-04-22
I found out that ATI replaced fglrxconfig with aticonfig in the 8.24.08 drivers (well, fglrxconfig wasn't available to me with this version).

I used the following aticonfig command line to setup my xorg.conf:
```

sudo aticonfig --initial=dual-head --dtop=clone --resolution=1400x1050 --mode2=1600x1200,1400x1050,1280x1024,1024x768

```

Rebooted, and everything worked great!

gerbman, thanks for the help!

---

### Post by gerbman on 2006-04-22
Awesome...good to know for future reference.

---

### Post by z5c on 2006-04-26
[QUOTE=scb147]I found out that ATI replaced fglrxconfig with aticonfig in the 8.24.08 drivers (well, fglrxconfig wasn't available to me with this version).

I used the following aticonfig command line to setup my xorg.conf:
```

sudo aticonfig --initial=dual-head --dtop=clone --resolution=1400x1050 --mode2=1600x1200,1400x1050,1280x1024,1024x768

```

Rebooted, and everything worked great!

gerbman, thanks for the help![/QUOTE]
could you please post your xorg.conf
Im trying for two days now to get a similiar setup working.
I want clone mode with 1440x900 on notebook and 1280x1024 on external tft.
All I got so far was either flickering chaos on both screens (with --mode2=1280x1024) or right resolution on notebook screen but weird resolution on tft with actually only a movable section of desktop visible (no --mode2).

---

