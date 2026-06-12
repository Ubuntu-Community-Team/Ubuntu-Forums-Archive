---
title: "Fglrx - Sigsegv"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by Thailok on 2007-11-11
In order to get compiz working without needing XGL I've installed the latest AMD fglrx driver 8.42.3. Installation went fine, just added the needed lines in the xorg.conf (I am pretty experienced in writing a working fglrx-compatible xorg.conf) and rebootet. But instead of greeting me with stunning desktop effects the X server simply did - nothing. Just a pitch black screen. And ctrl+alt+backspace didn't change anything. I was able to restart the system by pressing ctrl+alt+F1, logging in and typing sudo init 6, though. 
The Xorg-log informs me about a segmentation fault in the fglrx-module (which means, at least, that the installation of the module and the xorg.conf should be fine so far). 
Here the complete log:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Amarannon 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 12 01:13:04 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(**) Extension "Composite" is enabled
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 0000,0000 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1458,0c11 rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1458,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1458,5004 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1458,5004 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1458,5004 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1458,e000 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 13f6,0111 card 13f6,0111 rev 10 class 04,01,00 hdr 00
(II) PCI: 02:00:0: chip 1002,4e45 card 1002,0002 rev 00 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,4e65 card 1002,0003 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro] rev 0, Mem @ 0xd0000000/27, 0xe5000000/16, I/O @ 0xd000/8
(--) PCI: (2:0:1) ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary) rev 0, Mem @ 0xd8000000/27, 0xe5010000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[3] -1	0	0xe6003000 - 0xe6003fff (0x1000) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[1] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[2] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[3] -1	0	0xe6003000 - 0xe6003fff (0x1000) MX[B]
	[4] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[5] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[11] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
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
	[4] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[7] -1	0	0xe6003000 - 0xe6003fff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	Module class: X.Org Video Driver
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "fglrx"
(II) Reloading /usr/lib/xorg/modules/drivers//fglrx_drv.so
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
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x4E45) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[7] -1	0	0xe6003000 - 0xe6003fff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8208f00
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe6001000 - 0xe6001fff (0x1000) MX[B]
	[5] -1	0	0xe6000000 - 0xe60000ff (0x100) MX[B]
	[6] -1	0	0xe6004000 - 0xe6004fff (0x1000) MX[B]
	[7] -1	0	0xe6003000 - 0xe6003fff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "RADEON 9500 PRO / 9700" (Chipset = 0x4e45)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe5000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI R300
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: R300
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.42.3
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: IVM  Model: 1980  Serial#: 89274
(II) fglrx(0): Year: 2001  Week: 10
(II) fglrx(0): EDID Version: 1.2
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.714/0.286 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.626 redY: 0.340   greenX: 0.288 greenY: 0.608
(II) fglrx(0): blueX: 0.148 blueY: 0.064   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1280  vsize 960  refresh: 85  vid: 22913
(II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  360 x 270 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 78.8 MHz   Image Size:  360 x 270 mm
(II) fglrx(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 150 Hz, H min: 30  H max: 95 kHz, PixClock max 200 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0026cd8019ba5c0100
(II) fglrx(0): 	0a0b010228241b78ea4f29a057499b26
(II) fglrx(0): 	10484ca4430031594559615981598199
(II) fglrx(0): 	a94f01010101863d00c05100304040a0
(II) fglrx(0): 	1300680e1100001eea24006041002830
(II) fglrx(0): 	30601300680e1100001ec31e00204100
(II) fglrx(0): 	203010601300680e1100001e000000fd
(II) fglrx(0): 	0032961e5f14000a20202020202000a7
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware

Backtrace:
0: X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb7aa63db]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(DALCWDDE+0x1a2) [0xb7aa4b62]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlDalHelperAddCustomizeMode+0x1a1) [0xb7a08ce1]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0xb11) [0xb79dfbb1]
6: X(InitOutput+0x9a4) [0x80a8e54]
7: X(main+0x27b) [0x8076ceb]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7dc8050]
9: X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting


```

Any ideas beside contacting amd support?

(edit: Just realized, that this thread would've been better posted in multimedia. Sry, bout that)

---

### Post by gonzomir on 2007-11-12
Hi, I have a similar problem. I am running 7.10 upgraded from 7.4. After the upgrade I installed a new video card and went on enabling the eye candy. The card is Sapphire Radeon HD 2400 Pro. First tried the fglrx driver that comes with Ubuntu, but it didn't work. Then I downloaded the latest driver from Ati and installed it following the instructions, found on various HOWTOs - build deb packages, install them, build the kernel module, install it, configure X. After the restart I got a nice display, but everything was slow - scrolling, moving windows, etc. After some investigation I found that the kernel module that's loading is the old version from restricted-modules package, so I removed the package (with the sacriface of the meta package that keeps the kernel). Now I had the right kernel module, but when X starts, after some hard disk activity the computer freezes, no keyboard input accepted, no Ctrl-Alt-Backspace, no switching to console or reboot. The only way is to pres the reset button. And further investigation got into dead end for me - no Xorg.0.log gets written, nothing in other logs. Now I'm stuck with the vesa driver :-(

```

gonzo@bibiland:~$ cat /etc/X11/xorg.conf

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
        Load  "dbe"
        Load  "v4l"
EndSection

Section "ServerFlags"
        Option  "AllowMouseOpenFail" "true"
        Option  "AIGLX" "false"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us,bg"
        Option      "XkbVariant" "bds"
        Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "LCD2070WNX"
        Option       "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Radeon"
        Driver      "vesa"
#        Option      "VideoOverlay" "on"
#        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon"
        Monitor    "LCD2070WNX"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1680x1050@60" "1600x1024@60" "1440x900@60" "1024x768@60" "800x600@60"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1680x1050@60" "1600x1024@60" "1440x900@60" "1024x768@60" "800x600@60"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

```

gonzo@bibiland:~$ modinfo fglrx
filename:       /lib/modules/2.6.22-14-generic/misc/fglrx.ko
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany

/ long list of alis: lines cut /

depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           firegl:charp

```

```

gonzo@bibiland:~$ lsmod
Module                  Size  Used by
isofs                  36412  1 
tun                    12288  1 
af_packet              24840  2 
binfmt_misc            12936  1 
ppdev                  10244  0 
ipv6                  273892  16 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
ac                      6148  0 
battery                11012  0 
apparmor               40728  0 
bfusb                  13444  0 
bluetooth              57060  1 bfusb
dv1394                 20824  0 
raw1394                31096  0 
sbp2                   24072  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
psmouse                39952  0 
serio_raw               8068  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
fglrx                1487340  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 fglrx,intel_agp
evdev                  11136  4 
ext2                   67208  2 
mbcache                 9732  1 ext2
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  6 
8139too                27776  0 
ata_piix               17540  5 
ohci1394               36528  1 dv1394
ieee1394               96312  4 dv1394,raw1394,sbp2,ohci1394
e100                   37644  0 
8139cp                 25088  0 
mii                     6528  3 8139too,e100,8139cp
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 bfusb,usbhid,ehci_hcd,uhci_hcd
raid10                 26496  0 
raid456               128016  0 
xor                    16904  1 raid456
raid1                  25984  0 
raid0                   9728  0 
multipath               9984  0 
linear                  7552  0 
md_mod                 82324  6 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  2 dm_mirror,dm_snapshot
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
commoncap               8320  1 apparmor
fuse                   47124  5 
fbcon                  41760  0 
tileblit                3584  1 fbcon
font                    9344  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit

```

---

### Post by gonzomir on 2007-11-13
One more think - if the fglrx kernel module is not loaded or one from Ubuntu repository is loaded, the X driver works, but no direct rendering, so the display is very slow. But if the module loaded is the newest from ATI, the computer crashes. How can I know what's the problem with the fglrx kernel module? Where to look for for clues?

---

### Post by Thailok on 2007-12-23
I've read somewhere, that removing the "modeline"-options in the xorg.conf helps. 
In my case it solved the problem.

---

