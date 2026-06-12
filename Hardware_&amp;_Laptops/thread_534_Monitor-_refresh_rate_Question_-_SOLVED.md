---
title: "Monitor- refresh rate Question - SOLVED"
date: 2004-10-14
forum: Hardware &amp; Laptops
---

### Post by Perfect Storm on 2004-10-14
My problem is I can only pick refresh rate 60 hz under resolution 1600x1200 and my monitor can handle 85 hz under resolution 1600x1200

So I guess I have to change it in XF86Config-4

sudo init 3
&lt;password&gt;
cd /etc/X11
sudo vim XF86Config-4

I need some advise to do so, I messed up the config file once (luckly I had backups)


Monitor specs:
taken from [http://support.ap.dell.com/docs/monitors/p992/g_englsh/specs.htm](http://support.ap.dell.com/docs/monitors/p992/g_englsh/specs.htm)

> Model number  	P992
CRT (19")
	
Screen dimensions
Preset Image Size
	4:3 	Diagonal 17.32 inches (440 mm)
	Horizontal 13.86 inches (352 mm)
	Vertical 10.39 inches (264 mm)
Viewable Image Size (VIS) 	Diagonal 17.97 inches (456.4 mm)
	Horizontal 14.37 inches (365 mm)
	Vertical  10.79 inches (274 mm)
Aperture Grille Pitch 	0.24 – 0.25 mm
Deflection angle 	90°
Phosphor type 	P22
Faceplate coating 	AR Coating

Resolution
Horizontal scan range 	30 kHz to 107 kHz (automatic)
Vertical scan range 	48 Hz to 170 Hz (automatic)
Optimal preset resolution 	1024 x 768 at 85 Hz
Highest preset resolution 	1600 x 1200 at 85 Hz
Highest addressable resolution* 	1920 x 1200 at 75 Hz
* Addressable means the monitor will sync up to this mode.  However, Dell does not guarantee the image will be sized and centered correctly. 

Dell guarantees image size and centering for all preset modes listed in the following table.

Preset Display Modes
Display Mode 	Horizontal Frequency (kHz) 	Vertical Frequency (Hz) 	Pixel Clock (MHz) 	Sync Polarity (Horizontal /Vertical)
IBM®, VGA2, 720 x 400 	31.5 	70 	28.3 	-/+
IBM, VGA3, 640 x 480 	31.5 	60 	25.2 	-/-
VESA®, 640 x 480 	43.3 	85 	36.0 	-/-
VESA, 800 x 600 	53.7 	85 	56.3 	+/+
VESA, 1024 x 768 	60.0 	75 	78.8 	+/+
VESA, 1024 x 768 	68.7 	85 	94.5 	+/+
VESA, 1280 x 1024 	80.0 	75 	135.0 	+/+
VESA, 1280 x 1024 	91.1 	85 	157.5 	+/+
VESA, 1600 x 1200 	93.8 	75 	202.5 	+/+
VESA, 1600 x 1200 	106.3 	85 	229.5 	+/+

 
Electrical
	
Video input signals 	Analog, 0.7 Vpp, positive at 75 ohm
Synchronization input signals 	

Separate horizontal and vertical; and composite
TTL level, positive or negative
Sync on Green at 0.3 Vp-p
AC input voltage / frequency / current 	100 to 240 VAC / 50 or 60 Hz ± 3 Hz /
2.0 A (RMS) at 120 VAC and
1.0 A (RMS) at 220 VAC
Inrush current at 120 V 	50 A
Inrush current at 240 V 	80 A

 
Physical Characteristics
	
Connector type 	15-pin D-subminiature
Signal cable type 	Attached to monitor
Dimensions: 	

    Height

	471 mm (18.54 inches)

    Width

	451 mm (17.76 inches)

    Depth

	461 mm (18.15 inches)
Weight (monitor only) 	25.5 kg (56.1 lb)
Weight (with packaging) 	30.0 kg (66.0 lb)
Environmental
	
Temperature: 	

    Operating

	32° to 104°F (0° to 40°C)

    Nonoperating

	-4° to 140°F (-20° to 60°C)
Humidity: 	

    Operating

	10% to 80% (noncondensing)

    Nonoperating

	5% to 90% (noncondensing)
Altitude: 	

    Operating

	3,048 m (10,000 ft)

    Nonoperating

	10,675 m (35,000 ft)
Thermal dissipation 	461 BTU/hour (maximum)
427 BTU/hour (typical)
Power Management Modes

If you have VESA’s DPMS compliance display card or software installed in your PC, the monitor can automatically reduce its power consumption when not in use. The monitor will automatically “wake-up” if the keyboard, mouse or other input devices are detected. The following table shows the power consumption and signaling of this automatic power saving feature:

Power Management Definition

VESA’s Mode
Video
H-sync
V-sync
Power Used
	
LED color

ON
Active
Yes
Yes
	

Maximum
135 W

Typical
125 W

Minimum
80 W
	
Green
Active-OFF
Blanked
No
No
&lt; 3 W
	

Amber

OFF*
N/A
N/A
N/A
0 W
OFF

This monitor is ENERGY STAR®-compliant and TCO’95 power management compatible.

* Zero power consumption in OFF mode can only be achieved by disconnecting the power cable from the monitor. 

My XF86Config looks like:

> 

/snip

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-75
	VertRefresh	50-85
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


As you see I also want to setup my monitor with Horizontal scan range and Vertical scan range, refresh rate etc. But my problem is to where to put the right numbers in the right place.

Help appriciated.

Thanks

---

### Post by triad169 on 2004-10-14
OK Lets try this

```
sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.original
```

This backs up your XF86Config File

```
sudo vim XF86Config-4
```

remove under Monitor section

```
 Modeline &quot;1280x800@60&quot; 83.91 1280 1312 1624 1656 800 816 824 841 
```

change under Monitor section (note frequency ranged obtained from you monitor specs)

```

HorizSync 30 - 107
VertRefresh 48 - 170
```

Save you XF86Config-4 file.  Logout out of Gnome.  At login screen hit 

ctrl-alt-backspace

This will restart XServer with your new config. Check your frequency.

If for some reason your Xserver wont start and plops you to the command line.  Then just:

```
sudo cp /etc/X11/XF86Config-4.original /etc/X11/XF86Config-4
```

Now if for some reason your refresh still is stuck at 60Hz you will need to configure a modeline for that resolution and that frequency.
  You can read up about modelines at this url:

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugxconfig.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugxconfig.html)

Also when you have frequency setup in XF86Config-4 file you can adjust frequency using the GUI Gnome Program located under 

*Computer Menu -&gt; System Configuration -&gt; Screen Resolution*

*Please note BE VERY CAREFUL and make sure you enter all frequency ranges properly because you could theoretically mess up you monitor.  *

---

### Post by Perfect Storm on 2004-10-15
> remove under Monitor section

Code:
 Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841


change under Monitor section (note frequency ranged obtained from you monitor specs)

Code:

HorizSync 30 - 107
VertRefresh 48 - 170




w00t!!!!

That did it!

Thank :-)

---

### Post by beabroad on 2005-10-19
i am new to Linux.
i do not have XF86Config-4 file in my system. i use Ubuntu 5.10

---

### Post by Pablo_Escobar on 2005-10-19
It's because it's a Warty message (it used XF86Config-4 back then)
In Hoary and Breezy the file You're looking for is /etc/X11/xorg.conf

---

