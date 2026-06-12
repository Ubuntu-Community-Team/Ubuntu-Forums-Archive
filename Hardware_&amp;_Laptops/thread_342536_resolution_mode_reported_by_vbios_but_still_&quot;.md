---
title: "resolution mode reported by vbios but still &quot;no mode of this name&quot;!!!"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by j0sh0 on 2007-01-20
Hi all,
I'm desperately hoping someone can help me with an issue I'm having with my installation. First, the system specs:
HiGrade Notebook (based on FIC MB02), 1300MHz Pentium M(?)4, 256Meg RAM, intel 855gm integrated graphics, Edgy installation.
My problem is that I cannot get 1024x768 to display, at any depth, even though the vbios reports the mode for all supported depths (see Xorg.0.log). 

This is what I have tried so far: 
- reconfigured X with dpkg-reconfigure xserver-xorg NO LUCK
- removed refresh-rate lines from xorg.conf NO LUCK
- upgraded to the latest drivers (using apt-get) NO LUCK
- tried vesa driver NO LUCK
- used the test/hacked i810_drv.so driver from fairlite,demon.co.uk (?? not sure of exact address) NO LUCK
- installed 915resolution and overwritten one of the resolution modes I would never use with 1024x768 NO LUCK

I've searched the wiki, these forums, launchpad (? bug site), google but come up with nothing that has helped. Please, I've got no idea what to try next and surfing the web in 800x600 is excruciating! I can't work out why it wont allow me to choose 1024x768 when its listed in the vbios - from studying Xorg.0.log and the reported video modes, the only differences between the accessible resolutions (640x480 and 800x600, all depths) is the their ModeAttributes is 0x9b, whereas all other (inaccessible) resolutions are 0x9a. I've even tried overwriting 640x480 with 915resolution (hoping it would retain the 0x9b ModeAttribute) but X still reverts to 800x600.

Please I'm lost at what to do! I know there's got to be someone else out there who has had the same problem and fixed it!?!

All help greatly appreciated!
Regards

j0sh0

---

### Post by j0sh0 on 2007-01-20
Xorg.0.log:

[PHP]
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux laptop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 19 14:34:14 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3580 card 1509,2930 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 1509,2930 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 1509,2930 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:02:0: chip 8086,3582 card 1509,2930 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3582 card 1509,2930 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,24c2 card 1509,2990 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1509,2990 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1509,2990 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 8086,24c0 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1509,2990 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1509,2990 rev 03 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1509,2941 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1509,2970 rev 03 class 07,03,00 hdr 00
(II) PCI: 02:01:0: chip 8086,1043 card 8086,2527 rev 04 class 02,80,00 hdr 00
(II) PCI: 02:07:0: chip 1180,0475 card 3400,0000 rev b8 class 06,07,00 hdr 82
(II) PCI: 02:07:1: chip 1180,0551 card 1509,2980 rev 00 class 0c,00,10 hdr 80
(II) PCI: 02:08:0: chip 8086,103d card 1509,2920 rev 83 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 168c,001a card 1186,3a15 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
...
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:7:0), (2,3,6), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[1] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x28000000 - 0x29ffffff (0x2000000) MX[B]
(--) PCI:*(0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/27, 0xd0000000/19, I/O @ 0xde00/3
(--) PCI: (0:2:1) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0x20000000/27, 0x2a000000/19
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
	[0] -1	0	0x2c000000 - 0x2c00ffff (0x10000) MX[B]
	[1] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[2] -1	0	0xe8102000 - 0xe81027ff (0x800) MX[B]
	[3] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B]
	[4] -1	0	0xe8080800 - 0xe80808ff (0x100) MX[B]
	[5] -1	0	0xe8080c00 - 0xe8080dff (0x200) MX[B]
	[6] -1	0	0x2a080000 - 0x2a0803ff (0x400) MX[B]
	[7] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[8] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[11] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[12] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[13] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001100 - 0x0000111f (0x20) IX[B]
	[16] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[17] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[18] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[19] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[20] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x2a000000 - 0x2a07ffff (0x80000) MX[B](B)
	[1] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x2c000000 - 0x2c00ffff (0x10000) MX[B]
	[1] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[2] -1	0	0xe8102000 - 0xe81027ff (0x800) MX[B]
	[3] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B]
	[4] -1	0	0xe8080800 - 0xe80808ff (0x100) MX[B]
	[5] -1	0	0xe8080c00 - 0xe8080dff (0x200) MX[B]
	[6] -1	0	0x2a080000 - 0x2a0803ff (0x400) MX[B]
	[7] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[8] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[11] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[12] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[13] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001100 - 0x0000111f (0x20) IX[B]
	[16] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[17] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[18] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[19] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[20] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x2a000000 - 0x2a07ffff (0x80000) MX[B](B)
	[1] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x29ffffff (0x29f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x29ffffff (0x29f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x2c000000 - 0x2c00ffff (0x10000) MX[B]
	[5] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[6] -1	0	0xe8102000 - 0xe81027ff (0x800) MX[B]
	[7] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B]
	[8] -1	0	0xe8080800 - 0xe80808ff (0x100) MX[B]
	[9] -1	0	0xe8080c00 - 0xe8080dff (0x200) MX[B]
	[10] -1	0	0x2a080000 - 0x2a0803ff (0x400) MX[B]
	[11] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[12] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x2a000000 - 0x2a07ffff (0x80000) MX[B](B)
	[15] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[20] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[21] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00001100 - 0x0000111f (0x20) IX[B]
	[24] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[25] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[26] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[27] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[28] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.99.2, module version = 1.7.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(--) Chipset 852GM/855GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x29ffffff (0x29f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x2c000000 - 0x2c00ffff (0x10000) MX[B]
	[5] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[6] -1	0	0xe8102000 - 0xe81027ff (0x800) MX[B]
	[7] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B]
	[8] -1	0	0xe8080800 - 0xe80808ff (0x100) MX[B]
	[9] -1	0	0xe8080c00 - 0xe8080dff (0x200) MX[B]
	[10] -1	0	0x2a080000 - 0x2a0803ff (0x400) MX[B]
	[11] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[12] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x2a000000 - 0x2a07ffff (0x80000) MX[B](B)
	[15] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[20] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[21] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00001100 - 0x0000111f (0x20) IX[B]
	[24] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[25] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[26] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[27] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[28] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x29ffffff (0x29f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x2c000000 - 0x2c00ffff (0x10000) MX[B]
	[5] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[6] -1	0	0xe8102000 - 0xe81027ff (0x800) MX[B]
	[7] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B]
	[8] -1	0	0xe8080800 - 0xe80808ff (0x100) MX[B]
	[9] -1	0	0xe8080c00 - 0xe8080dff (0x200) MX[B]
	[10] -1	0	0x2a080000 - 0x2a0803ff (0x400) MX[B]
	[11] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[12] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x2a000000 - 0x2a07ffff (0x80000) MX[B](B)
	[15] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[16] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[23] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[24] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[25] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[26] -1	0	0x00001100 - 0x0000111f (0x20) IX[B]
	[27] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[28] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[29] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[30] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[31] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B](B)
	[32] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 16192 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 855GM
(--) I810(0): Chipset: "852GM/855GM"
(--) I810(0): Linear framebuffer at 0xD8000000
(--) I810(0): IO registers at addr 0xD0000000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 16252 kB stolen memory.
(II) I810(0): Kernel reported 48128 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 192508 kB available
(II) I810(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) I810(0): Monitoring connected displays enabled
(WW) I810(0): VideoRAM reduced to 12288 kByte (page aligned - was 16252)
(--) I810(0): Pre-allocated VideoRAM: 16252 kByte
(**) I810(0): VideoRAM: 12288 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2880
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (0,0)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Size of device LFP (local flat panel) is 1024 x 768
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1024 x 768
(==) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 12120 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1024x768
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12120 kByte
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006f3a
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 49
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 49
	LinNumberOfImagePages: 49
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006f3a
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006f3a
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 36 (1024x600)
	ModeAttributes: 0x9a
...removed extra video modes to allow post...
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006f3a
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 27
	LinNumberOfImagePages: 27
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006f3a
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9a
...snipped again...
Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0006f3a
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
...snipped again - you get the idea...
(II) I810(0): Generic Monitor: Using hsync range of 30.00-60.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): 1400 kBytes additional video memory is required to
	enable tiling mode for DRI.
(II) I810(0): 24 kBytes additional video memory is required to enable DRI.
(II) I810(0): Disabling DRI.
(--) I810(0): Virtual size is 800x600 (pitch 800)
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(==) I810(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 1	0	0xd0000000 - 0xd007ffff (0x80000) MS[B]
	[1] 1	0	0xd8000000 - 0xdfffffff (0x8000000) MS[B]
	[2] -1	0	0x00100000 - 0x29ffffff (0x29f00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x2c000000 - 0x2c00ffff (0x10000) MX[B]
	[7] -1	0	0xe8101000 - 0xe8101fff (0x1000) MX[B]
	[8] -1	0	0xe8102000 - 0xe81027ff (0x800) MX[B]
	[9] -1	0	0xe8100000 - 0xe8100fff (0x1000) MX[B]
	[10] -1	0	0xe8080800 - 0xe80808ff (0x100) MX[B]
	[11] -1	0	0xe8080c00 - 0xe8080dff (0x200) MX[B]
	[12] -1	0	0x2a080000 - 0x2a0803ff (0x400) MX[B]
	[13] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[14] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x2a000000 - 0x2a07ffff (0x80000) MX[B](B)
	[17] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[18] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] 1	0	0x0000de00 - 0x0000de07 (0x8) IS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[26] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[27] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[28] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[29] -1	0	0x00001100 - 0x0000111f (0x20) IX[B]
	[30] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[31] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[32] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[33] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[34] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B](B)
	[35] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 16192 kB
(II) I810(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 4100 kByte
(EE) I810(0): Failed to allocate HW cursor space.
(EE) I810(0): Failed to allocate HW (ARGB) cursor space.
(EE) I810(0): Failed to allocate Overlay register space.
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xbf0000
(WW) I810(0): Disabling HW cursor because the cursor memory allocation failed.
(WW) I810(0): Disabling Xv because the overlay register buffer allocation failed.
(II) I810(0): 0x81fe368: Memory at offset 0x00020000, size 4100 kBytes
(II) I810(0): 0x81ff0f0: Memory at offset 0x00000000, size 0 kBytes
(II) I810(0): 0x81ff118: Memory at offset 0x00000000, size 0 kBytes
(II) I810(0): 0x81fd6f4: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81fe3a8: Memory at offset 0x00bf0000, size 64 kBytes
(==) I810(0): Write-combining range (0xd8000000,0x8000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 28 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 156 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		24 128x128 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing SW Cursor!
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): direct rendering: Disabled
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(II) I810(0): Rotating to 0 degrees
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
ProcXCloseDevice to close or not ?
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
Synaptics DeviceOff called
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
	the saved state
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(WW) I810(0): Successfully set original devices (2)[/PHP]

---

### Post by j0sh0 on 2007-01-20
xorg.conf:

> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	16252
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by rsantos16 on 2007-01-20
Ok, here's the load down: I also had the same problem and I am using the same chipset. 915resolution is your easiest choice, the problem I found with 915resolution is that you need to modify a configuration file found under /etc/default/ and the file name is 915resolution; edit that file and in the mode try the available "free" modes in your system, then  set the xresol and yresol. in this file you can also set the depth "BIT" I have mine set to 32. The system will run this file or its configuration everytime you boot. If the first mode that you set does not work, then try a different mode. It happened to me where I set the first 12800x800 available that I saw and it did not work, then I tried a 3 one until it worked, but you only need to be changing the mode in that file. If you cannot find that file under /etc/default, the try running "locate 915resolution" and start from there. I now am enjoying my full screen at 1280x800 and 32 bit after I had tried the xorg etc to no avail, but configuring 915resolution the way I've described really  works,

Good luck and let me if it works, 

Rsantos16](*,)

---

### Post by RandomJoe on 2007-01-20
Does it give you any other resolutions besides 800x600?  For some reason, on my Latitude D610 I wasn't give the proper resolution as an option (1400x1060 or whatever - can't remember exactly) but listing the available VESA modes _did_ show it as one of the entries.  I wound up having to use 915res to replace one of the modes Ubuntu did list, and it worked.

---

### Post by j0sh0 on 2007-01-22
rsantos16: Thanks for the reply! I've tried overwriting all modes,one after the other, using the /etc/default/915resolution file. The vbios wouldn't even change with the standard i810 driver, so I used the vbios hack driver, but still no luck setting 1024x768.  X would just start in 800x600. I did set the "BIT" argument to 24, though, as in xorg.conf it doesn't have depth 32, but I'll try again using that depth instead.

RandomJoe: I can select 640x480 (no thanks!) or 800x600... As stated above, I've tried overwriting the modes available in ubuntu (gnome), but it still wont list 1024x768.

If this 915resolution dowsn't work my last resort is the intel modesetting driver, however from the posts regarding its installation it doesn't look promising! :-| 

Fingers crossed, will keep you posted.

---

### Post by jonnieza on 2007-05-22
hey rsantos16 having the exact probs and have tried your method, as i have the exact laptop- yet it still won't work at all. all i get 800x600 and it is the worst thing in the world! here is what i did:
jinggs@beastie:~$ sudo 915resolution -l 7e 1280 800 32
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $29f
Mode Table Entries: 39

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 7c : 1280x800, 8 bits/pixel
Mode 7d : 1280x800, 16 bits/pixel
Mode 7e : 1280x800, 32 bits/pixel
Patch mode 7e to resolution 1280x800 complete
Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 7c : 1280x800, 8 bits/pixel
Mode 7d : 1280x800, 16 bits/pixel
Mode 7e : 1280x800, 32 bits/pixel
jinggs@beastie:~$ sudo gedit /etc/default/915resolution

having changed the file to the correct settings then hitting ctrl alt to restart x, it still only gives me the option of 800x600 and 640x400. what am i doing wrong??
regards,
me

---

### Post by capdog on 2007-05-22
Hi Josh, did you ever get this to work? I'm going crazy with the same (similar) problem!

---

### Post by capdog on 2007-05-22
Got it to work! Here is a link to my specific solution:

[http://ubuntuforums.org/showthread.php?p=2702458](http://ubuntuforums.org/showthread.php?p=2702458)

---

