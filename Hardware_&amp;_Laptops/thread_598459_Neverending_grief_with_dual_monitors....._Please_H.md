---
title: "Neverending grief with dual monitors..... Please Help!"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Irwin J. Finster on 2007-10-31
Hi,

I am read to start crying for after hours and hours I am unable to get my pc with two monitors to work. I have 2 PC's with two monitors and setting them up in linux has given me grief without end. So far the only distro that was able to get two monitors running out of the box was Mandriva Spring 2007. Even the new Mandriva 2008 can't do it anymore :(

Now I installed Gusty on my main PC, and thought I could easily configure my monitors with the new tool. I tried hundreds of times, but to no avail. Most of the time only one screen lights up with only part of the desktop showing, and I can scroll around it using my mouse :(

My actual setup is as folllows:

Main card: Nvidia Geforce 5900 XT AGP  attached to Samsung SyncMaster 997MB

Second card: Nvidia Geforce 2 MX PCI attached to Dell P793

I have attached my current xorg.conf, as well as the one that Mandrive Spring 2007 has created and which worked for me.

I have tried all I can think of with and without the nvidia driver, Maybe someone else can help me.

---

### Post by casperlingus on 2007-11-02
I apologize, I haven't glanced at your posted xorg.conf files (I am at work, and short on time).  I wanted to give you my xorg.conf which I use for not only dual monitors, but one of this is rotated.  

I believe you have to give up desktop effects, but I personally don't mind (disabling the "Composite" module with Xinerama disables compiz).


```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

[B]Section "Device"
	Identifier	"QuadroFX2500 0"
	Driver		"nvidia"
	Busid		 "PCI:1:0:0"
	Screen		1
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"UseDisplayDevice" "DFP-0"
EndSection

Section "Device"
	Identifier	"QuadroFX2500 1"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Screen		0
	Option		"NoLogo"	"True"
	Option		"UseDisplayDevice" "DFP-2"
EndSection

Section "Monitor"
	Identifier	"Monitor Laptop"
	Option		"DPMS"
	Horizsync	28-96
	Vertrefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Monitor 2407"
	Horizsync	46-81
	Vertrefresh	43-76
EndSection


Section "Screen"
	Identifier	"Screen0"
	Device		"QuadroFX2500 1"
	Monitor		"Monitor 2407"
	Option		"Rotate" "left"
	Defaultdepth	24
	SubSection "Display"
		Depth	16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"QuadroFX2500 0"
	Monitor		"Monitor Laptop"
	Defaultdepth	24
	SubSection "Display"
		Depth	16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"2-monitor layout"
	Screen 		0 "Screen0" 0 0
	Screen		1 "Screen1" RightOf "Screen0"

	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
	Option		"Xinerama" "On"
EndSection

Section "Extensions"
	Option		"Composite" "false"
EndSection
[/B]

Section "Module"
	Load		"glx"
EndSection
```

Note that I explicitly specify "UseDisplayDevice DFP-0" and "DFP-2".  Leave out these two lines until you explicitly decide you need them.  If your primary monitor ends up being incorrect, then search the file /var/log/Xorg.0.log for "DFP" and/or "CRT" to see which monitors were detected and the ports on which they are connected (see highlighted example below).  Both my displays are digital, so they are both DFP.  But if you are using an analog cable for either of your monitors, it will appear as CRT-0 or something like it.

```

...

	[32] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "Rotate" "left"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-2"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using static 90-degree counterclockwise screen rotation.
(II) NVIDIA(0): NVIDIA GPU Quadro FX 2500M (G71GL) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.16.16
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
[B](--) NVIDIA(0): Connected display device(s) on Quadro FX 2500M at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0):     DELL 2407WFP (DFP-2)
[/B](--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(0): DELL 2407WFP (DFP-2): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 2407WFP (DFP-2): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-2
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1200"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (93, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(II) NVIDIA(0): The RandR extension is not compatible with the Rotate option. 
(II) NVIDIA(0):     Disabling RandR.
(==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32

...
```

I spent a lot of grief getting this to work as well, so I hope sharing my experience with this benefits you.  Good luck.

-Casper

---

### Post by casperlingus on 2007-11-04
Sir, I just glanced at your Mandriva xorg.conf and notice you labeled both screens with the option "Screen   0".  This could be the source of the problem.  Your primary monitor should be 0 the other one should be 1.

---

