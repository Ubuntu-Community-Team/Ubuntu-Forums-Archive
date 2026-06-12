---
title: "graphic problems I think"
date: 2009-01-18
forum: Hardware
---

### Post by DeltaFee on 2009-01-18
Hey I have a Toshiba satellite m35x-s329 and after installing ubuntu 8.04 I seem to have a problem. I can't drag and drop files into folders. I am not sure if this is a graphic card problem or a driver problem. I know that when I use 6.04 - 7.10 that I could do this. Thanks for the help.

---

### Post by taurus on 2009-01-18
Where do you want to drop the files to, directories?  Maybe it's more like a permission problem than a graphic problem.

---

### Post by DeltaFee on 2009-01-18
I mean like my home folder and folders that I create within my home directory. Also I noticed that the login entry window has enormous font. My laptop has a Intel extreme graphics chipset I notice on boot up there is a wrong driver being used.

---

### Post by densou on 2009-01-20
may I read your ```
/etc/X11/xorg.conf
``` and ```
/var/log/Xorg.0.log
``` ? (paste all here) :popcorn:

---

### Post by taurus on 2009-01-20
> **densou said:**
> may I read your ```
/etc/xorg.conf
```

Shouldn't it be /etc/X11/xorg.conf?

> ```
/var/Xorg.0.log
``` ? (paste all here) :popcorn:

Shouldn't this be /var/log/Xorg.0.log?

---

### Post by densou on 2009-01-20
> **taurus said:**
> *cut*

yeah lad, you're right .... I'm exausthed and still wandering here for helping Intel users :p

*time to get some sleep* nearly 2 a.m. :o

have a nice day ;)

---

### Post by DeltaFee on 2009-01-20
/var/log/x11.0.log
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
Current Operating System: Linux Defiant 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 20 15:19:09 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
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
(II) PCI: 00:00:0: chip 8086,3580 card 1179,ff00 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 1179,ff00 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 1179,ff00 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:02:0: chip 8086,3582 card 1179,ff00 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3582 card 1179,ff00 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,24c2 card 1179,ff00 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1179,ff00 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1179,ff00 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1179,ff00 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1179,ff00 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1179,ff00 rev 03 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1179,ff01 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1179,0001 rev 03 class 07,03,00 hdr 00
(II) PCI: 02:00:0: chip 1106,3044 card 1179,ff00 rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:01:0: chip 10ec,8139 card 1179,ff00 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 8086,4220 card 8086,2741 rev 05 class 02,80,00 hdr 00
(II) PCI: 02:04:0: chip 1524,1411 card 3800,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 02:04:1: chip 1524,0530 card 1179,ff00 rev 00 class 05,01,00 hdr 80
(II) PCI: 02:04:2: chip 1524,0550 card 1179,ff01 rev 00 class 08,05,01 hdr 80
(II) PCI: 02:04:3: chip 1524,0520 card 1179,ff00 rev 00 class 05,01,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe0200000 - 0xe02fffff (0x100000) MX[B]



---

### Post by DeltaFee on 2009-01-20
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[1] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(--) PCI:*(0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe8000000/27, 0xe0000000/19, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xf0000000/27, 0xe0080000/19
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

---

### Post by DeltaFee on 2009-01-20
(II) Active PCI resource ranges:
	[0] -1	0	0xe0202400 - 0xe020247f (0x80) MX[B]
	[1] -1	0	0xe0202000 - 0xe02020ff (0x100) MX[B]
	[2] -1	0	0xe0201c00 - 0xe0201c7f (0x80) MX[B]
	[3] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[4] -1	0	0xe0201800 - 0xe02018ff (0x100) MX[B]
	[5] -1	0	0xe0201000 - 0xe02017ff (0x800) MX[B]
	[6] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[7] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[8] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[9] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[10] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[16] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[17] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[18] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[21] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe0202400 - 0xe020247f (0x80) MX[B]
	[1] -1	0	0xe0202000 - 0xe02020ff (0x100) MX[B]
	[2] -1	0	0xe0201c00 - 0xe0201c7f (0x80) MX[B]
	[3] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[4] -1	0	0xe0201800 - 0xe02018ff (0x100) MX[B]
	[5] -1	0	0xe0201000 - 0xe02017ff (0x800) MX[B]
	[6] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[7] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[8] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[9] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[10] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[15] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[16] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[17] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[18] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[20] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[21] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]

---

### Post by DeltaFee on 2009-01-20
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0202400 - 0xe020247f (0x80) MX[B]
	[5] -1	0	0xe0202000 - 0xe02020ff (0x100) MX[B]
	[6] -1	0	0xe0201c00 - 0xe0201c7f (0x80) MX[B]
	[7] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[8] -1	0	0xe0201800 - 0xe02018ff (0x100) MX[B]
	[9] -1	0	0xe0201000 - 0xe02017ff (0x800) MX[B]
	[10] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[11] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[12] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[13] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[14] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[17] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[21] -1	0	0x00003400 - 0x0000347f (0x80) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[23] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[24] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[26] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[27] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)

---

### Post by DeltaFee on 2009-01-20
Testing
> 
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
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 852GM/855GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0202400 - 0xe020247f (0x80) MX[B]
	[5] -1	0	0xe0202000 - 0xe02020ff (0x100) MX[B]
	[6] -1	0	0xe0201c00 - 0xe0201c7f (0x80) MX[B]
	[7] -1	0	0xe0200000 - 0xe0200fff (0x1000) MX[B]
	[8] -1	0	0xe0201800 - 0xe02018ff (0x100) MX[B]
	[9] -1	0	0xe0201000 - 0xe02017ff (0x800) MX[B]
	[10] -1	0	0xe0100800 - 0xe01008ff (0x100) MX[B]
	[11] -1	0	0xe0100c00 - 0xe0100dff (0x200) MX[B]
	[12] -1	0	0x30000000 - 0x300003ff (0x400) MX[B]
	[13] -1	0	0xe0100000 - 0xe01003ff (0x400) MX[B]
	[14] -1	0	0xe0080000 - 0xe00fffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
	[17] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)


---

### Post by DeltaFee on 2009-01-20
**_/etc/X11/xorg.conf_**

> 
#xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


Sorry about the smilies

---

### Post by densou on 2009-01-23
**ALWAYS DO A BACKUP BEFORE EDITING**

I'd suggest to modify your xorg.conf into:
```

Section "Module"
	Load 	"bitmap"
	Load 	"ddc"
	Load 	"dbe"
	Load 	"dri"
	Load 	"extmod"
	Load 	"freetype"
	Load 	"glx"
	Load	"GLcore"
	Load 	"int10"
	Load 	"type1"
	Load	"v4l"
	Load 	"vbe"
EndSection


Section "Device"
        Identifier 	"intel"
        Driver     	"intel"
	Option          "AccelMethod"   "XAA"
	Option 		"AddARGBGLXVisuals" "On"
	Option 		"XAANoOffscreenPixmaps"		"true"
	Vendorname	"Intel"
EndSection

Section "DRI"
	Mode 	0666
EndSection

Section "Extensions"
	Option 		"Composite" 		"true"
EndSection

```

Note: add/edit the Sections mentioned ONLY ;)
Unless you perform an upgrade to Intrepid, you can't update Intel Video Drivers to a stable build (they require Xorg 1.5.x for working better).

---

### Post by DeltaFee on 2009-01-28
Heres after my edit of Xorg.conf not sure what I am doing wrong:

> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

#Edited
Section "Module"
	Load 	"bitmap"
	Load 	"ddc"
	Load 	"dbe"
	Load 	"dri"
	Load 	"extmod"
	Load 	"freetype"
	Load 	"glx"
	Load	"GLcore"
	Load 	"int10"
	Load 	"type1"
	Load	"v4l"
	Load 	"vbe"
EndSection
#UNEDITED

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

#EDIT
Section "Device"
	  Identifier 	"intel"
        Driver     	"intel"
	Option          "AccelMethod"   "XAA"
	Option 		"AddARGBGLXVisuals" "On"
	Option 		"XAANoOffscreenPixmaps"		"true"
	Vendorname	"Intel"
EndSection

Section "DRI"
	Mode 	0666
EndSection

Section "Extensions"
	Option 		"Composite" 		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
#End Edited

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


---

### Post by chomptown on 2009-04-20
> **densou said:**
> **ALWAYS DO A BACKUP BEFORE EDITING**

I'd suggest to modify your xorg.conf into:
```

Section "Module"
	Load 	"bitmap"
	Load 	"ddc"
	Load 	"dbe"
	Load 	"dri"
	Load 	"extmod"
	Load 	"freetype"
	Load 	"glx"
	Load	"GLcore"
	Load 	"int10"
	Load 	"type1"
	Load	"v4l"
	Load 	"vbe"
EndSection


Section "Device"
        Identifier 	"intel"
        Driver     	"intel"
	Option          "AccelMethod"   "XAA"
	Option 		"AddARGBGLXVisuals" "On"
	Option 		"XAANoOffscreenPixmaps"		"true"
	Vendorname	"Intel"
EndSection

Section "DRI"
	Mode 	0666
EndSection

Section "Extensions"
	Option 		"Composite" 		"true"
EndSection

```

Note: add/edit the Sections mentioned ONLY ;)
Unless you perform an upgrade to Intrepid, you can't update Intel Video Drivers to a stable build (they require Xorg 1.5.x for working better).

Thank you SOOOO much for this.  I've been searching for the right way to access the correct driver with the xorg.conf file for quite a while now.  It was originally using the "vesa" driver which only let me see 640x480 and I had no other options of screen size.  I'm using the Intel 845G onboard graphics processor.  I guess I'm just putting all of this info on here to let people know this is a great method of fixing the bug with our old onboard graphics processors.  Thanks again man.

---

### Post by densou on 2009-04-20
you're welcome, lad :KS

Be aware of i845 doesn't perform well as Hardy on both Intrepid and Jaunty.

You can also read [this thread]("http://ubuntuforums.org/showthread.php?t=1017426") about that purpose ;)

---

