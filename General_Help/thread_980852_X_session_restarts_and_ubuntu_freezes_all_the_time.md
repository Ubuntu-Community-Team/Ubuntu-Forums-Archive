---
title: "X session restarts and ubuntu freezes all the time."
date: 2008-11-13
forum: General Help
---

### Post by gryzzly on 2008-11-13
Hello. I installed 8.04 at work and it starts fine. But after a while I can see strange  visual traces on the screen and it restarts the X session so I have to login again. 

I installed nvidia-restricted driver before that.

I've also tried to uninstall it but still have same problem.

Please please help.

When it freezes the area with leds start to blink. (caps, num, whatever what was turned on). And only hard reboot helps.

xorg.log output:

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
Current Operating System: Linux mreyzlin-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 19 18:41:00 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
[B][COLOR="Red"](WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.[/COLOR][/B]
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
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80c0 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,80ad rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,80ad rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,80ad rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,80ad rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card f043,80ad rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 01:00:0: chip 10de,01f0 card 1043,80c0 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:8:0), (0,2,2), BCTRL: 0x0203 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfbf00000 - 0xfe0fffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xebc00000 - 0xf3dfffff (0x8200000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX - nForce GPU] rev 163, Mem @ 0xfd000000/24, 0xec000000/26, 0xf3d00000/19, BIOS @ 0xfe000000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [1] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [2] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [3] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [4] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [5] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [6] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [7] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [8] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [9] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [10] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [11] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [12] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [13] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [14] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [1] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [2] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [3] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [4] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [5] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [6] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [7] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [8] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [9] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [10] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [11] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [12] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [13] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [14] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [5] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [6] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [7] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [8] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [9] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [10] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [11] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [12] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [13] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [17] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [18] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [19] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [20] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.07  Wed Jul  2 12:30:36 PDT 2008
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  96.43.07  Wed Jul  2 12:18:58 PDT 2008
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
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.2.0
    ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [5] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [6] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [7] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [8] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [9] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [10] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [11] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [12] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [13] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [17] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [18] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [19] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [20] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [5] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [6] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [7] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [8] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [9] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [10] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [11] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [12] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [13] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [19] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [20] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [21] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [22] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [23] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
    [24] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [25] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX Integrated GPU at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 04.1f.20.02.01
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX Integrated GPU at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 300.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Insufficient memory bandwidth for MetaMode "800x512";
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): No valid modes for "800x512"; removing.
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B]
    [1] 0    0    0xec000000 - 0xefffffff (0x4000000) MX[B]
    [2] 0    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B]
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [7] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [8] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [9] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [10] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [11] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [12] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [13] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [14] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [15] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [16] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [17] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [18] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [19] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [22] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [23] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [24] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [25] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [26] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
    [27] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [28] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
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
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1280x1024"
SetClientVersion: 0 9

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f0c420]
2: /usr/bin/X(ProcAllowEvents+0xb4) [0x809a524]
3: /usr/bin/X [0x815076e]
4: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
5: /usr/bin/X(main+0x48b) [0x807471b]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ca6450]
7: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting



```

---

### Post by gryzzly on 2008-11-16
bump

maybe some command's outputs would help... some logs? I just don't know where to start digging...

Please help.

---

### Post by gryzzly on 2008-11-17
hey guys... bump... please

---

### Post by gryzzly on 2008-11-17
I also installed the latest drivers from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and made everything accordingly [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") but nothing worked.

---

### Post by gryzzly on 2008-11-19
is the forum dead?

---

### Post by gryzzly on 2008-11-19
xorg.log output:

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
Current Operating System: Linux mreyzlin-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 19 18:41:00 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80c0 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80c0 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,80ad rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,80ad rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,80ad rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,80ad rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card f043,80ad rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 01:00:0: chip 10de,01f0 card 1043,80c0 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:8:0), (0,2,2), BCTRL: 0x0203 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfbf00000 - 0xfe0fffff (0x2200000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xebc00000 - 0xf3dfffff (0x8200000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX - nForce GPU] rev 163, Mem @ 0xfd000000/24, 0xec000000/26, 0xf3d00000/19, BIOS @ 0xfe000000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [1] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [2] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [3] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [4] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [5] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [6] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [7] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [8] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [9] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [10] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [11] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [12] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [13] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [14] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [1] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [2] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [3] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [4] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [5] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [6] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [7] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [8] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [9] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [10] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [11] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [12] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [13] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [14] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [5] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [6] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [7] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [8] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [9] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [10] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [11] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [12] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [13] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [17] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [18] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [19] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [20] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.07  Wed Jul  2 12:30:36 PDT 2008
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  96.43.07  Wed Jul  2 12:18:58 PDT 2008
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
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.2.0
    ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [5] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [6] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [7] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [8] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [9] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [10] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [11] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [12] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [13] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [17] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [18] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [19] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [20] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [5] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [6] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [7] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [8] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [9] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [10] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [11] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [12] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [13] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [19] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [20] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [21] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [22] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [23] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
    [24] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [25] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX Integrated GPU at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 04.1f.20.02.01
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX Integrated GPU at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Proview (CRT-0)
(--) NVIDIA(0): Proview (CRT-0): 300.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Insufficient memory bandwidth for MetaMode "800x512";
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): No valid modes for "800x512"; removing.
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B]
    [1] 0    0    0xec000000 - 0xefffffff (0x4000000) MX[B]
    [2] 0    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B]
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [7] -1    0    0xfe700000 - 0xfe700fff (0x1000) MX[B]
    [8] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[B]
    [9] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [10] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[B]
    [11] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[B]
    [12] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[B]O
    [13] -1    0    0xfe000000 - 0xfe01ffff (0x20000) MX[B](B)
    [14] -1    0    0xf3d00000 - 0xf3d7ffff (0x80000) MX[B](B)
    [15] -1    0    0xec000000 - 0xefffffff (0x4000000) MX[B](B)
    [16] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [17] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [18] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [19] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [22] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
    [23] -1    0    0x0000ec00 - 0x0000ec7f (0x80) IX[B]
    [24] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [25] -1    0    0x0000eff0 - 0x0000eff7 (0x8) IX[B]
    [26] -1    0    0x0000ef80 - 0x0000ef9f (0x20) IX[B]
    [27] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [28] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
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
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1280x1024"
SetClientVersion: 0 9

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f0c420]
2: /usr/bin/X(ProcAllowEvents+0xb4) [0x809a524]
3: /usr/bin/X [0x815076e]
4: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
5: /usr/bin/X(main+0x48b) [0x807471b]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ca6450]
7: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting



```

---

### Post by BetaMaster on 2008-11-19
Hey.. I'm afraid I can't help you, but I just wanted to let you know that I'm in the same boat you're in - I've had a thread up for five days now and nobody's replied. Ubuntu Forums has been disappointing me lately..

---

### Post by gryzzly on 2008-11-20
this one is third thread without an answer :(

---

### Post by gryzzly on 2008-11-23
bump

---

### Post by gryzzly on 2008-11-25
bump

---

### Post by gryzzly on 2008-11-27
Installed 8.10 on the same machine, same thing happens.

By the way the only thing installed on machine in both case (except for updates) is [synergy]("https://help.ubuntu.com/community/SynergyHowto").

And the only WW (warning) I see in xorg.log is 
```
(WW) The directory "/usr/share/fonts/X11/cyrillic" doesn't exist.
        Entry deleted from font path.
```

---

