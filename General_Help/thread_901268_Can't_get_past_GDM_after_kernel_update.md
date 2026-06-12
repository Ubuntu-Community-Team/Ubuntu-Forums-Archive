---
title: "Can't get past GDM after kernel update"
date: 2008-08-26
forum: General Help
---

### Post by sjmacewan on 2008-08-26
Howdy,
I'm quite new to Ubuntu really, so you'll have to tell me what log files you need to see if it'll help.

Everything was running well on my Everex gBook until this morning when I installed a new kernel update. Now, when I try to log in using 2.6.24-19-generic I get to the GDM login, type in my username and password, it goes to a black screen (the last black screen seen before the login comes up) and then just reloads the GDM login. I never get to my desktop!

I can successfully login if I use a failsafe gnome session, or if I use an older kernel (2.6.24-18-generic)

Any ideas on what could be causing this?

Many thanks,
Sjmacewan

---

### Post by regala on 2008-08-26
> **sjmacewan said:**
> Howdy,
I'm quite new to Ubuntu really, so you'll have to tell me what log files you need to see if it'll help.

Everything was running well on my Everex gBook until this morning when I installed a new kernel update. Now, when I try to log in using 2.6.24-19-generic I get to the GDM login, type in my username and password, it goes to a black screen (the last black screen seen before the login comes up) and then just reloads the GDM login. I never get to my desktop!

I can successfully login if I use a failsafe gnome session, or if I use an older kernel (2.6.24-18-generic)

Any ideas on what could be causing this?

Many thanks,
Sjmacewan


Okay, now, we're gonna need some more informations.
What kind of video card do you use ? Can you show the content of /var/log/Xorg.0.log ?
(just log into your system on a terminal console with Ctrl+Alt+F1)

---

### Post by sjmacewan on 2008-08-26
Hi,
Sorry about this, I've been pretty frusterated with this machine.

The video card in an onboard Via chrome9hc igp...always problematic. I was using the beta drivers for it since they've been solving some ongoing problems.

Anyways, what I've done for now is a dpkg-reconfigure xserver-xorg

Since i've done that, am I right in assuming that the xorg logfile won't have the info you would have wanted? If not, no worries. I'm thinking I'll just sit tight on the settings that the reconfig used. I tried isolated the problem by comparing the new xorg to the old one, and it's the usage of the via drivers that's causing the problem.

Thanks for your reply though, I hate making threads only to 'solve' them before people help...sorry!

---

### Post by sjmacewan on 2008-08-26
Ok, nevermind, I need help!
the dpkg config was just not cutting it, so here's the xorg log (the right one)

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Scottop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 26 13:11:34 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0364 card 1106,0364 rev 80 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5364 card 0000,0000 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:6: chip 1106,6364 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:7: chip 1106,7364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1106,a364 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 1106,c364 card 0000,0000 rev 80 class 06,04,00 hdr 81
(II) PCI: 00:0f:0: chip 1106,0591 card 1509,1e90 rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1509,1e90 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1509,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1509,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1509,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3337 card 1734,10cb rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:7: chip 1106,287e card 1106,337e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1509,1e20 rev 7c class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,337b card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:13:1: chip 1106,337a card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 01:00:0: chip 1106,3371 card 1509,1e30 rev 01 class 03,00,00 hdr 00
(II) PCI: 04:01:0: chip 1106,3288 card 1e40,1509 rev 10 class 04,03,00 hdr 00
(II) PCI: 05:01:0: chip 168c,001a card 168c,2052 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:19:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xc9100000 - 0xc91fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:19:1), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xc9000000 - 0xc90fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3371) rev 1, Mem @ 0xa0000000/29, 0xc8000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xc7ffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc9000000 - 0xc900ffff (0x10000) MX[B]
	[1] -1	0	0xc9100000 - 0xc9103fff (0x4000) MX[B]
	[2] -1	0	0xc9400400 - 0xc94004ff (0x100) MX[B]
	[3] -1	0	0xc9400000 - 0xc94000ff (0x100) MX[B]
	[4] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[6] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[7] -1	0	0x00004c60 - 0x00004c7f (0x20) IX[B]
	[8] -1	0	0x00004c40 - 0x00004c5f (0x20) IX[B]
	[9] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[10] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[11] -1	0	0x00004c90 - 0x00004c9f (0x10) IX[B]
	[12] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[13] -1	0	0x00004c80 - 0x00004c8f (0x10) IX[B]
	[14] -1	0	0x00004ca0 - 0x00004ca3 (0x4) IX[B]
	[15] -1	0	0x00004ca8 - 0x00004caf (0x8) IX[B]
	[16] -1	0	0x00004ca4 - 0x00004ca7 (0x4) IX[B]
	[17] -1	0	0x00004cb0 - 0x00004cb7 (0x8) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc9000000 - 0xc900ffff (0x10000) MX[B]
	[1] -1	0	0xc9100000 - 0xc9103fff (0x4000) MX[B]
	[2] -1	0	0xc9400400 - 0xc94004ff (0x100) MX[B]
	[3] -1	0	0xc9400000 - 0xc94000ff (0x100) MX[B]
	[4] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[6] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[7] -1	0	0x00004c60 - 0x00004c7f (0x20) IX[B]
	[8] -1	0	0x00004c40 - 0x00004c5f (0x20) IX[B]
	[9] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[10] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[11] -1	0	0x00004c90 - 0x00004c9f (0x10) IX[B]
	[12] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[13] -1	0	0x00004c80 - 0x00004c8f (0x10) IX[B]
	[14] -1	0	0x00004ca0 - 0x00004ca3 (0x4) IX[B]
	[15] -1	0	0x00004ca8 - 0x00004caf (0x8) IX[B]
	[16] -1	0	0x00004ca4 - 0x00004ca7 (0x4) IX[B]
	[17] -1	0	0x00004cb0 - 0x00004cb7 (0x8) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc9000000 - 0xc900ffff (0x10000) MX[B]
	[5] -1	0	0xc9100000 - 0xc9103fff (0x4000) MX[B]
	[6] -1	0	0xc9400400 - 0xc94004ff (0x100) MX[B]
	[7] -1	0	0xc9400000 - 0xc94000ff (0x100) MX[B]
	[8] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[14] -1	0	0x00004c60 - 0x00004c7f (0x20) IX[B]
	[15] -1	0	0x00004c40 - 0x00004c5f (0x20) IX[B]
	[16] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[17] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[18] -1	0	0x00004c90 - 0x00004c9f (0x10) IX[B]
	[19] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[20] -1	0	0x00004c80 - 0x00004c8f (0x10) IX[B]
	[21] -1	0	0x00004ca0 - 0x00004ca3 (0x4) IX[B]
	[22] -1	0	0x00004ca8 - 0x00004caf (0x8) IX[B]
	[23] -1	0	0x00004ca4 - 0x00004ca7 (0x4) IX[B]
	[24] -1	0	0x00004cb0 - 0x00004cb7 (0x8) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 4.1.79
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) via: driver for VIA chipsets: CLE266, KM400/KN400, K8M800/K8N800,
	PM800/PM880/CN400, P4M800PRO, CX700, K8M890, P4M890, CN750, P4M900,
	VX800
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset P4M900 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc9000000 - 0xc900ffff (0x10000) MX[B]
	[5] -1	0	0xc9100000 - 0xc9103fff (0x4000) MX[B]
	[6] -1	0	0xc9400400 - 0xc94004ff (0x100) MX[B]
	[7] -1	0	0xc9400000 - 0xc94000ff (0x100) MX[B]
	[8] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[14] -1	0	0x00004c60 - 0x00004c7f (0x20) IX[B]
	[15] -1	0	0x00004c40 - 0x00004c5f (0x20) IX[B]
	[16] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[17] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[18] -1	0	0x00004c90 - 0x00004c9f (0x10) IX[B]
	[19] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[20] -1	0	0x00004c80 - 0x00004c8f (0x10) IX[B]
	[21] -1	0	0x00004ca0 - 0x00004ca3 (0x4) IX[B]
	[22] -1	0	0x00004ca8 - 0x00004caf (0x8) IX[B]
	[23] -1	0	0x00004ca4 - 0x00004ca7 (0x4) IX[B]
	[24] -1	0	0x00004cb0 - 0x00004cb7 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc9000000 - 0xc900ffff (0x10000) MX[B]
	[5] -1	0	0xc9100000 - 0xc9103fff (0x4000) MX[B]
	[6] -1	0	0xc9400400 - 0xc94004ff (0x100) MX[B]
	[7] -1	0	0xc9400000 - 0xc94000ff (0x100) MX[B]
	[8] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[17] -1	0	0x00004c60 - 0x00004c7f (0x20) IX[B]
	[18] -1	0	0x00004c40 - 0x00004c5f (0x20) IX[B]
	[19] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[20] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[21] -1	0	0x00004c90 - 0x00004c9f (0x10) IX[B]
	[22] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[23] -1	0	0x00004c80 - 0x00004c8f (0x10) IX[B]
	[24] -1	0	0x00004ca0 - 0x00004ca3 (0x4) IX[B]
	[25] -1	0	0x00004ca8 - 0x00004caf (0x8) IX[B]
	[26] -1	0	0x00004ca4 - 0x00004ca7 (0x4) IX[B]
	[27] -1	0	0x00004cb0 - 0x00004cb7 (0x8) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(==) VIA(0): Depth 24, (==) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VIA(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 131072 kB
(II) VIA(0): VESA VBE OEM: VIA N3364


(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(II) VIA(0): MapBase = b7901000, MmioBase=c8000000
(II) VIA(0): RegCR08 = 0, RegCR09=4f
(--) VIA(0): Chipset: "P4M900"
(--) VIA(0): Chipset Rev.: 0
(**) VIA(0): Option "PanelID" "19"
(==) VIA(0): Not using video BIOS to set modes
(II) VIA(0): MergedFB mode forced off.
(**) VIA(0): (OPTION) LCD Panel ID is 19.
(**) VIA(0): TV scan mode is 0
(**) VIA(0): Option: Cap0 auto detect= 0
(**) VIA(0): Option: Cap1 auto detect= 0
(**) VIA(0): Option: Cap0_FieldSwap Disabled
(**) VIA(0): Option: Cap0_HFilter Enabled
(**) VIA(0): Option: Cap1_HFilter Enabled
(**) VIA(0): Option: Capture Over Scan ON
(**) VIA(0): Option: HQV Filter Manual Select Disabled
(**) VIA(0): Option: Set MPEG decode frame buffer number Disable
(**) VIA(0): Option: Capture 1 use H/W auto flip
(**) VIA(0): Option: Capture 0 use V1 engine : Default path
(**) VIA(0): Option: HQV Manual Switch Disabled
(**) VIA(0): Option: No mpeg add one line on bottom = 0
(**) VIA(0): Option: DeBlocking Disable!!
(**) VIA(0): DeBlocking Minimum Width Default : 320
(**) VIA(0): DeBlocking Minimum Height Default: 240
(**) VIA(0): Option: Use 2D BitBlt method to write event-tag into VQ and make sure MPEG decode END Disable
(--) VIA(0): mapping MMIO @ 0xc8000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xc8200000 with size 0x200000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  131072k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VIA(0): VESA VBE DDC supported
(II) VIA(0): VESA VBE DDC Level 2
(II) VIA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VIA(0): VESA VBE DDC read failed
(II) VIA(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 1:ddc2" removed.
(--) VIA(0): No DDC signal
(--) VIA(0): Max Monitor H Size =  1024
(--) VIA(0): Max Monitor V Size =  768
(II) VIA(0): Monitor: Using hsync range of 30.00-113.00 kHz
(II) VIA(0): Monitor: Using vrefresh range of 50.00-100.00 Hz
(II) VIA(0): Clock range:  20.00 to 270.00 MHz
(II) VIA(0): Not using mode "1440x1050" (height too large for virtual size)
(II) VIA(0): Not using mode "1600x900" (width too large for virtual size)
(II) VIA(0): Not using mode "1600x1024" (width too large for virtual size)
(II) VIA(0): Not using mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using mode "1856x1392" (width too large for virtual size)
(II) VIA(0): Not using mode "1920x1080" (width too large for virtual size)
(II) VIA(0): Not using mode "2048x1536" (width too large for virtual size)
(II) VIA(0): Not using mode "1440x1050" (height too large for virtual size)
(II) VIA(0): Not using mode "1440x1050" (height too large for virtual size)
(II) VIA(0): Not using default mode "640x350" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (height too large for virtual size)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "832x624" (horizontal timing out of range)
(II) VIA(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1440x1050" (height too large for virtual size)
(II) VIA(0): Not using default mode "1600x900" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(**) VIA(0): Virtual size is 1440x900 (pitch 1440)
(**) VIA(0): *Mode "1440x900": 106.5 MHz, 55.9 kHz, 60.0 Hz
(II) VIA(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(**) VIA(0):  Default mode "1440x900": 106.5 MHz, 55.9 kHz, 60.0 Hz
(II) VIA(0): Modeline "1440x900"x60.0  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync (55.9 kHz)
(**) VIA(0):  Mode "1366x768": 85.9 MHz, 47.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1366x768"x60.0   85.86  1366 1440 1584 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
(**) VIA(0):  Default mode "1366x768": 85.9 MHz, 47.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1366x768"x60.0   85.86  1366 1440 1584 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
(**) VIA(0):  Mode "1360x768": 85.5 MHz, 49.0 kHz, 60.7 Hz
(II) VIA(0): Modeline "1360x768"x60.7   85.50  1360 1392 1712 1744  768 783 791 807 +hsync +vsync (49.0 kHz)
(**) VIA(0):  Default mode "1360x768": 85.5 MHz, 49.0 kHz, 60.7 Hz
(II) VIA(0): Modeline "1360x768"x60.7   85.50  1360 1392 1712 1744  768 783 791 807 +hsync +vsync (49.0 kHz)
(**) VIA(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(**) VIA(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) VIA(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(**) VIA(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) VIA(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) VIA(0):  Mode "1280x768": 118.5 MHz, 68.6 kHz, 85.0 Hz
(II) VIA(0): Modeline "1280x768"x85.0  118.50  1280 1368 1504 1728  768 769 772 807 (68.6 kHz)
(**) VIA(0):  Mode "1280x768": 103.0 MHz, 60.2 kHz, 75.0 Hz
(II) VIA(0): Modeline "1280x768"x75.0  103.00  1280 1360 1496 1712  768 769 772 802 (60.2 kHz)
(**) VIA(0):  Mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x768"x60.0   80.10  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) VIA(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x768"x60.0   80.10  1280 1344 1480 1680  768 769 772 795 -hsync +vsync (47.7 kHz)
(**) VIA(0):  Mode "1280x720": 74.6 MHz, 44.2 kHz, 59.2 Hz
(II) VIA(0): Modeline "1280x720"x59.2   74.60  1280 1341 1474 1688  720 721 724 746 (44.2 kHz)
(**) VIA(0):  Default mode "1280x720": 74.6 MHz, 44.2 kHz, 59.2 Hz
(II) VIA(0): Modeline "1280x720"x59.2   74.60  1280 1341 1474 1688  720 721 724 746 -hsync +vsync (44.2 kHz)
(**) VIA(0):  Mode "1200x720": 70.2 MHz, 44.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "1200x720"x60.0   70.18  1200 1256 1384 1568  720 721 724 746 -hsync +vsync (44.8 kHz)
(**) VIA(0):  Default mode "1200x720": 70.2 MHz, 44.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "1200x720"x60.0   70.18  1200 1256 1384 1568  720 721 724 746 -hsync +vsync (44.8 kHz)
(**) VIA(0):  Mode "1152x720": 67.3 MHz, 44.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
(**) VIA(0):  Default mode "1152x720": 67.3 MHz, 44.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
(**) VIA(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) VIA(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) VIA(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) VIA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) VIA(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) VIA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) VIA(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) VIA(0):  Mode "1280x600": 61.5 MHz, 37.3 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x600"x60.0   61.50  1280 1336 1464 1648  600 601 604 622 -hsync +vsync (37.3 kHz)
(**) VIA(0):  Default mode "1280x600": 61.5 MHz, 37.3 kHz, 60.0 Hz
(II) VIA(0): Modeline "1280x600"x60.0   61.50  1280 1336 1464 1648  600 601 604 622 -hsync +vsync (37.3 kHz)
(**) VIA(0):  Mode "1088x612": 53.0 MHz, 38.0 kHz, 60.0 Hz
(II) VIA(0): Modeline "1088x612"x60.0   52.95  1088 1128 1240 1392  612 613 616 634 -hsync +vsync (38.0 kHz)
(**) VIA(0):  Default mode "1088x612": 53.0 MHz, 38.0 kHz, 60.0 Hz
(II) VIA(0): Modeline "1088x612"x60.0   52.95  1088 1128 1240 1392  612 613 616 634 -hsync +vsync (38.0 kHz)
(**) VIA(0):  Default mode "1024x600": 49.0 MHz, 37.3 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x600"x60.0   48.96  1024 1064 1168 1312  600 601 604 622 -hsync +vsync (37.3 kHz)
(**) VIA(0):  Mode "1000x600": 48.1 MHz, 37.3 kHz, 60.0 Hz
(II) VIA(0): Modeline "1000x600"x60.0   48.07  1000 1040 1144 1288  600 601 604 622 -hsync +vsync (37.3 kHz)
(**) VIA(0):  Default mode "1000x600": 48.1 MHz, 37.3 kHz, 60.0 Hz
(II) VIA(0): Modeline "1000x600"x60.0   48.07  1000 1040 1144 1288  600 601 604 622 -hsync +vsync (37.3 kHz)
(**) VIA(0):  Mode "960x600": 46.0 MHz, 37.3 kHz, 60.0 Hz
(II) VIA(0): Modeline "960x600"x60.0   45.98  960 1000 1096 1232  600 601 604 622 -hsync +vsync (37.3 kHz)
(**) VIA(0):  Default mode "960x600": 46.0 MHz, 37.3 kHz, 60.0 Hz
(II) VIA(0): Modeline "960x600"x60.0   45.98  960 1000 1096 1232  600 601 604 622 -hsync +vsync (37.3 kHz)
(**) VIA(0):  Mode "1024x512": 53.3 MHz, 40.1 kHz, 75.0 Hz
(II) VIA(0): Modeline "1024x512"x75.0   53.30  1024 1072 1176 1328  512 513 516 535 (40.1 kHz)
(**) VIA(0):  Mode "1024x512": 41.3 MHz, 31.9 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x512"x60.0   41.30  1024 1056 1160 1296  512 513 516 531 (31.9 kHz)
(**) VIA(0):  Default mode "1024x512": 41.3 MHz, 31.9 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x512"x60.0   41.30  1024 1056 1160 1296  512 513 516 531 -hsync +vsync (31.9 kHz)
(**) VIA(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) VIA(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) VIA(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) VIA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) VIA(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) VIA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) VIA(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) VIA(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) VIA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) VIA(0):  Mode "720x576": 42.6 MHz, 45.1 kHz, 75.0 Hz
(II) VIA(0): Modeline "720x576"x75.0   42.60  720 760 832 944  576 577 580 602 (45.1 kHz)
(**) VIA(0):  Mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) VIA(0): Modeline "720x576"x60.1   32.70  720 744 816 912  576 577 580 597 (35.9 kHz)
(**) VIA(0):  Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) VIA(0): Modeline "720x576"x60.1   32.70  720 744 816 912  576 577 580 597 -hsync +vsync (35.9 kHz)
(**) VIA(0):  Mode "856x480": 41.3 MHz, 37.7 kHz, 75.1 Hz
(II) VIA(0): Modeline "856x480"x75.1   41.30  856 888 976 1096  480 481 484 502 (37.7 kHz)
(**) VIA(0):  Mode "856x480": 31.7 MHz, 29.8 kHz, 59.9 Hz
(II) VIA(0): Modeline "856x480"x59.9   31.70  856 872 960 1064  480 481 484 497 (29.8 kHz)
(**) VIA(0):  Default mode "856x480": 31.7 MHz, 29.8 kHz, 59.9 Hz
(II) VIA(0): Modeline "856x480"x59.9   31.70  856 872 960 1064  480 481 484 497 -hsync +vsync (29.8 kHz)
(**) VIA(0):  Mode "848x480": 47.4 MHz, 42.9 kHz, 85.0 Hz
(II) VIA(0): Modeline "848x480"x85.0   47.40  848 888 976 1104  480 481 484 505 (42.9 kHz)
(**) VIA(0):  Mode "848x480": 41.0 MHz, 37.7 kHz, 75.1 Hz
(II) VIA(0): Modeline "848x480"x75.1   41.00  848 880 968 1088  480 481 484 502 (37.7 kHz)
(**) VIA(0):  Mode "848x480": 31.5 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "848x480"x60.0   31.50  848 864 952 1056  480 481 484 497 (29.8 kHz)
(**) VIA(0):  Default mode "848x480": 31.5 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "848x480"x60.0   31.50  848 864 952 1056  480 481 484 497 -hsync +vsync (29.8 kHz)
(**) VIA(0):  Default mode "800x480": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x480"x60.3   40.00  800 832 960 1056  480 541 545 628 -hsync +vsync (37.9 kHz)
(**) VIA(0):  Mode "800x480": 29.6 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "800x480"x60.0   29.58  800 816 896 992  480 481 484 497 (29.8 kHz)
(**) VIA(0):  Mode "720x480": 34.9 MHz, 37.6 kHz, 74.9 Hz
(II) VIA(0): Modeline "720x480"x74.9   34.90  720 752 824 928  480 481 484 502 (37.6 kHz)
(**) VIA(0):  Mode "720x480": 26.7 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "720x480"x60.0   26.70  720 736 808 896  480 481 484 497 (29.8 kHz)
(**) VIA(0):  Default mode "720x480": 26.7 MHz, 29.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "720x480"x60.0   26.70  720 736 808 896  480 481 484 497 -hsync +vsync (29.8 kHz)
(**) VIA(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) VIA(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) VIA(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) VIA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) VIA(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) VIA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) VIA(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) VIA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) VIA(0):  Default mode "480x640": 24.8 MHz, 39.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "480x640"x60.0   24.82  480 504 552 624  640 641 644 663 -hsync +vsync (39.8 kHz)
(==) VIA(0): DPI set to (96, 96)
(**) VIA(0): disable DVI Display SW scaling, It isn't HDMI
(II) VIA(0): VIASetDisplayPath is Single
(II) VIA(0): Active Device is 0x2
(II) VIA(0): IGA: CRT=1, TV=1, DFP=1, LCD=2
(II) VIALoadVideoOption
(WW) No Video option file .VIAVIDEORC exist. 
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc8000000 - 0xc8ffffff (0x1000000) MS[B]
	[1] 0	0	0xa0000000 - 0xbfffffff (0x20000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc9000000 - 0xc900ffff (0x10000) MX[B]
	[7] -1	0	0xc9100000 - 0xc9103fff (0x4000) MX[B]
	[8] -1	0	0xc9400400 - 0xc94004ff (0x100) MX[B]
	[9] -1	0	0xc9400000 - 0xc94000ff (0x100) MX[B]
	[10] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xa0000000 - 0xbfffffff (0x20000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[19] -1	0	0x00004c60 - 0x00004c7f (0x20) IX[B]
	[20] -1	0	0x00004c40 - 0x00004c5f (0x20) IX[B]
	[21] -1	0	0x00004c20 - 0x00004c3f (0x20) IX[B]
	[22] -1	0	0x00004c00 - 0x00004c1f (0x20) IX[B]
	[23] -1	0	0x00004c90 - 0x00004c9f (0x10) IX[B]
	[24] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[25] -1	0	0x00004c80 - 0x00004c8f (0x10) IX[B]
	[26] -1	0	0x00004ca0 - 0x00004ca3 (0x4) IX[B]
	[27] -1	0	0x00004ca8 - 0x00004caf (0x8) IX[B]
	[28] -1	0	0x00004ca4 - 0x00004ca7 (0x4) IX[B]
	[29] -1	0	0x00004cb0 - 0x00004cb7 (0x8) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(--) VIA(0): mapping framebuffer @ 0xa0000000 with size 0x8000000
(==) VIA(0): Write-combining range (0xa0000000,0x8000000)
(--) VIA(0): Frame buffer start: 0xaf67c000, free start: 0x4f1a00 end: 0x8000000
(--) VIA(0): mapping MMIO @ 0xc8000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xc8200000 with size 0x200000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(EE) VIA(0):  Couldn't open "/dev/video2"
(II) VIA(0): VIAScreenInit : V4L Disabled : fd2 = -1 
(II) VIA(0): [drm] Detect H5s1 chipset: 000a  chipid: 3371
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "via_chrome9"
(EE) [drm] drmOpen failed.
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): VIASetDisplayPath is Single
(II) VIA(0): Active Device is 0x2
(II) VIA(0): IGA: CRT=1, TV=1, DFP=1, LCD=2
(II) VIA(0): VIALoadUserDuoViewVideoOutputDeviceSetting exit:TVtype=1, TVScan=0
(II) VIA(0): VIAFindModeUseBIOSTable exit:TVtype=1, TVScan=0
(II) VIA(0): VIADISP3DScalingParasSetting exit:TVtype=1, TVScan=0
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): VIASetMode exit:TVtype=1, TVScan=0
(II) VIA(0): into 3D initial...3Dinitial? 0
(II) VIA(0): H5 3D Engine has been initilized.
(II) VIA(0): VIAWriteMode exit:TVtype=1, TVScan=0
(II) VIA(0): lpVIAGraphicInfo->dwXServerEnabled is 1
(EE) VIA(0):  Couldn't open "/dev/video2"
(II) VIA(0): VIAModeInit exit:TVtype=1, TVScan=0
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): Frame Buffer From (0,0) To (1440,2047)
(II) VIA(0): Using 2047 lines for offscreen memory.
(II) VIA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		14 256x256 slots
		32 8x8 color pattern slots
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(II) VIA(0): DPMS enabled
(II) VIA(0): direct rendering disabled
(II) VIA(0): lpVIAGraphicInfo->dwXServerEnabled is 1
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) VIA(0): VIALeaveVT

```

---

### Post by Hero of Time on 2008-08-26
I'm having the same issue. I have an ATi Mobility Radeon x1400 as videocard, so that is out of the equation now. Even tried different video drivers, no luck. Currently, I only have the -19 kernel installed, so going back to an old kernel directly is not possible, I have to download and install it (something I don't like to do).

This is my Xorg.0.log file.
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Patrick-Laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 27 00:22:34 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Laptop Monitor"
(**) |   |-->Device "ATi Mobility Radeon x1400"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "BlankTime" "0"
(**) Option "StandbyTime" "10"
(**) Option "SuspendTime" "10"
(**) Option "OffTime" "10"
(**) Option "AIGLX" "on"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1734,10b0 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1734,10b0 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1734,10b0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1734,10b0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1734,10b0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1734,10b0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1734,10b0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1734,10b0 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1734,10b0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 1734,10b0 rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1734,10b0 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7145 card 1734,10b0 rev 00 class 03,00,00 hdr 00
(II) PCI: 04:00:0: chip 8086,4222 card 8086,1001 rev 02 class 02,80,00 hdr 00
(II) PCI: 05:04:0: chip 104c,8023 card 1734,10b0 rev 00 class 0c,00,10 hdr 00
(II) PCI: 05:05:0: chip 10ec,8169 card 1734,10b0 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb0100000 - 0xb01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfac00000 - 0xfebfffff (0x4000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xb0200000 - 0xb02fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xb0300000 - 0xb03fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility X1400 rev 0, Mem @ 0xc0000000/28, 0xb0100000/16, I/O @ 0x2000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb0304800 - 0xb03048ff (0x100) MX[B]
	[1] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[2] -1	0	0xb0304000 - 0xb03047ff (0x800) MX[B]
	[3] -1	0	0xb0200000 - 0xb0200fff (0x1000) MX[B]
	[4] -1	0	0xb0004400 - 0xb00047ff (0x400) MX[B]
	[5] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[6] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[7] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[10] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[11] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[12] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[13] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[14] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[15] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[16] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[25] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb0304800 - 0xb03048ff (0x100) MX[B]
	[1] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[2] -1	0	0xb0304000 - 0xb03047ff (0x800) MX[B]
	[3] -1	0	0xb0200000 - 0xb0200fff (0x1000) MX[B]
	[4] -1	0	0xb0004400 - 0xb00047ff (0x400) MX[B]
	[5] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[6] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[7] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[10] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[11] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[12] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[13] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[14] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[15] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[16] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[25] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0304800 - 0xb03048ff (0x100) MX[B]
	[5] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[6] -1	0	0xb0304000 - 0xb03047ff (0x800) MX[B]
	[7] -1	0	0xb0200000 - 0xb0200fff (0x1000) MX[B]
	[8] -1	0	0xb0004400 - 0xb00047ff (0x400) MX[B]
	[9] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[16] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[17] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[18] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[19] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[20] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[21] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[22] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.49.7
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.49.7
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.493                    
(II) ATI Proprietary Linux Driver Build Date: May 12 2008 11:03:20
(--) Chipset Supported AMD Graphics Processor (0x7145) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0304800 - 0xb03048ff (0x100) MX[B]
	[5] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[6] -1	0	0xb0304000 - 0xb03047ff (0x800) MX[B]
	[7] -1	0	0xb0200000 - 0xb0200fff (0x1000) MX[B]
	[8] -1	0	0xb0004400 - 0xb00047ff (0x400) MX[B]
	[9] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[16] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[17] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[18] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[19] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[20] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[21] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[22] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820c750
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0304800 - 0xb03048ff (0x100) MX[B]
	[5] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[6] -1	0	0xb0304000 - 0xb03047ff (0x800) MX[B]
	[7] -1	0	0xb0200000 - 0xb0200fff (0x1000) MX[B]
	[8] -1	0	0xb0004400 - 0xb00047ff (0x400) MX[B]
	[9] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[22] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[23] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[31] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[32] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[34] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "True"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1400" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x1734, PciSubDevice = 0x10b0)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xb0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.49.7
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: CPT  Model: 13b1  Serial#: 0
(II) fglrx(0): Year: 2006  Week: 6
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.615 redY: 0.332   greenX: 0.315 greenY: 0.561
(II) fglrx(0): blueX: 0.152 blueY: 0.127   whiteX: 0.315 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 813 v_border: 0
(II) fglrx(0):  CPT
(II) fglrx(0):  CLAA154WA05A
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff000e14b11300000000
(II) fglrx(0): 	06100103802115780a8e2d9d55508f27
(II) fglrx(0): 	20505400000001010101010101010101
(II) fglrx(0): 	010101010101ea1a008050200d301820
(II) fglrx(0): 	13004bcf100000190000000f00202020
(II) fglrx(0): 	2020202020206e050f00000000fe0043
(II) fglrx(0): 	50540a202020202020202020000000fe
(II) fglrx(0): 	00434c414131353457413035412000c1
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  4 power states available:
(II) fglrx(0):   1. 446/342MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 297/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 297/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/135MHz @ 60Hz [low voltage, enable sleep]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 10 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1304 1336 1408  800 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1304 1336 1408  768 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1304 1336 1408  768 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 1304 1336 1408  600 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 1304 1336 1408  480 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 1304 1336 1408  400 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 1304 1336 1408  384 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 1304 1336 1408  300 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 1304 1336 1408  240 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 1304 1336 1408  200 801 804 813 +hsync +vsync (48.9 kHz)
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.90  1280 1304 1336 1408  800 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.90  1280 1304 1336 1408  768 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.90  1024 1304 1336 1408  768 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.90  800 1304 1336 1408  600 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.90  640 1304 1336 1408  480 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.90  640 1304 1336 1408  400 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.90  512 1304 1336 1408  384 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.90  400 1304 1336 1408  300 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.90  320 1304 1336 1408  240 801 804 813 +hsync +vsync (48.9 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.90  320 1304 1336 1408  200 801 804 813 +hsync +vsync (48.9 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xb0100000 - 0xb010ffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xb0304800 - 0xb03048ff (0x100) MX[B]
	[7] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[8] -1	0	0xb0304000 - 0xb03047ff (0x800) MX[B]
	[9] -1	0	0xb0200000 - 0xb0200fff (0x1000) MX[B]
	[10] -1	0	0xb0004400 - 0xb00047ff (0x400) MX[B]
	[11] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[12] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[13] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[25] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[26] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[27] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[34] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[35] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[36] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[37] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x80000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.49.7
(II) fglrx(0):     Date: May 12 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00082000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc1005000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2480
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		19 256x256 slots
		5 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
Receive enable interrupt ret message
...irqEnableMask: 10000000
...dwIRQEnableId: 00000008
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbVariant" "altgr-intl"
(**) Generic Keyboard: XkbVariant: "altgr-intl"
(**) Option "XkbOptions" "lv3:ralt_switch:altwin:meta_win"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch:altwin:meta_win"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) AIGLX: Suspending AIGLX clients for VT switch
```
As you can see, there are no errors in the log. I managed to get it working today once, by uninstalling Compiz, but I made sure that when it was working again, and I reinstalled Compiz, that I shut down properly with Compiz disabled. I use Xubuntu, so failsafe Gnome will not even work, it will throw me directly to a failsafe terminal session.
My login goes up to the splash screen, showing a few loading things and once it hits the autostart, it stops. Splash screen goes away, mouse cursor is the only thing left on a black background. Earlier today, I was stuck with just a desktop background image. During the splash loading, I did see my desktop icons briefly.

---

### Post by markbuntu on 2008-08-26
Graphics problems are not the only reason gdm will recycle. If gdm cannot parse your password it will also recycle. You can try making a new user and see if that works, some people have had success with that.

---

### Post by rossjman1 on 2008-08-26
Thanks for the warning! I guess I will wait a day or so before updating!!!

---

### Post by Hero of Time on 2008-08-26
> **markbuntu said:**
> Graphics problems are not the only reason gdm will recycle. If gdm cannot parse your password it will also recycle. You can try making a new user and see if that works, some people have had success with that.
My GDM does not recycle, it just stays on the black screen with mouse cursor. Until I of course hit Ctrl+Alt+Backspace.

---

### Post by Hero of Time on 2008-08-27
I managed to get it working again. I wondered why it would show a black background after it was done loading. So I hit Alt+F2 and guess, what. I could run programs. First thing I ran was my panel. From there I could open my preferences and let Xfce manage my desktop. Now it works just fine again.

---

### Post by jeffreypine on 2008-08-27
I cannot get past GDM after kernel update.

.xsession-errors says, 

"error while loading shared libraries: libgnome-2.so.0"

also, if I try to reinstall or update on tty using aptitutde (or any of the other various methods), I get errors saying I must manually fix the problem using "dpkg --configure -a", which does nothing except display the error, 
"cannot mmap file /usr/lib/libgnomebt.so.0.0.2."

I'm stumped.

Any clues would be fantastic.

---

