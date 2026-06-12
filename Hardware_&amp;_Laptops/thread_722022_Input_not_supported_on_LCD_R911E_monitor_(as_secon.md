---
title: "Input not supported on LCD R911E monitor (as secondary monitor)."
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by mwiley63 on 2008-03-12
I have searched all over the forums, and could not find a good answer anywhere. 

I have a dual head set up (2 separate desktops), with a syncmaster as my primary monitor(DVI), and a R911E(VGA) as my secondary.  When I start up, the R911E display "Input Not Supported", but the other monitor is just fine.  

I also cannot seem to run xrandr, it only detects one screen.  What I need is to have the refresh rate of the R911E set ot something like 75. 

Heere are my monitor settings in my xorg.conf file:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LCD R911E"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection
```

These are the settings of specifications I looked up on the internet for these models.  

An easy way to fix, but by no means a good solution is to open up the nvidia driver program, and set the refresh rate of the R911E monitor there.  This however, is a bad solution if I am running compiz.  If compiz is running I get an error and am not able to change the refresh rate of the R911E monitor.  

Here is the rest of the relevant information from my xorg.conf file:

```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:7:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
	Option		"UseFBDev"	"true"
	Option		"AddARGBGLXVisuals"	"True"
    SubSection     "Display"
        Depth       24
	Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option	   "UseFBDev"	"true"
    Option         "AddARGBGLXVisuals"	"True"
    SubSection     "Display"
        Depth       24
	Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
    EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
```

Any guidance is greatly appreciated.

---

