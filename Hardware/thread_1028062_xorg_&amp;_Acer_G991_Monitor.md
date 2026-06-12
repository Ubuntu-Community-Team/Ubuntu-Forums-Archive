---
title: "xorg &amp; Acer G991 Monitor"
date: 2009-01-02
forum: Hardware
---

### Post by lillypilly on 2009-01-02
I am running 8.10 on a Intel 946GZ system with an Acer G991 19" monitor using the xserver-xorg-video-intel driver. 

On earlier versions of Ubuntu I was always able to select the Acer G991 monitor when I went into System Preferences Screen Resolution. Since installing 8.10 when I go in there it shows my monitor as being an Acer America 17".
The monitor displays the desktop background over the complete area but I cannot put any icons into the bottom 2" of the screen and anything running in maximise only uses the top 17" of the screen. If I unmaximise the screen I can drag the window down to the full screen size but if I maximise the window it reverts to the top again.
I have tried using a xorg.confg file several times but have found that to get the computer to run without bootup errors I have had to delete this file and currently do not have this file at all in the X11 directory.

Below is what I think is the relevant area of the xorg.0.log

 PCI:*(0@0:2:0) Intel Corporation 82946GZ/GL Integrated Graphics Controller rev 2, Mem @ 0x50100000/1048576, 0x40000000/268435456, I/O @ 0x000020e0/8
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Using default built-in configuration (48 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default intel Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (3)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (4)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices

Any suggestions would be appreciated

---

