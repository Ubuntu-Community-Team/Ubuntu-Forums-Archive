---
title: "[SOLVED] X Not Reading Mouse Correctly"
date: 2008-10-04
forum: General Help
---

### Post by Unanimated on 2008-10-04
My issue is similar to the whole Synaptics Touchpad disabling thing, only I don't have a touchpad. I have a keyboard and mouse. When I type with the keyboard, my mouse movement is delayed by about 1 second, which is very annoying. Also, the lights on my keyboard (Num Lock, Caps Lock, etc.) don't light up when I press their respective buttons, but their function still works. I looked in xorg.conf, and everything looks fine. Any help?

---

### Post by phorim on 2008-10-04
Can you specify which make and model of mouse and keyboard you are using?  The more information we have on your system the better.

---

### Post by harlan on 2008-10-04
Boot from the Ubuntu LiveCD and if you don't have problems with the mouse, etc, using the LiveCD then copy the xorg.conf from the LiveCD to the harddisk.

It's an easy way to fix problems about the X11 configuration.

---

### Post by Unanimated on 2008-10-05
> **harlan said:**
> Boot from the Ubuntu LiveCD and if you don't have problems with the mouse, etc, using the LiveCD then copy the xorg.conf from the LiveCD to the harddisk.

It's an easy way to fix problems about the X11 configuration.
I'll try that, and if it doesn't work, then I'll post the information.

---

### Post by Unanimated on 2008-10-05
Well, I took the xorg.conf from the LiveCD, where the whole mouse thing was working fine, then applied it to my current Ubuntu installation, and it didn't work.

My keyboard is a Dynex DX-MKB101, and its serial number is 063001895.
My mouse is a Logitech M-BJ67B, and its serial number is LNA40512556.

---

### Post by Unanimated on 2008-10-06
bump

---

### Post by Unanimated on 2008-10-08
bump

---

### Post by caleb12 on 2008-10-08
What version of Xorg are you using? Interpid shipped with 7.4 and 1.5 - which started to rely more on evdev doing the hotplugging than the config options of xorg.conf. Sounds like this maybe an issue for you... Check your /var/log/Xorg.0.log file and post the contents related to keyboard and mouse options. Also, your xorg.conf - you may need to specify the drivers... for instance mine looks as such: 

Section "InputDevice"
        Identifier      "Configured Keyboard"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event0"
        Option          "Name"          "AT Translated Set 2 keyboard"
EndSection

Section "InputDevice"
        Identifier      "VX Nano"
        Driver          "evdev"
        Option          "Device"                "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
        Option          "Name"                  "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-0000:00:1d.3-2/input0"
        Option          "Buttons"               "9"
        Option          "WHEELRelativeAxisButtons" "4 5"
        Option          "HWHEELRelativeAxisButtons" "7 6"
        Option          "Protocol"              "evdev"
        Option          "CorePointer"
EndSection

Notice in keyboard section I am using evdev as the module, not the standard kbd - also my keyboard was all kinds of crazy until I added the dev phys option into my VX nano section. For some reason the VX nano loads two instances of itself and one is identified as a keyboard and was wreaking havoc with my real keyboard... 

Hopefully that helps...

---

### Post by Unanimated on 2008-10-11
Yeah, it was a lot to look at and I'm getting tired, so here's that entire file (/var/log/Xorg.0.log)

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
Current Operating System: Linux sam-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 10 16:03:09 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
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
(II) PCI: 00:00:0: chip 1106,0305 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8305 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 40 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 1a class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 1a class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 40 class 06,00,00 hdr 00
(II) PCI: 00:07:5: chip 1106,3058 card 1462,3300 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:09:0: chip 1102,0004 card 1102,0051 rev 03 class 04,01,00 hdr 80
(II) PCI: 00:09:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 00:09:2: chip 1102,4001 card 1102,0010 rev 00 class 0c,00,10 hdr 80
(II) PCI: 00:0d:0: chip 1317,0985 card 1317,0570 rev 11 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,00f3 card 0000,0000 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6200] rev 162, Mem @ 0xe0000000/24, 0xd0000000/28, 0xe1000000/24
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
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe4004000 - 0xe40043ff (0x400) MX[B]
	[1] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[2] -1	0	0xe4005000 - 0xe40057ff (0x800) MX[B]
	[3] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[4] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[12] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe4004000 - 0xe40043ff (0x400) MX[B]
	[1] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[2] -1	0	0xe4005000 - 0xe40057ff (0x800) MX[B]
	[3] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[4] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[12] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
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
	[4] -1	0	0xe4004000 - 0xe40043ff (0x400) MX[B]
	[5] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[6] -1	0	0xe4005000 - 0xe40057ff (0x800) MX[B]
	[7] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[8] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[18] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.13  Tue Jun 10 17:10:47 PDT 2008
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  177.13  Tue Jun 10 16:49:34 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4004000 - 0xe40043ff (0x400) MX[B]
	[5] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[6] -1	0	0xe4005000 - 0xe40057ff (0x800) MX[B]
	[7] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[8] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[18] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4004000 - 0xe40043ff (0x400) MX[B]
	[5] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[6] -1	0	0xe4005000 - 0xe40057ff (0x800) MX[B]
	[7] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[8] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV43) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.57.08
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     DELL E172FP (CRT-1)
(--) NVIDIA(0): DELL E172FP (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4004000 - 0xe40043ff (0x400) MX[B]
	[5] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[6] -1	0	0xe4005000 - 0xe40057ff (0x800) MX[B]
	[7] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[8] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1280x1024_75"
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by david_kt on 2008-10-11
> **Unanimated said:**
> Yeah, it was a lot to look at and I'm getting tired, so here's that entire file (/var/log/Xorg.0.log)

Try a quick fix:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Until now, sometimes I need to run this after a while (compiz fusion suddenly refuse to run, may be after some upgrade). And every time it help me to fix my problem.

DK

---

### Post by Unanimated on 2008-10-11
I'm sorry to say that that didn't work.

---

### Post by david_kt on 2008-10-11
> **Unanimated said:**
> I'm sorry to say that that didn't work.

What is the output of below:

```
glxinfo | grep render

```

DK

---

### Post by caleb12 on 2008-10-11
Are you using the evdev driver? Check in synaptic or apt-get for a xserver-xorg-input-evdev - if that is installed try these options, instead of the current ones in xorg.conf:

Input Device "Keyboard0"
Driver        "evdev"
Identifier    "Configured Keyboard
Option        "Device" "/dev/input/**YOUR_DEVICE_LOCATION**"
Option        "Name" "**YOUR_DEVICE**"
EndSection

Input Device "Mouse0"
Identifier   "Configured Mouse"
Driver        "evdev"
Option "Device" "/dev/input/by-id/**YOUR_DEVICE**"
Option "Name" "YOUR_DEVICE"
Option "Dev Phys" "YOUR_LOCATION"
Option "Buttons" "9"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
Option "Protocol" "evdev"
Option "CorePointer"
EndSection

So, there are a couple variable locations above that you will need to define... 

Use the following command:

cat /proc/bus/input/devices

The keyboard will look similar to this:

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard" **<- Name of your Device**
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=kbd **event0** rfkill **<- The event0 is the location = /dev/input/event0**
B: EV=120013

The output for a mouse will be:

I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:10.0-2/input0 **<- This is the Dev Phys option in your mouse config**
H: Handlers=mouse1 event3 **<- We will use a different device file for the mouse**
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103


To find the **device location of your mouse**, look into the /dev/input/by-id and /dev/input/by-path directory. I recommend to always use /dev/input/by-id/MyMouseName-event-mouse as device instead of the eventX files. Note that you'll find MyMouseName-mouse and MyMouseName-event-mouse, of which only the latter will work with evdev.

For your reading pleasure; my sources:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware)

Hope that helps...

---

### Post by Unanimated on 2008-10-11
@ david_kt:
```
direct rendering: Yes
OpenGL renderer string: GeForce 6200/AGP/SSE/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 

```
@ caleb12:
Thanks, I'll try that.

EDIT: cat /proc/bus/input/devices returns this:
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0006 Version=0056
N: Name="ImExPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c216 Version=0110
N: Name="Logitech Logitech Dual Action"
P: Phys=usb-0000:00:07.2-2.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2.2/1-2.2:1.0/input/input6
U: Uniq=
H: Handlers=event6 js0 
B: EV=1b
B: KEY=fff 0 0 0 0 0 0 0 0 0
B: ABS=30027
B: MSC=10

I: Bus=0003 Vendor=1267 Product=0103 Version=0110
N: Name="HID 1267:0103"
P: Phys=usb-0000:00:07.2-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2.3/1-2.3:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1267 Product=0103 Version=0110
N: Name="HID 1267:0103"
P: Phys=usb-0000:00:07.2-2.3/input1
S: Sysfs=/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2.3/1-2.3:1.1/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=1f
B: KEY=37fff ac3027 bf004444 0 0 1 c04 a37c000 267bfa d941dfed 9e0000 0 0 0
B: REL=40
B: ABS=1 0
B: MSC=10

I: Bus=0006 Vendor=001f Product=001f Version=0000
N: Name="Mouseemu virtual keyboard"
P: Phys=
S: Sysfs=/devices/virtual/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=100003
B: KEY=1ffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff

I: Bus=0006 Vendor=001f Product=001e Version=0000
N: Name="Mouseemu virtual mouse"
P: Phys=
S: Sysfs=/devices/virtual/input/input10
U: Uniq=
H: Handlers=mouse2 event10 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

The Logitech mouse is my mouse, and Logitech Dual Action is a gamepad I have connected. I also have a Nintendo Wifi USB Connector connected, and a bluetooth dongle. And, obviously, my keyboard. I'm confused on which input I'm supposed to put in. Setting evdev and not doing anything else completely disables my mouse and keyboard and forces me to set everything back with nano in Ctrl+Alt+F1.

---

### Post by Unanimated on 2008-10-11
bump

---

### Post by caleb12 on 2008-10-11
So, for the mouse section you have two devices:

I: Bus=0011 Vendor=0002 Product=0006 Version=0056
N: Name="ImExPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c216 Version=0110
N: Name="Logitech Logitech Dual Action"
P: Phys=**usb-0000:00:07.2-2.2/input0**
S: Sysfs=/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2.2/1-2.2:1.0/input/input6
U: Uniq=
H: Handlers=event6 js0 
B: EV=1b
B: KEY=fff 0 0 0 0 0 0 0 0 0
B: ABS=30027
B: MSC=10


So, when it comes to mice like these - mine also has two entries - which was confusing evdev; so you have to use the:

Option "Dev Phys" "**usb-0000:00:07.2-2.2/input0**"

which will reference the specific device you are configuring. 

As for the:

Option "Device"  setting, you will need to look in this folder:

/dev/input/by-id/ 

you will have two files in there: 

MyMouseName-event-mouse &
MyMouseName-mouse

You will want to use the MyMouseName-event-mouse

Option "Device" /dev/input/by-id/MyMouseName-event-mouse 

~~~~~~~~~~~~~~~~~
I'm running out the door, or I'd try to be more specific... Be back in a bit...

---

### Post by Unanimated on 2008-10-11
Nope, that didn't work. I also tried taking the xorg.conf file from the LiveCD, where everything works perfectly, and all that does is put it in low-graphics mode.

EDIT: I suppose I could also try putting my X11 folder into a tarball and copy/overwrite the X11 folder from the LiveCD.

---

### Post by caleb12 on 2008-10-11
Hmmm, sucks... Maybe try removing all the other devices except for mouse and keyboard, maybe all that other stuff is messing with it... dunno, sorry, I'm out of ideas. 

The above posts fixed my issues with the keyboard...

---

### Post by Unanimated on 2008-10-11
Yeah, I just did that, and it didn't work. I'm assuming that means it has nothing to do with Xorg.

EDIT: I mean copying over the LiveCD X11 folder.

---

### Post by Unanimated on 2008-10-11
bump

---

### Post by caleb12 on 2008-10-11
The only other thing I can think... in order to remove evdev from hotplugging any devices... is to add

Section "ServerFlags"
	Option		"AutoEnableDevices"	"false"
	Option		"AutoAddDevices"	"false"
	Option		"AllowEmptyInput"	"false"
EndSection

To the xorg.conf - this will tell xorg to not accept devices from evdev... then again, the devices you want to use will have to be explicitly identified according to xorg rules... 

If that doesnt work, I'd start looking at kernel modules that are getting loaded... it's weird that it all works fine in the LiveCD.

---

### Post by david_kt on 2008-10-11
> **Unanimated said:**
> @ david_kt:
```
direct rendering: Yes
OpenGL renderer string: GeForce 6200/AGP/SSE/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 

```

Looks good, but now try to boot using live cd, which you say having no problem. After that, try the same command:

```
 glxinfo | grep render
```

and compare the result.

I am suspecting there is an issue with the driver of the card. So, if you could check what driver used in the live cd, and then force you system to use it instead of the default you are using now.

DK

---

### Post by Unanimated on 2008-10-11
I appreciate your help and everything, but I just have a question - what does my video card have to do with this? It also did it before I upgraded my video card. Today, I also downloaded the upgraded version of a video card driver from NVIDIA's site.

---

### Post by david_kt on 2008-10-11
> **Unanimated said:**
> I appreciate your help and everything, but I just have a question - what does my video card have to do with this? It also did it before I upgraded my video card. Today, I also downloaded the upgraded version of a video card driver from NVIDIA's site.

The problem similar to problem in video card driver. It consume your cpu and memory to emulate (or whatsoever you called it) the graphic so as your computer looks like stop working for a few seconds.

So, I suspect the one used in the live cd is suitable for your card, but not the subsequent or latest driver. But I could be wrong offcourse.

DK

---

### Post by Unanimated on 2008-10-11
On that note, I think you might be. My computer doesn't seem like it stops working, everything keeps moving, just that my mouse doesn't move, which is incredibly annoying. Should I file this as a bug on Launchpad or something?

---

### Post by david_kt on 2008-10-12
> **Unanimated said:**
> On that note, I think you might be. My computer doesn't seem like it stops working, everything keeps moving, just that my mouse doesn't move, which is incredibly annoying. Should I file this as a bug on Launchpad or something?

Yes you could inform as a bug and let the developer confirm it and fix it. But if you could confirm first exactly what cause this problem, it is much better and faster to get a fix.

DK

---

### Post by Unanimated on 2008-10-12
By spending about 2 minutes in Launchpad, I discovered that mouseemu was causing the slowdown. Disabling it, then removing it, solved the problem and now my mouse works perfectly.

---

