---
title: "Another restricted ATI driver issue...."
date: 2008-07-14
forum: Hardware
---

### Post by Turboaaa2001 on 2008-07-14
As I write this question I am working on a few ways to fix this issue, but I would love some help non the less.

I have had this issue with several ATI based video cards but always thought it was because the cards are outdated.

Right now I am putting together a system as follows 

PCChips A13G+ MOBO
nVidia MCP61S Chipset
AMD Athlon X2 4050e 2.1GHZ
1GB DDR2
HIS HD 2600 Pro 512MB GDDR2 w/ IceQ cooling.

What happens is I install the OS, download all the updates, then attempt to enable the ATI restricted drivers. After I activate the driver and reboot my monitor comes back to tell me

"*_CANNOT DISPLAY THIS VIDEO MODE. cHANGE COMPUTER DISPLAY INPUT TO 1024X768 @ 60HZ_*"

My monitor is somewhat of a generic brand 15" LCD that is very old and is used only to work on machines that I will either sell or are in need of repair.

One thing I do need to note is that when I first install the OS the resolution is off to begin with and needs to be changed to a non-wide screen format.

Thanks for all your help.

---

### Post by markbuntu on 2008-07-14
What does the Xorg.0.log tell you about this monitor?

---

### Post by Turboaaa2001 on 2008-07-14
Below is a partial copy of the log file.

```
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux cusstom2 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 14 20:36:15 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
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
(II) PCI: 00:00:0: chip 10de,03ea card 1019,2604 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,03e0 card 1019,2604 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,03eb card 1019,2604 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,03f5 card 1019,2604 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,03f1 card 1019,2604 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,03f2 card 1019,2604 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,03f3 card 0000,0000 rev a1 class 06,04,01 hdr 01
(II) PCI: 00:05:0: chip 10de,03f0 card 1019,a88d rev a2 class 04,03,00 hdr 80
(II) PCI: 00:06:0: chip 10de,03ec card f019,2604 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,03ef card 1019,2604 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 10de,03f6 card 1019,2604 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:09:0: chip 10de,03e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,03e9 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,03e9 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 02:00:0: chip 1002,9589 card 17af,2002 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,aa08 card 17af,aa08 rev 00 class 04,03,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:4:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000c000 - 0x0000c0ff (0x100) IX[B]
    [1] -1    0    0x0000c400 - 0x0000c4ff (0x100) IX[B]
    [2] -1    0    0x0000c800 - 0x0000c8ff (0x100) IX[B]
    [3] -1    0    0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:9:0), (0,2,2), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000b000 - 0x0000b0ff (0x100) IX[B]
    [1] -1    0    0x0000b400 - 0x0000b4ff (0x100) IX[B]
    [2] -1    0    0x0000b800 - 0x0000b8ff (0x100) IX[B]
    [3] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
    [0] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
    [0] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[B]
    [1] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[B]
    [2] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[B]
    [3] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
    [0] -1    0    0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
    [0] -1    0    0x00009000 - 0x000090ff (0x100) IX[B]
    [1] -1    0    0x00009400 - 0x000094ff (0x100) IX[B]
    [2] -1    0    0x00009800 - 0x000098ff (0x100) IX[B]
    [3] -1    0    0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
    [0] -1    0    0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
    [0] -1    0    0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc unknown chipset (0x9589) rev 0, Mem @ 0xe0000000/28, 0xfdde0000/16, I/O @ 0xbc00/8
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
(II) Active PCI resource ranges:
    [0] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [1] -1    0    0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
    [2] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
    [3] -1    0    0xfe028000 - 0xfe02bfff (0x4000) MX[B]
    [4] -1    0    0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
    [5] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [6] -1    0    0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
    [7] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [8] -1    0    0x0000d800 - 0x0000d80f (0x10) IX[B]
    [9] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [10] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [11] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [12] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [13] -1    0    0x0000ec00 - 0x0000ec07 (0x8) IX[B]
    [14] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [15] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[B]
    [16] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[B]
    [17] -1    0    0x0000fc00 - 0x0000fc3f (0x40) IX[B]
    [18] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [1] -1    0    0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
    [2] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
    [3] -1    0    0xfe028000 - 0xfe02bfff (0x4000) MX[B]
    [4] -1    0    0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
    [5] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [6] -1    0    0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
    [7] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [8] -1    0    0x0000d800 - 0x0000d80f (0x10) IX[B]
    [9] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [10] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [11] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [12] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [13] -1    0    0x0000ec00 - 0x0000ec07 (0x8) IX[B]
    [14] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [15] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[B]
    [16] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[B]
    [17] -1    0    0x0000fc00 - 0x0000fc3f (0x40) IX[B]
    [18] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
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
    [4] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [5] -1    0    0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
    [6] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
    [7] -1    0    0xfe028000 - 0xfe02bfff (0x4000) MX[B]
    [8] -1    0    0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [10] -1    0    0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
    [11] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [14] -1    0    0x0000d800 - 0x0000d80f (0x10) IX[B]
    [15] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [16] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [17] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [18] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [19] -1    0    0x0000ec00 - 0x0000ec07 (0x8) IX[B]
    [20] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [21] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[B]
    [22] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[B]
    [23] -1    0    0x0000fc00 - 0x0000fc3f (0x40) IX[B]
    [24] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
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
(==) AIGLX enabled
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
(II) Matched ati from file name ati.ids in autoconfig
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 6.8.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 4.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
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
(II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI Radeon X550XTX (RV370) 5657 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
    ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
    ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 02:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon HD 2600 Pro found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [5] -1    0    0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
    [6] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
    [7] -1    0    0xfe028000 - 0xfe02bfff (0x4000) MX[B]
    [8] -1    0    0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [10] -1    0    0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
    [11] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [14] -1    0    0x0000d800 - 0x0000d80f (0x10) IX[B]
    [15] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [16] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [17] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [18] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [19] -1    0    0x0000ec00 - 0x0000ec07 (0x8) IX[B]
    [20] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [21] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[B]
    [22] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[B]
    [23] -1    0    0x0000fc00 - 0x0000fc3f (0x40) IX[B]
    [24] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [5] -1    0    0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
    [6] -1    0    0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
    [7] -1    0    0xfe028000 - 0xfe02bfff (0x4000) MX[B]
    [8] -1    0    0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [10] -1    0    0xfdde0000 - 0xfddeffff (0x10000) MX[B](B)
    [11] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [12] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [13] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [14] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [15] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [16] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [17] -1    0    0x0000d800 - 0x0000d80f (0x10) IX[B]
    [18] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [19] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [20] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [21] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [22] -1    0    0x0000ec00 - 0x0000ec07 (0x8) IX[B]
    [23] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[B]
    [24] -1    0    0x0000f400 - 0x0000f43f (0x40) IX[B]
    [25] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[B]
    [26] -1    0    0x0000fc00 - 0x0000fc3f (0x40) IX[B]
    [27] -1    0    0x0000bc00 - 0x0000bcff (0x100) IX[B](B)
    [28] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [29] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000fdde0000: size 64KB
(II) RADEON(0): PCI bus 2 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon HD 2600 Pro" (ChipID = 0x9589)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(II) RADEON(0): PCIE card detected
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): Getting BIOS copy from legacy VBIOS location
(II) RADEON(0): ATOM BIOS Rom:
    SubsystemVendorID: 0x17af SubsystemID: 0x2002
    IOBaseAddress: 0xbc00
    Filename: SX41504.bin
    BIOS Bootup Message: 
113-00SG2H02-00R-HT RV630PRO PCIE 256M DDR2 DVI-I\VO\DVI-I 525M/650E         
(II) RADEON(0): Framebuffer space used by Firmware (kb): 19
(II) RADEON(0): Start of VRAM area used by Firmware: 0xfffb400
(II) RADEON(0): Framebuffer space used by Firmware (kb): 19
(II) RADEON(0): Start of VRAM area used by Firmware: 0xfffb400
(II) RADEON(0): AtomBIOS requests 19kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffb400
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 650000
(II) RADEON(0): Default Memory Clock: 525000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
(II) RADEON(0): Direct rendering not officially supported on RN50/RC410/R600
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 650.000000, mclk: 525.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 0002 02
src object id 2113 19
src object id 2116 22
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[1] EngineID: 1 I2CAddr: 0
record type 2
record type 4
object id 000f 01
src object id 2116 22
record type 4
record type 7
object id 0002 02
src object id 210f 15
src object id 2115 21
record type 1
 rhdAtomParseI2CRecord:  I2C Record: HW_Line[0] EngineID: 1 I2CAddr: 0
record type 2
record type 4
(II) RADEON(0): Output DVI-1 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC NTSC-J PAL PAL-M
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x7e50
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DIN
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- Primary
 TMDS Type -- LVTMA
 DDC Type  -- 0x7e40
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
```

---

### Post by markbuntu on 2008-07-15
That says that you are using the open source Radeon driver, not the restricted fglrx driver from ati. This driver is somewhat incomplete for your card.

Check in Hardware Drivers that the restricted driver is "in use".

Your monitor is also not talking to your computer so the system is guessing at its capabilities. It could be the Radeon driver, I am not very familiar with it. 

Try another monitor.

Xorg.0.log should say "fglrx" instead of "Radeon" if you are using the restricted driver.

---

### Post by Turboaaa2001 on 2008-07-16
I connected the system to another monitor and it was able to read it. It even changed the resolution to the screen's native res.

Sadly the driver issue continued. I never have this issue with nVidia cards.

I have decided to give up making this into a gaming Linux build for now.

Thanks for all your help.

---

