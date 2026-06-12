---
title: "Broken Xwindows after upgrading to Jaunty 9.04"
date: 2009-05-31
forum: Hardware
---

### Post by Francesc Dorca on 2009-05-31
Problem X.org Ubuntu 9.04
-------------------------

After upgrading without problems Ubuntu from version 7.10 to 8.04 and to 8.10, the latest upgrade to 9.04 of my laptop Acer Aspire 1350 with a graphic card VIA S3 Unichrome VT8378 my xwindows crashed. I tried (without any success):

- Edit the content of the configuration file of X.org
- dpkg-reconfigure xserver-xorg
- sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

Ubuntu still works properly, but only from the command line, and the contents of file /var/log/Xorg.0.log is following:

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: UNKNOWN
Current Operating System: Linux tux 2.6.18-6-k7 #1 SMP Tue May 5 01:21:08 UTC 2009 i686
Build Date: 29 May 2008
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 19 18:09:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Monitor genèric"
(**) | |-->Device "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/cyrillic" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi" does not exist.
Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
Entry deleted from font path.
(**) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi
(==) RgbPath set to "/etc/X11/rgb"
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
(II) PCI: 00:00:0: chip 1106,3205 card 1106,7205 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b168 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 104c,ac50 card 2000,0000 rev 02 class 06,07,00 hdr 02
(II) PCI: 00:08:0: chip 104c,8026 card 1025,0033 rev 00 class 0c,00,10 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1025,0033 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1025,0033 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1025,0033 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1025,0033 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1025,0033 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1025,0033 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1025,0033 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 1025,0033 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1025,0033 rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1106,7205 card 1025,0033 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
[0] -1 0 0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
[0] -1 0 0xd1000000 - 0xd1ffffff (0x1000000) MX[b]
(II) Bus 1 prefetchable memory range:
[0] -1 0 0xf0000000 - 0xf3ffffff (0x4000000) MX[b]
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:7:0), (0,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
[0] -1 0 0x00002000 - 0x000020ff (0x100) IX[b]
[1] -1 0 0x00002400 - 0x000024ff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
[0] -1 0 0x62000000 - 0x63ffffff (0x2000000) MX[b]
(II) Bus 2 prefetchable memory range:
[0] -1 0 0x60000000 - 0x61ffffff (0x2000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x7205) rev 1, Mem @ 0xf0000000/26, 0xd1000000/24
(II) Addressable bus resource ranges are
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX[b]
[1] -1 0 0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
[0] -1 0 0xd0004c00 - 0xd0004cff (0x100) MX[b]
[1] -1 0 0xd0004800 - 0xd00048ff (0x100) MX[b]
[2] -1 0 0xd0000000 - 0xd0003fff (0x4000) MX[b]
[3] -1 0 0xd0004000 - 0xd00047ff (0x800) MX[b]
[4] -1 0 0xe0000000 - 0xdfffffff (0x0) MX[b]O
[5] -1 0 0xd1000000 - 0xd1ffffff (0x1000000) MX[b](B)
[6] -1 0 0xf0000000 - 0xf3ffffff (0x4000000) MX[b](B)
[7] -1 0 0x00001800 - 0x000018ff (0x100) IX[b]
[8] -1 0 0x00001400 - 0x000014ff (0x100) IX[b]
[9] -1 0 0x00001000 - 0x000010ff (0x100) IX[b]
[10] -1 0 0x00001c60 - 0x00001c6f (0x10) IX[b]
[11] -1 0 0x00001c40 - 0x00001c5f (0x20) IX[b]
[12] -1 0 0x00001c20 - 0x00001c3f (0x20) IX[b]
[13] -1 0 0x00001c00 - 0x00001c1f (0x20) IX[b]
(II) Active PCI resource ranges after removing overlaps:
[0] -1 0 0xd0004c00 - 0xd0004cff (0x100) MX[b]
[1] -1 0 0xd0004800 - 0xd00048ff (0x100) MX[b]
[2] -1 0 0xd0000000 - 0xd0003fff (0x4000) MX[b]
[3] -1 0 0xd0004000 - 0xd00047ff (0x800) MX[b]
[4] -1 0 0xe0000000 - 0xdfffffff (0x0) MX[b]O
[5] -1 0 0xd1000000 - 0xd1ffffff (0x1000000) MX[b](B)
[6] -1 0 0xf0000000 - 0xf3ffffff (0x4000000) MX[b](B)
[7] -1 0 0x00001800 - 0x000018ff (0x100) IX[b]
[8] -1 0 0x00001400 - 0x000014ff (0x100) IX[b]
[9] -1 0 0x00001000 - 0x000010ff (0x100) IX[b]
[10] -1 0 0x00001c60 - 0x00001c6f (0x10) IX[b]
[11] -1 0 0x00001c40 - 0x00001c5f (0x20) IX[b]
[12] -1 0 0x00001c20 - 0x00001c3f (0x20) IX[b]
[13] -1 0 0x00001c00 - 0x00001c1f (0x20) IX[b]
(II) OS-reported resource ranges after removing overlaps with PCI:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xd0004c00 - 0xd0004cff (0x100) MX[b]
[5] -1 0 0xd0004800 - 0xd00048ff (0x100) MX[b]
[6] -1 0 0xd0000000 - 0xd0003fff (0x4000) MX[b]
[7] -1 0 0xd0004000 - 0xd00047ff (0x800) MX[b]
[8] -1 0 0xe0000000 - 0xdfffffff (0x0) MX[b]O
[9] -1 0 0xd1000000 - 0xd1ffffff (0x1000000) MX[b](B)
[10] -1 0 0xf0000000 - 0xf3ffffff (0x4000000) MX[b](B)
[11] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[12] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[13] -1 0 0x00001800 - 0x000018ff (0x100) IX[b]
[14] -1 0 0x00001400 - 0x000014ff (0x100) IX[b]
[15] -1 0 0x00001000 - 0x000010ff (0x100) IX[b]
[16] -1 0 0x00001c60 - 0x00001c6f (0x10) IX[b]
[17] -1 0 0x00001c40 - 0x00001c5f (0x20) IX[b]
[18] -1 0 0x00001c20 - 0x00001c3f (0x20) IX[b]
[19] -1 0 0x00001c00 - 0x00001c1f (0x20) IX[b]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.2.0
ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.1.0
ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers/via_drv.so
(II) Module via: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 0.2.1
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
compiled for 4.2.0, module version = 1.0.0
Module class: XFree86 XInput Driver
ABI class: XFree86 XInput driver, version 0.3
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
PM800/PM880/CN400
(II) Primary Device is: PCI 01:00:0
(--) Chipset KM400/KN400 found
(!!) VIA Technologies does not support or endorse this driver in any way.
(!!) For support please contact the driver maintainer or your X vendor.
(II) resource ranges after xf86ClaimFixedResources() call:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xd0004c00 - 0xd0004cff (0x100) MX[b]
[5] -1 0 0xd0004800 - 0xd00048ff (0x100) MX[b]
[6] -1 0 0xd0000000 - 0xd0003fff (0x4000) MX[b]
[7] -1 0 0xd0004000 - 0xd00047ff (0x800) MX[b]
[8] -1 0 0xe0000000 - 0xdfffffff (0x0) MX[b]O
[9] -1 0 0xd1000000 - 0xd1ffffff (0x1000000) MX[b](B)
[10] -1 0 0xf0000000 - 0xf3ffffff (0x4000000) MX[b](B)
[11] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[12] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[13] -1 0 0x00001800 - 0x000018ff (0x100) IX[b]
[14] -1 0 0x00001400 - 0x000014ff (0x100) IX[b]
[15] -1 0 0x00001000 - 0x000010ff (0x100) IX[b]
[16] -1 0 0x00001c60 - 0x00001c6f (0x10) IX[b]
[17] -1 0 0x00001c40 - 0x00001c5f (0x20) IX[b]
[18] -1 0 0x00001c20 - 0x00001c3f (0x20) IX[b]
[19] -1 0 0x00001c00 - 0x00001c1f (0x20) IX[b]
(II) resource ranges after probing:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xd0004c00 - 0xd0004cff (0x100) MX[b]
[5] -1 0 0xd0004800 - 0xd00048ff (0x100) MX[b]
[6] -1 0 0xd0000000 - 0xd0003fff (0x4000) MX[b]
[7] -1 0 0xd0004000 - 0xd00047ff (0x800) MX[b]
[8] -1 0 0xe0000000 - 0xdfffffff (0x0) MX[b]O
[9] -1 0 0xd1000000 - 0xd1ffffff (0x1000000) MX[b](B)
[10] -1 0 0xf0000000 - 0xf3ffffff (0x4000000) MX[b](B)
[11] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b]
[12] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b]
[13] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b]
[14] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[15] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[16] -1 0 0x00001800 - 0x000018ff (0x100) IX[b]
[17] -1 0 0x00001400 - 0x000014ff (0x100) IX[b]
[18] -1 0 0x00001000 - 0x000010ff (0x100) IX[b]
[19] -1 0 0x00001c60 - 0x00001c6f (0x10) IX[b]
[20] -1 0 0x00001c40 - 0x00001c5f (0x20) IX[b]
[21] -1 0 0x00001c20 - 0x00001c3f (0x20) IX[b]
[22] -1 0 0x00001c00 - 0x00001c1f (0x20) IX[b]
[23] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b]
[24] 0 0 0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 0.1.0
ABI class: X.Org Video Driver, version 1.0
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(==) VIA(0): Using XAA acceleration architecture
(==) VIA(0): Using HW cursor
(--) VIA(0): Chipset: "KM400/KN400"
(--) VIA(0): mapping MMIO @ 0xd1000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xd1200000 with size 0x10000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) VIA(0): Chipset Rev.: 3
(--) VIA(0): Detected Acer Aspire 135x.
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram = 65536k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) VIA(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) VIA(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 1:ddc2" removed.
(II) VIA(0): Enabling panel from PCI-Subsystem Id information.
(WW) VIA(0): This device is supposed to have a TV encoder but we are unable to detect it (support missing?).
(II) VIA(0): Monitor genèric: Using hsync range of 28.00-51.00 kHz
(II) VIA(0): Monitor genèric: Using vrefresh range of 43.00-60.00 Hz
(II) VIA(0): Clock range: 20.00 to 230.00 MHz
(II) VIA(0): I2C device "I2C bus 2:ddc2" registered at address 0xA0.
(II) VIA(0): I2C device "I2C bus 2:ddc2" removed.
(II) VIA(0): Manufacturer: QDS Model: 11 Serial#: 0
(II) VIA(0): Year: 2093 Week: 40
(II) VIA(0): EDID Version: 1.2
(II) VIA(0): Digital Display Input
(II) VIA(0): Max H-Image Size [cm]: horiz.: 30 vert.: 23
(II) VIA(0): Gamma: 2.20
(II) VIA(0): No DPMS capabilities specified; RGB/Color Display
(II) VIA(0): First detailed timing is preferred mode
(II) VIA(0): redX: 0.591 redY: 0.325 greenX: 0.314 greenY: 0.562
(II) VIA(0): blueX: 0.137 blueY: 0.119 whiteX: 0.312 whiteY: 0.328
(II) VIA(0): Manufacturer's mask: 0
(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 65.0 MHz Image Size: 304 x 228 mm
(II) VIA(0): h_active: 1024 h_sync: 1048 h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) VIA(0): v_active: 768 v_sync: 771 v_sync_end 777 v_blanking: 806 v_border: 0
(II) VIA(0): JFC3A12039630
(II) VIA(0): QD15XL061
(II) VIA(0): Using panel at 1024x768.
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "640x350" (unknown reason)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "640x400" (unknown reason)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "720x400" (unknown reason)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "640x480" (unknown reason)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "640x480" (unknown reason)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "640x480" (unknown reason)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "640x480" (unknown reason)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "800x600" (unknown reason)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "800x600" (unknown reason)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "800x600" (unknown reason)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "800x600" (unknown reason)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "800x600" (unknown reason)
(II) VIA(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (interlace mode not supported)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1024x768" (unknown reason)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1024x768" (unknown reason)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1024x768" (unknown reason)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1024x768" (unknown reason)
(II) VIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1152x864" (unknown reason)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1280x960" (unknown reason)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1280x960" (unknown reason)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1280x1024" (unknown reason)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1280x1024" (unknown reason)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1280x1024" (unknown reason)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1600x1200" (unknown reason)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1600x1200" (unknown reason)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1600x1200" (unknown reason)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1600x1200" (unknown reason)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1600x1200" (unknown reason)
(II) VIA(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1792x1344" (unknown reason)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1856x1392" (unknown reason)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "832x624" (unknown reason)
(II) VIA(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1280x768" (unknown reason)
(II) VIA(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1280x800" (unknown reason)
(II) VIA(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1152x768" (unknown reason)
(II) VIA(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1152x864" (unknown reason)
(II) VIA(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1400x1050" (unknown reason)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1400x1050" (unknown reason)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): CrtcHSyncEnd out of range.
(II) VIA(0): Not using default mode "1400x1050" (horizontal sync too wide)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1400x1050" (unknown reason)
(II) VIA(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): CrtcHSyncEnd out of range.
(II) VIA(0): Not using default mode "1440x900" (horizontal sync too wide)
(II) VIA(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1600x1024" (unknown reason)
(II) VIA(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1680x1050" (unknown reason)
(II) VIA(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1920x1200" (unknown reason)
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) VIA(0): Not using default mode "1920x1200" (unknown reason)
(II) VIA(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) VIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "640x480" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "800x600" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1152x864" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1280x1024" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1600x1200" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1280x768" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1280x960" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "848x480" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1400x1050" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "720x480" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "720x576" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1024x512" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "856x480" (unknown reason)
(II) VIA(0): ViaPanelGetIndex: Non-nativeresolutions are broken.
(II) VIA(0): Not using default mode "1024x576" (unknown reason)
(II) VIA(0): Not using mode "800x600" (no mode of this name)
(II) VIA(0): Not using mode "640x480" (no mode of this name)
(--) VIA(0): Virtual size is 1024x768 (pitch 1024)
(**) VIA(0): *Default mode "1024x768": 65.0 MHz (scaled from -1363962.0 MHz), 48.4 kHz, 60.0 Hz
(II) VIA(0): Modeline "1024x768" 65.03 1024 1048 1184 1344 768 770 776 806 -hsync -vsync
(++) VIA(0): DPI set to (96, 96)
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
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC? No, I don't.
(II) resource ranges after preInit:
[0] 0 0 0xd1000000 - 0xd1ffffff (0x1000000) MS[b]
[1] 0 0 0xf0000000 - 0xf3ffffff (0x4000000) MS[b]
[2] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
[3] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[4] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[5] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[6] -1 0 0xd0004c00 - 0xd0004cff (0x100) MX[b]
[7] -1 0 0xd0004800 - 0xd00048ff (0x100) MX[b]
[8] -1 0 0xd0000000 - 0xd0003fff (0x4000) MX[b]
[9] -1 0 0xd0004000 - 0xd00047ff (0x800) MX[b]
[10] -1 0 0xe0000000 - 0xdfffffff (0x0) MX[b]O
[11] -1 0 0xd1000000 - 0xd1ffffff (0x1000000) MX[b](B)
[12] -1 0 0xf0000000 - 0xf3ffffff (0x4000000) MX[b](B)
[13] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b]
[14] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b]
[15] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b]
[16] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[17] -1 0 0x00000000 - 0x000000ff (0x100) IX[b]
[18] -1 0 0x00001800 - 0x000018ff (0x100) IX[b]
[19] -1 0 0x00001400 - 0x000014ff (0x100) IX[b]
[20] -1 0 0x00001000 - 0x000010ff (0x100) IX[b]
[21] -1 0 0x00001c60 - 0x00001c6f (0x10) IX[b]
[22] -1 0 0x00001c40 - 0x00001c5f (0x20) IX[b]
[23] -1 0 0x00001c20 - 0x00001c3f (0x20) IX[b]
[24] -1 0 0x00001c00 - 0x00001c1f (0x20) IX[b]
[25] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b]
[26] 0 0 0x000003c0 - 0x000003df (0x20) IS[b]
(--) VIA(0): mapping framebuffer @ 0xf0000000 with size 0x4000000
(==) VIA(0): Write-combining range (0xf0000000,0x4000000)
(--) VIA(0): Frame buffer start: 0xb3b16000, free start: 0x300000 end: 0x4000000
(--) VIA(0): mapping MMIO @ 0xd1000000 with size 0x9000
(--) VIA(0): mapping BitBlt MMIO @ 0xd1200000 with size 0x10000
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): 3D Engine has been initialized.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) VIA(0): [drm] loaded kernel module for "via" driver
(II) VIA(0): [drm] DRM interface version 1.2
(II) VIA(0): [drm] created "via" driver at busid "PCI:1:0:0"
(II) VIA(0): [drm] added 8192 byte SAREA at 0xf8f72000
(II) VIA(0): [drm] mapped SAREA 0xf8f72000 to 0xb3b04000
(II) VIA(0): [drm] framebuffer handle = 0xf0000000
(II) VIA(0): [drm] added 1 reserved context for kernel
(II) VIA(0): [dri] visual configs initialized.
(II) VIA(0): [drm] register handle = 0xd1000000
(II) VIA(0): [drm] framebuffer handle = 0xf0000000
(II) VIA(0): [drm] mmio Registers = 0xd1000000
(II) VIA(0): [dri] mmio mapped.
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): Using XFree86 Acceleration Architecture (XAA)
Screen to screen bit blits
Solid filled rectangles
8x8 mono pattern filled rectangles
8x8 color pattern filled rectangles
Solid Lines
Dashed Lines
Image Writes
Offscreen Pixmaps
Setting up tile and stipple cache:
31 128x128 slots
12 256x256 slots
4 512x512 slots
32 8x8 color pattern slots
(==) VIA(0): Backing store disabled
(**) Option "dpms"
(**) VIA(0): DPMS enabled
(II) VIA(0): [drm] Detected AGP vendor 0x1106, device 0x3205
(II) VIA(0): [drm] Didn't find any AGP v3 compatible device. Trying AGP 4X mode.
(II) VIA(0): [drm] Trying to enable AGP fast writes.
(II) VIA(0): [drm] drmAgpEnabled succeeded
(II) VIA(0): [drm] agpAddr = 0xe0000000
(II) VIA(0): [drm] agpBase = (nil)
(II) VIA(0): [drm] agpAddr = 0xe0000000
(II) VIA(0): [drm] agpSize = 0x01e00000
(II) VIA(0): [drm] agp physical addr = 0x00000000
(II) VIA(0): [dri] use agp.
(II) VIA(0): [drm] Using 54251488 bytes for DRM memory heap.
(II) VIA(0): [dri] frame buffer initialized.
(II) VIA(0): X context handle = 0x1
(II) VIA(0): [drm] installed DRM signal handler
(II) VIA(0): [DRI] installation complete
(II) VIA(0): [dri] kernel data initialized.
(II) VIA(0): [drm] Irq handler installed, using IRQ 4.
(II) VIA(0): direct rendering enabled
(II) VIA(0): Benchmarking video copy. Less is better.
(--) VIA(0): Timed libc YUV420 copy... 11958217. Throughput: 11932399.5 MiB/s.
(--) VIA(0): Timed kernel YUV420 copy... 11965733. Throughput: 11924904.4 MiB/s.
(--) VIA(0): Timed SSE YUV420 copy... 11961001. Throughput: 11929622.1 MiB/s.
(--) VIA(0): Timed MMX YUV420 copy... 11958251. Throughput: 11932365.6 MiB/s.
(--) VIA(0): Timed 3DNow! YUV420 copy... 11964516. Throughput: 11926117.4 MiB/s.
(--) VIA(0): Timed MMX2 YUV420 copy... 11951380. Throughput: 11939225.6 MiB/s.
(--) VIA(0): Using MMX2 YUV42X copy for video.
(WW) VIA(0): [XvMC] Not supported on this chipset.
(==) RandR enabled
(II) Setting vga for screen 0.
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x22
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
xkb_keycodes { include "xfree86+aliases(qwerty)" };
xkb_types { include "complete" };
xkb_compatibility { include "complete" };
xkb_symbols { include "pc(pc105)+es" };
xkb_geometry { include "pc(pc105)" };
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
SetGrabKeysState - disabled
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
SetGrabKeysState - disabled
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
xkb_types { include "%" };
xkb_compatibility { include "%" };
xkb_symbols { include "%" };
xkb_geometry { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
SetGrabKeysState - disabled
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
SetGrabKeysState - disabled
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
Synaptics DeviceOff called
(II) VIA(0): [drm] Freeing agp memory
(II) VIA(0): [drm] Releasing agp module
(II) VIA(0): [drm] removed 1 reserved context for kernel
(II) VIA(0): [drm] unmapping 8192 bytes of SAREA 0xf8f72000 at 0xb3b04000
(II) VIA(0): [drm] Irq handler uninstalled.

```

Any suggestion about how to fix the problem?

Thanks in advance :KS,


Francesc Dorca

---

### Post by ToasterThief on 2009-05-31
Try this:
 
```
sudo apt-get install ubuntu-desktop --reinstall
```

If this results in any errors please post them.

---

