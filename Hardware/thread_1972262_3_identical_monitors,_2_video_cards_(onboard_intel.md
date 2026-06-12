---
title: "3 identical monitors, 2 video cards (onboard intel, external ati)"
date: 2012-05-03
forum: Hardware
---

### Post by eriktim on 2012-05-03
Dear all,

After searching for many hours I hope to find my solution here.
I use Ubuntu 10.04 (64 bit) with two video cards

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82437FX (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]

```

I have connected three monitors, all are the Samsung SyncMaster 2443. I have no xorg.conf and two monitors (attached to the on-board Intel card) have the same strange output while the other remains black, also
```
$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0* 
   1280x1024       0.0  
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0 
```

I have no clue how to use the three monitors with the two cards. Using any of the cards when disabling the other works smoothly. Am I doing something wrong? Do I miss a setting? Do I need to (manually) write xorg.conf? Any help is appreciated!

Many thanks in advance!

Regards,
Erik

---

### Post by eriktim on 2012-05-04
OK, I found one error, I added [FONT="Courier New"]ppa: xorg-edgers/ppa[/FONT] (and already had added [FONT="Courier New"]ppa:glasen/intel-driver[/FONT] as well). Removing the first gave me two monitors that worked again.

xrandr now results in:
```
$ xrandr -q
Screen 0: minimum 320 x 200, current 3120 x 1920, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1200+1200+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      50.0     60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       50.0     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        60.0  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1200x1920+0+0 left (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      50.0     60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       50.0     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        60.0  
DP2 disconnected (normal left inverted right x axis y axis)

```

I have tried generating a xorg.conf file by switching to console mode (CTRL-ALT-F1) and typing 
```

sudo service gdm stop
sudo Xorg -configure
sudo X -config ~/xorg.conf.custom

```

However, this leaves me with three blanks screens. Shouldn't this at least give me two working monitors?

I also tried the following xorg.conf without success:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" LeftOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
	Load  "glx"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Samsung"
	ModelName    "SyncMaster 2443"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Samsung"
	ModelName    "SyncMaster 2443"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Samsung"
	ModelName    "SyncMaster 2443"
EndSection


Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV516 [Radeon X1300/X1550 Series]"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82437FX"
	BusID       "PCI:0:2:0"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card0"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by eriktim on 2012-05-21
Anybody?

---

