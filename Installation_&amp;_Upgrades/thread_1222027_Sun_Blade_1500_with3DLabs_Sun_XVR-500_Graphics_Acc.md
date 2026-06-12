---
title: "Sun Blade 1500 with3DLabs Sun XVR-500 Graphics Accelerator Xorg Configuration"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by minds on 2009-07-24
Hello all,

I have just installed Gutsy on a sun blade, but can't seem to get Gnome or KDE running. I'm pretty new to Linux and could be missing something obvious. I think there is a problem with my video driver and xorg.conf file. When I try to start xorg this is the output:
```
root@comp:# X

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.4)
Current Operating System: Linux digilab7 2.6.22-14-sparc64 #1 Sun Oct 14 21:57:46 GMT 2007 sparc64
Build Date: 13 June 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 24 11:33:14 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found

```

Here is the relevant part of my xorg.conf file:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sunffb"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

```

Here is the tail of the Xorg.0.log file as well:
```
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "sunffb"
(II) Loading /usr/lib/xorg/modules/drivers//sunffb_drv.so
(II) Module sunffb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) SUNFFB: driver for Creator, Creator 3D and Elite 3D
(EE) No devices detected.

Fatal server error:
no screens found

```

I've read some other posts that suggest there may not be a proper driver for the XVR-500, so I tried vga and vsa, but I get similar output when I try these - no screens found. Perhaps I am not specifying the video card correctly in the xorg.conf file? 

Thanks in advance.

---

