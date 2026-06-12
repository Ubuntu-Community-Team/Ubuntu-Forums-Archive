---
title: "Problem in Display in sony vaio VPCCW16FG"
date: 2010-10-18
forum: Hardware
---

### Post by simar.mohar on 2010-10-18
Actually I'm having a long time problem with display. Because there are a lot of problems and all seems to be interlinked so I will mention them all here
1. In karmic koala
   The display works fine but brightness can't be controlled. The indicator appears and the level changes there when i use the Brightness UP and brightness down keys but actually no change in brightness take place. In the Xorg.0.log I can trace a line like
```
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```This is the full Xorg.0.log

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux SIMAR-VAIO 2.6.31-22-generic-pae #65-Ubuntu SMP Thu Sep 16 16:02:41 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic-pae root=UUID=15e8b11e-1bbe-4b55-bfc4-04461df4e941 ro quiet splash
Build Date: 06 May 2010  09:30:46PM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 18 13:35:08 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0a2a:104d:905e nVidia Corporation rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default nv Device 0"
        Driver    "nv"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default nv Screen 0"
        Device    "Builtin Default nv Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default nv Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default nv Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default nv Device 0"
(==) No monitor specified for screen "Builtin Default nv Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
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
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.1.14
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
     RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
     GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
     GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
     Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
     GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
     GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
     Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
     Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
     GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
     GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
     GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
     GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
     GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
     Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
     GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
     Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
     GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
     Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
     GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
     GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
     GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
     GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
     Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
     GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
     GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
     GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
     Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
     GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
     Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
     GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
     GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
     GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
     Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
     GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
     GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
     GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
     GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
     GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
     GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
     Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
     GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
     Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
     GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
     GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
     GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
     Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
     Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
     Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
     GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
     GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
     GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
     GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
     GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
     Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
     GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
     GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
     Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
     GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
     GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
     Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
     GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
     GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
     GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
     Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
     GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
     GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
     GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
     GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
     GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
     Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
     GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
     GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
     GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
     Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
     Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
     GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
     GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
     Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
     GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
     GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
     GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
     GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
     GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
     GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
     Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
     GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
     GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
     GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
     GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
     GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
     GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
     GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
     Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
     GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
     GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
     Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
     Quadro NVS 450,  Quadro NVS 295
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
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
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
c000:0409: 66 ILLEGAL EXTENDED X86 OPCODE!
(II) VESA(0): VESA BIOS not detected
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```After searching internet I found this [http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2) and found that the EDID information is not able to transmit in ubuntu. 

2. When I install nvidia driver the display completely goes off after Ubuntu splash.. I have found some workaround using the EDID exported from windows and then configure the Xorg.cong to use that EDID information explicitly. Still the brightness issue remains.

3. After installing Lucid 'fresh installation' the display goes off completely. I hope this is due to noveau driver.

4. If I upgrade Lucid in a working(nvidia workaround) karmic then the display works fine but no brightness still

5. When I either 'fresh install' or upgrade 'maverick' form a working lucid there is no display at all.

I think the only issue is the EDID information is not reaching the kernel from the monitor. can't we fix this stuff so that the bug is removed. I have already filed a bug in ubuntu some 6 months back but no one has even seen the bug..

I hope I can fix this bug if some experienced user can assist me..

---

### Post by pagonde on 2010-12-13
my vaio laptop have this problem
model: VPCCW 2QGX/B
graphic: Nvidia Geforce 320M

after install maverick, laptop LCD was black, and external monitor work fine
after install either nvidia latest driver in nvidia,com  or "apt-get install nvidia-current, external and LCD was black, ( system was halted)

i think the problem is this fact that this vaio LED Display not recognised by ubuntu (and any other linux distro,,),  N O T   VGA, and related drivers...

maybe EDID files, can help us...

    -> i try openSuSE 11.3, kubuntu 10.4, kubuntu 10.10, ubuntu 10.4, ubuntu 10.10 and fedora

i love ubuntu, please help me :(

---

### Post by simar.mohar on 2010-12-16
Keep an eye on this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668554](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668554)

---

