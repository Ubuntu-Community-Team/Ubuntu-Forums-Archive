---
title: "Via p4m900 can't login"
date: 2009-08-13
forum: Hardware
---

### Post by surg3on on 2009-08-13
Hi all!
After installing the proprietary installer of via chrome (9.83.4055), I can't login to gnome in normal mode, but only in safe mode, though gdm starts just fine (when I try to login the screen flickers, changes to my desktop background color, changes to black and then reverts to gdm login).
I want to install 3d support here to play at least tuxracer or something like that with 3d support, has anybody succeeded in installing this driver?
I am using kernel 2.6.24 on an i686 system.
So here's Xorg.0.log with some strange errors:

> 
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux ubuntu 2.6.24-24-generic #1 SMP Fri Jul 24 22:46:06 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 14 01:13:11 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Monitor"
(**) |   |-->Device "Configured Video Device"
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
    Using the first mouse device.
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
(II) PCI: 00:00:0: chip 1106,0364 card 1043,81ce rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5364 card 0000,0000 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:6: chip 1106,6364 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:7: chip 1106,7364 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,5337 card 1043,81cf rev 80 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,81cf rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,81cf rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,81cf rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,81cf rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,81cf rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,81cf rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3337 card 1043,81cf rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:7: chip 1106,287e card 1106,337e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,337b card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:13:1: chip 1106,337a card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 01:00:0: chip 1106,3371 card 1043,81ce rev 01 class 03,00,00 hdr 00
(II) PCI: 04:07:0: chip 10ec,8167 card 1043,820d rev 10 class 02,00,00 hdr 00
(II) PCI: 80:01:0: chip 1106,3288 card 1043,81b3 rev 10 class 04,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12, BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xdd000000 - 0xdeffffff (0x2000000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xd8000000 - 0xdbffffff (0x4000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:19:1), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
    [0] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[b]
    [1] -1    0    0x0000c400 - 0x0000c4ff (0x100) IX[b]
    [2] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[b]
    [3] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[b]
(II) Bus 4 non-prefetchable memory range:
    [0] -1    0    0xdfe00000 - 0xdfefffff (0x100000) MX[b]
(II) Host-to-PCI bridge:
(II) Bus 128: bridge is at (0:0:0), (128,128,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 128 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 128 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 128 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3371) rev 1, Mem @ 0xd8000000/26, 0xdd000000/24
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xcfffc000 - 0xcfffffff (0x4000) MX[b]
    [1] -1    0    0xdfeff000 - 0xdfeff0ff (0x100) MX[b]
    [2] -1    0    0xdffff000 - 0xdffff0ff (0x100) MX[b]
    [3] -1    0    0xdd000000 - 0xddffffff (0x1000000) MX[b](B)
    [4] -1    0    0xd8000000 - 0xdbffffff (0x4000000) MX[b](B)
    [5] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[b]
    [6] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [7] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [8] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [9] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [10] -1    0    0x0000e400 - 0x0000e40f (0x10) IX[b]
    [11] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [12] -1    0    0x0000ec00 - 0x0000ec0f (0x10) IX[b]
    [13] -1    0    0x0000f000 - 0x0000f003 (0x4) IX[b]
    [14] -1    0    0x0000f400 - 0x0000f407 (0x8) IX[b]
    [15] -1    0    0x0000f800 - 0x0000f803 (0x4) IX[b]
    [16] -1    0    0x0000fc00 - 0x0000fc07 (0x8) IX[b]
(II) Inactive PCI resource ranges:
    [0] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xcfffc000 - 0xcfffffff (0x4000) MX[b]
    [1] -1    0    0xdfeff000 - 0xdfeff0ff (0x100) MX[b]
    [2] -1    0    0xdffff000 - 0xdffff0ff (0x100) MX[b]
    [3] -1    0    0xdd000000 - 0xddffffff (0x1000000) MX[b](B)
    [4] -1    0    0xd8000000 - 0xdbffffff (0x4000000) MX[b](B)
    [5] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[b]
    [6] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [7] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [8] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [9] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [10] -1    0    0x0000e400 - 0x0000e40f (0x10) IX[b]
    [11] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [12] -1    0    0x0000ec00 - 0x0000ec0f (0x10) IX[b]
    [13] -1    0    0x0000f000 - 0x0000f003 (0x4) IX[b]
    [14] -1    0    0x0000f400 - 0x0000f407 (0x8) IX[b]
    [15] -1    0    0x0000f800 - 0x0000f803 (0x4) IX[b]
    [16] -1    0    0x0000fc00 - 0x0000fc07 (0x8) IX[b]
(II) Inactive PCI resource ranges after removing overlaps:
    [0] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xcfffc000 - 0xcfffffff (0x4000) MX[b]
    [5] -1    0    0xdfeff000 - 0xdfeff0ff (0x100) MX[b]
    [6] -1    0    0xdffff000 - 0xdffff0ff (0x100) MX[b]
    [7] -1    0    0xdd000000 - 0xddffffff (0x1000000) MX[b](B)
    [8] -1    0    0xd8000000 - 0xdbffffff (0x4000000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
    [10] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [11] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [12] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[b]
    [13] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [14] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [15] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [16] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [17] -1    0    0x0000e400 - 0x0000e40f (0x10) IX[b]
    [18] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [19] -1    0    0x0000ec00 - 0x0000ec0f (0x10) IX[b]
    [20] -1    0    0x0000f000 - 0x0000f003 (0x4) IX[b]
    [21] -1    0    0x0000f400 - 0x0000f407 (0x IX[b]
    [22] -1    0    0x0000f800 - 0x0000f803 (0x4) IX[b]
    [23] -1    0    0x0000fc00 - 0x0000fc07 (0x IX[b]
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
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 0.1.1
    ABI class: X.Org Video Driver, version 2.0
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
(II) v4l driver for Video4Linux
(II) via: driver for VIA chipsets: CLE266, KM400/KN400, K8M800/K8N800,
    PM800/PM880/CN400, P4M800PRO, CX700, K8M890, P4M890, CN750, P4M900,
    VX800
(II) Primary Device is: PCI 01:00:0
(--) Chipset P4M900 found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xcfffc000 - 0xcfffffff (0x4000) MX[b]
    [5] -1    0    0xdfeff000 - 0xdfeff0ff (0x100) MX[b]
    [6] -1    0    0xdffff000 - 0xdffff0ff (0x100) MX[b]
    [7] -1    0    0xdd000000 - 0xddffffff (0x1000000) MX[b](B)
    [8] -1    0    0xd8000000 - 0xdbffffff (0x4000000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
    [10] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [11] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [12] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[b]
    [13] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [14] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [15] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [16] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [17] -1    0    0x0000e400 - 0x0000e40f (0x10) IX[b]
    [18] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [19] -1    0    0x0000ec00 - 0x0000ec0f (0x10) IX[b]
    [20] -1    0    0x0000f000 - 0x0000f003 (0x4) IX[b]
    [21] -1    0    0x0000f400 - 0x0000f407 (0x IX[b]
    [22] -1    0    0x0000f800 - 0x0000f803 (0x4) IX[b]
    [23] -1    0    0x0000fc00 - 0x0000fc07 (0x IX[b]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xcfffc000 - 0xcfffffff (0x4000) MX[b]
    [5] -1    0    0xdfeff000 - 0xdfeff0ff (0x100) MX[b]
    [6] -1    0    0xdffff000 - 0xdffff0ff (0x100) MX[b]
    [7] -1    0    0xdd000000 - 0xddffffff (0x1000000) MX[b](B)
    [8] -1    0    0xd8000000 - 0xdbffffff (0x4000000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
    [10] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [11] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [12] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [15] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[b]
    [16] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [17] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [18] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [19] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [20] -1    0    0x0000e400 - 0x0000e40f (0x10) IX[b]
    [21] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [22] -1    0    0x0000ec00 - 0x0000ec0f (0x10) IX[b]
    [23] -1    0    0x0000f000 - 0x0000f003 (0x4) IX[b]
    [24] -1    0    0x0000f400 - 0x0000f407 (0x8) IX[b]
    [25] -1    0    0x0000f800 - 0x0000f803 (0x4) IX[b]
    [26] -1    0    0x0000fc00 - 0x0000fc07 (0x8) IX[b]
    [27] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [28] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
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
(II) VIA(0): VESA VBE Total Mem: 65536 kB
(II) VIA(0): VESA VBE OEM: VIA M3364

(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(II) VIA(0): MapBase = b7883000, MmioBase=dd000000
(II) VIA(0): RegCR08 = 0, RegCR09=4f
(--) VIA(0): Chipset: "P4M900"
(--) VIA(0): Chipset Rev.: 0
(==) VIA(0): Not using video BIOS to set modes
(II) VIA(0): MergedFB mode forced off.
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
(--) VIA(0): mapping MMIO @ 0xdd000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xdd200000 with size 0x200000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(**) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  65536k
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
(II) VIA(0): VESA VBE DDC read successfully
(II) VIA(0): Manufacturer: GSM  Model: 4373  Serial#: 169618
(II) VIA(0): Year: 2004  Week: 11
(II) VIA(0): EDID Version: 1.3
(II) VIA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VIA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VIA(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) VIA(0): Gamma: 2.20
(II) VIA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VIA(0): First detailed timing is preferred mode
(II) VIA(0): redX: 0.641 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) VIA(0): blueX: 0.147 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) VIA(0): Supported VESA Video Modes:
(II) VIA(0): 720x400@70Hz
(II) VIA(0): 640x480@60Hz
(II) VIA(0): 640x480@75Hz
(II) VIA(0): 800x600@60Hz
(II) VIA(0): 800x600@75Hz
(II) VIA(0): 832x624@75Hz
(II) VIA(0): 1024x768@60Hz
(II) VIA(0): 1024x768@75Hz
(II) VIA(0): 1280x1024@75Hz
(II) VIA(0): 1152x870@75Hz
(II) VIA(0): Manufacturer's mask: 0
(II) VIA(0): Supported Future Video Modes:
(II) VIA(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) VIA(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) VIA(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) VIA(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) VIA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VIA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VIA(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) VIA(0): Monitor name: L1716S
(II) VIA(0): Monitor name: 
(II) VIA(0): EDID (in hex):
(II) VIA(0):     00ffffffffffff001e6d734392960200
(II) VIA(0):     0b0e01036e221b78ea2ee5a4574a9c25
(II) VIA(0):     115054a56b80314f454f614f81800101
(II) VIA(0):     010101010101302a009851002a403070
(II) VIA(0):     1300520e1100001e000000fd00384b1e
(II) VIA(0):     530e000a202020202020000000fc004c
(II) VIA(0):     31373136530a202020202020000000fc
(II) VIA(0):     000a20202020202020202020202000d4
(II) VIA(0): EDID vendor "GSM", prod id 17267
(II) VIA(0): Using hsync ranges from config file
(II) VIA(0): Using vrefresh ranges from config file
(II) VIA(0): Printing DDC gathered Modelines:
(II) VIA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) VIA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VIA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VIA(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VIA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VIA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) VIA(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) VIA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VIA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VIA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VIA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VIA(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) VIA(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) VIA(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) VIA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(--) VIA(0): Max Monitor H Size =  1280
(--) VIA(0): Max Monitor V Size =  1024
(II) VIA(0): Monitor: Using hsync range of 30.00-113.00 kHz
(II) VIA(0): Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) VIA(0): Monitor: Using maximum pixel clock of 140.00 MHz
(II) VIA(0): Clock range:  20.00 to 270.00 MHz
(II) VIA(0): Not using mode "1088x612" (width too large for virtual size)
(II) VIA(0): Not using mode "1152x720" (width too large for virtual size)
(II) VIA(0): Not using mode "1200x720" (width too large for virtual size)
(II) VIA(0): Not using mode "1280x600" (width too large for virtual size)
(II) VIA(0): Not using mode "1280x720" (width too large for virtual size)
(II) VIA(0): Not using mode "1280x768" (width too large for virtual size)
(II) VIA(0): Not using mode "1360x768" (width too large for virtual size)
(II) VIA(0): Not using mode "1366x768" (width too large for virtual size)
(II) VIA(0): Not using mode "1440x900" (width too large for virtual size)
(II) VIA(0): Not using mode "1440x1050" (width too large for virtual size)
(II) VIA(0): Not using mode "1600x900" (width too large for virtual size)
(II) VIA(0): Not using mode "1600x1024" (width too large for virtual size)
(II) VIA(0): Not using mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using mode "1856x1392" (width too large for virtual size)
(II) VIA(0): Not using mode "1920x1080" (width too large for virtual size)
(II) VIA(0): Not using mode "2048x1536" (width too large for virtual size)
(II) VIA(0): Not using mode "1280x768" (width too large for virtual size)
(II) VIA(0): Not using mode "1440x1050" (width too large for virtual size)
(II) VIA(0): Not using mode "1280x768" (width too large for virtual size)
(II) VIA(0): Not using mode "1440x1050" (width too large for virtual size)
(II) VIA(0): Not using mode "848x480" (vrefresh out of range)
(II) VIA(0): Not using mode "1280x960@60" (width too large for virtual size)
(II) VIA(0): Not using mode "1280x1024@60" (width too large for virtual size)
(II) VIA(0): Not using default mode "640x350" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vertical timing out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1280x1024" (width too large for virtual size)
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
(II) VIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) VIA(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x768" (width too large for virtual size)
(II) VIA(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
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
(II) VIA(0): Not using driver mode "1280x1024" (width too large for virtual size)
(II) VIA(0): Not using driver mode "720x400" (vertical timing out of range)
(II) VIA(0): Not using driver mode "1280x1024" (width too large for virtual size)
(II) VIA(0): Not using driver mode "832x624" (horizontal timing out of range)
(II) VIA(0): Not using driver mode "1152x864" (width too large for virtual size)
(II) VIA(0): Not using driver mode "1280x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "1088x612" (width too large for virtual size)
(II) VIA(0): Not using default mode "1152x720" (width too large for virtual size)
(II) VIA(0): Not using default mode "1200x720" (width too large for virtual size)
(II) VIA(0): Not using default mode "1280x600" (width too large for virtual size)
(II) VIA(0): Not using default mode "1280x720" (width too large for virtual size)
(II) VIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) VIA(0): Not using default mode "1360x768" (width too large for virtual size)
(II) VIA(0): Not using default mode "1366x768" (width too large for virtual size)
(II) VIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) VIA(0): Not using default mode "1440x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x900" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(**) VIA(0): Virtual size is 1024x768 (pitch 1024)
(**) VIA(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) VIA(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) VIA(0):  Mode "1024x768@60": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768@60"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) VIA(0):  Driver mode "1024x768": 82.0 MHz, 60.3 kHz, 74.9 Hz
(II) VIA(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(**) VIA(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) VIA(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) VIA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) VIA(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) VIA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) VIA(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
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
(**) VIA(0):  Mode "800x600@56": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) VIA(0): Modeline "800x600@56"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) VIA(0):  Mode "800x600@60": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600@60"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) VIA(0):  Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) VIA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) VIA(0):  Driver mode "800x600": 49.0 MHz, 47.1 kHz, 74.9 Hz
(II) VIA(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(**) VIA(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VIA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
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
(**) VIA(0):  Mode "640x480@60": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) VIA(0): Modeline "640x480@60"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) VIA(0):  Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) VIA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) VIA(0):  Driver mode "640x480": 30.8 MHz, 37.7 kHz, 74.8 Hz
(II) VIA(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(**) VIA(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) VIA(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) VIA(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) VIA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) VIA(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) VIA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) VIA(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) VIA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) VIA(0):  Default mode "480x640": 24.8 MHz, 39.8 kHz, 60.0 Hz
(II) VIA(0): Modeline "480x640"x60.0   24.82  480 504 552 624  640 641 644 663 -hsync +vsync (39.8 kHz)
(**) VIA(0): Display dimensions: (340, 270) mm
(**) VIA(0): DPI set to (76, 72)
(**) VIA(0): disable DVI Display SW scaling, It isn't HDMI
(II) VIA(0): VIASetDisplayPath is Single
(II) VIA(0): Active Device is 0x1
(II) VIA(0): IGA: CRT=1, TV=1, DFP=1, LCD=2
(II) VIALoadVideoOption
(WW) No Video option file .VIAVIDEORC exist. 
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xdd000000 - 0xddffffff (0x1000000) MS[b]
    [1] 0    0    0xd8000000 - 0xdbffffff (0x4000000) MS[b]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [6] -1    0    0xcfffc000 - 0xcfffffff (0x4000) MX[b]
    [7] -1    0    0xdfeff000 - 0xdfeff0ff (0x100) MX[b]
    [8] -1    0    0xdffff000 - 0xdffff0ff (0x100) MX[b]
    [9] -1    0    0xdd000000 - 0xddffffff (0x1000000) MX[b](B)
    [10] -1    0    0xd8000000 - 0xdbffffff (0x4000000) MX[b](B)
    [11] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
    [12] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [13] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [14] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [15] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [16] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [17] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[b]
    [18] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [19] -1    0    0x0000d800 - 0x0000d81f (0x20) IX[b]
    [20] -1    0    0x0000dc00 - 0x0000dc1f (0x20) IX[b]
    [21] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [22] -1    0    0x0000e400 - 0x0000e40f (0x10) IX[b]
    [23] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [24] -1    0    0x0000ec00 - 0x0000ec0f (0x10) IX[b]
    [25] -1    0    0x0000f000 - 0x0000f003 (0x4) IX[b]
    [26] -1    0    0x0000f400 - 0x0000f407 (0x8) IX[b]
    [27] -1    0    0x0000f800 - 0x0000f803 (0x4) IX[b]
    [28] -1    0    0x0000fc00 - 0x0000fc07 (0x8) IX[b]
    [29] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [30] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(--) VIA(0): mapping framebuffer @ 0xd8000000 with size 0x4000000
(==) VIA(0): Write-combining range (0xd8000000,0x4000000)
(--) VIA(0): Frame buffer start: 0xb35fe000, free start: 0x300000 end: 0x4000000
(--) VIA(0): mapping MMIO @ 0xdd000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xdd200000 with size 0x200000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(EE) VIA(0):  Couldn't open "/dev/video2"
(II) VIA(0): VIAScreenInit : V4L Disabled : fd2 = -1 
(II) VIA(0): [drm] Detect H5s1 chipset: 000a  chipid: 3371
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "via_chrome9"
(EE) [drm] drmOpen failed.
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
(II) VIA(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) VIA(0): I2C device "I2C bus 2:TV" removed.
(II) VIA(0): VIASetDisplayPath is Single
(II) VIA(0): Active Device is 0x1
(II) VIA(0): IGA: CRT=1, TV=1, DFP=1, LCD=2
(II) VIA(0): VIALoadUserDuoViewVideoOutputDeviceSetting exit:TVtype=1, TVScan=0
(EE) VIA(0): Refresh rate setting in XF86Config(-4) is not supported!!
(EE) VIA(0): Driver will try to find another refresh rate instead.
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
(II) VIA(0): Frame Buffer From (0,0) To (1024,2047)
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
        10 256x256 slots
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
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
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
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeededHere's my xorg.conf:

> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "de"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection

Section "Device"
    Driver "via"
    VendorName  "VIA Tech"
    BoardName   "via"
    Identifier    "Configured Video Device"
    Boardname    "vesa"
    Busid        "PCI:1:0:0"
    Screen    0
EndSection

Section "Monitor"
    Identifier "Monitor"
    ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
    ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
    ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
    ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
    ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
    ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
    ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
    ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
    ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
    ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
    ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
    ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
    ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
    ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
    ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
    ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
    ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
    ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
    ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
    ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
    ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
    ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
    ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
    ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
    ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
    ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
    ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
    ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
    ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
    ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
    ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
    ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
    ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
    ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x1024"
    Horizsync    31.5-64.0
    Vertrefresh    56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Monitor  "Monitor"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Modes  "1024x768" 
        Virtual 1024 768
        Depth    24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
    Load  "glx"
    Load  "dri"
    Load  "extmod"
    Load        "GLcore"
    Load        "v4l"
EndSection
Section "ServerFlags"
EndSection

Section "DRI"
    Group 0
    Mode 0666
EndSection
So what can I try to fight this problem?
Anyway, I am new to ubuntu, so I appreciate your help a lot. Are there maybe some tutorials for users who come from others distros (I am coming from gentoo) to quickly get along with aptitude, sudo and any other ubuntu specifics?

Thanks in advance,
surgeon

---

