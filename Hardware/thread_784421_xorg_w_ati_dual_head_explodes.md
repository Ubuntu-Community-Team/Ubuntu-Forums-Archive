---
title: "xorg w/ ati dual head explodes"
date: 2008-05-06
forum: Hardware
---

### Post by zoinksbob on 2008-05-06
I am trying to set up my dual-head displays in 8.04.  My first vid card is an nVidia, and my second is an ATI.  Ubuntu auto-detected the nVidia just fine, and I installed with no trouble.  Then the GNOME display config tool didn't see my ATI card, so I tried to edit the xorg.conf file manually.  My edits cause xorg to crash with "signal 11," whatever that is.  The exact same xorg.conf works find under Fedora 8, so I know there are no syntax errors.  Below are my xorg.conf and the tail of the X log file.  I'm guessing this is a bug in the ATI drivers.  Any suggestions?

xorg.conf:

# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" LeftOf "Screen0"
	Option	    "Xinerama" "on"
	Option	    "Clone" "off"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "SNY"
	ModelName    "CPD-E540"
	HorizSync    31.0 - 128.0
	VertRefresh  85.0 - 85.0
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "SyncMaster"
	HorizSync    30.0 - 80.0
	VertRefresh  60.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 7300 GS"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "radeon"
	VendorName  "Videocard Vendor"
	BoardName   "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	BusID       "PCI:6:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Modes    "1600x1200"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



log file:
Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f5ebbe15100]
2: /usr/bin/X11/X(RRCrtcSetRotations+0) [0x51c180]
3: /usr/bin/X11/X(xf86RandR12SetRotations+0x74) [0x4b3e24]
4: /usr/bin/X11/X(xf86CrtcScreenInit+0xa3) [0x4af7c3]
5: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONScreenInit+0x110c) [0x7f5eb95f888c]
6: /usr/bin/X11/X(AddScreen+0x238) [0x436208]
7: /usr/bin/X11/X(InitOutput+0x266) [0x469006]
8: /usr/bin/X11/X(main+0x29f) [0x4369bf]
9: /lib/libc.so.6(__libc_start_main+0xf4) [0x7f5ebbe011c4]
10: /usr/bin/X11/X(FontFileCompleteXLFD+0x279) [0x435ed9]

Fatal server error:
Caught signal 11.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
disable montype: 1
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xffff0000 0xe3ffe000
(II) RADEON(1):   MC_AGP_LOCATION  : 0x003fffc0
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV

---

