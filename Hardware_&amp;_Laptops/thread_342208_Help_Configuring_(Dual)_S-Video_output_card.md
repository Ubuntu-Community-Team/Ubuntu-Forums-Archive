---
title: "Help Configuring (Dual) S-Video output card"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by MisterAdams on 2007-01-19
Hi, I am new to linux and Ubuntu. I would like to know how to, if possible, configure my dual output Nvidia? video card. I forget the manufacturer but it is labeled Gforce mx4000 nv19pl or (nvi9pl) rev 1.0 and has a standard vga connection and a s-video connection (the one I would like to get working. I have just installed ubuntu a couple of days ago and assume it is the current version. 
Thanks for the help!
         Mark

---

### Post by lank23 on 2007-02-24
I have the same issue,

My s-video will work but only while Ubuntu is booting, then once I get the login screen the S-Video is turned off.

To get this far I followed the wiki on dual monitors and installed the nvidia driver with synaptic.

Here is the needed sections of my /etc/X11/xorg.conf file

```


Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"     
	BusID   "PCI:04:02:0"
EndSection



Section "Device"
        Identifier      "Device1"
        Driver 		"nvidia"
        Screen 1
	BusID   "PCI:04:02:0"
EndSection

Section "Monitor"
        Identifier      "Monitor" #CRT Monitor
        HorizSync       30-70
        VertRefresh     50-140
        Option          "DPMS"
EndSection


Section "Monitor"
        Identifier "Television" #TV S-Video
        HorizSync 30-50
        VertRefresh 60
EndSection


Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
        Option  "ConnectedMonitor" "CRT"
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "NTSC-M"
        Option  "ConnectedMonitor" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection



Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0        "Screen0"
        Screen 1        "Screen1" rightof "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection


```

Any help on this will be great.

Specs:
Ubuntu 6.10
nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)

lank23

---

### Post by n8bounds on 2007-02-25
[http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)

---

### Post by lank23 on 2007-02-25
I did get the S-video to work in twin view mode, but only with
  
Option "TwinViewOrientation" "RightOf"

 When the setting is

Option "TwinViewOrientation" "Clone"

GDM freezes and does not display desktop.

, see below xorg.conf sections.


```


Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:4:2:0"
	Option "TwinView" "True"
	Option "UseEdidFreqs" "False"	
	Option "TwinViewOrientation" "RightOf"
	Option "MetaModes" "1024x768,800x600,640x480; 640x480"
	Option "UseDisplayDevice" "CRT,TV"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
EndSection



```

lank23

---

### Post by lank23 on 2007-02-25
Got it working in Clone mode  1024x768 on the CRT and 640x480 on the S-video.  

Here is the xorg.conf sections for clone mode with a GeForce4 MX 4000.  Cheers



```

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:4:2:0"
	Option "TwinView" "True"
	Option "UseEdidFreqs" "False"	
	Option "TwinViewOrientation" "Clone"
	Option "TVOutFormat" "SVIDEO"
	Option "TVStandard" "NTSC-M"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
	Option "UseDisplayDevice" "CRT,TV"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
EndSection

```

---

