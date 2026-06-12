---
title: "Unusual Dual Monitor Woes - Dell Precision M90"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by casperlingus on 2007-05-01
Laptop:  Dell Precision M90
Video Card:  Nvidia Quadro FX 2500
Monitor #2:  Dell 2407WFP

I've done a bit of research to get as far as I have, and the problem appears to not be documented anywhere else.  Simply put, my laptop sees the 2nd monitor, it thinks it's there, and it thinks it's talking to it--of course, though, it is not.   My xorg.conf was carefully constructed, and Xorg.log.0 insists that the monitor was detected and is being used.  However, the 2nd monitor remains in powersave mode, not even pretending to be receiving a signal.

I can use the CRT cable, and change DFP-1 to CRT-0 in my xorg.conf and the dual monitor setup works.  I've also tried a similar setup at home (currently at work), and found similar results--the laptop **thinks** the second DFP device is there, but doesn't talk to it.  It seems that somehow Linux can read information from the DFP-1 connection, but it can't send anything on it.

This might be a video card issue, because I have dual-monitors setup in Windows all the time (both DFP), no problem.  It's more likely a driver issue.  The video card was actually just replaced and I have the same problem.    Has anyone ever heard of this?  Any fixes?

I posted the relevant sections of xorg.conf and Xorg.log.0 below

xorg.conf:
```

Section "Device"
	Identifier	"QuadroFX2500 0"
	Driver		"nvidia"
	Busid		   "PCI:1:0:0"
   Screen      0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
   **Option      "UseDisplayDevice" "DFP-0"**
EndSection

Section "Device"
	Identifier	"QuadroFX2500 1"
	Driver		"nvidia"
	Busid		   "PCI:1:0:0"
   Screen      1
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
   #Option      "UseDisplayDevice" "CRT-0"
   **Option      "UseDisplayDevice" "DFP-1"**
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
   Device      "QuadroFX2500 0"
   Monitor     "Monitor Laptop"
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
   Device      "QuadroFX2500 1"
   Monitor     "Monitor 2407"
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
   Identifier "2-monitor layout"
   Screen     0 "Screen0" 0 0
   Screen     1 "Screen1" LeftOf "Screen0"

	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
   Option "Xinerama" "On"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Xorg.log.0
```

(==) Log file: "/var/log/Xorg.0.log", Time: Tue May  1 10:32:33 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "2-monitor layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor Laptop"
(**) |   |-->Device "QuadroFX2500 0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor 2407"
(**) |   |-->Device "QuadroFX2500 1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"

...

(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "On"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)

...

(--) PCI:*(1:0:0) nVidia Corporation G71 [Quadro FX 2500M] rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xde000000/24, I/O @ 0xef00/7, BIOS @ 0xdfe00000/17

...

(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found

...

(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro FX 2500M at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.16.16
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro FX 2500M at [b]PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0):     DELL 2407WFP (DFP-1) [/b]
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(0): DELL 2407WFP (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 2407WFP (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1200"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (131, 132); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "NoLogo" "True"
(**) NVIDIA(1): Option "UseDisplayDevice" "DFP-1"
(**) NVIDIA(1): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU Quadro FX 2500M at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 05.71.22.16.16
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on Quadro FX 2500M at [b]PCI:1:0:0:
(--) NVIDIA(1):     Seiko (DFP-0)
(--) NVIDIA(1):     DELL 2407WFP (DFP-1)[/b]
(--) NVIDIA(1): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): Seiko (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(1): DELL 2407WFP (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(1): DELL 2407WFP (DFP-1): Internal Single Link TMDS
(II) NVIDIA(1): Assigned Display Device: DFP-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1920x1200"
(II) NVIDIA(1): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(1): DPI set to (93, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
(WW) NVIDIA(1): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(1):     UBB.
(--) Depth 24 pixmap format is 32 bpp

```

---

### Post by casperlingus on 2007-05-07
BUMP!

Has no one ever tried running Ubuntu/Linux with an Nvidia Quadro FX 2500 card???  There's gotta be a reason that Windows can use the DVI output and Linux can't... perhaps the linux NVIDIA drivers don't completely encompass my video card...

---

### Post by casperlingus on 2007-05-08
I finally went to the nvidia-linux forum and posted my question there.  It turns out that the default nvidia drivers for Ubuntu do not *officially* support my graphics card, but the newest one does support it (v 1.0-9755).  I went and installed it from nvidia website.  The install was flawless, and upon restarting X, I noticed that something had changed in Xorg.log.0

most notably, was the following couple lines:

```
(--) NVIDIA(0): Connected display device(s) on Quadro FX 2500M at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0):     DELL 2407WFP **(DFP-1)**
```
was now replaced with 
```
(--) NVIDIA(0): Connected display device(s) on Quadro FX 2500M at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0):     DELL 2407WFP **(DFP-2)**
```

...?!   I respecified "UseDisplayDevice" in my xorg.conf and it works!  I'm not positive I needed the new driver to to do this, because the old Xorg.log.0 **did** mentioned that DFP-2 was an available video out device (but I didn't try it because it detected the monitor on DFP-1).  Perhaps adding the line:  "UseDisplayDevice" "DFP-2" in my xorg.conf would've fixed it.

-----------------------------------------------------------------

Now my problem is that that when I reboot, X fails to start with the message:

```
API mismatch: the NVIDIA kernel module has version 1.0-7184, but this X module has the version 1.0-9755
```

I tried 
1) uninstalling the new drivers 
2) reinstalling the old drivers, 
3) uninstalling the old drivers with the --purge command, 
4) then reinstalling the new drivers

This did not solve the problem.  Upon reboot X fails to start and then sends me to a terminal.  If I remove and reinsert the nvidia modules I can startx successfully (that's how I'm posting now).  
```
startx      #ERROR
sudo rmmod nvidia
sudo modprobe nvidia
startx      #SUCCESSFUL
```
I can see the problem clearly, I just don't know how to fix it so that X will not try to load the old nvidia module on boot.

-Casper

---

### Post by volyblmn on 2007-08-31
Hi, I'm not sure if you've already found a solution but I tried this and it worked flawlessly.  Just follow the instructions and then download/install the latest 100.xxxx drivers from nVidia.  I'm using an M90 with a Quadro FX 2500 and Dell 2407WFP too...

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

