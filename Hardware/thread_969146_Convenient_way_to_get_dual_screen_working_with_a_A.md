---
title: "Convenient way to get dual screen working with a ATI-based laptop running fglrx ?"
date: 2008-11-03
forum: Hardware
---

### Post by aurelieng on 2008-11-03
Hi all,

I am in front of a Lenovo Thinkpad T60P with an ATI card (Mobility FireGL V5250, fglrx driver), and would like to be able to use an external monitor from time to time, without having to restart X.

Unfortunately, I cannot setup properly the two monitors (the built-in 1680x1050 and a Dell E248WFP 1920x1200) using the System Settings/Monitor and Display tool of Kubuntu 8.04. The two resolutions are either not available or not working as expected (shifted picture and/or wrong aspect ratio), and a combersome X restart is needed each time something is changed.

I'm usually working with nvidia-based laptops, and nvidia-settings usually does a very good job in setting up and using an external monitor. Thus, I wonder if there is a similar tool for ATI graphic cards ? Or, is there something else I should try ?

Thanks !

Aurelien.


Graphic card details:
```
1:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250] (prog-if 00 [VGA controller])
       Subsystem: Lenovo Unknown device 20a4
       Flags: bus master, fast devsel, latency 0, IRQ 16
       Memory at d0000000 (32-bit, prefetchable) [size=256M]
       I/O ports at 2000 [size=256]
       Memory at ee100000 (32-bit, non-prefetchable) [size=64K]
       [virtual] Expansion ROM at ee120000 [disabled] [size=128K]
       Capabilities: <access denied>

```

---

### Post by CorporateGoth on 2008-11-03
Indeed there is, the ATI Catalyst Control Center, you should have it if you have the restricted driver installed.

FYI, I have a T60p (15", 1600x1200 res), with an external monitor when docked (also 1600x1200).  Here is my X config under 8.10:

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "EnableMonitor" "lvds,tmds1"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"

		#		Viewport	0 0
		#		Virtual		1600 1200
		Modes    "1600x1200"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

I'll leave modifying it to suit your needs as an exercise for the reader.

Alternatively, use the 'aticonfig' command-line tool, it will also do the trick.

---

### Post by aurelieng on 2008-11-03
Well... I do not see an external screen in your /etc/X11/xorg.conf. Is it managed somewhat dynamically with the ATI Catalyst Control Center ?

Anyway, I tried the ATI Catalyst Control Center with the default xorg.conf, and does not work very well: the external screen does not seem to be detected, and if it is activated anyway (strange that one can activate sth that cannot be detected), it displays the wrong resolution, the wrong aspect ratio, or the two combined.

Aticonfig is also not as straightforward as I expected. It seems that it can generate xorg.conf files, but if it is true, you have to restart X each time you plug/unplug your monitor ?

Strange and sad too see such a bad support on this monitor/laptop combination.

---

