---
title: "nVidia/GLX module problem"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by gcranston on 2006-05-06
On a Dell Inspiron 2650, with nVidia GeForce  Go.  Dapper Beta.

Trying to get the nVidia graphic driver going from the nVidia .run package (version 1.0.8756)

I get a fatal error when tyring to start X.  Seems GLCore fails then glx fails, and I can't get accelerated graphics.

Further down, something called 'wacom' fails.  I have no idea what that is, but I don't think I need it in there.  Can I just comment it out?

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux localghost 2.6.15-21-386 #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May  6 15:16:47 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV11 [GeForce2 Go]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1a30 card 1028,00f3 rev 05 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 05 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2482 card 1028,00f3 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2484 card 1028,00f3 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,248c card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,248a card 1028,00f3 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2483 card 1028,00f3 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2485 card 1028,00f3 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,2486 card 14f1,5421 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0112 card 1028,00f3 rev b2 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 10b7,9200 card 1028,00f3 rev 78 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1217,6972 card 3401,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x00003000 - 0x000030ff (0x100) IX[B]
        [1] -1  0       0x00003400 - 0x000034ff (0x100) IX[B]
        [2] -1  0       0x00003800 - 0x000038ff (0x100) IX[B]
        [3] -1  0       0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xe8000000 - 0xe80fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0x30000000 - 0x32ffffff (0x3000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
        [0] -1  0       0x00003400 - 0x000034ff (0x100) IX[B]
        [1] -1  0       0x00003800 - 0x000038ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
        [0] -1  0       0x30000000 - 0x31ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV11 [GeForce2 Go] rev 178, Mem @ 0xe0000000/24, 0xf0000000/27
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xec000000 from 0xefffffff to 0xebffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xe8000000 - 0xe800007f (0x80) MX[B]
        [1] -1  0       0x33000000 - 0x330003ff (0x400) MX[B]
        [2] -1  0       0xec000000 - 0xebffffff (0x0) MX[B]O
        [3] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [4] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [5] -1  0       0x00003000 - 0x0000307f (0x80) IX[B]
        [6] -1  0       0x00002000 - 0x0000207f (0x80) IX[B]
        [7] -1  0       0x00002400 - 0x000024ff (0x100) IX[B]
        [8] -1  0       0x00001880 - 0x000018bf (0x40) IX[B]
        [9] -1  0       0x00001c00 - 0x00001cff (0x100) IX[B]
        [10] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [11] -1 0       0x00001840 - 0x0000184f (0x10) IX[B]
        [12] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [13] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe8000000 - 0xe800007f (0x80) MX[B]
        [1] -1  0       0x33000000 - 0x330003ff (0x400) MX[B]
        [2] -1  0       0xec000000 - 0xebffffff (0x0) MX[B]O
        [3] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [4] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [5] -1  0       0x00003000 - 0x0000307f (0x80) IX[B]
        [6] -1  0       0x00002000 - 0x0000207f (0x80) IX[B]
        [7] -1  0       0x00002400 - 0x000024ff (0x100) IX[B]
        [8] -1  0       0x00001880 - 0x000018bf (0x40) IX[B]
        [9] -1  0       0x00001c00 - 0x00001cff (0x100) IX[B]
        [10] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [11] -1 0       0x00001840 - 0x0000184f (0x10) IX[B]
        [12] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [13] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x32ffffff (0x32f00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x32ffffff (0x32f00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xe8000000 - 0xe800007f (0x80) MX[B]
        [6] -1  0       0x33000000 - 0x330003ff (0x400) MX[B]
        [7] -1  0       0xec000000 - 0xebffffff (0x0) MX[B]O
        [8] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x00003000 - 0x0000307f (0x80) IX[B]
        [13] -1 0       0x00002000 - 0x0000207f (0x80) IX[B]
        [14] -1 0       0x00002400 - 0x000024ff (0x100) IX[B]
        [15] -1 0       0x00001880 - 0x000018bf (0x40) IX[B]
        [16] -1 0       0x00001c00 - 0x00001cff (0x100) IX[B]
        [17] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [18] -1 0       0x00001840 - 0x0000184f (0x10) IX[B]
        [19] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [20] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
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
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(WW) Warning, couldn't open module GLcore
(II) UnloadModule: "GLcore"
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules/extensions/libglx.so
(EE) Failed to load module "glx" (a required submodule could not be loaded, 0)
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 6.99.99.904, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
        Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
        Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
        GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
        GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
        Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
        GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
        GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
        GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
        GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
        GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
        GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
        Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
        GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
        GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
        GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
        Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
        GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
        Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
        GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
        GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
        GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
        GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
        GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
        GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
        Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
        GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
        GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
        GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
        GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
        GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
        Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
        GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 GT, GeForce 6800 GT,
        GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000, GeForce 6800 GS,
        GeForce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800,
        GeForce Go 6800 Ultra, Quadro FX Go1400, Quadro FX 3450/4000 SDI,
        Quadro FX 1400, GeForce 6600 GT, GeForce 6600, GeForce 6600 LE,
        GeForce 6600 VE, GeForce Go 6600, GeForce 6610 XL,
        GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, GeForce Go 6600,
        GeForce Go 6600 GT, Quadro FX 540, GeForce 6200, GeForce 6500,
        GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
        GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
        GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
        GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
        GeForce 7800 GTX, GeForce 7800 GTX, GeForce 7800 GT, GeForce 7800 GS,
        GeForce 7800 SLI, GeForce Go 7800, GeForce Go 7800 GTX,
        Quadro FX 4500, GeForce 7300 LE, GeForce Go 7200, GeForce Go 7300,
        GeForce Go 7400, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
        Quadro FX 350, GeForce 7300 GS, GeForce Go 7600, GeForce Go 7600 GT,
        Quadro NVS 300M, Quadro FX 550M, GeForce Go 7900 GS,
        GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M, GeForce 6150,
        GeForce 6150 LE, GeForce 6100, GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce2 Go found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x32ffffff (0x32f00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xe8000000 - 0xe800007f (0x80) MX[B]
        [6] -1  0       0x33000000 - 0x330003ff (0x400) MX[B]
        [7] -1  0       0xec000000 - 0xebffffff (0x0) MX[B]O
        [8] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x00003000 - 0x0000307f (0x80) IX[B]
        [13] -1 0       0x00002000 - 0x0000207f (0x80) IX[B]
        [14] -1 0       0x00002400 - 0x000024ff (0x100) IX[B]
        [15] -1 0       0x00001880 - 0x000018bf (0x40) IX[B]
        [16] -1 0       0x00001c00 - 0x00001cff (0x100) IX[B]
        [17] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [18] -1 0       0x00001840 - 0x0000184f (0x10) IX[B]
        [19] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [20] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x32ffffff (0x32f00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xe8000000 - 0xe800007f (0x80) MX[B]
        [6] -1  0       0x33000000 - 0x330003ff (0x400) MX[B]
        [7] -1  0       0xec000000 - 0xebffffff (0x0) MX[B]O
        [8] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [9] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
        [10] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [11] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [12] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x00003000 - 0x0000307f (0x80) IX[B]
        [16] -1 0       0x00002000 - 0x0000207f (0x80) IX[B]
        [17] -1 0       0x00002400 - 0x000024ff (0x100) IX[B]
        [18] -1 0       0x00001880 - 0x000018bf (0x40) IX[B]
        [19] -1 0       0x00001c00 - 0x00001cff (0x100) IX[B]
        [20] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [21] -1 0       0x00001840 - 0x0000184f (0x10) IX[B]
        [22] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [23] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
        [24] 0  0       0xe10003b0 - 0xe10003bb (0xc) IS[B]
        [25] 0  0       0xe10003c0 - 0xe10003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce2 Go"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF0000000
(--) NV(0): MMIO registers at 0xE0000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: LGP  Model: 9846  Serial#: 0
(II) NV(0): Year: 1990  Week: 0
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 29  vert.: 21
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing not preferred mode in violation of standard!(II) NV(0): redX: 0.579 redY: 0.329   greenX: 0.310 greenY: 0.538
(II) NV(0): blueX: 0.151 blueY: 0.128   whiteX: 0.313 whiteY: 0.328
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 65.0 MHz   Image Size:  286 x 214 mm
(II) NV(0): h_active: 1024  h_sync: 1048  h_sync_end 1696 h_blank_end 1344 h_border: 0
(II) NV(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(--) NV(0): CRTC 1 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 1
(--) NV(0): Panel size is 1024 x 768
(II) NV(0): Panel is LVDS
(--) NV(0): VideoRAM: 16384 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(WW) NV(0): config file hsync range 28-51kHz not within DDC hsync ranges.
(WW) NV(0): config file vrefresh range 43-60Hz not within DDC vrefresh ranges.




```

After I fix this, I need to get dual heads going.  Is this a fairly rudimentary thing to do?  Is there a gui, or am I editing the xorg.conf by hand?

Thanks

-Graham

---

### Post by gcranston on 2006-05-06
and my current xorg.conf:

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "NVIDIA Corporation NV11 [GeForce2 Go]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 Go]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

The only difference between this and the one that generated the error is changing the driver 'nv' to 'nvidia' and commenting out Load 'dri'

Thanks,

-Graham

---

### Post by Slavus on 2006-05-09
Gah, I have the _*exact*_ same problem, I guess nobody on these forums really knows.

         :(

---

### Post by Scunizi on 2006-05-12
Slavus just because you don't get an answer right away doesn't mean nobody looks.  I've been searching threads for days on glx & xgl and viola this thread popped up on the first page.  You issues with the nVidia driver can be solved and solutions have been mentioned in numerous threads throughout this system.

As an example take a look at [http://ubuntuforums.org/showthread.php?t=75074&highlight=testers]("http://ubuntuforums.org/showthread.php?t=75074&highlight=testers")

or

[http://ubuntuforums.org/showthread.php?t=174045&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=174045&highlight=nvidia)

Instead of trying to install by hand, have you tried using Synaptic?  The latest drivers are there and installed just fine on Dapper B.  I've also got Compiz & xgl working in twinview... but that's another story.  Looks like both of you might be fairly new to this board and maybe Ubuntu.  Give it some time and patients and things will come together.  I learn something new every day about this system.

---

### Post by gcranston on 2006-05-16
I have also kept searching and tried the packaged drivers, which are working fine for me.  Do

sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`

then comment out 

Load dri             and 
Load GLCore 

and change the driver under the display section from 'nv' to 'nvidia' in your /etc/X11/xorg.conf (after making a backup of course) and you should be good to go.

Just for the curious, I will post when I get twinview or dual heads working to this thread.

And by the way, the main reason I went with the binary driver from nvidia, is because as far back as warty, and FC2 and FC3 before that, I'd had problem with package drivers not working properly if at all, and had almost no problems with running the proprietary package from nVidia.  It would seem as though the tables have turned.  I'm very glad they have.

-Graham

---

### Post by gcranston on 2006-10-07
If anyone is still watching this thread, I did get TwinView going, but bailed on an attempt to get compiz/xgl running.  My xorg looks like this:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "NVIDIA Corporation NV11 [GeForce2 Go]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "NvAGP" "2"
#       Option "NoLogo" "1"
        Option "RenderAccel" "0"
        Option "CursorShadow" "1"
        #Option "Coolbits" "1"
        Option "ConnectedMonitor" "crt, dfp"
        Option "NoPowerConnectorCheck"
        Option "TwinView" "1"
        Option "Metamodes" "1024x768,1024x768; 1024x768,NULL"
        Option "SecondMonitorHorizSync" "31-82"
        Option "SecondMonitorVertRefresh" "56-76"
        # Option "NoTwinViewXineramaInfo"

EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 Go]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Viewport 0 0
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport 0 0
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport 0 0
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport 0 0
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport 0 0
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport 0 0
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        Option "Xinerama" "Off"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Good luck!!

---

