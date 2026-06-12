---
title: "Problem with TV-out (nvidia)"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by markkun on 2007-02-28
I have problem getting anything out of my tv with my new Geforce 3 Titanium 200. The older Gforce 2 MX 400 or something worked fine, but not this one. Is the card broken or is it feisty's X that gives the troubles?

Here's what's the error that I have:

```
(--) NVIDIA(1): Connected display device(s) on GeForce3 Ti 200 at PCI:4:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(1):     Brooktree 871 TV Encoder (TV-0)
(--) NVIDIA(1): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): Brooktree 871 TV Encoder (TV-0): 165.0 MHz maximum pixel
(--) NVIDIA(1):     clock
(--) NVIDIA(1): TV encoder: Brooktree 871
[COLOR="Red"](WW) NVIDIA(1): There are only 1 CRTCs available, trimming display device list
(WW) NVIDIA(1):     from "TV-0" to "".[/COLOR]
(II) NVIDIA(1): Assigned Display Device:
(WW) NVIDIA(1): No valid modes for "800x600_60"; removing.
(WW) NVIDIA(1):
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1):
(WW) NVIDIA(1): No valid modes for "nvidia-auto-select"; removing.
(EE) NVIDIA(1): Unable to use default mode "nvidia-auto-select".

```

And here is my xorg.conf:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


Section "Module"
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	#Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "type1"
	Load "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection


Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection


Section "Device"
	Identifier "Device[0]"
	Driver "nvidia"
	BusID "PCI:4:0:0"
	screen 0
	Option "RenderAccel" "true"
	Option "AllowGLXWithComposite" "true"
	Option     "UseDisplayDevice"     "CRT-0"
EndSection


Section "Device"
	Driver "nvidia"
	Identifier "Device[1]"
	Screen 1
	Option "TVOutFormat" "SVIDEO" #or SVIDEO etc
	Option "TVStandard" "PAL-B" #or NTSC etc
	Option "ConnectedMonitor" "CRT,TV"
	BusID "PCI:4:0:0" #adjust using 'lspci' or cat /proc/pci
	Option     "UseDisplayDevice"     "TV-0"
	#Option "RenderAccel" "true"
	#Option "AllowGLXWithComposite" "true"
EndSection


Section "Monitor"
	Identifier "Monitor[0]" #CRT
	Option "DPMS"
EndSection


Section "Monitor"
	Identifier "Monitor[1]" #TV
	HorizSync 30-50
	VertRefresh 60
EndSection


Section "Screen"
	Identifier "Screen[0]"
	Device "Device[0]"
	Monitor "Monitor[0]"
	DefaultDepth 24
	SubSection "Display"
		Depth 1
		Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1600x1200" "1280x1024""1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Section "Screen"
	Device "Device[1]"
	Identifier "Screen[1]"
	Monitor "Monitor[1]"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "800x600_60"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier "Simple Layout"
	Screen 0 "Screen[0]"
	Screen 1 "Screen[1]" RightOf "Screen[0]"
	InputDevice "Configured Mouse" "CorePointer"
	InputDevice "Generic Keyboard" "CoreKeyboard"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

