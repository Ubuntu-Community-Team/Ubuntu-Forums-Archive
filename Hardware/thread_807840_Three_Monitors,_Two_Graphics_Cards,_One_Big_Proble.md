---
title: "Three Monitors, Two Graphics Cards, One Big Problem"
date: 2008-05-26
forum: Hardware
---

### Post by jak on 2008-05-26
I've got three screens, a 17" on the left, 22" in the center and 17" on the right.
The left 17" (COMPAQ FP7317) and 22" (Acer AL2202W) are plugged into a nvidia 7600 GS card are currently work with TwinView which was configured using nvidia-settings.

Now I've got back from University for this year and have a bit more space in my room, I've put an older ATI Radeon 9200SE PCI card in, and put my righthand 17" (Samsung Samtron 73v) into that.

I've configured xorg.conf the best I could, obviously getting rid of TwinView for the combination of nvidia and ati cards, and trying Xinerama.

The problem is Xorg seems to load, shows the nVidia logo on the left and middle screens which then disappears but instead of showing the login screen it simply repeats this again and again. This Xorg.0.log shows this as the last two lines I believe.

My Xorg.0.log:
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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.1)
Current Operating System: Linux desktop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686
Build Date: 21 May 2008  12:19:32PM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 26 02:11:11 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Screen "Screen2" (2)
(**) |   |-->Monitor "Monitor2"
(**) |   |-->Device "Videocard2"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "1"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
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
(II) PCI: 00:00:0: chip 8086,2578 card 8086,2578 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 8086,257b card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 8086,257e card 8086,257e rev 02 class 08,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1014,02a7 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1014,02a7 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1014,02a7 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1014,02a7 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1014,02a7 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1014,02a7 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1014,02a7 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1014,02a7 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1014,1f00 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,02e1 card 1043,8237 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 8086,1019 card 1014,02a7 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:04:0: chip 1814,0201 card 1462,6834 rev 01 class 02,80,00 hdr 00
(II) PCI: 03:05:0: chip 9005,801e card 1014,005e rev 03 class 01,00,00 hdr 00
(II) PCI: 03:06:0: chip 1516,0803 card 0000,0000 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:08:0: chip 104c,8023 card 1014,028a rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:0a:0: chip 1002,5964 card 174b,7c25 rev 01 class 03,00,00 hdr 80
(II) PCI: 03:0a:1: chip 1002,5d44 card 174b,7c24 rev 01 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xf2000000 - 0xf4ffffff (0x3000000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x00009000 - 0x000090ff (0x100) IX[b]
    [1] -1    0    0x00009400 - 0x000094ff (0x100) IX[b]
    [2] -1    0    0x00009800 - 0x000098ff (0x100) IX[b]
    [3] -1    0    0x00009c00 - 0x00009cff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xf5000000 - 0xf50fffff (0x100000) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
    [0] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [1] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [2] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [3] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b]
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xf0000000 - 0xf1ffffff (0x2000000) MX[b]
(II) Bus 3 prefetchable memory range:
    [0] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G73 [GeForce 7600 GS] rev 162, Mem @ 0xf2000000/24, 0xd0000000/28, 0xf3000000/24
(--) PCI: (3:10:0) ATI Technologies Inc RV280 [Radeon 9200 SE] rev 1, Mem @ 0xe0000000/27, 0xf1000000/16, I/O @ 0xac00/8, BIOS @ 0xf0080000/17
(--) PCI: (3:10:1) ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) rev 1, Mem @ 0xe8000000/27, 0xf1010000/16
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
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xf1020000 - 0xf1023fff (0x4000) MX[b]
    [1] -1    0    0xf1028000 - 0xf10287ff (0x800) MX[b]
    [2] -1    0    0xf1029000 - 0xf10293ff (0x400) MX[b]
    [3] -1    0    0xf1026000 - 0xf1027fff (0x2000) MX[b]
    [4] -1    0    0xf1024000 - 0xf1025fff (0x2000) MX[b]
    [5] -1    0    0xf5000000 - 0xf501ffff (0x20000) MX[b]
    [6] -1    0    0xf5102000 - 0xf51020ff (0x100) MX[b]
    [7] -1    0    0xf5101000 - 0xf51011ff (0x200) MX[b]
    [8] -1    0    0xa0000000 - 0xa00003ff (0x400) MX[b]
    [9] -1    0    0xf5100000 - 0xf51003ff (0x400) MX[b]
    [10] -1    0    0xfecf0000 - 0xfecf0fff (0x1000) MX[b]
    [11] -1    0    0xc0000000 - 0xbfffffff (0x0) MX[b]O
    [12] -1    0    0xf3000000 - 0xf3ffffff (0x1000000) MX[b](B)
    [13] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [14] -1    0    0xf2000000 - 0xf2ffffff (0x1000000) MX[b](B)
    [15] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [16] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [17] -1    0    0x0000dc00 - 0x0000dc3f (0x40) IX[b]
    [18] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [19] -1    0    0x00000500 - 0x0000051f (0x20) IX[b]
    [20] -1    0    0x0000d000 - 0x0000d00f (0x10) IX[b]
    [21] -1    0    0x0000cc00 - 0x0000cc03 (0x4) IX[b]
    [22] -1    0    0x0000c800 - 0x0000c807 (0x8) IX[b]
    [23] -1    0    0x0000c400 - 0x0000c403 (0x4) IX[b]
    [24] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[b]
    [25] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [26] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [27] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [28] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [29] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [30] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[b]
    [31] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [32] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [33] -1    0    0x0000bc00 - 0x0000bc1f (0x20) IX[b]
(II) Inactive PCI resource ranges:
    [0] -1    0    0xf1010000 - 0xf101ffff (0x10000) MX[b](B)
    [1] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [2] -1    0    0xf0080000 - 0xf009ffff (0x20000) MX[b](B)
    [3] -1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b](B)
    [4] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [5] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [6] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [7] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xf1020000 - 0xf1023fff (0x4000) MX[b]
    [1] -1    0    0xf1028000 - 0xf10287ff (0x800) MX[b]
    [2] -1    0    0xf1029000 - 0xf10293ff (0x400) MX[b]
    [3] -1    0    0xf1026000 - 0xf1027fff (0x2000) MX[b]
    [4] -1    0    0xf1024000 - 0xf1025fff (0x2000) MX[b]
    [5] -1    0    0xf5000000 - 0xf501ffff (0x20000) MX[b]
    [6] -1    0    0xf5102000 - 0xf51020ff (0x100) MX[b]
    [7] -1    0    0xf5101000 - 0xf51011ff (0x200) MX[b]
    [8] -1    0    0xa0000000 - 0xa00003ff (0x400) MX[b]
    [9] -1    0    0xf5100000 - 0xf51003ff (0x400) MX[b]
    [10] -1    0    0xfecf0000 - 0xfecf0fff (0x1000) MX[b]
    [11] -1    0    0xc0000000 - 0xbfffffff (0x0) MX[b]O
    [12] -1    0    0xf3000000 - 0xf3ffffff (0x1000000) MX[b](B)
    [13] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [14] -1    0    0xf2000000 - 0xf2ffffff (0x1000000) MX[b](B)
    [15] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [16] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [17] -1    0    0x0000dc00 - 0x0000dc3f (0x40) IX[b]
    [18] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [19] -1    0    0x00000500 - 0x0000051f (0x20) IX[b]
    [20] -1    0    0x0000d000 - 0x0000d00f (0x10) IX[b]
    [21] -1    0    0x0000cc00 - 0x0000cc03 (0x4) IX[b]
    [22] -1    0    0x0000c800 - 0x0000c807 (0x8) IX[b]
    [23] -1    0    0x0000c400 - 0x0000c403 (0x4) IX[b]
    [24] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[b]
    [25] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [26] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [27] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [28] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [29] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [30] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[b]
    [31] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [32] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [33] -1    0    0x0000bc00 - 0x0000bc1f (0x20) IX[b]
(II) Inactive PCI resource ranges after removing overlaps:
    [0] -1    0    0xf1010000 - 0xf101ffff (0x10000) MX[b](B)
    [1] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [2] -1    0    0xf0080000 - 0xf009ffff (0x20000) MX[b](B)
    [3] -1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b](B)
    [4] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [5] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [6] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [7] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b](B)
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
    [4] -1    0    0xf1020000 - 0xf1023fff (0x4000) MX[b]
    [5] -1    0    0xf1028000 - 0xf10287ff (0x800) MX[b]
    [6] -1    0    0xf1029000 - 0xf10293ff (0x400) MX[b]
    [7] -1    0    0xf1026000 - 0xf1027fff (0x2000) MX[b]
    [8] -1    0    0xf1024000 - 0xf1025fff (0x2000) MX[b]
    [9] -1    0    0xf5000000 - 0xf501ffff (0x20000) MX[b]
    [10] -1    0    0xf5102000 - 0xf51020ff (0x100) MX[b]
    [11] -1    0    0xf5101000 - 0xf51011ff (0x200) MX[b]
    [12] -1    0    0xa0000000 - 0xa00003ff (0x400) MX[b]
    [13] -1    0    0xf5100000 - 0xf51003ff (0x400) MX[b]
    [14] -1    0    0xfecf0000 - 0xfecf0fff (0x1000) MX[b]
    [15] -1    0    0xc0000000 - 0xbfffffff (0x0) MX[b]O
    [16] -1    0    0xf3000000 - 0xf3ffffff (0x1000000) MX[b](B)
    [17] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [18] -1    0    0xf2000000 - 0xf2ffffff (0x1000000) MX[b](B)
    [19] -1    0    0xf1010000 - 0xf101ffff (0x10000) MX[b](B)
    [20] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [21] -1    0    0xf0080000 - 0xf009ffff (0x20000) MX[b](B)
    [22] -1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b](B)
    [23] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [26] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [27] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [28] -1    0    0x0000dc00 - 0x0000dc3f (0x40) IX[b]
    [29] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [30] -1    0    0x00000500 - 0x0000051f (0x20) IX[b]
    [31] -1    0    0x0000d000 - 0x0000d00f (0x10) IX[b]
    [32] -1    0    0x0000cc00 - 0x0000cc03 (0x4) IX[b]
    [33] -1    0    0x0000c800 - 0x0000c807 (0x8) IX[b]
    [34] -1    0    0x0000c400 - 0x0000c403 (0x4) IX[b]
    [35] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[b]
    [36] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [37] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [38] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [39] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [40] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [41] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[b]
    [42] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [43] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [44] -1    0    0x0000bc00 - 0x0000bc1f (0x20) IX[b]
    [45] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [46] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [47] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b](B)
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
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
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
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 4.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
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
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
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
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
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
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf1020000 - 0xf1023fff (0x4000) MX[b]
    [5] -1    0    0xf1028000 - 0xf10287ff (0x800) MX[b]
    [6] -1    0    0xf1029000 - 0xf10293ff (0x400) MX[b]
    [7] -1    0    0xf1026000 - 0xf1027fff (0x2000) MX[b]
    [8] -1    0    0xf1024000 - 0xf1025fff (0x2000) MX[b]
    [9] -1    0    0xf5000000 - 0xf501ffff (0x20000) MX[b]
    [10] -1    0    0xf5102000 - 0xf51020ff (0x100) MX[b]
    [11] -1    0    0xf5101000 - 0xf51011ff (0x200) MX[b]
    [12] -1    0    0xa0000000 - 0xa00003ff (0x400) MX[b]
    [13] -1    0    0xf5100000 - 0xf51003ff (0x400) MX[b]
    [14] -1    0    0xfecf0000 - 0xfecf0fff (0x1000) MX[b]
    [15] -1    0    0xc0000000 - 0xbfffffff (0x0) MX[b]O
    [16] -1    0    0xf3000000 - 0xf3ffffff (0x1000000) MX[b](B)
    [17] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [18] -1    0    0xf2000000 - 0xf2ffffff (0x1000000) MX[b](B)
    [19] -1    0    0xf1010000 - 0xf101ffff (0x10000) MX[b](B)
    [20] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [21] -1    0    0xf0080000 - 0xf009ffff (0x20000) MX[b](B)
    [22] -1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b](B)
    [23] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [26] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [27] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [28] -1    0    0x0000dc00 - 0x0000dc3f (0x40) IX[b]
    [29] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [30] -1    0    0x00000500 - 0x0000051f (0x20) IX[b]
    [31] -1    0    0x0000d000 - 0x0000d00f (0x10) IX[b]
    [32] -1    0    0x0000cc00 - 0x0000cc03 (0x4) IX[b]
    [33] -1    0    0x0000c800 - 0x0000c807 (0x8) IX[b]
    [34] -1    0    0x0000c400 - 0x0000c403 (0x4) IX[b]
    [35] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[b]
    [36] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [37] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [38] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [39] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [40] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [41] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[b]
    [42] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [43] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [44] -1    0    0x0000bc00 - 0x0000bc1f (0x20) IX[b]
    [45] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [46] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [47] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b](B)
(WW) RADEON: No matching Device section for instance (BusID PCI:3:10:1) found
(--) Chipset ATI Radeon 9200SE 5964 (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf1020000 - 0xf1023fff (0x4000) MX[b]
    [5] -1    0    0xf1028000 - 0xf10287ff (0x800) MX[b]
    [6] -1    0    0xf1029000 - 0xf10293ff (0x400) MX[b]
    [7] -1    0    0xf1026000 - 0xf1027fff (0x2000) MX[b]
    [8] -1    0    0xf1024000 - 0xf1025fff (0x2000) MX[b]
    [9] -1    0    0xf5000000 - 0xf501ffff (0x20000) MX[b]
    [10] -1    0    0xf5102000 - 0xf51020ff (0x100) MX[b]
    [11] -1    0    0xf5101000 - 0xf51011ff (0x200) MX[b]
    [12] -1    0    0xa0000000 - 0xa00003ff (0x400) MX[b]
    [13] -1    0    0xf5100000 - 0xf51003ff (0x400) MX[b]
    [14] -1    0    0xfecf0000 - 0xfecf0fff (0x1000) MX[b]
    [15] -1    0    0xc0000000 - 0xbfffffff (0x0) MX[b]O
    [16] -1    0    0xf3000000 - 0xf3ffffff (0x1000000) MX[b](B)
    [17] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [18] -1    0    0xf2000000 - 0xf2ffffff (0x1000000) MX[b](B)
    [19] -1    0    0xf1010000 - 0xf101ffff (0x10000) MX[b](B)
    [20] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [21] -1    0    0xf0080000 - 0xf009ffff (0x20000) MX[b](B)
    [22] -1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b](B)
    [23] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [26] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [27] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [28] -1    0    0x0000dc00 - 0x0000dc3f (0x40) IX[b]
    [29] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [30] -1    0    0x00000500 - 0x0000051f (0x20) IX[b]
    [31] -1    0    0x0000d000 - 0x0000d00f (0x10) IX[b]
    [32] -1    0    0x0000cc00 - 0x0000cc03 (0x4) IX[b]
    [33] -1    0    0x0000c800 - 0x0000c807 (0x8) IX[b]
    [34] -1    0    0x0000c400 - 0x0000c403 (0x4) IX[b]
    [35] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[b]
    [36] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [37] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [38] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [39] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [40] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [41] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[b]
    [42] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [43] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [44] -1    0    0x0000bc00 - 0x0000bc1f (0x20) IX[b]
    [45] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [46] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [47] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf1020000 - 0xf1023fff (0x4000) MX[b]
    [5] -1    0    0xf1028000 - 0xf10287ff (0x800) MX[b]
    [6] -1    0    0xf1029000 - 0xf10293ff (0x400) MX[b]
    [7] -1    0    0xf1026000 - 0xf1027fff (0x2000) MX[b]
    [8] -1    0    0xf1024000 - 0xf1025fff (0x2000) MX[b]
    [9] -1    0    0xf5000000 - 0xf501ffff (0x20000) MX[b]
    [10] -1    0    0xf5102000 - 0xf51020ff (0x100) MX[b]
    [11] -1    0    0xf5101000 - 0xf51011ff (0x200) MX[b]
    [12] -1    0    0xa0000000 - 0xa00003ff (0x400) MX[b]
    [13] -1    0    0xf5100000 - 0xf51003ff (0x400) MX[b]
    [14] -1    0    0xfecf0000 - 0xfecf0fff (0x1000) MX[b]
    [15] -1    0    0xc0000000 - 0xbfffffff (0x0) MX[b]O
    [16] -1    0    0xf3000000 - 0xf3ffffff (0x1000000) MX[b](B)
    [17] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [18] -1    0    0xf2000000 - 0xf2ffffff (0x1000000) MX[b](B)
    [19] -1    0    0xf1010000 - 0xf101ffff (0x10000) MX[b](B)
    [20] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [21] -1    0    0xf0080000 - 0xf009ffff (0x20000) MX[b](B)
    [22] -1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b](B)
    [23] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [27] 1    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [28] 1    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [29] 1    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [32] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [33] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [34] -1    0    0x0000dc00 - 0x0000dc3f (0x40) IX[b]
    [35] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [36] -1    0    0x00000500 - 0x0000051f (0x20) IX[b]
    [37] -1    0    0x0000d000 - 0x0000d00f (0x10) IX[b]
    [38] -1    0    0x0000cc00 - 0x0000cc03 (0x4) IX[b]
    [39] -1    0    0x0000c800 - 0x0000c807 (0x8) IX[b]
    [40] -1    0    0x0000c400 - 0x0000c403 (0x4) IX[b]
    [41] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[b]
    [42] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [43] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [44] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [45] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [46] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [47] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[b]
    [48] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [49] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [50] -1    0    0x0000bc00 - 0x0000bc1f (0x20) IX[b]
    [51] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [52] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [53] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b](B)
    [54] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [55] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
    [56] 1    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [57] 1    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Setting vga for screen 2.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-1"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.61.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     Acer AL2202W (CRT-0)
(--) NVIDIA(0):     COMPAQ FP7317 (CRT-1)
(--) NVIDIA(0): Acer AL2202W (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): COMPAQ FP7317 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (90, 91); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(1): Creating default Display subsection in Screen section
    "Screen1" for depth/fbbpp 24/32
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "CRT-1: nvidia-auto-select +0+0"
(**) NVIDIA(1): Option "TwinViewXineramaInfoOrder" "CRT-1"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.73.22.61.00
(II) NVIDIA(1): Detected AGP rate: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(1):     Acer AL2202W (CRT-0)
(--) NVIDIA(1):     COMPAQ FP7317 (CRT-1)
(--) NVIDIA(1): Acer AL2202W (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): COMPAQ FP7317 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
(II) NVIDIA(1): Assigned Display Device: CRT-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "CRT-1:nvidia-auto-select+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(1): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
(==) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(II) RADEON(2): MMIO registers at 0x00000000f1000000: size 64KB
(II) RADEON(2): PCI bus 3 card 10 func 0
(**) RADEON(2): Depth 24, (--) framebuffer bpp 32
(II) RADEON(2): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(2): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(2): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(2): RGB weight 888
(II) RADEON(2): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(2): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:03:0a.0/rom: got 52KB
(--) RADEON(2): Chipset: "ATI Radeon 9200SE 5964 (AGP)" (ChipID = 0x5964)
(--) RADEON(2): Linear framebuffer at 0x00000000e0000000
(--) RADEON(2): BIOS at 0xf0080000
(II) RADEON(2): PCI card detected
(II) RADEON(2): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:03:0a.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:03:0a.0
(II) RADEON(2): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(2): Page Flipping disabled
(II) RADEON(2): Will try to use DMA for Xv image transfers
(II) RADEON(2): Generation 2 PCI interface, using max accessible memory
(II) RADEON(2): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(2): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(2): Color tiling enabled by default
(II) RADEON(2): Max desktop size set to 2048x1200
(II) RADEON(2): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(2): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(2): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 16600, sclk: 166.000000, mclk: 200.000000
(II) RADEON(2): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=16600
(II) RADEON(2): Bios Connector table: 
(II) RADEON(2): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(2): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(2): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(2): Output VGA-0 using monitor section Monitor2
(II) RADEON(2): I2C bus "VGA-0" initialized.
(II) RADEON(2): Output DVI-0 has no monitor section
(II) RADEON(2): DFP table revision: 4
(II) RADEON(2): I2C bus "DVI-0" initialized.
(II) RADEON(2): Output S-video has no monitor section
(II) RADEON(2): Default TV standard: PAL
(II) RADEON(2): TV standards supported by chip: NTSC PAL 
(II) RADEON(2): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(2): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(2): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(2): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(2): EDID vendor "STN", prod id 33
(II) RADEON(2): Using hsync ranges from config file
(II) RADEON(2): Using vrefresh ranges from config file
(II) RADEON(2): Printing DDC gathered Modelines:
(II) RADEON(2): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(2): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(2): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(2): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(2): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(2): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(2): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(2): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(2): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(2): Manufacturer: STN  Model: 21  Serial#: 1196634423
(II) RADEON(2): Year: 2005  Week: 1
(II) RADEON(2): EDID Version: 1.3
(II) RADEON(2): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(2): Sync:  Separate  Composite
(II) RADEON(2): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(2): Gamma: 2.20
(II) RADEON(2): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(2): First detailed timing is preferred mode
(II) RADEON(2): redX: 0.633 redY: 0.351   greenX: 0.298 greenY: 0.592
(II) RADEON(2): blueX: 0.143 blueY: 0.092   whiteX: 0.316 whiteY: 0.337
(II) RADEON(2): Supported VESA Video Modes:
(II) RADEON(2): 720x400@70Hz
(II) RADEON(2): 640x480@60Hz
(II) RADEON(2): 640x480@67Hz
(II) RADEON(2): 640x480@72Hz
(II) RADEON(2): 640x480@75Hz
(II) RADEON(2): 800x600@56Hz
(II) RADEON(2): 800x600@60Hz
(II) RADEON(2): 800x600@72Hz
(II) RADEON(2): 800x600@75Hz
(II) RADEON(2): 832x624@75Hz
(II) RADEON(2): 1024x768@60Hz
(II) RADEON(2): 1024x768@70Hz
(II) RADEON(2): 1024x768@75Hz
(II) RADEON(2): 1280x1024@75Hz
(II) RADEON(2): 1152x870@75Hz
(II) RADEON(2): Manufacturer's mask: 0
(II) RADEON(2): Supported Future Video Modes:
(II) RADEON(2): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(2): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(2): Supported additional Video Mode:
(II) RADEON(2): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(2): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(2): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(2): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(2): Monitor name: SAMTRON
(II) RADEON(2): Serial No: H9NY102300
(II) RADEON(2): EDID (in hex):
(II) RADEON(2):     00ffffffffffff004e8e210037315347
(II) RADEON(2):     010f01036c221b782a36a1a2594c9724
(II) RADEON(2):     175156bfef808180714f010101010101
(II) RADEON(2):     010101010101302a009851002a403070
(II) RADEON(2):     1300520e1100001e000000fd00384b1e
(II) RADEON(2):     510e000a202020202020000000fc0053
(II) RADEON(2):     414d54524f4e0a2020202020000000ff
(II) RADEON(2):     0048394e593130323330300a202000ff
finished output detect: 0
(II) RADEON(2): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(2): I2C device "DVI-0:ddc2" removed.
(II) RADEON(2): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(2): I2C device "DVI-0:ddc2" removed.
(II) RADEON(2): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(2): I2C device "DVI-0:ddc2" removed.
(II) RADEON(2): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(2): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(2): EDID vendor "STN", prod id 33
(II) RADEON(2): Using hsync ranges from config file
(II) RADEON(2): Using vrefresh ranges from config file
(II) RADEON(2): Printing DDC gathered Modelines:
(II) RADEON(2): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(2): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(2): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(2): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(2): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(2): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(2): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(2): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(2): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(2): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(2): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(2): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(2): Manufacturer: STN  Model: 21  Serial#: 1196634423
(II) RADEON(2): Year: 2005  Week: 1
(II) RADEON(2): EDID Version: 1.3
(II) RADEON(2): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(2): Sync:  Separate  Composite
(II) RADEON(2): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(2): Gamma: 2.20
(II) RADEON(2): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(2): First detailed timing is preferred mode
(II) RADEON(2): redX: 0.633 redY: 0.351   greenX: 0.298 greenY: 0.592
(II) RADEON(2): blueX: 0.143 blueY: 0.092   whiteX: 0.316 whiteY: 0.337
(II) RADEON(2): Supported VESA Video Modes:
(II) RADEON(2): 720x400@70Hz
(II) RADEON(2): 640x480@60Hz
(II) RADEON(2): 640x480@67Hz
(II) RADEON(2): 640x480@72Hz
(II) RADEON(2): 640x480@75Hz
(II) RADEON(2): 800x600@56Hz
(II) RADEON(2): 800x600@60Hz
(II) RADEON(2): 800x600@72Hz
(II) RADEON(2): 800x600@75Hz
(II) RADEON(2): 832x624@75Hz
(II) RADEON(2): 1024x768@60Hz
(II) RADEON(2): 1024x768@70Hz
(II) RADEON(2): 1024x768@75Hz
(II) RADEON(2): 1280x1024@75Hz
(II) RADEON(2): 1152x870@75Hz
(II) RADEON(2): Manufacturer's mask: 0
(II) RADEON(2): Supported Future Video Modes:
(II) RADEON(2): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(2): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(2): Supported additional Video Mode:
(II) RADEON(2): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(2): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(2): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(2): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(2): Monitor name: SAMTRON
(II) RADEON(2): Serial No: H9NY102300
(II) RADEON(2): EDID (in hex):
(II) RADEON(2):     00ffffffffffff004e8e210037315347
(II) RADEON(2):     010f01036c221b782a36a1a2594c9724
(II) RADEON(2):     175156bfef808180714f010101010101
(II) RADEON(2):     010101010101302a009851002a403070
(II) RADEON(2):     1300520e1100001e000000fd00384b1e
(II) RADEON(2):     510e000a202020202020000000fc0053
(II) RADEON(2):     414d54524f4e0a2020202020000000ff
(II) RADEON(2):     0048394e593130323330300a202000ff
in RADEONProbeOutputModes
(II) RADEON(2): EDID vendor "STN", prod id 33
(II) RADEON(2): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(2): I2C device "DVI-0:ddc2" removed.
(II) RADEON(2): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(2): I2C device "DVI-0:ddc2" removed.
(II) RADEON(2): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(2): I2C device "DVI-0:ddc2" removed.
(II) RADEON(2): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(2): Detected non-DDC Monitor Type: 0
(II) RADEON(2): Output VGA-0 connected
(II) RADEON(2): Output DVI-0 disconnected
(II) RADEON(2): Output S-video disconnected
(II) RADEON(2): Output VGA-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(2): Display dimensions: (340, 270) mm
(**) RADEON(2): DPI set to (95, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(==) RADEON(2): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(2): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.2.0
    ABI class: X.Org Video Driver, version 2.0
(==) RADEON(2): Assuming overlay scaler buffer width is 1536
(II) RADEON(2): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(2): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(!!) RADEON(2): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
    [0] 1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b]
    [1] 1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [6] -1    0    0xf1020000 - 0xf1023fff (0x4000) MX[b]
    [7] -1    0    0xf1028000 - 0xf10287ff (0x800) MX[b]
    [8] -1    0    0xf1029000 - 0xf10293ff (0x400) MX[b]
    [9] -1    0    0xf1026000 - 0xf1027fff (0x2000) MX[b]
    [10] -1    0    0xf1024000 - 0xf1025fff (0x2000) MX[b]
    [11] -1    0    0xf5000000 - 0xf501ffff (0x20000) MX[b]
    [12] -1    0    0xf5102000 - 0xf51020ff (0x100) MX[b]
    [13] -1    0    0xf5101000 - 0xf51011ff (0x200) MX[b]
    [14] -1    0    0xa0000000 - 0xa00003ff (0x400) MX[b]
    [15] -1    0    0xf5100000 - 0xf51003ff (0x400) MX[b]
    [16] -1    0    0xfecf0000 - 0xfecf0fff (0x1000) MX[b]
    [17] -1    0    0xc0000000 - 0xbfffffff (0x0) MX[b]O
    [18] -1    0    0xf3000000 - 0xf3ffffff (0x1000000) MX[b](B)
    [19] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [20] -1    0    0xf2000000 - 0xf2ffffff (0x1000000) MX[b](B)
    [21] -1    0    0xf1010000 - 0xf101ffff (0x10000) MX[b](B)
    [22] -1    0    0xe8000000 - 0xefffffff (0x8000000) MX[b](B)
    [23] -1    0    0xf0080000 - 0xf009ffff (0x20000) MX[b](B)
    [24] -1    0    0xf1000000 - 0xf100ffff (0x10000) MX[b](B)
    [25] -1    0    0xe0000000 - 0xe7ffffff (0x8000000) MX[b](B)
    [26] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [27] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [28] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [29] 1    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
    [30] 1    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
    [31] 1    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
    [32] 1    0    0x0000ac00 - 0x0000acff (0x100) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [35] -1    0    0x0000a800 - 0x0000a8ff (0x100) IX[b]
    [36] -1    0    0x00009000 - 0x0000901f (0x20) IX[b]
    [37] -1    0    0x0000dc00 - 0x0000dc3f (0x40) IX[b]
    [38] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [39] -1    0    0x00000500 - 0x0000051f (0x20) IX[b]
    [40] -1    0    0x0000d000 - 0x0000d00f (0x10) IX[b]
    [41] -1    0    0x0000cc00 - 0x0000cc03 (0x4) IX[b]
    [42] -1    0    0x0000c800 - 0x0000c807 (0x8) IX[b]
    [43] -1    0    0x0000c400 - 0x0000c403 (0x4) IX[b]
    [44] -1    0    0x0000c000 - 0x0000c007 (0x8) IX[b]
    [45] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [46] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [47] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [48] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [49] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [50] -1    0    0x0000b800 - 0x0000b81f (0x20) IX[b]
    [51] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [52] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [53] -1    0    0x0000bc00 - 0x0000bc1f (0x20) IX[b]
    [54] -1    0    0x0000a400 - 0x0000a4ff (0x100) IX[b]
    [55] -1    0    0x0000a000 - 0x0000a0ff (0x100) IX[b]
    [56] -1    0    0x0000ac00 - 0x0000acff (0x100) IX[b](B)
    [57] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [58] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
    [59] 1    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [60] 1    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Initialized AGP GART.
(II) NVIDIA(1): Setting mode "CRT-1:nvidia-auto-select+0+0"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) RADEON(2): RADEONScreenInit e0000000 0 0
(==) RADEON(2): Write-combining range (0xe0000000,0x8000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(2): Using 24 bit depth buffer
(II) RADEON(2): RADEONInitMemoryMap() : 
(II) RADEON(2):   mem_size         : 0x08000000
(II) RADEON(2):   MC_FB_LOCATION   : 0xe7ffe000
(II) RADEON(2):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(2): Depth moves disabled by default
(II) RADEON(2): CP in BM mode
(II) RADEON(2): Using 8 MB GART aperture
(II) RADEON(2): Using 1 MB for the ring buffer
(II) RADEON(2): Using 2 MB for vertex/indirect buffers
(II) RADEON(2): Using 5 MB for GART textures
(II) RADEON(2): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(2): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(2): Largest offscreen area available: 1280 x 6989
(II) RADEON(2): Will use front buffer at offset 0x0
(II) RADEON(2): Will use back buffer at offset 0x1838000
(II) RADEON(2): Will use depth buffer at offset 0x1e14000
(II) RADEON(2): Will use 94208 kb for textures at offset 0x23f0000
(WW) RADEON(2): Direct rendering is not supported when Xinerama is enabled
(EE) RADEON(2): [dri] DRIScreenInit failed.  Disabling DRI.
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(2): RADEONRestoreMemMapRegisters() : 
(II) RADEON(2):   MC_FB_LOCATION   : 0xe7ffe000 0x1fff0000
(II) RADEON(2):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(2): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(2): Backing store disabled
(WW) RADEON(2): Direct rendering disabled
(II) RADEON(2): Render acceleration enabled
(II) RADEON(2): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(II) RADEON(2): Acceleration enabled
(**) Option "dpms"
(**) RADEON(2): DPMS enabled
(==) RADEON(2): Silken mouse enabled
(II) RADEON(2): Using hardware cursor 0 (scanline 1202)
(II) RADEON(2): Using hardware cursor 1 (scanline 1205)
(II) RADEON(2): Largest offscreen area available: 1280 x 6982
(II) RADEON(2): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) RADEON(2): no multimedia table present, disabling Rage Theatre.
(II) RADEON(2): RandR 1.2 enabled, ignore the following RandR disabled message.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7ee4420]
2: /usr/bin/X(xf86RandR12SetRotations+0x6b) [0x80f9d2b]
3: /usr/bin/X(xf86CrtcScreenInit+0x9e) [0x80f588e]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONScreenInit+0x135a) [0xb790ef3a]
5: /usr/bin/X(AddScreen+0x1fc) [0x8073d9c]
6: /usr/bin/X(InitOutput+0x21e) [0x80a9c4e]
7: /usr/bin/X(main+0x296) [0x8074526]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c75450]
9: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 2 shares mem & io resources
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00001398, 0x00001398)
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x000013b4, 0x000013b4)
```And my xorg.conf :
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2202W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "COMPAQ FP7317"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "SAMTRON 73v"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection


Section "Device"
    Identifier     "Videocard2"
    Driver         "radeon"
    VendorName     "ATI"
    BoardName      "9200SE"
    BusID          "PCI:3:10:0"
    Screen          0
EndSection


Section "Screen"

# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1680+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +1280+0, CRT-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier  "Screen2"
    Device      "VideoCard2"
    Monitor     "Monitor2"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection


```I hope someone can help, theres a good chance I've failed to notice some simple error.. always forgetting the semi-colon in programming afterall.

Thanks,
Jak

---

### Post by jak on 2008-05-27
:(?

---

### Post by jak on 2008-05-28
Well I have three working screens. No Xinerama (but thats because I've yet to try it). And the third (right hand) screen is far from perfect as theres no video playback or 3D on it possible because I've resorted to the vesa driver.

My new xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
#    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2202W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "COMPAQ FP7317"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "SAMTRON 73v"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection


Section "Device"
    Identifier     "Videocard2"
    Driver         "vesa"
    VendorName     "ATI"
    BoardName      "9200SE"
    BusID          "PCI:3:10:0"
  #  Screen          0
EndSection


Section "Screen"

# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1680+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +1280+0, CRT-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier  "Screen2"
    Device      "VideoCard2"
    Monitor     "Monitor2"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
#        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
#        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
#        ViewPort    0 0
    EndSubsection
EndSection


```

If anyone has any suggestions about getting both nvidia and ati drivers to work together.... pleaaaase say! DPMS doesn't appear to work on the right screen either but is fine on the nvidia cards. Should I buy a PCI nvidia card? I saw a 6200 recently..

---

