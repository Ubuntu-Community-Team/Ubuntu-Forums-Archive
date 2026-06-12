---
title: "Widescreen with Intel graphics chipset"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by BlvdKing on 2006-06-18
I had a hard time getting widescreen to work on my Dell XPS M140 notebook with Dapper release.  This information was buried, so I though I would post the solution for easy reference.

The solution is simple: install the 915resolution package in Synaptic or run this in the terminal:

```
sudo apt-get install 915resolution
```

After installing the package, follow the instructions in this file to configure your screen:

```
/usr/share/doc/915resolution/README.Debian
```

A reboot is required after configuring the 915resolution config file.  This program will run every time you reboot you computer.  :D

---

### Post by MetalMusicAddict on 2006-06-18
On a side note. How do you like the laptop? A friend bought the new 700 desktop series and now Im looking at the XPS line. He got the desktop *and* the 2407 screen for $2400. Their trying to push 'em and he got a sweet deal from a manager. I guess calling Dell is better than online.

Im gonna wait 'till his comes in to decide to get a laptop on new desktop.

---

### Post by BlvdKing on 2006-06-18
I like it.  I got it for $750 with a 9 cell battery.  Battery life is better than six hours, which is really nice.  This laptop is discontinued, but the Inspiron e1405 is the exact same computer with a core duo starting at $759.  If I were ordering today, I would go with that.
This laptop is rugged and the screen looks good.  It has a weak graphics card.  As always, dell installs tons of crap on the computer, including two hidden partitions.  It's also on the heavier side with the 9 cell battery.  Overall, I am satisfied with the laptop, especially the battery life.

---

### Post by supanova on 2006-06-21
Hi 

Can you please post your /etc/default/915resolution and /etc/X11/xorg.conf file?

I'm having some problems running 1920x1200 on my 23" Philips 230W LCD 

Thanks

---

### Post by oldornot on 2007-07-24
just 915resolution on UBUNTU 7.04 didnt help me (i have intel 845). I installed xserver-xorg-video-intel (i810 driver will be unisntalled) and changed Driver      "i810" to "intel" in xorg.conf, you also might need to add Modeline to monitor section (find your ModeLine in /var/log/Xorg.0.log)


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
#	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
#	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
#	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "record"
	Load  "xtrap"
	Load  "GLcore"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
	Load  "type1"
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
#	DisplaySize	  520   330	# mm
#	DisplaySize	  542   406	# mm 1600x1200@75dpi
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL 2407WFP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
#	HorizSync    30.0 - 83.0
#	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
	Modeline "1920x1200"  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
#	Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	BusID       "PCI:0:2:0"
#	Option "ModeValidation" "NoMaxPClkCheck"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

---

