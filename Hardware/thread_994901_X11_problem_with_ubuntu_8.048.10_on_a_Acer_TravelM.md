---
title: "X11 problem with ubuntu 8.04/8.10 on a Acer TravelMate C102Ti"
date: 2008-11-27
forum: Hardware
---

### Post by tutu on 2008-11-27
Hi,
I try to install ubuntu on an Acer TravelMate C100 (C102Ti). The problem is that graphics doesn't work. Booting from CD works fine and selecting Language and so on also works. But when the switching to graphics mode the screen stays dark. One has to reboot... Alternative CD (non graphics installation) works. Now ubuntu is installed. But the same problem when trying to start X11. In recovery mode everything works fine. But when starting XWindows again a blank screen only. I attach the full Xorg.0.log. I played around with different xorg.conf files but I always ended up with the same problem.

Can anyone help me?

```
Xorg.0.log:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux toflap1 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
 Before reporting problems, check http://wiki.x.org
 to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
 (++) from command line, (!!) notice, (II) informational,
 (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 13 20:29:35 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "LaptopLCD"
(**) | |-->Device "SiliconMotion"
(**) |-->Input Device "touchpad"
(**) |-->Input Device "usbmouse"
(**) |-->Input Device "Keyboard1"
(**) |-->Input Device "cursor"
(**) |-->Input Device "stylus"
(**) |-->Input Device "eraser"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
 X.Org ANSI C Emulation: 0.4
 X.Org Video Driver: 4.1
 X.Org XInput driver : 2.1
 X.Org Server Extension : 1.1
 X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 2

(--) PCI:*(0@0:2:0) Silicon Motion, Inc. SM720 Lynx3DM rev 193, Mem @ 0x14000000/0
(II) System resource ranges:
 [0] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
 [1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
 [2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
 [3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
 [4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
 [5] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.0.0
 Module class: X.Org Server Extension
 ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.0.0
 Module class: X.Org Server Extension
 ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.0.0
 ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
 compiled for 1.5.2, module version = 2.1.0
 Module class: X.Org Font Renderer
 ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.13.0
 Module class: X.Org Server Extension
 ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.0.0
 ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "siliconmotion"

(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
 compiled for 1.5.0, module version = 1.6.0
 Module class: X.Org Video Driver
 ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 0.15.2
 Module class: X.Org XInput Driver
 ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
 compiled for 1.4.99.905, module version = 1.3.0
 Module class: X.Org XInput Driver
 ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
 compiled for 1.4.99.905, module version = 1.3.1
 Module class: X.Org XInput Driver
 ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "wacom"

(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
 compiled for 4.3.99.902, module version = 1.0.0
 Module class: X.Org XInput Driver
 ABI class: X.Org XInput driver, version 2.1
(II) Wacom driver level: 47-0.8.1-4 $
(II) Silicon Motion: driver (version 1.6.0) for Silicon Motion Lynx chipsets:
 Lynx, LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for siliconmotion
(--) Chipset Lynx3DM found
(II) resource ranges after xf86ClaimFixedResources() call:
 [0] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
 [1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
 [2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
 [3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
 [4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
 [5] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
 [0] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
 [1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
 [2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
 [3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
 [4] 0 0 0x000a0000 - 0x000affff (0x10000) MS[B]
 [5] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[B]
 [6] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[B]
 [7] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
 [8] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
 [9] 0 0 0x000003b0 - 0x000003bb (0xc) IS[B]
 [10] 0 0 0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 0.1.0
 ABI class: X.Org Video Driver, version 4.1
(**) Silicon MotionDepth 24, (--) framebuffer bpp 32
(==) Silicon MotionRGB weight 888
(==) Silicon MotionDefault visual is TrueColor
(==) Silicon MotionUsing Hardware Cursor
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.0.0
 ABI class: X.Org Video Driver, version 4.1
(II) Silicon MotionPrimary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.1.0
 ABI class: X.Org Video Driver, version 4.1
(II) Silicon MotionVESA BIOS not detected
(--) Silicon MotionChipset: "Lynx3DM"
(II) Silicon MotionvgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Silicon MotionTFT Panel Size = 1024x768
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Silicon MotionI2C bus "I2C bus" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) Silicon MotionNo DDC signal
(II) Silicon MotionI2C device "I2C bus:ddc2" registered at address 0xA0.
(II) Silicon MotionI2C device "I2C bus:ddc2" removed.
(==) Silicon MotionUsing gamma correction (1.0, 1.0, 1.0)
(--) Silicon Motionvideoram: 8192kB
(--) Silicon MotionDetected current MCLK value of 100.227 MHz
(WW) Silicon Motionxf86UnMapVidMem: cannot find region for [0xb76c2000,0x200000]
(II) Silicon MotionLaptopLCD: Using hsync range of 21.50-48.50 kHz
(II) Silicon MotionLaptopLCD: Using vrefresh range of 30.00-70.00 Hz
(II) Silicon MotionClock range: 20.00 to 200.00 MHz
(II) Silicon MotionMode: 640x350 32-bpp, 85.079948Hz
(II) Silicon MotionNot using default mode "640x350" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x400 32-bpp, 85.079948Hz
(II) Silicon MotionNot using default mode "640x400" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 720x400 32-bpp, 85.038902Hz
(II) Silicon MotionNot using default mode "720x400" (vrefresh out of range)
(II) Silicon MotionNot using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 32-bpp, 59.940475Hz
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 32-bpp, 72.808800Hz
(II) Silicon MotionNot using default mode "640x480" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 32-bpp, 75.000000Hz
(II) Silicon MotionNot using default mode "640x480" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 32-bpp, 85.008308Hz
(II) Silicon MotionNot using default mode "640x480" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 32-bpp, 56.250000Hz
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 32-bpp, 60.316540Hz
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 32-bpp, 72.187569Hz
(II) Silicon MotionNot using default mode "800x600" (vrefresh out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 32-bpp, 75.000000Hz
(II) Silicon MotionNot using default mode "800x600" (vrefresh out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 32-bpp, 85.136887Hz
(II) Silicon MotionNot using default mode "800x600" (hsync out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1024x768 32-bpp, 60.003841Hz
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1024x768 32-bpp, 70.069359Hz
(II) Silicon MotionNot using default mode "1024x768" (hsync out of range)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1024x768 32-bpp, 75.028580Hz
(II) Silicon MotionNot using default mode "1024x768" (hsync out of range)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1024x768 32-bpp, 84.996689Hz
(II) Silicon MotionNot using default mode "1024x768" (hsync out of range)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1152x864 32-bpp, 75.000000Hz
(II) Silicon MotionNot using default mode "1152x864" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1280x960 32-bpp, 60.000000Hz
(II) Silicon MotionNot using default mode "1280x960" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1280x960 32-bpp, 85.002472Hz
(II) Silicon MotionNot using default mode "1280x960" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1280x1024 32-bpp, 60.019741Hz
(II) Silicon MotionNot using default mode "1280x1024" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1280x1024 32-bpp, 75.024673Hz
(II) Silicon MotionNot using default mode "1280x1024" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1280x1024 32-bpp, 85.024101Hz
(II) Silicon MotionNot using default mode "1280x1024" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1600x1200 32-bpp, 60.000000Hz
(II) Silicon MotionNot using default mode "1600x1200" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1600x1200 32-bpp, 65.000000Hz
(II) Silicon MotionNot using default mode "1600x1200" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1600x1200 32-bpp, 70.000000Hz
(II) Silicon MotionNot using default mode "1600x1200" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1792x1344" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1792x1344" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1856x1392" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1856x1392" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 832x624 32-bpp, 74.551270Hz
(II) Silicon MotionNot using default mode "832x624" (hsync out of range)
(II) Silicon MotionNot using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1152x864 32-bpp, 59.997059Hz
(II) Silicon MotionNot using default mode "1152x864" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1152x864 32-bpp, 70.001450Hz
(II) Silicon MotionNot using default mode "1152x864" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1152x864 32-bpp, 74.998001Hz
(II) Silicon MotionNot using default mode "1152x864" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1152x864 32-bpp, 84.998978Hz
(II) Silicon MotionNot using default mode "1152x864" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1152x864 32-bpp, 85.057350Hz
(II) Silicon MotionNot using default mode "1152x864" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1152x864 32-bpp, 99.998604Hz
(II) Silicon MotionNot using default mode "1152x864" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1360x768 32-bpp, 59.960026Hz
(II) Silicon MotionNot using default mode "1360x768" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1360x768 32-bpp, 59.798992Hz
(II) Silicon MotionNot using default mode "1360x768" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1400x1050 32-bpp, 59.975616Hz
(II) Silicon MotionNot using default mode "1400x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1400x1050 32-bpp, 69.998573Hz
(II) Silicon MotionNot using default mode "1400x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1400x1050 32-bpp, 74.757210Hz
(II) Silicon MotionNot using default mode "1400x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1400x1050 32-bpp, 85.000206Hz
(II) Silicon MotionNot using default mode "1400x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1440x900 32-bpp, 59.887444Hz
(II) Silicon MotionNot using default mode "1440x900" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1600x1024 32-bpp, 60.169086Hz
(II) Silicon MotionNot using default mode "1600x1024" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1680x1050 32-bpp, 59.883251Hz
(II) Silicon MotionNot using default mode "1680x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1680x1050 32-bpp, 59.954250Hz
(II) Silicon MotionNot using default mode "1680x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1680x1050 32-bpp, 69.876373Hz
(II) Silicon MotionNot using default mode "1680x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1680x1050 32-bpp, 74.892029Hz
(II) Silicon MotionNot using default mode "1680x1050" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 1920x1080 32-bpp, 59.933880Hz
(II) Silicon MotionNot using default mode "1920x1080" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 32-bpp, 59.940475Hz
(II) Silicon MotionNot using default mode "1024x768" (width too large for virtual size)
(II) Silicon MotionNot using default mode "800x600" (width too large for virtual size)
(II) Silicon MotionNot using default mode "800x600" (width too large for virtual size)
(--) Silicon MotionVirtual size is 640x480 (pitch 640)
(**) Silicon Motion*Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) Silicon MotionModeline "640x480"x59.9 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
(==) Silicon MotionDPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.0.0
 ABI class: X.Org ANSI C Emulation, version 0.4
(==) Silicon MotionUsing XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
 compiled for 1.5.2, module version = 1.2.0
 ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC? No, I don't.
(II) resource ranges after preInit:
 [0] -1 0 0xffffffff - 0xffffffff (0x1) MX[B]
 [1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[B]
 [2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[B]
 [3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
 [4] 0 0 0x000a0000 - 0x000affff (0x10000) MS[B]
 [5] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[B]
 [6] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[B]
 [7] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[B]
 [8] -1 0 0x00000000 - 0x00000000 (0x1) IX[B]
 [9] 0 0 0x000003b0 - 0x000003bb (0xc) IS[B]
 [10] 0 0 0x000003c0 - 0x000003df (0x20) IS[B]

Fatal server error:
AddScreen/ScreenInit failed for driver 0

```

---

### Post by tutu on 2008-12-09
Hi again,

finally I found a solution:

[http://readlist.com/lists/lists.freedesktop.org/xorg/5/27538.html](http://readlist.com/lists/lists.freedesktop.org/xorg/5/27538.html)

and answers! Thanks to Francisco Jerez!

It is really necessary to insert the patches from Francisco Jerez to the ubuntu siliconmotion xserver! Who is responsible for that?

Best regards Tobias

---

### Post by acab1983 on 2009-08-15
Hello all,

I have the same problem

but no idea about how I should install the patch Francisco Jerez wrote.

Anyone can help me?


Thankyou very much in advance.

Daniele

---

