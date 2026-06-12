---
title: "Trying to configure extended desktop"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by jgoguen on 2005-05-08
I've been trying for some time now to get extended desktop working. I want to have two monitors with one desktop stretched across them. I've searched through the forums, but nothing posted so far has been of much help. I've got a Compaq Presario 2200 laptop with Hoary. I've gone through Synaptic and made sure I had the latest available upgrades for everything. I'm using Xorg. Using lspci, I found the following two display controllers:
 ```
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
``` 

The most help has been from [this post]("http://www.ubuntuforums.org/showthread.php?t=31686&highlight=xinerama+desktop"), which has helped me get to the point where I can have a modified xorg.conf file without any problems. Normally, X won't load after making most of the changes recomended on the forums. What I have now is a clone of my laptop display on my external monitor, which I had without making any modifications to the xorg.conf file. The laptop display is capable of at most 1024x768, and the external monitor can support up to 1280x1024. Below are appropriate sections from my current xorg.conf file:

```
Section "Module"
		Load	"GLcore"
		Load	"bitmap"
		Load	"dbe"
		Load	"ddc"
		Load	"dri"
		Load	"extmod"
		Load	"freetype"
		Load	"glx"
		Load	"int10"
		Load	"record"
		Load	"speedo"
		Load	"type1"
		Load	"v4l"
		Load	"vbe"
		Load	"xtt"
EndSection

Section "Device"
		Identifier	  "Laptop"
		Driver		  "i810"
		BusID		   "PCI:0:2:0"
EndSection

Section "Device"
		Identifier	  "External"
		Driver		  "i810"
		BusID		   "PCI:0:2:1"
EndSection

Section "Monitor"
		Identifier	  "Laptop Monitor"
		HorizSync	   28-49
		VertRefresh	 43-72
		Option		  "DPMS"
EndSection

Section "Monitor"
		Identifier	  "External Monitor"
		HorizSync	   28-49
		VertRefresh	 43-72
		Option		  "DPMS"
EndSection

Section "Screen"
		Identifier	  "Laptop Screen"
		Device		  "Laptop"
		Monitor		 "Laptop Monitor"
		DefaultDepth	24
		SubSection "Display"
			 Depth		 24
			 Modes		 "1024x768" "800x600" "640x480"
		EndSubSection
EndSection

Section "Screen"
		Identifier	  "External Screen"
		Device		  "External"
		Monitor		 "External Monitor"
		DefaultDepth	24
		SubSection "Display"
			 Depth		 24
			 Modes		 "1024x768" "800x600" "640x480"
		EndSubSection
EndSection

Section "ServerLayout"
		Identifier	  "Default Layout"
		Screen		  0 "Laptop Screen" 0 0
	    Screen		 1 "External Screen" RightOf "Laptop Screen"
		Option		  "Xinerama" "On"
		Option		  "Clone" "Off"
		InputDevice	 "Generic Keyboard"
		InputDevice	 "Configured Mouse"
		InputDevice	 "Synaptics Touchpad"
EndSection

Section "ServerFlags"
		Option		  "Xinerama" "On"
EndSection

Section "DRI"
		Mode	0666
EndSection
```

I've tried using MonitorLayout in the Device section as well, and if I use "LFP,CRT" then my X display will only show on the external monitor. Using "CRT,LFP" gives me a display only on the laptop display, "CRT,CRT" gives a poor quality display on the external monitor only, and "LFP,LFP" gives a poor quality display on the laptop monitor only, using the configuration above.  I've also tried switching the BusIDs for the devices, which gives me the same display clone I have now.

Also, I don't always have a monitor connected to the laptop, and when there's no monitor I need Xorg to ignore extended desktop and use only the laptop display, if that's possible. If anyone has any ideas or knows what works, would you please let me know?

---

### Post by mrkslntbob on 2005-05-13
I am having the same problem.
I have an Intel 855G on and HP Pavilion ZE4949US Laptop.
I get a clone of the laptop LCD on the external monitor, but want extended desktop.
My /etc/X11/xorg.conf looks similar.
Has anyone gotten "extended desktop" to work on and intel 855GM?

---

### Post by jgoguen on 2005-06-11
I saw that Intel had drivers out for my card, so I went after them. No luck, I just got the same cloned screens as before. Here's my latest xorg.conf:
```

Section "ServerLayout"
	Identifier	 "Multihead layout"
	Screen	  0  "Screen0" LeftOf "Screen1"
	Screen	  1  "Screen1" 0 0
	InputDevice	"Mouse0" "CorePointer"
	InputDevice	"Keyboard0" "CoreKeyboard"
	Option		"Xinerama" "off"
	Option		"Clone" "on"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver	  "kbd"
	Option		"XkbModel" "pc105"
	Option		"XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver	  "mouse"
	Option		"Protocol" "IMPS/2"
	Option		"Device" "/dev/input/mice"
	Option		"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName	"L7AK4"
	DisplaySize  340	270
	HorizSync	31.0 - 80.0
	VertRefresh  50.0 - 75.0
	Option		"dpms"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName	"Monitor 1024x768"
#	HorizSync	35.0 - 75.0
#	VertRefresh  55.0 - 75.0
	VertRefresh	60.0
#	1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
	Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
	Option		"dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver	  "i810"
	VendorName  "Videocard vendor"
	BoardName   "Intel 852"
	Option	"MonitorLayout"	"LFP,CRT"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver	  "i810"
	VendorName  "Videocard Vendor"
	BoardName   "Intel 852"
	BusID	   "PCI:0:2:0"
	Screen	  1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device	 "Videocard0"
	Monitor	"Monitor0"
	DefaultDepth	 24
	SubSection "Display"
		Viewport   0 0
		Depth	 24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device	 "Videocard1"
	Monitor	"Monitor1"
	DefaultDepth	 24
	SubSection "Display"
		Viewport   0 0
		Depth	 24
		Modes	"1024x768"
	EndSubSection
EndSection

Section "DRI"
	Group		0
	Mode		 0666
EndSection
```

My Xorg log from running 'xinit -- :2' is [here](http://v5o5jotqkgfu3btr91t7w5fhzedjaoaz8igl.unbf.ca/~r1hh8/Xorg.2.log)

---

### Post by cpscotti on 2006-03-29
Man! This is the only problem I have with my ubuntu!

Seems impossible to run Extended Desktop! ( I know it is not because win***** does it!)

I Tryed A lot of xorg.conf s but same problem!!! when loading X it stops in a gray screen with to little white rectangles!!

I'll post my xorg.conf soon!

---

### Post by jgoguen on 2006-03-29
Try this xorg.conf as a start.  This works on my laptop, no guarantees that it'll work the same unless you have the exact same laptop as I do.  You may have to edit it to get it working properly.

```
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        0 "Default Screen"
    Screen        1 "Default Screen 2" RightOf "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option        "Xinerama"    "True"
EndSection

Section "Files"
    FontPath    "unix/:7100"            # local font server
    # if the local font server has problems, we can fall back on these
    FontPath    "/usr/lib/X11/fonts/misc"
    FontPath    "/usr/lib/X11/fonts/cyrillic"
    FontPath    "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/lib/X11/fonts/Type1"
    FontPath    "/usr/lib/X11/fonts/CID"
    FontPath    "/usr/lib/X11/fonts/100dpi"
    FontPath    "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "keyboard"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Option        "MonitorLayout"        "CRT,LFP"
    VideoRam    65536
    Option        "FlipPrimary"        "false"
    Option        "DevicePresence"    "true"
    Option        "VBERestore"        "false"
    Screen        0    

EndSection

Section "Device"
    Identifier    "Intel Corporation 82830 CGC [Chipset Graphics Controller] 2"
    Driver        "i810"
    BusID        "PCI:0:2:0"
    Option        "MonitorLayout"        "CRT,LFP"
    Option        "DevicePresence"    "true"
    VideoRam    65536
    Option        "VBERestore"        "false"
    Screen        1    
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-49
    VertRefresh    43-72
EndSection

Section "Monitor"
    Identifier    "Generic Monitor 2"
    Option        "DPMS"
    HorizSync    28-49
    VertRefresh    43-72
EndSection

Section "Screen"
    Identifier    "Default Screen 2"
    Device        "Intel Corporation 82830 CGC [Chipset Graphics Controller] 2"
    Monitor        "Generic Monitor 2"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection
EndSection

Section "DRI"
    Mode    0666    #Disable by Xinerama
EndSection
```

---

### Post by stackcheese on 2006-06-11
is there a way to have ubuntu/gdm (too much of a noob to know which) detect that I have a second monitor plugged in and then load a different ServerLayout Identifier?

So instead of loading once xorg.conf when using one monitor and then loading a seperate xorg.conf I can have one large xorg config that detects what kind of setup i'm currently running?

---

### Post by Tristan9669 on 2006-07-08
can anyone help me setup an extended deskop onto a tv with an ati 9000 video card

---

### Post by ehcmx on 2006-07-11
Hi averybody,

As all of you I already configure my ubuntu 6.06 to work with two desktops.Unfurtunatelly no desktop extended between two monitors, besides, two independent desktops in two different monitors.

Now I am facing next problems:
1.- Supouse that I start Firefox in one desktop and I try to open another firefox in the second desktop, then apears a message saing: *Firefox is already runnig, but is not responding. To open a new window you must first close the existing firefox process or restart your system*.

2.- Supose I have opened OpenOffice Word processor in monitor No.1. If I start on the second monitor another OO Word processor the new document is opened on the first monitor.

What do I have to do have two desktops totaly indenpendent?

I will aprecaite your support.

---

