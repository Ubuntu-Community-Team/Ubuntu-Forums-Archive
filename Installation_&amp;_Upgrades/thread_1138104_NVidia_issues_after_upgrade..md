---
title: "NVidia issues after upgrade."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by evankruiselbergen on 2009-04-26
guys

I am a noob at linux, but started the upgrade from 8.10 to 9.04 anyway.
However after the upgrade my nvidia driver is not working. I tried several solutions from this forum and others, but with no result. 

What ever driver version I try I get errors. 

please see the log below.

----------------------------------------------------------

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux erik-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 26 10:55:31 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce Go 7600] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000cf00/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.51  Thu Apr 16 19:32:09 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched nv from file name nv.ids
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.12
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
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
    GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
    GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
    GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
    GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
    Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
    GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
    GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
    GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
    Quadro FX 540, GeForce 6200, GeForce 6500,
    GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
    GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
    GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
    GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT,
    GeForce 6200, GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
    GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
    GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
    GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
    GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
    GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7300 GT,
    GeForce 7600 GT, GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE,
    GeForce 7300 GT, GeForce Go 7700, GeForce Go 7600,
    GeForce Go 7600 GT, Quadro NVS 300M, GeForce Go 7900 SE,
    Quadro FX 550M, Quadro FX 560, GeForce 7900 GTX, GeForce 7900 GT,
    GeForce 7900 GS, GeForce Go 7900 GS, GeForce Go 7900 GTX,
    Quadro FX 2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500,
    Quadro FX 1500, Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE,
    GeForce 6100, GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX,
    GeForce 8800 GTS, GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600,
    GeForce 8600 GTS, GeForce 8600 GT, GeForce 8600 GT, GeForce 8600 GS,
    GeForce 8400 GS, GeForce 9500M GS, GeForce 8600M GT,
    GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M,
    Quadro FX 570M, Quadro FX 1600M, Quadro FX 570, Quadro FX 1700,
    GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS, GeForce 8300 GS,
    GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
    GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
    Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
    Quadro NVS 290, GeForce GTX 280, GeForce GTX 260,
    GeForce 8800 GTS 512, GeForce 8800 GT, GeForce 9800 GX2,
    GeForce 8800 GS, GeForce 8800M GTS, GeForce 8800M GTX,
    GeForce 8800 GS, GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX,
    GeForce 9800 GTK+, GeForce 9800 GT, GeForce GTS 250, Quadro FX 3700,
    Quadro FX 3600M, GeForce 9600 GT, GeForce 9600 GS, GeForce 9800M GTS,
    GeForce 9700M GTS, GeForce 9800M GTS, GeForce 9500 GT,
    GeForce 9600M GT, GeForce 9600M GS, GeForce 9600M GT,
    GeForce 9500M G, GeForce 9300 GS, GeForce 8400 GS, GeForce 9300M GS,
    GeForce 9200M GS, GeForce 9300M GS, Quadro NVS 150M, Quadro NVS 160M
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce Go 7600 at 01@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce Go 7600"
(II) NV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 800
(II) NV(0): NOTE: This driver cannot reconfigure the BIOS-programmed size.
(II) NV(0): These dimensions will be used as the panel size for mode validation.
(II) NV(0): Panel is LVDS
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using hsync range of 0.00-49.31 kHz
(II) NV(0): Configured Monitor: Using vrefresh range of 0.00-59.91 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (vrefresh out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) NV(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) NV(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1080" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NV(0): Virtual size is 1280x800 (pitch 1280)
(**) NV(0): *Driver mode "1280x800": 71.0 MHz, 49.3 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
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
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(**) Option "xkb_variant" "euro"
(**) AT Translated Set 2 keyboard: xkb_variant: "euro"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(**) Option "xkb_variant" "euro"
(**) Video Bus: xkb_variant: "euro"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found

---

### Post by Malta paul on 2009-04-26
I guess you can boot in the default graphics mode?
If so go to System>Administration>Hardware Drivers and see what driver is detected and recommended. Then select it, activate and reboot.
Good luck:)

---

### Post by evankruiselbergen on 2009-04-26
that is what I tried earlier.. didn't work either. it recommends the 180 nvidia driver, but that is installing but also failing..

---

### Post by evankruiselbergen on 2009-04-26
Here's the log when I installed the 180 drivers via the hardware drivers app. 

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux erik-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 26 13:34:13 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce Go 7600] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000cf00/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by evankruiselbergen on 2009-04-26
the latest log shows more errors.. for some reason it is not detecting the correct resolution, Which should be 1280 x 800.

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux erik-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Apr 26 13:48:49 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce Go 7600] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000cf00/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G73 Board - toshg73m
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 14
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 14
    LinNumberOfImagePages: 14
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 101 (640x480)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
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
    NumberOfImages: 10
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 10
    LinNumberOfImagePages: 10
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 102 (800x600)
    ModeAttributes: 0x31f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 100
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 4
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 3
    BankSize: 0
    NumberOfImages: 14
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 100
    BnkNumberOfImagePages: 14
    LinNumberOfImagePages: 14
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 103 (800x600)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
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
    NumberOfImages: 6
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 800
    BnkNumberOfImagePages: 6
    LinNumberOfImagePages: 6
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 104 (1024x768)
    ModeAttributes: 0x31f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 128
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 4
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 3
    BankSize: 0
    NumberOfImages: 6
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 128
    BnkNumberOfImagePages: 6
    LinNumberOfImagePages: 6
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 105 (1024x768)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
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
    NumberOfImages: 3
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 3
    LinNumberOfImagePages: 3
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 10e (320x200)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 30
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 30
    LinNumberOfImagePages: 30
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 10f (320x200)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 1280
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 14
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 14
    LinNumberOfImagePages: 14
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 111 (640x480)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
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
    NumberOfImages: 4
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 4
    LinNumberOfImagePages: 4
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 112 (640x480)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
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
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 114 (800x600)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
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
    NumberOfImages: 2
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 115 (800x600)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 117 (1024x768)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 118 (1024x768)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 160 (1280x800)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 800
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 161 (1280x800)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc000a0ef
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 800
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xe0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G73 Board - toshg73m
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): virtual address = 0xa682e000,
    physical address = 0xe0000000, size = 268435456
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(**) Option "xkb_variant" "euro"
(**) AT Translated Set 2 keyboard: xkb_variant: "euro"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(**) Option "xkb_variant" "euro"
(**) Video Bus: xkb_variant: "euro"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found

---

### Post by RedStickHam on 2009-04-26
I have the NVIDIO GeForceFX5500.  It's an older card, but it works fine for me.  I used the upgrade tool to upgrade from 8.04 to 9.04 and had the same problem.  What I ended up doing was downloading Envyng using Symantic Package Manager and installed the driver using that software.  After a reboot, it's working fine.

Hope this helps.

RedStickHam

---

### Post by evankruiselbergen on 2009-04-26
been there done that... also no luck.. even tried compiling a new driver from the nvidia website.. even that did not work. I cannot go back to the 177 driver since it shows in the database, but I cannot select it.

---

### Post by ed-koala on 2009-04-26
see my post here:

[http://ubuntuforums.org/showthread.php?t=1139101]("http://ubuntuforums.org/showthread.php?t=1139101")

Hope it does the trick, I have 2 video cards tho.

---

### Post by inobe on 2009-04-27
> **evankruiselbergen said:**
> been there done that... also no luck.. even tried compiling a new driver from the nvidia website.. even that did not work. I cannot go back to the 177 driver since it shows in the database, but I cannot select it.

i helped someone with the same problem, the infamous black ui.

[http://ubuntuforums.org/showthread.php?t=1129280](http://ubuntuforums.org/showthread.php?t=1129280)

after post #10 it gets very easy and interesting.

if you have a problem' let me know so that we can proceed on this thread.

---

### Post by evankruiselbergen on 2009-04-28
Found it. This Toshiba laptop (Qosmio F30-123) has a V-tuner based on CX23418 using module CX18.

What I had to do is blacklist this cx18 module then load the nvidia drivers.. all works now.

---

### Post by nazko on 2009-06-18
how can i blacklist this c18 thing?
i have qosmio f30 aswell and i have those problems every since i start using linux.my favorite was kubuntu but that nvidia x configuration is such a pain in the *** that i deside to use ubuntu.i have and other problem with my laptop - i can't manage to fix my buil-in mic.it's never worked on linux...anyone can help?

---

