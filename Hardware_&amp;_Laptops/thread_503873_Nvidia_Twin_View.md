---
title: "Nvidia Twin View"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-07-18
I have read the previous posts, i have still not found any joy.

I can get the twin view mode to start just fine, my problem is i cannot get the displays configured in the correct order.  i wish to use my laptop display as the primary monitor, with my analog LCD as the right hand monitor.  The monitor is really bossy and insists on being the primary monitor.

I cannot get this straightened out, RightHand LeftHand, monitor0 monitor 1... i cannot fix this; can somebody have a look?

```

Section "Device"
	Identifier     "Videocard0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce Go 6600"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"True"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL1916W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option 	   "TwinView" "1"
    Option         "TwinViewOrientation" "RightOf"   
    Option         "UseEdidFreqs" "True"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1680+0" 
    Option         "UseDisplayDevice" "DFP, CRT"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Screen0" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

```

thanks.

---

### Post by djgrandmarquis on 2007-07-18
Have you installed the nvidia-settings program via Synaptic? It provides a graphical way to manipulate X settings. I used it to set up my dual monitors visually; it might help clarify things for you.

You might try switching "TwinViewOrientation."

---

### Post by hardyn on 2007-07-18
yeah... that is how i roughed out what i have,

I can get it to display fine with while in the gui... but a reboot will adopt the CRT as the default monitor

---

### Post by djgrandmarquis on 2007-07-18
Are you running the settings tool as root?

---

### Post by hardyn on 2007-07-18
yes

---

### Post by cprofitt on 2007-07-18
I am having the same issue...

Get it all setup with the Nvidia GUI -- save to the xorg.conf file (yes as root) -- then on reboot the main screen becomes the VGA LCD and not my DVI LCD.

the logon prompt and panels are all on the VGA LCD... I am researching the issue tonight and will post back here if I find any solutions via metacrawler.

---

### Post by djgrandmarquis on 2007-07-19
Sorry, I don't have much experience in troubleshooting this sort of thing.

I have Xinerama enabled... not sure if that's related to this situation.

Did you try defining Monitor1 and Monitor2 the opposite way? Perhaps the way the devices are initialized at boot time makes a difference somehow.

---

