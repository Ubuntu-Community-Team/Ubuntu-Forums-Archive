---
title: "Fujitsy Esprimo V5535 sis Graphic -1280x768 instead of 1280x800  Resloution prolbem"
date: 2012-11-08
forum: Hardware
---

### Post by lin9 on 2012-11-08
**Re: Ubuntu 10.10 and SiS mirage 3 grapichs**             
                                                                uhhm guys,

I did everything as writtenin that other tread (means copied sis driver+ xorg.conf) here - but I just can choose 1280 x 768 resolution ???

- in the xorg.conf the 1280x800 mode is listed...I didn't change anything....

what happened? why I can't choose 1280 x 800 ??

please help..also sufferd since serveral years on that dumb 1024  resolution..now so close to a real solution....just 32 tiny pixels away  from it ....are missing :sad:

please help!

- edit: my xrandr -q gives:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x768        0.0* 
   1024x768       76.0  
   800x600        73.0  
   640x480        73.0 


thanks,

...just another desperate fujitsu V5535 user
                                                                                                                                    *                                              Last edited by lin9; 1 Day Ago at 05:48 AM..                                                           *             
                                        [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_offline.gif[/IMG]                                                                                                                      [[IMG]http://ubuntuforums.org/images/rebrand/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=12339708")

---

### Post by Yellow Pasque on 2012-11-08
You should post your /var/log/Xorg.0.log
Most likely, you're using the generic VESA driver and it doesn't support 1200x800.

---

### Post by lin9 on 2012-11-08
```
[    21.218] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    21.218] X Protocol Version 11, Revision 0
[    21.218] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    21.218] Current Operating System: Linux pe47-ESPRIMO-Mobile-V5535 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686
[    21.218] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=ea9e6741-6723-4d04-8a39-c2f1d1559374 ro quiet splash vt.handoff=7
[    21.218] Build Date: 29 August 2012  12:10:05AM
[    21.218] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.218] Current version of pixman: 0.24.4
[    21.218]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    21.218] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.218] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  8 12:47:44 2012
[    21.235] (==) Using config file: "/etc/X11/xorg.conf"
[    21.235] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.285] (==) No Layout section.  Using the first Screen section.
[    21.285] (**) |-->Screen "Default Screen" (0)
[    21.285] (**) |   |-->Monitor "Configured Monitor"
[    21.287] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    21.287] (**) |   |-->Device "device1"
[    21.287] (==) Automatically adding devices
[    21.287] (==) Automatically enabling devices
[    21.300] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.300]     Entry deleted from font path.
[    21.300] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.300]     Entry deleted from font path.
[    21.300] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.300]     Entry deleted from font path.
[    21.300] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.300]     Entry deleted from font path.
[    21.300] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.300]     Entry deleted from font path.
[    21.300] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    21.300]     Entry deleted from font path.
[    21.300] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    21.300] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.300] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.301] (II) Loader magic: 0xb77c95a0
[    21.301] (II) Module ABI versions:
[    21.301]     X.Org ANSI C Emulation: 0.4
[    21.301]     X.Org Video Driver: 11.0
[    21.301]     X.Org XInput driver : 16.0
[    21.301]     X.Org Server Extension : 6.0
[    21.302] (--) PCI:*(0:1:0:0) 1039:6351:1734:1125 rev 16, Mem @ 0xc0000000/268435456, 0xd4000000/131072, I/O @ 0x00009000/128
[    21.302] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.302] (WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
[    21.302] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    21.302] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    21.302] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    21.302] (II) "record" will be loaded by default.
[    21.302] (II) "dri" will be loaded even though the default is to disable it.
[    21.302] (II) "dri2" will be loaded by default.
[    21.302] (II) LoadModule: "dbe"
[    21.326] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.344] (II) Module dbe: vendor="X.Org Foundation"
[    21.344]     compiled for 1.11.3, module version = 1.0.0
[    21.344]     Module class: X.Org Server Extension
[    21.344]     ABI class: X.Org Server Extension, version 6.0
[    21.344] (II) Loading extension DOUBLE-BUFFER
[    21.344] (II) LoadModule: "v4l"
[    21.346] (WW) Warning, couldn't open module v4l
[    21.346] (II) UnloadModule: "v4l"
[    21.346] (II) Unloading v4l
[    21.346] (EE) Failed to load module "v4l" (module does not exist, 0)
[    21.346] (II) LoadModule: "extmod"
[    21.346] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.360] (II) Module extmod: vendor="X.Org Foundation"
[    21.360]     compiled for 1.11.3, module version = 1.0.0
[    21.360]     Module class: X.Org Server Extension
[    21.360]     ABI class: X.Org Server Extension, version 6.0
[    21.360] (II) Loading extension MIT-SCREEN-SAVER
[    21.360] (II) Loading extension XFree86-VidModeExtension
[    21.360] (II) Loading extension XFree86-DGA
[    21.360] (II) Loading extension DPMS
[    21.360] (II) Loading extension XVideo
[    21.360] (II) Loading extension XVideo-MotionCompensation
[    21.360] (II) Loading extension X-Resource
[    21.360] (II) LoadModule: "glx"
[    21.360] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.390] (II) Module glx: vendor="X.Org Foundation"
[    21.390]     compiled for 1.11.3, module version = 1.0.0
[    21.390]     ABI class: X.Org Server Extension, version 6.0
[    21.390] (==) AIGLX enabled
[    21.390] (II) Loading extension GLX
[    21.390] (II) LoadModule: "record"
[    21.390] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.392] (II) Module record: vendor="X.Org Foundation"
[    21.392]     compiled for 1.11.3, module version = 1.13.0
[    21.392]     Module class: X.Org Server Extension
[    21.392]     ABI class: X.Org Server Extension, version 6.0
[    21.392] (II) Loading extension RECORD
[    21.392] (II) LoadModule: "dri2"
[    21.392] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.393] (II) Module dri2: vendor="X.Org Foundation"
[    21.393]     compiled for 1.11.3, module version = 1.2.0
[    21.393]     ABI class: X.Org Server Extension, version 6.0
[    21.393] (II) Loading extension DRI2
[    21.393] (II) LoadModule: "sisimedia"
[    21.394] (II) Loading /usr/lib/xorg/modules/drivers/sisimedia_drv.so
[    21.422] (II) Module sisimedia: vendor="X.Org Foundation"
[    21.422]     compiled for 1.8.99.906, module version = 0.8.0
[    21.422]     Module class: X.Org Video Driver
[    21.422]     ABI class: X.Org Video Driver, version 8.0
[    21.422] (EE) module ABI major version ( doesn't match the server's version (11)
[    21.422] (II) UnloadModule: "sisimedia"
[    21.422] (II) Unloading sisimedia
[    21.422] (EE) Failed to load module "sisimedia" (module requirement mismatch, 0)
[    21.422] (==) Matched sis as autoconfigured driver 0
[    21.422] (==) Matched vesa as autoconfigured driver 1
[    21.422] (==) Matched fbdev as autoconfigured driver 2
[    21.422] (==) Assigned the driver to the xf86ConfigLayout
[    21.422] (II) LoadModule: "sis"
[    21.423] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    21.454] (II) Module sis: vendor="X.Org Foundation"
[    21.454]     compiled for 1.11.3, module version = 0.10.3
[    21.454]     Module class: X.Org Video Driver
[    21.454]     ABI class: X.Org Video Driver, version 11.0
[    21.454] (II) LoadModule: "vesa"
[    21.455] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.466] (II) Module vesa: vendor="X.Org Foundation"
[    21.466]     compiled for 1.11.3, module version = 2.3.0
[    21.466]     Module class: X.Org Video Driver
[    21.466]     ABI class: X.Org Video Driver, version 11.0
[    21.466] (II) LoadModule: "fbdev"
[    21.466] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.472] (II) Module fbdev: vendor="X.Org Foundation"
[    21.472]     compiled for 1.11.3, module version = 0.4.2
[    21.472]     ABI class: X.Org Video Driver, version 11.0
[    21.472] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS[M]661[F|M]X/[M]741[GX]/[M]760[GX]/[M]761[GX]/662, SIS340,
    [M]670/[M]770[GX], [M]671/[M]771[GX]
[    21.472] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40/XG42)
[    21.472] (II) VESA: driver for VESA chipsets: vesa
[    21.472] (II) FBDEV: driver for framebuffer: fbdev
[    21.472] (++) using VT number 7

[    21.473] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.473] (WW) Falling back to old probe method for fbdev
[    21.479] (II) Loading sub module "fbdevhw"
[    21.479] (II) LoadModule: "fbdevhw"
[    21.480] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.480] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.480]     compiled for 1.11.3, module version = 0.0.2
[    21.480]     ABI class: X.Org Video Driver, version 11.0
[    21.480] (II) Loading sub module "vbe"
[    21.480] (II) LoadModule: "vbe"
[    21.481] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    21.481] (II) Module vbe: vendor="X.Org Foundation"
[    21.481]     compiled for 1.11.3, module version = 1.1.0
[    21.481]     ABI class: X.Org Video Driver, version 11.0
[    21.481] (II) Loading sub module "int10"
[    21.481] (II) LoadModule: "int10"
[    21.482] (II) Loading /usr/lib/xorg/modules/libint10.so
[    21.497] (II) Module int10: vendor="X.Org Foundation"
[    21.497]     compiled for 1.11.3, module version = 1.0.0
[    21.497]     ABI class: X.Org Video Driver, version 11.0
[    21.497] (II) VESA(0): initializing int10
[    21.502] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    21.504] (II) VESA(0): VESA BIOS detected
[    21.504] (II) VESA(0): VESA VBE Version 3.0
[    21.504] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[    21.504] (II) VESA(0): VESA VBE OEM: SiS
[    21.504] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    21.504] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    21.504] (II) VESA(0): VESA VBE OEM Product: 6330
[    21.504] (II) VESA(0): VESA VBE OEM Product Rev: 3.74.10A
[    21.518] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[    21.518] (==) VESA(0): RGB weight 888
[    21.518] (==) VESA(0): Default visual is TrueColor
[    21.519] (**) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.519] (II) Loading sub module "ddc"
[    21.519] (II) LoadModule: "ddc"
[    21.519] (II) Module "ddc" already built-in
[    21.606] (II) VESA(0): VESA VBE DDC supported
[    21.606] (II) VESA(0): VESA VBE DDC Level none
[    21.606] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    21.639] (II) VESA(0): VESA VBE DDC read failed
[    21.639] (II) VESA(0): VESA VBE PanelID read failed
[    21.639] (II) VESA(0): Searching for matching VESA mode(s):
[    21.639] Mode: 11c (1280x768 )
[    21.639]     ModeAttributes: 0x9f
[    21.639]     WinAAttributes: 0x7
[    21.639]     WinBAttributes: 0x0
[    21.639]     WinGranularity: 64
[    21.639]     WinSize: 64
[    21.639]     WinASegment: 0xa000
[    21.639]     WinBSegment: 0xa000
[    21.639]     WinFuncPtr: 0xc000877b
[    21.639]     BytesPerScanline: 1280
[    21.639]     XResolution: 1280
[    21.639]     YResolution: 768
[    21.639]     XCharSize: 8
[    21.639]     YCharSize: 16
[    21.639]     NumberOfPlanes: 1
[    21.639]     BitsPerPixel: 8
[    21.639]     NumberOfBanks: 1
[    21.639]     MemoryModel: 4
[    21.639]     BankSize: 0
[    21.639]     NumberOfImages: 7
[    21.639]     RedMaskSize: 0
[    21.639]     RedFieldPosition: 0
[    21.639]     GreenMaskSize: 0
[    21.639]     GreenFieldPosition: 0
[    21.639]     BlueMaskSize: 0
[    21.639]     BlueFieldPosition: 0
[    21.639]     RsvdMaskSize: 0
[    21.639]     RsvdFieldPosition: 0
[    21.639]     DirectColorModeInfo: 0
[    21.639]     PhysBasePtr: 0xc0000000
[    21.639]     LinBytesPerScanLine: 1280
[    21.639]     BnkNumberOfImagePages: 7
[    21.639]     LinNumberOfImagePages: 7
[    21.640]     LinRedMaskSize: 0
[    21.640]     LinRedFieldPosition: 0
[    21.640]     LinGreenMaskSize: 0
[    21.640]     LinGreenFieldPosition: 0
[    21.640]     LinBlueMaskSize: 0
[    21.640]     LinBlueFieldPosition: 0
[    21.640]     LinRsvdMaskSize: 0
[    21.640]     LinRsvdFieldPosition: 0
[    21.640]     MaxPixelClock: 0
[    21.640] Mode: 11d (1280x768)
[    21.640]     ModeAttributes: 0x9b
[    21.640]     WinAAttributes: 0x7
[    21.640]     WinBAttributes: 0x0
[    21.640]     WinGranularity: 64
[    21.640]     WinSize: 64
[    21.640]     WinASegment: 0xa000
[    21.640]     WinBSegment: 0xa000
[    21.640]     WinFuncPtr: 0xc000877b
[    21.640]     BytesPerScanline: 2560
[    21.640]     XResolution: 1280
[    21.640]     YResolution: 768
[    21.640]     XCharSize: 8
[    21.640]     YCharSize: 16
[    21.640]     NumberOfPlanes: 1
[    21.640]     BitsPerPixel: 16
[    21.640]     NumberOfBanks: 1
[    21.640]     MemoryModel: 6
[    21.640]     BankSize: 0
[    21.640]     NumberOfImages: 3
[    21.640]     RedMaskSize: 5
[    21.640]     RedFieldPosition: 11
[    21.640]     GreenMaskSize: 6
[    21.640]     GreenFieldPosition: 5
[    21.640]     BlueMaskSize: 5
[    21.640]     BlueFieldPosition: 0
[    21.640]     RsvdMaskSize: 0
[    21.640]     RsvdFieldPosition: 0
[    21.640]     DirectColorModeInfo: 0
[    21.640]     PhysBasePtr: 0xc0000000
[    21.640]     LinBytesPerScanLine: 2560
[    21.640]     BnkNumberOfImagePages: 3
[    21.640]     LinNumberOfImagePages: 3
[    21.640]     LinRedMaskSize: 5
[    21.640]     LinRedFieldPosition: 11
[    21.640]     LinGreenMaskSize: 6
[    21.640]     LinGreenFieldPosition: 5
[    21.640]     LinBlueMaskSize: 5
[    21.640]     LinBlueFieldPosition: 0
[    21.640]     LinRsvdMaskSize: 0
[    21.640]     LinRsvdFieldPosition: 0
[    21.640]     MaxPixelClock: 0
[    21.641] *Mode: 11e (1280x768)
[    21.641]     ModeAttributes: 0x9b
[    21.641]     WinAAttributes: 0x7
[    21.641]     WinBAttributes: 0x0
[    21.641]     WinGranularity: 64
[    21.641]     WinSize: 64
[    21.641]     WinASegment: 0xa000
[    21.641]     WinBSegment: 0xa000
[    21.641]     WinFuncPtr: 0xc000877b
[    21.641]     BytesPerScanline: 5120
[    21.641]     XResolution: 1280
[    21.641]     YResolution: 768
[    21.641]     XCharSize: 8
[    21.641]     YCharSize: 16
[    21.641]     NumberOfPlanes: 1
[    21.641]     BitsPerPixel: 32
[    21.641]     NumberOfBanks: 1
[    21.641]     MemoryModel: 6
[    21.641]     BankSize: 0
[    21.641]     NumberOfImages: 1
[    21.641]     RedMaskSize: 8
[    21.641]     RedFieldPosition: 16
[    21.641]     GreenMaskSize: 8
[    21.641]     GreenFieldPosition: 8
[    21.641]     BlueMaskSize: 8
[    21.641]     BlueFieldPosition: 0
[    21.641]     RsvdMaskSize: 8
[    21.641]     RsvdFieldPosition: 24
[    21.641]     DirectColorModeInfo: 0
[    21.641]     PhysBasePtr: 0xc0000000
[    21.641]     LinBytesPerScanLine: 5120
[    21.641]     BnkNumberOfImagePages: 1
[    21.641]     LinNumberOfImagePages: 1
[    21.641]     LinRedMaskSize: 8
[    21.641]     LinRedFieldPosition: 16
[    21.641]     LinGreenMaskSize: 8
[    21.641]     LinGreenFieldPosition: 8
[    21.641]     LinBlueMaskSize: 8
[    21.641]     LinBlueFieldPosition: 0
[    21.641]     LinRsvdMaskSize: 8
[    21.641]     LinRsvdFieldPosition: 24
[    21.641]     MaxPixelClock: 0
[    21.641] Mode: 101 (640x480)
[    21.641]     ModeAttributes: 0x9f
[    21.641]     WinAAttributes: 0x7
[    21.641]     WinBAttributes: 0x0
[    21.641]     WinGranularity: 64
[    21.641]     WinSize: 64
[    21.641]     WinASegment: 0xa000
[    21.641]     WinBSegment: 0xa000
[    21.641]     WinFuncPtr: 0xc000877b
[    21.641]     BytesPerScanline: 640
[    21.641]     XResolution: 640
[    21.641]     YResolution: 480
[    21.641]     XCharSize: 8
[    21.641]     YCharSize: 16
[    21.641]     NumberOfPlanes: 1
[    21.641]     BitsPerPixel: 8
[    21.641]     NumberOfBanks: 1
[    21.641]     MemoryModel: 4
[    21.641]     BankSize: 0
[    21.641]     NumberOfImages: 24
[    21.641]     RedMaskSize: 0
[    21.641]     RedFieldPosition: 0
[    21.641]     GreenMaskSize: 0
[    21.641]     GreenFieldPosition: 0
[    21.641]     BlueMaskSize: 0
[    21.641]     BlueFieldPosition: 0
[    21.641]     RsvdMaskSize: 0
[    21.641]     RsvdFieldPosition: 0
[    21.641]     DirectColorModeInfo: 0
[    21.641]     PhysBasePtr: 0xc0000000
[    21.641]     LinBytesPerScanLine: 640
[    21.641]     BnkNumberOfImagePages: 24
[    21.642]     LinNumberOfImagePages: 24
[    21.642]     LinRedMaskSize: 0
[    21.642]     LinRedFieldPosition: 0
[    21.642]     LinGreenMaskSize: 0
[    21.642]     LinGreenFieldPosition: 0
[    21.642]     LinBlueMaskSize: 0
[    21.642]     LinBlueFieldPosition: 0
[    21.642]     LinRsvdMaskSize: 0
[    21.642]     LinRsvdFieldPosition: 0
[    21.642]     MaxPixelClock: 0
[    21.642] Mode: 100 (640x400)
[    21.642]     ModeAttributes: 0x9f
[    21.642]     WinAAttributes: 0x7
[    21.642]     WinBAttributes: 0x0
[    21.642]     WinGranularity: 64
[    21.642]     WinSize: 64
[    21.642]     WinASegment: 0xa000
[    21.642]     WinBSegment: 0xa000
[    21.642]     WinFuncPtr: 0xc000877b
[    21.642]     BytesPerScanline: 640
[    21.642]     XResolution: 640
[    21.642]     YResolution: 400
[    21.642]     XCharSize: 8
[    21.642]     YCharSize: 16
[    21.642]     NumberOfPlanes: 1
[    21.642]     BitsPerPixel: 8
[    21.642]     NumberOfBanks: 1
[    21.642]     MemoryModel: 4
[    21.642]     BankSize: 0
[    21.642]     NumberOfImages: 31
[    21.642]     RedMaskSize: 0
[    21.642]     RedFieldPosition: 0
[    21.642]     GreenMaskSize: 0
[    21.642]     GreenFieldPosition: 0
[    21.642]     BlueMaskSize: 0
[    21.642]     BlueFieldPosition: 0
[    21.642]     RsvdMaskSize: 0
[    21.642]     RsvdFieldPosition: 0
[    21.642]     DirectColorModeInfo: 0
[    21.642]     PhysBasePtr: 0xc0000000
[    21.642]     LinBytesPerScanLine: 640
[    21.642]     BnkNumberOfImagePages: 31
[    21.642]     LinNumberOfImagePages: 31
[    21.642]     LinRedMaskSize: 0
[    21.642]     LinRedFieldPosition: 0
[    21.642]     LinGreenMaskSize: 0
[    21.642]     LinGreenFieldPosition: 0
[    21.642]     LinBlueMaskSize: 0
[    21.642]     LinBlueFieldPosition: 0
[    21.642]     LinRsvdMaskSize: 0
[    21.642]     LinRsvdFieldPosition: 0
[    21.642]     MaxPixelClock: 0
[    21.643] Mode: 103 (800x600)
[    21.643]     ModeAttributes: 0x9f
[    21.643]     WinAAttributes: 0x7
[    21.643]     WinBAttributes: 0x0
[    21.643]     WinGranularity: 64
[    21.643]     WinSize: 64
[    21.643]     WinASegment: 0xa000
[    21.643]     WinBSegment: 0xa000
[    21.643]     WinFuncPtr: 0xc000877b
[    21.643]     BytesPerScanline: 800
[    21.643]     XResolution: 800
[    21.643]     YResolution: 600
[    21.643]     XCharSize: 8
[    21.643]     YCharSize: 16
[    21.643]     NumberOfPlanes: 1
[    21.643]     BitsPerPixel: 8
[    21.643]     NumberOfBanks: 1
[    21.643]     MemoryModel: 4
[    21.643]     BankSize: 0
[    21.643]     NumberOfImages: 15
[    21.643]     RedMaskSize: 0
[    21.643]     RedFieldPosition: 0
[    21.643]     GreenMaskSize: 0
[    21.643]     GreenFieldPosition: 0
[    21.643]     BlueMaskSize: 0
[    21.643]     BlueFieldPosition: 0
[    21.643]     RsvdMaskSize: 0
[    21.643]     RsvdFieldPosition: 0
[    21.643]     DirectColorModeInfo: 0
[    21.643]     PhysBasePtr: 0xc0000000
[    21.643]     LinBytesPerScanLine: 800
[    21.643]     BnkNumberOfImagePages: 15
[    21.643]     LinNumberOfImagePages: 15
[    21.643]     LinRedMaskSize: 0
[    21.643]     LinRedFieldPosition: 0
[    21.643]     LinGreenMaskSize: 0
[    21.643]     LinGreenFieldPosition: 0
[    21.643]     LinBlueMaskSize: 0
[    21.643]     LinBlueFieldPosition: 0
[    21.643]     LinRsvdMaskSize: 0
[    21.643]     LinRsvdFieldPosition: 0
[    21.643]     MaxPixelClock: 0
[    21.643] Mode: 104 (1024x768)
[    21.643]     ModeAttributes: 0x1f
[    21.643]     WinAAttributes: 0x7
[    21.643]     WinBAttributes: 0x0
[    21.643]     WinGranularity: 64
[    21.643]     WinSize: 64
[    21.643]     WinASegment: 0xa000
[    21.643]     WinBSegment: 0xa000
[    21.643]     WinFuncPtr: 0xc000877b
[    21.643]     BytesPerScanline: 128
[    21.643]     XResolution: 1024
[    21.643]     YResolution: 768
[    21.643]     XCharSize: 8
[    21.643]     YCharSize: 16
[    21.643]     NumberOfPlanes: 4
[    21.643]     BitsPerPixel: 4
[    21.643]     NumberOfBanks: 1
[    21.643]     MemoryModel: 3
[    21.643]     BankSize: 0
[    21.643]     NumberOfImages: 15
[    21.643]     RedMaskSize: 0
[    21.643]     RedFieldPosition: 0
[    21.643]     GreenMaskSize: 0
[    21.643]     GreenFieldPosition: 0
[    21.643]     BlueMaskSize: 0
[    21.643]     BlueFieldPosition: 0
[    21.644]     RsvdMaskSize: 0
[    21.644]     RsvdFieldPosition: 0
[    21.644]     DirectColorModeInfo: 0
[    21.644]     PhysBasePtr: 0xc0000000
[    21.644]     LinBytesPerScanLine: 128
[    21.644]     BnkNumberOfImagePages: 15
[    21.644]     LinNumberOfImagePages: 15
[    21.644]     LinRedMaskSize: 0
[    21.644]     LinRedFieldPosition: 0
[    21.644]     LinGreenMaskSize: 0
[    21.644]     LinGreenFieldPosition: 0
[    21.644]     LinBlueMaskSize: 0
[    21.644]     LinBlueFieldPosition: 0
[    21.644]     LinRsvdMaskSize: 0
[    21.644]     LinRsvdFieldPosition: 0
[    21.644]     MaxPixelClock: 0
[    21.644] Mode: 105 (1024x768)
[    21.644]     ModeAttributes: 0x9f
[    21.644]     WinAAttributes: 0x7
[    21.644]     WinBAttributes: 0x0
[    21.644]     WinGranularity: 64
[    21.644]     WinSize: 64
[    21.644]     WinASegment: 0xa000
[    21.644]     WinBSegment: 0xa000
[    21.644]     WinFuncPtr: 0xc000877b
[    21.644]     BytesPerScanline: 1024
[    21.644]     XResolution: 1024
[    21.644]     YResolution: 768
[    21.644]     XCharSize: 8
[    21.644]     YCharSize: 16
[    21.644]     NumberOfPlanes: 1
[    21.644]     BitsPerPixel: 8
[    21.644]     NumberOfBanks: 1
[    21.644]     MemoryModel: 4
[    21.644]     BankSize: 0
[    21.644]     NumberOfImages: 9
[    21.644]     RedMaskSize: 0
[    21.644]     RedFieldPosition: 0
[    21.644]     GreenMaskSize: 0
[    21.644]     GreenFieldPosition: 0
[    21.644]     BlueMaskSize: 0
[    21.644]     BlueFieldPosition: 0
[    21.645]     RsvdMaskSize: 0
[    21.645]     RsvdFieldPosition: 0
[    21.645]     DirectColorModeInfo: 0
[    21.645]     PhysBasePtr: 0xc0000000
[    21.645]     LinBytesPerScanLine: 1024
[    21.645]     BnkNumberOfImagePages: 9
[    21.645]     LinNumberOfImagePages: 9
[    21.645]     LinRedMaskSize: 0
[    21.645]     LinRedFieldPosition: 0
[    21.645]     LinGreenMaskSize: 0
[    21.645]     LinGreenFieldPosition: 0
[    21.645]     LinBlueMaskSize: 0
[    21.645]     LinBlueFieldPosition: 0
[    21.645]     LinRsvdMaskSize: 0
[    21.645]     LinRsvdFieldPosition: 0
[    21.645]     MaxPixelClock: 0
[    21.645] Mode: 10d (320x200)
[    21.645]     ModeAttributes: 0x9b
[    21.645]     WinAAttributes: 0x7
[    21.645]     WinBAttributes: 0x0
[    21.645]     WinGranularity: 64
[    21.645]     WinSize: 64
[    21.645]     WinASegment: 0xa000
[    21.645]     WinBSegment: 0xa000
[    21.645]     WinFuncPtr: 0xc000877b
[    21.645]     BytesPerScanline: 640
[    21.645]     XResolution: 320
[    21.645]     YResolution: 200
[    21.645]     XCharSize: 8
[    21.645]     YCharSize: 8
[    21.645]     NumberOfPlanes: 1
[    21.645]     BitsPerPixel: 15
[    21.645]     NumberOfBanks: 1
[    21.645]     MemoryModel: 6
[    21.645]     BankSize: 0
[    21.645]     NumberOfImages: 63
[    21.645]     RedMaskSize: 5
[    21.645]     RedFieldPosition: 10
[    21.645]     GreenMaskSize: 5
[    21.645]     GreenFieldPosition: 5
[    21.645]     BlueMaskSize: 5
[    21.645]     BlueFieldPosition: 0
[    21.645]     RsvdMaskSize: 0
[    21.645]     RsvdFieldPosition: 0
[    21.645]     DirectColorModeInfo: 0
[    21.645]     PhysBasePtr: 0xc0000000
[    21.645]     LinBytesPerScanLine: 640
[    21.645]     BnkNumberOfImagePages: 63
[    21.645]     LinNumberOfImagePages: 63
[    21.645]     LinRedMaskSize: 5
[    21.645]     LinRedFieldPosition: 10
[    21.645]     LinGreenMaskSize: 5
[    21.645]     LinGreenFieldPosition: 5
[    21.646]     LinBlueMaskSize: 5
[    21.646]     LinBlueFieldPosition: 0
[    21.646]     LinRsvdMaskSize: 0
[    21.646]     LinRsvdFieldPosition: 0
[    21.646]     MaxPixelClock: 0
[    21.646] Mode: 10e (320x200)
[    21.646]     ModeAttributes: 0x9b
[    21.646]     WinAAttributes: 0x7
[    21.646]     WinBAttributes: 0x0
[    21.646]     WinGranularity: 64
[    21.646]     WinSize: 64
[    21.646]     WinASegment: 0xa000
[    21.646]     WinBSegment: 0xa000
[    21.646]     WinFuncPtr: 0xc000877b
[    21.646]     BytesPerScanline: 640
[    21.646]     XResolution: 320
[    21.646]     YResolution: 200
[    21.646]     XCharSize: 8
[    21.646]     YCharSize: 8
[    21.646]     NumberOfPlanes: 1
[    21.646]     BitsPerPixel: 16
[    21.646]     NumberOfBanks: 1
[    21.646]     MemoryModel: 6
[    21.646]     BankSize: 0
[    21.646]     NumberOfImages: 63
[    21.646]     RedMaskSize: 5
[    21.646]     RedFieldPosition: 11
[    21.646]     GreenMaskSize: 6
[    21.646]     GreenFieldPosition: 5
[    21.646]     BlueMaskSize: 5
[    21.646]     BlueFieldPosition: 0
[    21.646]     RsvdMaskSize: 0
[    21.646]     RsvdFieldPosition: 0
[    21.646]     DirectColorModeInfo: 0
[    21.646]     PhysBasePtr: 0xc0000000
[    21.646]     LinBytesPerScanLine: 640
[    21.646]     BnkNumberOfImagePages: 63
[    21.646]     LinNumberOfImagePages: 63
[    21.646]     LinRedMaskSize: 5
[    21.646]     LinRedFieldPosition: 11
[    21.646]     LinGreenMaskSize: 6
[    21.646]     LinGreenFieldPosition: 5
[    21.646]     LinBlueMaskSize: 5
[    21.646]     LinBlueFieldPosition: 0
[    21.646]     LinRsvdMaskSize: 0
[    21.646]     LinRsvdFieldPosition: 0
[    21.646]     MaxPixelClock: 0
[    21.647] Mode: 110 (640x480)
[    21.647]     ModeAttributes: 0x9b
[    21.647]     WinAAttributes: 0x7
[    21.647]     WinBAttributes: 0x0
[    21.647]     WinGranularity: 64
[    21.647]     WinSize: 64
[    21.647]     WinASegment: 0xa000
[    21.647]     WinBSegment: 0xa000
[    21.647]     WinFuncPtr: 0xc000877b
[    21.647]     BytesPerScanline: 1280
[    21.647]     XResolution: 640
[    21.647]     YResolution: 480
[    21.647]     XCharSize: 8
[    21.647]     YCharSize: 16
[    21.647]     NumberOfPlanes: 1
[    21.647]     BitsPerPixel: 15
[    21.647]     NumberOfBanks: 1
[    21.647]     MemoryModel: 6
[    21.647]     BankSize: 0
[    21.647]     NumberOfImages: 11
[    21.647]     RedMaskSize: 5
[    21.647]     RedFieldPosition: 10
[    21.647]     GreenMaskSize: 5
[    21.647]     GreenFieldPosition: 5
[    21.647]     BlueMaskSize: 5
[    21.647]     BlueFieldPosition: 0
[    21.647]     RsvdMaskSize: 0
[    21.647]     RsvdFieldPosition: 0
[    21.647]     DirectColorModeInfo: 0
[    21.647]     PhysBasePtr: 0xc0000000
[    21.647]     LinBytesPerScanLine: 1280
[    21.647]     BnkNumberOfImagePages: 11
[    21.647]     LinNumberOfImagePages: 11
[    21.647]     LinRedMaskSize: 5
[    21.647]     LinRedFieldPosition: 10
[    21.647]     LinGreenMaskSize: 5
[    21.647]     LinGreenFieldPosition: 5
[    21.647]     LinBlueMaskSize: 5
[    21.647]     LinBlueFieldPosition: 0
[    21.647]     LinRsvdMaskSize: 0
[    21.647]     LinRsvdFieldPosition: 0
[    21.647]     MaxPixelClock: 0
[    21.648] Mode: 111 (640x480)
[    21.648]     ModeAttributes: 0x9b
[    21.648]     WinAAttributes: 0x7
[    21.648]     WinBAttributes: 0x0
[    21.648]     WinGranularity: 64
[    21.648]     WinSize: 64
[    21.648]     WinASegment: 0xa000
[    21.648]     WinBSegment: 0xa000
[    21.648]     WinFuncPtr: 0xc000877b
[    21.648]     BytesPerScanline: 1280
[    21.648]     XResolution: 640
[    21.648]     YResolution: 480
[    21.648]     XCharSize: 8
[    21.648]     YCharSize: 16
[    21.648]     NumberOfPlanes: 1
[    21.648]     BitsPerPixel: 16
[    21.648]     NumberOfBanks: 1
[    21.648]     MemoryModel: 6
[    21.648]     BankSize: 0
[    21.648]     NumberOfImages: 11
[    21.648]     RedMaskSize: 5
[    21.648]     RedFieldPosition: 11
[    21.648]     GreenMaskSize: 6
[    21.648]     GreenFieldPosition: 5
[    21.648]     BlueMaskSize: 5
[    21.648]     BlueFieldPosition: 0
[    21.648]     RsvdMaskSize: 0
[    21.648]     RsvdFieldPosition: 0
[    21.648]     DirectColorModeInfo: 0
[    21.648]     PhysBasePtr: 0xc0000000
[    21.648]     LinBytesPerScanLine: 1280
[    21.648]     BnkNumberOfImagePages: 11
[    21.648]     LinNumberOfImagePages: 11
[    21.648]     LinRedMaskSize: 5
[    21.648]     LinRedFieldPosition: 11
[    21.648]     LinGreenMaskSize: 6
[    21.648]     LinGreenFieldPosition: 5
[    21.648]     LinBlueMaskSize: 5
[    21.648]     LinBlueFieldPosition: 0
[    21.648]     LinRsvdMaskSize: 0
[    21.648]     LinRsvdFieldPosition: 0
[    21.648]     MaxPixelClock: 0
[    21.648] Mode: 113 (800x600)
[    21.648]     ModeAttributes: 0x9b
[    21.648]     WinAAttributes: 0x7
[    21.648]     WinBAttributes: 0x0
[    21.648]     WinGranularity: 64
[    21.648]     WinSize: 64
[    21.648]     WinASegment: 0xa000
[    21.648]     WinBSegment: 0xa000
[    21.648]     WinFuncPtr: 0xc000877b
[    21.648]     BytesPerScanline: 1600
[    21.649]     XResolution: 800
[    21.649]     YResolution: 600
[    21.649]     XCharSize: 8
[    21.649]     YCharSize: 16
[    21.649]     NumberOfPlanes: 1
[    21.649]     BitsPerPixel: 15
[    21.649]     NumberOfBanks: 1
[    21.649]     MemoryModel: 6
[    21.649]     BankSize: 0
[    21.649]     NumberOfImages: 7
[    21.649]     RedMaskSize: 5
[    21.649]     RedFieldPosition: 10
[    21.649]     GreenMaskSize: 5
[    21.649]     GreenFieldPosition: 5
[    21.649]     BlueMaskSize: 5
[    21.649]     BlueFieldPosition: 0
[    21.649]     RsvdMaskSize: 0
[    21.649]     RsvdFieldPosition: 0
[    21.649]     DirectColorModeInfo: 0
[    21.649]     PhysBasePtr: 0xc0000000
[    21.649]     LinBytesPerScanLine: 1600
[    21.649]     BnkNumberOfImagePages: 7
[    21.649]     LinNumberOfImagePages: 7
[    21.649]     LinRedMaskSize: 5
[    21.649]     LinRedFieldPosition: 10
[    21.649]     LinGreenMaskSize: 5
[    21.649]     LinGreenFieldPosition: 5
[    21.649]     LinBlueMaskSize: 5
[    21.649]     LinBlueFieldPosition: 0
[    21.649]     LinRsvdMaskSize: 0
[    21.649]     LinRsvdFieldPosition: 0
[    21.649]     MaxPixelClock: 0
[    21.649] Mode: 114 (800x600)
[    21.649]     ModeAttributes: 0x9b
[    21.649]     WinAAttributes: 0x7
[    21.649]     WinBAttributes: 0x0
[    21.649]     WinGranularity: 64
[    21.649]     WinSize: 64
[    21.649]     WinASegment: 0xa000
[    21.649]     WinBSegment: 0xa000
[    21.649]     WinFuncPtr: 0xc000877b
[    21.649]     BytesPerScanline: 1600
[    21.649]     XResolution: 800
[    21.649]     YResolution: 600
[    21.649]     XCharSize: 8
[    21.649]     YCharSize: 16
[    21.649]     NumberOfPlanes: 1
[    21.649]     BitsPerPixel: 16
[    21.649]     NumberOfBanks: 1
[    21.649]     MemoryModel: 6
[    21.649]     BankSize: 0
[    21.649]     NumberOfImages: 7
[    21.649]     RedMaskSize: 5
[    21.649]     RedFieldPosition: 11
[    21.649]     GreenMaskSize: 6
[    21.649]     GreenFieldPosition: 5
[    21.649]     BlueMaskSize: 5
[    21.649]     BlueFieldPosition: 0
[    21.649]     RsvdMaskSize: 0
[    21.649]     RsvdFieldPosition: 0
[    21.649]     DirectColorModeInfo: 0
[    21.649]     PhysBasePtr: 0xc0000000
[    21.649]     LinBytesPerScanLine: 1600
[    21.649]     BnkNumberOfImagePages: 7
[    21.649]     LinNumberOfImagePages: 7
[    21.649]     LinRedMaskSize: 5
[    21.649]     LinRedFieldPosition: 11
[    21.649]     LinGreenMaskSize: 6
[    21.650]     LinGreenFieldPosition: 5
[    21.650]     LinBlueMaskSize: 5
[    21.650]     LinBlueFieldPosition: 0
[    21.650]     LinRsvdMaskSize: 0
[    21.650]     LinRsvdFieldPosition: 0
[    21.650]     MaxPixelClock: 0
[    21.650] Mode: 116 (1024x768 )
[    21.650]     ModeAttributes: 0x9b
[    21.650]     WinAAttributes: 0x7
[    21.650]     WinBAttributes: 0x0
[    21.650]     WinGranularity: 64
[    21.650]     WinSize: 64
[    21.650]     WinASegment: 0xa000
[    21.650]     WinBSegment: 0xa000
[    21.650]     WinFuncPtr: 0xc000877b
[    21.650]     BytesPerScanline: 2048
[    21.650]     XResolution: 1024
[    21.650]     YResolution: 768
[    21.650]     XCharSize: 8
[    21.650]     YCharSize: 16
[    21.650]     NumberOfPlanes: 1
[    21.650]     BitsPerPixel: 15
[    21.650]     NumberOfBanks: 1
[    21.650]     MemoryModel: 6
[    21.650]     BankSize: 0
[    21.650]     NumberOfImages: 4
[    21.650]     RedMaskSize: 5
[    21.650]     RedFieldPosition: 10
[    21.650]     GreenMaskSize: 5
[    21.650]     GreenFieldPosition: 5
[    21.650]     BlueMaskSize: 5
[    21.650]     BlueFieldPosition: 0
[    21.650]     RsvdMaskSize: 0
[    21.650]     RsvdFieldPosition: 0
[    21.650]     DirectColorModeInfo: 0
[    21.650]     PhysBasePtr: 0xc0000000
[    21.650]     LinBytesPerScanLine: 2048
[    21.650]     BnkNumberOfImagePages: 4
[    21.650]     LinNumberOfImagePages: 4
[    21.650]     LinRedMaskSize: 5
[    21.650]     LinRedFieldPosition: 10
[    21.650]     LinGreenMaskSize: 5
[    21.650]     LinGreenFieldPosition: 5
[    21.650]     LinBlueMaskSize: 5
[    21.650]     LinBlueFieldPosition: 0
[    21.650]     LinRsvdMaskSize: 0
[    21.650]     LinRsvdFieldPosition: 0
[    21.650]     MaxPixelClock: 0
[    21.651] Mode: 117 (1024x768 )
[    21.651]     ModeAttributes: 0x9b
[    21.651]     WinAAttributes: 0x7
[    21.651]     WinBAttributes: 0x0
[    21.651]     WinGranularity: 64
[    21.651]     WinSize: 64
[    21.651]     WinASegment: 0xa000
[    21.651]     WinBSegment: 0xa000
[    21.651]     WinFuncPtr: 0xc000877b
[    21.651]     BytesPerScanline: 2048
[    21.651]     XResolution: 1024
[    21.651]     YResolution: 768
[    21.651]     XCharSize: 8
[    21.651]     YCharSize: 16
[    21.651]     NumberOfPlanes: 1
[    21.651]     BitsPerPixel: 16
[    21.651]     NumberOfBanks: 1
[    21.651]     MemoryModel: 6
[    21.651]     BankSize: 0
[    21.651]     NumberOfImages: 4
[    21.651]     RedMaskSize: 5
[    21.651]     RedFieldPosition: 11
[    21.651]     GreenMaskSize: 6
[    21.651]     GreenFieldPosition: 5
[    21.651]     BlueMaskSize: 5
[    21.651]     BlueFieldPosition: 0
[    21.651]     RsvdMaskSize: 0
[    21.651]     RsvdFieldPosition: 0
[    21.651]     DirectColorModeInfo: 0
[    21.651]     PhysBasePtr: 0xc0000000
[    21.651]     LinBytesPerScanLine: 2048
[    21.651]     BnkNumberOfImagePages: 4
[    21.651]     LinNumberOfImagePages: 4
[    21.651]     LinRedMaskSize: 5
[    21.651]     LinRedFieldPosition: 11
[    21.651]     LinGreenMaskSize: 6
[    21.651]     LinGreenFieldPosition: 5
[    21.651]     LinBlueMaskSize: 5
[    21.651]     LinBlueFieldPosition: 0
[    21.651]     LinRsvdMaskSize: 0
[    21.651]     LinRsvdFieldPosition: 0
[    21.651]     MaxPixelClock: 0
[    21.651] Mode: 127 (320x240)
[    21.651]     ModeAttributes: 0x9f
[    21.651]     WinAAttributes: 0x7
[    21.651]     WinBAttributes: 0x0
[    21.651]     WinGranularity: 64
[    21.651]     WinSize: 64
[    21.652]     WinASegment: 0xa000
[    21.652]     WinBSegment: 0xa000
[    21.652]     WinFuncPtr: 0xc000877b
[    21.652]     BytesPerScanline: 320
[    21.652]     XResolution: 320
[    21.652]     YResolution: 240
[    21.652]     XCharSize: 8
[    21.652]     YCharSize: 8
[    21.652]     NumberOfPlanes: 1
[    21.652]     BitsPerPixel: 8
[    21.652]     NumberOfBanks: 1
[    21.652]     MemoryModel: 4
[    21.652]     BankSize: 0
[    21.652]     NumberOfImages: 63
[    21.652]     RedMaskSize: 0
[    21.652]     RedFieldPosition: 0
[    21.652]     GreenMaskSize: 0
[    21.652]     GreenFieldPosition: 0
[    21.652]     BlueMaskSize: 0
[    21.652]     BlueFieldPosition: 0
[    21.652]     RsvdMaskSize: 0
[    21.652]     RsvdFieldPosition: 0
[    21.652]     DirectColorModeInfo: 0
[    21.652]     PhysBasePtr: 0xc0000000
[    21.652]     LinBytesPerScanLine: 320
[    21.652]     BnkNumberOfImagePages: 63
[    21.652]     LinNumberOfImagePages: 63
[    21.652]     LinRedMaskSize: 0
[    21.652]     LinRedFieldPosition: 0
[    21.652]     LinGreenMaskSize: 0
[    21.652]     LinGreenFieldPosition: 0
[    21.652]     LinBlueMaskSize: 0
[    21.652]     LinBlueFieldPosition: 0
[    21.652]     LinRsvdMaskSize: 0
[    21.652]     LinRsvdFieldPosition: 0
[    21.652]     MaxPixelClock: 0
[    21.652] Mode: 128 (400x300)
[    21.652]     ModeAttributes: 0x9f
[    21.652]     WinAAttributes: 0x7
[    21.652]     WinBAttributes: 0x0
[    21.652]     WinGranularity: 64
[    21.652]     WinSize: 64
[    21.652]     WinASegment: 0xa000
[    21.652]     WinBSegment: 0xa000
[    21.652]     WinFuncPtr: 0xc000877b
[    21.652]     BytesPerScanline: 400
[    21.652]     XResolution: 400
[    21.652]     YResolution: 300
[    21.652]     XCharSize: 8
[    21.652]     YCharSize: 8
[    21.652]     NumberOfPlanes: 1
[    21.652]     BitsPerPixel: 8
[    21.652]     NumberOfBanks: 1
[    21.652]     MemoryModel: 4
[    21.652]     BankSize: 0
[    21.653]     NumberOfImages: 63
[    21.653]     RedMaskSize: 0
[    21.653]     RedFieldPosition: 0
[    21.653]     GreenMaskSize: 0
[    21.653]     GreenFieldPosition: 0
[    21.653]     BlueMaskSize: 0
[    21.653]     BlueFieldPosition: 0
[    21.653]     RsvdMaskSize: 0
[    21.653]     RsvdFieldPosition: 0
[    21.653]     DirectColorModeInfo: 0
[    21.653]     PhysBasePtr: 0xc0000000
[    21.653]     LinBytesPerScanLine: 400
[    21.653]     BnkNumberOfImagePages: 63
[    21.653]     LinNumberOfImagePages: 63
[    21.653]     LinRedMaskSize: 0
[    21.653]     LinRedFieldPosition: 0
[    21.653]     LinGreenMaskSize: 0
[    21.653]     LinGreenFieldPosition: 0
[    21.653]     LinBlueMaskSize: 0
[    21.653]     LinBlueFieldPosition: 0
[    21.653]     LinRsvdMaskSize: 0
[    21.653]     LinRsvdFieldPosition: 0
[    21.653]     MaxPixelClock: 0
[    21.653] Mode: 129 (512x384)
[    21.653]     ModeAttributes: 0x9f
[    21.653]     WinAAttributes: 0x7
[    21.653]     WinBAttributes: 0x0
[    21.653]     WinGranularity: 64
[    21.653]     WinSize: 64
[    21.653]     WinASegment: 0xa000
[    21.653]     WinBSegment: 0xa000
[    21.653]     WinFuncPtr: 0xc000877b
[    21.653]     BytesPerScanline: 512
[    21.653]     XResolution: 512
[    21.653]     YResolution: 384
[    21.653]     XCharSize: 8
[    21.653]     YCharSize: 8
[    21.653]     NumberOfPlanes: 1
[    21.653]     BitsPerPixel: 8
[    21.653]     NumberOfBanks: 1
[    21.653]     MemoryModel: 4
[    21.653]     BankSize: 0
[    21.653]     NumberOfImages: 41
[    21.653]     RedMaskSize: 0
[    21.653]     RedFieldPosition: 0
[    21.653]     GreenMaskSize: 0
[    21.653]     GreenFieldPosition: 0
[    21.653]     BlueMaskSize: 0
[    21.653]     BlueFieldPosition: 0
[    21.653]     RsvdMaskSize: 0
[    21.653]     RsvdFieldPosition: 0
[    21.653]     DirectColorModeInfo: 0
[    21.653]     PhysBasePtr: 0xc0000000
[    21.653]     LinBytesPerScanLine: 512
[    21.653]     BnkNumberOfImagePages: 41
[    21.653]     LinNumberOfImagePages: 41
[    21.653]     LinRedMaskSize: 0
[    21.653]     LinRedFieldPosition: 0
[    21.653]     LinGreenMaskSize: 0
[    21.653]     LinGreenFieldPosition: 0
[    21.653]     LinBlueMaskSize: 0
[    21.653]     LinBlueFieldPosition: 0
[    21.653]     LinRsvdMaskSize: 0
[    21.653]     LinRsvdFieldPosition: 0
[    21.653]     MaxPixelClock: 0
[    21.654] Mode: 12a (320x240)
[    21.654]     ModeAttributes: 0x9b
[    21.654]     WinAAttributes: 0x7
[    21.654]     WinBAttributes: 0x0
[    21.654]     WinGranularity: 64
[    21.654]     WinSize: 64
[    21.654]     WinASegment: 0xa000
[    21.654]     WinBSegment: 0xa000
[    21.654]     WinFuncPtr: 0xc000877b
[    21.654]     BytesPerScanline: 640
[    21.654]     XResolution: 320
[    21.654]     YResolution: 240
[    21.654]     XCharSize: 8
[    21.654]     YCharSize: 8
[    21.654]     NumberOfPlanes: 1
[    21.654]     BitsPerPixel: 16
[    21.654]     NumberOfBanks: 1
[    21.654]     MemoryModel: 6
[    21.654]     BankSize: 0
[    21.654]     NumberOfImages: 41
[    21.654]     RedMaskSize: 5
[    21.654]     RedFieldPosition: 11
[    21.654]     GreenMaskSize: 6
[    21.654]     GreenFieldPosition: 5
[    21.654]     BlueMaskSize: 5
[    21.654]     BlueFieldPosition: 0
[    21.654]     RsvdMaskSize: 0
[    21.654]     RsvdFieldPosition: 0
[    21.654]     DirectColorModeInfo: 0
[    21.654]     PhysBasePtr: 0xc0000000
[    21.654]     LinBytesPerScanLine: 640
[    21.654]     BnkNumberOfImagePages: 41
[    21.654]     LinNumberOfImagePages: 41
[    21.654]     LinRedMaskSize: 5
[    21.654]     LinRedFieldPosition: 11
[    21.654]     LinGreenMaskSize: 6
[    21.654]     LinGreenFieldPosition: 5
[    21.654]     LinBlueMaskSize: 5
[    21.654]     LinBlueFieldPosition: 0
[    21.654]     LinRsvdMaskSize: 0
[    21.654]     LinRsvdFieldPosition: 0
[    21.654]     MaxPixelClock: 0
[    21.655] Mode: 12b (400x300)
[    21.655]     ModeAttributes: 0x9b
[    21.655]     WinAAttributes: 0x7
[    21.655]     WinBAttributes: 0x0
[    21.655]     WinGranularity: 64
[    21.655]     WinSize: 64
[    21.655]     WinASegment: 0xa000
[    21.655]     WinBSegment: 0xa000
[    21.655]     WinFuncPtr: 0xc000877b
[    21.655]     BytesPerScanline: 800
[    21.655]     XResolution: 400
[    21.655]     YResolution: 300
[    21.655]     XCharSize: 8
[    21.655]     YCharSize: 8
[    21.655]     NumberOfPlanes: 1
[    21.655]     BitsPerPixel: 16
[    21.655]     NumberOfBanks: 1
[    21.655]     MemoryModel: 6
[    21.655]     BankSize: 0
[    21.655]     NumberOfImages: 31
[    21.655]     RedMaskSize: 5
[    21.655]     RedFieldPosition: 11
[    21.655]     GreenMaskSize: 6
[    21.655]     GreenFieldPosition: 5
[    21.655]     BlueMaskSize: 5
[    21.655]     BlueFieldPosition: 0
[    21.655]     RsvdMaskSize: 0
[    21.655]     RsvdFieldPosition: 0
[    21.655]     DirectColorModeInfo: 0
[    21.655]     PhysBasePtr: 0xc0000000
[    21.655]     LinBytesPerScanLine: 800
[    21.655]     BnkNumberOfImagePages: 31
[    21.655]     LinNumberOfImagePages: 31
[    21.655]     LinRedMaskSize: 5
[    21.655]     LinRedFieldPosition: 11
[    21.655]     LinGreenMaskSize: 6
[    21.655]     LinGreenFieldPosition: 5
[    21.655]     LinBlueMaskSize: 5
[    21.655]     LinBlueFieldPosition: 0
[    21.655]     LinRsvdMaskSize: 0
[    21.655]     LinRsvdFieldPosition: 0
[    21.655]     MaxPixelClock: 0
[    21.655] Mode: 12c (512x384)
[    21.655]     ModeAttributes: 0x9b
[    21.655]     WinAAttributes: 0x7
[    21.655]     WinBAttributes: 0x0
[    21.656]     WinGranularity: 64
[    21.656]     WinSize: 64
[    21.656]     WinASegment: 0xa000
[    21.656]     WinBSegment: 0xa000
[    21.656]     WinFuncPtr: 0xc000877b
[    21.656]     BytesPerScanline: 1024
[    21.656]     XResolution: 512
[    21.656]     YResolution: 384
[    21.656]     XCharSize: 8
[    21.656]     YCharSize: 8
[    21.656]     NumberOfPlanes: 1
[    21.656]     BitsPerPixel: 16
[    21.656]     NumberOfBanks: 1
[    21.656]     MemoryModel: 6
[    21.656]     BankSize: 0
[    21.656]     NumberOfImages: 20
[    21.656]     RedMaskSize: 5
[    21.656]     RedFieldPosition: 11
[    21.656]     GreenMaskSize: 6
[    21.656]     GreenFieldPosition: 5
[    21.656]     BlueMaskSize: 5
[    21.656]     BlueFieldPosition: 0
[    21.656]     RsvdMaskSize: 0
[    21.656]     RsvdFieldPosition: 0
[    21.656]     DirectColorModeInfo: 0
[    21.656]     PhysBasePtr: 0xc0000000
[    21.656]     LinBytesPerScanLine: 1024
[    21.656]     BnkNumberOfImagePages: 20
[    21.656]     LinNumberOfImagePages: 20
[    21.656]     LinRedMaskSize: 5
[    21.656]     LinRedFieldPosition: 11
[    21.656]     LinGreenMaskSize: 6
[    21.656]     LinGreenFieldPosition: 5
[    21.656]     LinBlueMaskSize: 5
[    21.656]     LinBlueFieldPosition: 0
[    21.656]     LinRsvdMaskSize: 0
[    21.656]     LinRsvdFieldPosition: 0
[    21.656]     MaxPixelClock: 0
[    21.656] Mode: 12d (320x200)
[    21.656]     ModeAttributes: 0x9f
[    21.656]     WinAAttributes: 0x7
[    21.656]     WinBAttributes: 0x0
[    21.656]     WinGranularity: 64
[    21.656]     WinSize: 64
[    21.656]     WinASegment: 0xa000
[    21.656]     WinBSegment: 0xa000
[    21.656]     WinFuncPtr: 0xc000877b
[    21.656]     BytesPerScanline: 320
[    21.656]     XResolution: 320
[    21.656]     YResolution: 200
[    21.656]     XCharSize: 8
[    21.656]     YCharSize: 8
[    21.656]     NumberOfPlanes: 1
[    21.656]     BitsPerPixel: 8
[    21.656]     NumberOfBanks: 1
[    21.656]     MemoryModel: 4
[    21.656]     BankSize: 0
[    21.656]     NumberOfImages: 127
[    21.656]     RedMaskSize: 0
[    21.656]     RedFieldPosition: 0
[    21.657]     GreenMaskSize: 0
[    21.657]     GreenFieldPosition: 0
[    21.657]     BlueMaskSize: 0
[    21.657]     BlueFieldPosition: 0
[    21.657]     RsvdMaskSize: 0
[    21.657]     RsvdFieldPosition: 0
[    21.657]     DirectColorModeInfo: 0
[    21.657]     PhysBasePtr: 0xc0000000
[    21.657]     LinBytesPerScanLine: 320
[    21.657]     BnkNumberOfImagePages: 127
[    21.657]     LinNumberOfImagePages: 127
[    21.657]     LinRedMaskSize: 0
[    21.657]     LinRedFieldPosition: 0
[    21.657]     LinGreenMaskSize: 0
[    21.657]     LinGreenFieldPosition: 0
[    21.657]     LinBlueMaskSize: 0
[    21.657]     LinBlueFieldPosition: 0
[    21.657]     LinRsvdMaskSize: 0
[    21.657]     LinRsvdFieldPosition: 0
[    21.657]     MaxPixelClock: 0
[    21.657] Mode: 131 (640x400)
[    21.657]     ModeAttributes: 0x9b
[    21.657]     WinAAttributes: 0x7
[    21.657]     WinBAttributes: 0x0
[    21.657]     WinGranularity: 64
[    21.657]     WinSize: 64
[    21.657]     WinASegment: 0xa000
[    21.657]     WinBSegment: 0xa000
[    21.657]     WinFuncPtr: 0xc000877b
[    21.657]     BytesPerScanline: 1280
[    21.657]     XResolution: 640
[    21.657]     YResolution: 400
[    21.657]     XCharSize: 8
[    21.657]     YCharSize: 16
[    21.657]     NumberOfPlanes: 1
[    21.657]     BitsPerPixel: 16
[    21.657]     NumberOfBanks: 1
[    21.657]     MemoryModel: 6
[    21.657]     BankSize: 0
[    21.657]     NumberOfImages: 15
[    21.657]     RedMaskSize: 5
[    21.657]     RedFieldPosition: 11
[    21.657]     GreenMaskSize: 6
[    21.657]     GreenFieldPosition: 5
[    21.657]     BlueMaskSize: 5
[    21.657]     BlueFieldPosition: 0
[    21.657]     RsvdMaskSize: 0
[    21.657]     RsvdFieldPosition: 0
[    21.657]     DirectColorModeInfo: 0
[    21.657]     PhysBasePtr: 0xc0000000
[    21.657]     LinBytesPerScanLine: 1280
[    21.657]     BnkNumberOfImagePages: 15
[    21.657]     LinNumberOfImagePages: 15
[    21.657]     LinRedMaskSize: 5
[    21.657]     LinRedFieldPosition: 11
[    21.657]     LinGreenMaskSize: 6
[    21.657]     LinGreenFieldPosition: 5
[    21.657]     LinBlueMaskSize: 5
[    21.657]     LinBlueFieldPosition: 0
[    21.657]     LinRsvdMaskSize: 0
[    21.657]     LinRsvdFieldPosition: 0
[    21.657]     MaxPixelClock: 0
[    21.658] *Mode: 112 (640x480)
[    21.658]     ModeAttributes: 0x9b
[    21.658]     WinAAttributes: 0x7
[    21.658]     WinBAttributes: 0x0
[    21.658]     WinGranularity: 64
[    21.658]     WinSize: 64
[    21.658]     WinASegment: 0xa000
[    21.658]     WinBSegment: 0xa000
[    21.658]     WinFuncPtr: 0xc000877b
[    21.658]     BytesPerScanline: 2560
[    21.658]     XResolution: 640
[    21.658]     YResolution: 480
[    21.658]     XCharSize: 8
[    21.658]     YCharSize: 16
[    21.658]     NumberOfPlanes: 1
[    21.658]     BitsPerPixel: 32
[    21.658]     NumberOfBanks: 1
[    21.658]     MemoryModel: 6
[    21.658]     BankSize: 0
[    21.658]     NumberOfImages: 5
[    21.658]     RedMaskSize: 8
[    21.658]     RedFieldPosition: 16
[    21.658]     GreenMaskSize: 8
[    21.658]     GreenFieldPosition: 8
[    21.658]     BlueMaskSize: 8
[    21.658]     BlueFieldPosition: 0
[    21.658]     RsvdMaskSize: 8
[    21.658]     RsvdFieldPosition: 24
[    21.658]     DirectColorModeInfo: 0
[    21.658]     PhysBasePtr: 0xc0000000
[    21.658]     LinBytesPerScanLine: 2560
[    21.658]     BnkNumberOfImagePages: 5
[    21.658]     LinNumberOfImagePages: 5
[    21.658]     LinRedMaskSize: 8
[    21.658]     LinRedFieldPosition: 16
[    21.658]     LinGreenMaskSize: 8
[    21.658]     LinGreenFieldPosition: 8
[    21.658]     LinBlueMaskSize: 8
[    21.658]     LinBlueFieldPosition: 0
[    21.658]     LinRsvdMaskSize: 8
[    21.658]     LinRsvdFieldPosition: 24
[    21.658]     MaxPixelClock: 0
[    21.659] *Mode: 115 (800x600)
[    21.659]     ModeAttributes: 0x9b
[    21.659]     WinAAttributes: 0x7
[    21.659]     WinBAttributes: 0x0
[    21.659]     WinGranularity: 64
[    21.659]     WinSize: 64
[    21.659]     WinASegment: 0xa000
[    21.659]     WinBSegment: 0xa000
[    21.659]     WinFuncPtr: 0xc000877b
[    21.659]     BytesPerScanline: 3200
[    21.659]     XResolution: 800
[    21.659]     YResolution: 600
[    21.659]     XCharSize: 8
[    21.659]     YCharSize: 16
[    21.659]     NumberOfPlanes: 1
[    21.659]     BitsPerPixel: 32
[    21.659]     NumberOfBanks: 1
[    21.659]     MemoryModel: 6
[    21.659]     BankSize: 0
[    21.659]     NumberOfImages: 3
[    21.659]     RedMaskSize: 8
[    21.659]     RedFieldPosition: 16
[    21.659]     GreenMaskSize: 8
[    21.659]     GreenFieldPosition: 8
[    21.659]     BlueMaskSize: 8
[    21.659]     BlueFieldPosition: 0
[    21.659]     RsvdMaskSize: 8
[    21.659]     RsvdFieldPosition: 24
[    21.659]     DirectColorModeInfo: 0
[    21.659]     PhysBasePtr: 0xc0000000
[    21.659]     LinBytesPerScanLine: 3200
[    21.659]     BnkNumberOfImagePages: 3
[    21.659]     LinNumberOfImagePages: 3
[    21.659]     LinRedMaskSize: 8
[    21.659]     LinRedFieldPosition: 16
[    21.659]     LinGreenMaskSize: 8
[    21.659]     LinGreenFieldPosition: 8
[    21.659]     LinBlueMaskSize: 8
[    21.659]     LinBlueFieldPosition: 0
[    21.659]     LinRsvdMaskSize: 8
[    21.659]     LinRsvdFieldPosition: 24
[    21.659]     MaxPixelClock: 0
[    21.660] *Mode: 118 (1024x768 )
[    21.660]     ModeAttributes: 0x9b
[    21.660]     WinAAttributes: 0x7
[    21.660]     WinBAttributes: 0x0
[    21.660]     WinGranularity: 64
[    21.660]     WinSize: 64
[    21.660]     WinASegment: 0xa000
[    21.660]     WinBSegment: 0xa000
[    21.660]     WinFuncPtr: 0xc000877b
[    21.660]     BytesPerScanline: 4096
[    21.660]     XResolution: 1024
[    21.660]     YResolution: 768
[    21.660]     XCharSize: 8
[    21.660]     YCharSize: 16
[    21.660]     NumberOfPlanes: 1
[    21.660]     BitsPerPixel: 32
[    21.660]     NumberOfBanks: 1
[    21.660]     MemoryModel: 6
[    21.660]     BankSize: 0
[    21.660]     NumberOfImages: 1
[    21.660]     RedMaskSize: 8
[    21.660]     RedFieldPosition: 16
[    21.660]     GreenMaskSize: 8
[    21.660]     GreenFieldPosition: 8
[    21.660]     BlueMaskSize: 8
[    21.660]     BlueFieldPosition: 0
[    21.660]     RsvdMaskSize: 8
[    21.660]     RsvdFieldPosition: 24
[    21.660]     DirectColorModeInfo: 0
[    21.660]     PhysBasePtr: 0xc0000000
[    21.660]     LinBytesPerScanLine: 4096
[    21.660]     BnkNumberOfImagePages: 1
[    21.660]     LinNumberOfImagePages: 1
[    21.660]     LinRedMaskSize: 8
[    21.660]     LinRedFieldPosition: 16
[    21.660]     LinGreenMaskSize: 8
[    21.660]     LinGreenFieldPosition: 8
[    21.660]     LinBlueMaskSize: 8
[    21.660]     LinBlueFieldPosition: 0
[    21.660]     LinRsvdMaskSize: 8
[    21.660]     LinRsvdFieldPosition: 24
[    21.660]     MaxPixelClock: 0
[    21.660] Mode: 102 (800x600)
[    21.661]     ModeAttributes: 0x1f
[    21.661]     WinAAttributes: 0x7
[    21.661]     WinBAttributes: 0x0
[    21.661]     WinGranularity: 64
[    21.661]     WinSize: 64
[    21.661]     WinASegment: 0xa000
[    21.661]     WinBSegment: 0xa000
[    21.661]     WinFuncPtr: 0xc000877b
[    21.661]     BytesPerScanline: 100
[    21.661]     XResolution: 800
[    21.661]     YResolution: 600
[    21.661]     XCharSize: 8
[    21.661]     YCharSize: 16
[    21.661]     NumberOfPlanes: 4
[    21.661]     BitsPerPixel: 4
[    21.661]     NumberOfBanks: 1
[    21.661]     MemoryModel: 3
[    21.661]     BankSize: 0
[    21.661]     NumberOfImages: 31
[    21.661]     RedMaskSize: 0
[    21.661]     RedFieldPosition: 0
[    21.661]     GreenMaskSize: 0
[    21.661]     GreenFieldPosition: 0
[    21.661]     BlueMaskSize: 0
[    21.661]     BlueFieldPosition: 0
[    21.661]     RsvdMaskSize: 0
[    21.661]     RsvdFieldPosition: 0
[    21.661]     DirectColorModeInfo: 0
[    21.661]     PhysBasePtr: 0xc0000000
[    21.661]     LinBytesPerScanLine: 100
[    21.661]     BnkNumberOfImagePages: 31
[    21.661]     LinNumberOfImagePages: 31
[    21.661]     LinRedMaskSize: 0
[    21.661]     LinRedFieldPosition: 0
[    21.661]     LinGreenMaskSize: 0
[    21.661]     LinGreenFieldPosition: 0
[    21.661]     LinBlueMaskSize: 0
[    21.661]     LinBlueFieldPosition: 0
[    21.661]     LinRsvdMaskSize: 0
[    21.661]     LinRsvdFieldPosition: 0
[    21.661]     MaxPixelClock: 0
[    21.661] 
[    21.661] (II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
[    21.661] (II) VESA(0): Configured Monitor: Using hsync range of 30.00-63.00 kHz
[    21.661] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-75.00 Hz
[    21.661] (II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
[    21.661] (II) VESA(0): Not using built-in mode "1280x768" (no mode of this name)
[    21.661] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    21.661] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    21.661] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    21.661] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    21.661] (II) VESA(0): Configured Monitor: Using hsync range of 30.00-63.00 kHz
[    21.661] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-75.00 Hz
[    21.661] (II) VESA(0): Not using mode "1280x800@60" (no mode of this name)
[    21.661] (--) VESA(0): Virtual size is 1280x768 (pitch 1280)
[    21.661] (**) VESA(0):  Built-in mode "1280x768"
[    21.661] (**) VESA(0):  Built-in mode "1024x768"
[    21.661] (**) VESA(0):  Built-in mode "800x600"
[    21.661] (**) VESA(0):  Built-in mode "640x480"
[    21.661] (==) VESA(0): DPI set to (96, 96)
[    21.661] (II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
[    21.661] (II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
[    21.661] (II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
[    21.662] (**) VESA(0): Using "Shadow Framebuffer"
[    21.662] (II) Loading sub module "shadow"
[    21.662] (II) LoadModule: "shadow"
[    21.662] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.698] (II) Module shadow: vendor="X.Org Foundation"
[    21.698]     compiled for 1.11.3, module version = 1.1.0
[    21.698]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.698] (II) Loading sub module "fb"
[    21.698] (II) LoadModule: "fb"
[    21.698] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.768] (II) Module fb: vendor="X.Org Foundation"
[    21.768]     compiled for 1.11.3, module version = 1.0.0
[    21.768]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.768] (II) UnloadModule: "sis"
[    21.768] (II) Unloading sis
[    21.768] (II) UnloadModule: "fbdev"
[    21.768] (II) Unloading fbdev
[    21.768] (II) UnloadModule: "fbdevhw"
[    21.768] (II) Unloading fbdevhw
[    21.768] (==) Depth 24 pixmap format is 32 bpp
[    21.769] (II) Loading sub module "int10"
[    21.769] (II) LoadModule: "int10"
[    21.769] (II) Loading /usr/lib/xorg/modules/libint10.so
[    21.769] (II) Module int10: vendor="X.Org Foundation"
[    21.769]     compiled for 1.11.3, module version = 1.0.0
[    21.769]     ABI class: X.Org Video Driver, version 11.0
[    21.769] (II) VESA(0): initializing int10
[    21.774] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    21.775] (II) VESA(0): VESA BIOS detected
[    21.775] (II) VESA(0): VESA VBE Version 3.0
[    21.775] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[    21.775] (II) VESA(0): VESA VBE OEM: SiS
[    21.775] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    21.775] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    21.775] (II) VESA(0): VESA VBE OEM Product: 6330
[    21.775] (II) VESA(0): VESA VBE OEM Product Rev: 3.74.10A
[    21.807] (II) VESA(0): virtual address = 0xa6d72000,
    physical address = 0xc0000000, size = 268435456
[    21.817] (II) VESA(0): Setting up VESA Mode 0x11E (1280x768)
[    21.916] (==) VESA(0): Default visual is TrueColor
[    21.927] (==) VESA(0): Backing store disabled
[    21.927] (**) VESA(0): DPMS enabled
[    21.927] (WW) VESA(0): Option "EnableSiSCtrl" is not used
[    21.927] (WW) VESA(0): Option "useROMData " is not used
[    21.927] (WW) VESA(0): Option "ForceCRT1Type" is not used
[    21.927] (WW) VESA(0): Option "ForceCRT2Type" is not used
[    21.927] (WW) VESA(0): Option "CRT1Gamma" is not used
[    21.927] (WW) VESA(0): Option "CRT2Gamma" is not used
[    21.927] (WW) VESA(0): Option "Brightness" is not used
[    21.927] (WW) VESA(0): Option "Contrast" is not used
[    21.927] (WW) VESA(0): Option "CRT1Saturation" is not used
[    21.927] (WW) VESA(0): Option "XvOnCRT2" is not used
[    21.927] (WW) VESA(0): Option "XvDefaultContrast" is not used
[    21.927] (WW) VESA(0): Option "XvDefaultBrightness" is not used
[    21.927] (WW) VESA(0): Option "XvDefaultHue" is not used
[    21.927] (WW) VESA(0): Option "XvDefaultSaturation" is not used
[    21.927] (WW) VESA(0): Option "XvDefaultDisableGfxLR" is not used
[    21.927] (WW) VESA(0): Option "XvGamma" is not used
[    21.927] (==) RandR enabled
[    21.927] (II) Initializing built-in extension Generic Event Extension
[    21.927] (II) Initializing built-in extension SHAPE
[    21.927] (II) Initializing built-in extension MIT-SHM
[    21.927] (II) Initializing built-in extension XInputExtension
[    21.927] (II) Initializing built-in extension XTEST
[    21.927] (II) Initializing built-in extension BIG-REQUESTS
[    21.927] (II) Initializing built-in extension SYNC
[    21.927] (II) Initializing built-in extension XKEYBOARD
[    21.927] (II) Initializing built-in extension XC-MISC
[    21.927] (II) Initializing built-in extension SECURITY
[    21.927] (II) Initializing built-in extension XINERAMA
[    21.927] (II) Initializing built-in extension XFIXES
[    21.927] (II) Initializing built-in extension RENDER
[    21.927] (II) Initializing built-in extension RANDR
[    21.927] (II) Initializing built-in extension COMPOSITE
[    21.927] (II) Initializing built-in extension DAMAGE
[    21.939] (II) AIGLX: Screen 0 is not DRI2 capable
[    21.939] (II) AIGLX: Screen 0 is not DRI capable
[    23.263] (II) AIGLX: Loaded and initialized swrast
[    23.263] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.427] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.461] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    23.461] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.461] (II) LoadModule: "evdev"
[    23.462] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.489] (II) Module evdev: vendor="X.Org Foundation"
[    23.489]     compiled for 1.11.3, module version = 2.7.0
[    23.489]     Module class: X.Org XInput Driver
[    23.489]     ABI class: X.Org XInput driver, version 16.0
[    23.489] (II) Using input driver 'evdev' for 'Power Button'
[    23.489] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.489] (**) Power Button: always reports core events
[    23.490] (**) evdev: Power Button: Device: "/dev/input/event3"
[    23.490] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.490] (--) evdev: Power Button: Found keys
[    23.490] (II) evdev: Power Button: Configuring as keyboard
[    23.490] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    23.490] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.490] (**) Option "xkb_rules" "evdev"
[    23.490] (**) Option "xkb_model" "pc105"
[    23.490] (**) Option "xkb_layout" "de"
[    23.514] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    23.522] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    23.522] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.522] (II) Using input driver 'evdev' for 'Video Bus'
[    23.522] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.522] (**) Video Bus: always reports core events
[    23.522] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    23.522] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.522] (--) evdev: Video Bus: Found keys
[    23.522] (II) evdev: Video Bus: Configuring as keyboard
[    23.522] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input5/event5"
[    23.522] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.522] (**) Option "xkb_rules" "evdev"
[    23.522] (**) Option "xkb_model" "pc105"
[    23.522] (**) Option "xkb_layout" "de"
[    23.523] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.523] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.523] (II) Using input driver 'evdev' for 'Power Button'
[    23.523] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.523] (**) Power Button: always reports core events
[    23.523] (**) evdev: Power Button: Device: "/dev/input/event1"
[    23.523] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.523] (--) evdev: Power Button: Found keys
[    23.523] (II) evdev: Power Button: Configuring as keyboard
[    23.523] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    23.523] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    23.523] (**) Option "xkb_rules" "evdev"
[    23.523] (**) Option "xkb_model" "pc105"
[    23.523] (**) Option "xkb_layout" "de"
[    23.524] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    23.524] (II) No input driver specified, ignoring this device.
[    23.524] (II) This device may have been added with another device file.
[    23.525] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    23.525] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    23.525] (II) Using input driver 'evdev' for 'Sleep Button'
[    23.525] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.525] (**) Sleep Button: always reports core events
[    23.525] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    23.525] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    23.525] (--) evdev: Sleep Button: Found keys
[    23.525] (II) evdev: Sleep Button: Configuring as keyboard
[    23.525] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    23.525] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    23.525] (**) Option "xkb_rules" "evdev"
[    23.525] (**) Option "xkb_model" "pc105"
[    23.525] (**) Option "xkb_layout" "de"
[    23.526] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event7)
[    23.526] (II) No input driver specified, ignoring this device.
[    23.526] (II) This device may have been added with another device file.
[    23.526] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event8)
[    23.526] (II) No input driver specified, ignoring this device.
[    23.526] (II) This device may have been added with another device file.
[    23.527] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    23.527] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.527] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.527] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.527] (**) AT Translated Set 2 keyboard: always reports core events
[    23.527] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    23.527] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.527] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.527] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.527] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    23.527] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    23.527] (**) Option "xkb_rules" "evdev"
[    23.527] (**) Option "xkb_model" "pc105"
[    23.527] (**) Option "xkb_layout" "de"
[    23.528] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    23.528] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.528] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.528] (II) LoadModule: "synaptics"
[    23.528] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.538] (II) Module synaptics: vendor="X.Org Foundation"
[    23.538]     compiled for 1.11.3, module version = 1.6.2
[    23.538]     Module class: X.Org XInput Driver
[    23.538]     ABI class: X.Org XInput driver, version 16.0
[    23.538] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    23.538] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.538] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.538] (**) Option "Device" "/dev/input/event6"
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.544] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.544] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    23.544] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    23.544] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    23.544] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    23.544] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    23.544] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.544] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    23.544] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.544] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.544] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.545] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    23.545] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    32.523] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    64.933] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    67.140] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
```

---

### Post by lin9 on 2012-11-08
ok, above the wished log file, had to exchange some "smilies" at: 768 )


so, what do I have to do exactly ??

ty

---

### Post by Yellow Pasque on 2012-11-09
In the future, please use [ code ][ /code ] tags for large blocks of text.
The first thing I would try is making an /etc/X11/xorg.conf file that looks like:
```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "sis"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by lin9 on 2012-11-09
my actual xconf.org

```

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier "device1"
        Driver "sisimedia"
        Option "DPMS"
        Option "EnableSiSCtrl" "yes"
        Option "useROMData " "False"
# [sisctrl] Set CRT1 device type (Note: overrides auto-detection)
    Option "ForceCRT1Type" "NONE"

    # [sisctrl] Set CRT2 device type (Note: overrides auto-detection)
    Option "ForceCRT2Type" "LCD"

    # [sisctrl] LCD related options
    # Currently all set to defaults

    # [sisctrl] Enable/disable Gamma correction for CRT1
    Option "CRT1Gamma" "on"

    # [sisctrl] Enable/disable gamma correction for CRT2
    Option "CRT2Gamma" "on"

    # [sisctrl] Brightness/contrast for CRT1 and CRT2
    Option "Brightness" "0.000 0.000 0.000"
    Option "Contrast" "0.000 0.000 0.000"

    # [sisctrl] Saturation for CRT1
    Option "CRT1Saturation" "1"

    # Xv (video overlay) head selection
    Option "XvOnCRT2" "yes"

    # [sisctrl] Xv (video overlay) related options
    Option "XvDefaultContrast" "64"
    Option "XvDefaultBrightness" "10"
    Option "XvDefaultHue" "1"
    Option "XvDefaultSaturation" "1"
    Option "XvDefaultDisableGfxLR" "no"
    Option "XvGamma" "on"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
        Option "DPMS"
        HorizSync 30 - 63
        VertRefresh 50 - 75
# Gamma correction for CRT1 and CRT2
    Gamma 1.000 1.000 1.000
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
        DefaultDepth    24
SubSection "Display"
        Depth   24
                Modes           "1280x800@60"   
        EndSubSection
    Device        "Configured Video Device"
EndSection
Section "Module"
    Disable "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "GLcore"
EndSection
Section "DRI"
        Mode 0666
EndSection

```...looks to me  as if already written there??  :(

---

### Post by Yellow Pasque on 2012-11-10
Your current xorg.conf says:
```
Driver  "sisimedia"
```
sisimedia is basically deprecated in favor of regular sis driver, although it looks like people are still patching sisimedia to support current xorg servers: [https://bugs.archlinux.org/task/28906](https://bugs.archlinux.org/task/28906)

Try changing the line to "sis", or better yet, just move the xorg.conf out of the way and see if that helps.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by lin9 on 2012-11-12
okay did rename xorg.conf into xorg.conf.bak... restarted  and now  I get the following message:


none of the saved resolution configuration can be used

none of the following modes is compatible with possible modes:
CRTC "310": testing mode "1024x768@61Hz" with output "1280x768@0Hz"
CRTC "310": testing mode "800x600@61Hz" with output "1280x768@0Hz"
CRTC "310": testing mode "640x480@60Hz" with output "1280x768@0Hz"
etc...

in information panel /graphics it says driver: vesa 6330

please help

---

### Post by lin9 on 2012-11-13
nobody has an idea? please help :(

---

### Post by Yellow Pasque on 2012-11-14
When you get the above error message, does the GUI (X) fail to start?
Please try my xorg.conf and post the /var/log/Xorg.0.log when you boot with it.

---

### Post by cwsnyder on 2012-11-14
> **lin9 said:**
> **Re: Ubuntu 10.10 and SiS mirage 3 grapichs**- edit: my xrandr -q gives:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x768        0.0* 
   1024x768       76.0  
   800x600        73.0  
   640x480        73.0 


thanks,

...just another desperate fujitsu V5535 user
                                                                                                                                    *                                              Last edited by lin9; 1 Day Ago at 05:48 AM..                                                           *             
First, do you have the x11-xserver-utils installed, or just xrandr?

Second, I filed a bug [https://bugs.launchpad.net/bugs/1078695](https://bugs.launchpad.net/bugs/1078695) which seems to affect you as well, the whole 'xrandr: Failed to get size of gamma for output default'

On the installs which I have seen either on my own or in the forums, if you cannot set the gamma using xgamma and your display is not detected properly, you are not able to fix it properly with either xorg.conf or xrandr.  You can come close to setting the native display setting, but not quite, and I don't know why.

---

### Post by lin9 on 2012-11-20
so what does that mean? what shall I do?

Im not sure, I tried some  xrandr commands but also the xorg thing.

So what else can I try to get whole 1280 x 800 solution? 

thank you for help

---

### Post by Yellow Pasque on 2012-11-20
> Please try my xorg.conf and post the /var/log/Xorg.0.log when you boot with it.
...

---

### Post by lin9 on 2012-11-22
uhhm sorry didn't read it...so xorg.0.log:
```

[    28.890] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    28.890] X Protocol Version 11, Revision 0
[    28.890] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    28.890] Current Operating System: Linux pe47-ESPRIMO-Mobile-V5535 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686
[    28.890] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=ea9e6741-6723-4d04-8a39-c2f1d1559374 ro quiet splash vt.handoff=7
[    28.890] Build Date: 29 August 2012  12:10:05AM
[    28.890] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    28.890] Current version of pixman: 0.24.4
[    28.890]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.890] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.890] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov 16 19:32:30 2012
[    28.907] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.908] (==) No Layout section.  Using the first Screen section.
[    28.908] (==) No screen section available. Using defaults.
[    28.908] (**) |-->Screen "Default Screen Section" (0)
[    28.908] (**) |   |-->Monitor "<default monitor>"
[    28.908] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.908] (==) Automatically adding devices
[    28.908] (==) Automatically enabling devices
[    28.908] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.908]     Entry deleted from font path.
[    28.908] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.908]     Entry deleted from font path.
[    28.908] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.908]     Entry deleted from font path.
[    28.908] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.908]     Entry deleted from font path.
[    28.908] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.908]     Entry deleted from font path.
[    28.908] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    28.908]     Entry deleted from font path.
[    28.908] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    28.908] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.908] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.908] (II) Loader magic: 0xb77645a0
[    28.908] (II) Module ABI versions:
[    28.908]     X.Org ANSI C Emulation: 0.4
[    28.908]     X.Org Video Driver: 11.0
[    28.908]     X.Org XInput driver : 16.0
[    28.908]     X.Org Server Extension : 6.0
[    28.909] (--) PCI:*(0:1:0:0) 1039:6351:1734:1125 rev 16, Mem @ 0xc0000000/268435456, 0xd4000000/131072, I/O @ 0x00009000/128
[    28.909] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.909] (II) LoadModule: "extmod"
[    28.926] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    28.926] (II) Module extmod: vendor="X.Org Foundation"
[    28.926]     compiled for 1.11.3, module version = 1.0.0
[    28.926]     Module class: X.Org Server Extension
[    28.926]     ABI class: X.Org Server Extension, version 6.0
[    28.926] (II) Loading extension MIT-SCREEN-SAVER
[    28.926] (II) Loading extension XFree86-VidModeExtension
[    28.926] (II) Loading extension XFree86-DGA
[    28.927] (II) Loading extension DPMS
[    28.927] (II) Loading extension XVideo
[    28.927] (II) Loading extension XVideo-MotionCompensation
[    28.927] (II) Loading extension X-Resource
[    28.927] (II) LoadModule: "dbe"
[    28.927] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    28.927] (II) Module dbe: vendor="X.Org Foundation"
[    28.927]     compiled for 1.11.3, module version = 1.0.0
[    28.927]     Module class: X.Org Server Extension
[    28.927]     ABI class: X.Org Server Extension, version 6.0
[    28.927] (II) Loading extension DOUBLE-BUFFER
[    28.927] (II) LoadModule: "glx"
[    28.927] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.927] (II) Module glx: vendor="X.Org Foundation"
[    28.927]     compiled for 1.11.3, module version = 1.0.0
[    28.927]     ABI class: X.Org Server Extension, version 6.0
[    28.927] (==) AIGLX enabled
[    28.927] (II) Loading extension GLX
[    28.927] (II) LoadModule: "record"
[    28.928] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    28.928] (II) Module record: vendor="X.Org Foundation"
[    28.928]     compiled for 1.11.3, module version = 1.13.0
[    28.928]     Module class: X.Org Server Extension
[    28.928]     ABI class: X.Org Server Extension, version 6.0
[    28.928] (II) Loading extension RECORD
[    28.928] (II) LoadModule: "dri"
[    28.928] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    28.947] (II) Module dri: vendor="X.Org Foundation"
[    28.947]     compiled for 1.11.3, module version = 1.0.0
[    28.947]     ABI class: X.Org Server Extension, version 6.0
[    28.947] (II) Loading extension XFree86-DRI
[    28.947] (II) LoadModule: "dri2"
[    28.948] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.948] (II) Module dri2: vendor="X.Org Foundation"
[    28.948]     compiled for 1.11.3, module version = 1.2.0
[    28.948]     ABI class: X.Org Server Extension, version 6.0
[    28.948] (II) Loading extension DRI2
[    28.948] (==) Matched sis as autoconfigured driver 0
[    28.948] (==) Matched vesa as autoconfigured driver 1
[    28.948] (==) Matched fbdev as autoconfigured driver 2
[    28.948] (==) Assigned the driver to the xf86ConfigLayout
[    28.948] (II) LoadModule: "sis"
[    28.953] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    28.953] (II) Module sis: vendor="X.Org Foundation"
[    28.953]     compiled for 1.11.3, module version = 0.10.3
[    28.953]     Module class: X.Org Video Driver
[    28.953]     ABI class: X.Org Video Driver, version 11.0
[    28.953] (II) LoadModule: "vesa"
[    28.954] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.954] (II) Module vesa: vendor="X.Org Foundation"
[    28.954]     compiled for 1.11.3, module version = 2.3.0
[    28.954]     Module class: X.Org Video Driver
[    28.954]     ABI class: X.Org Video Driver, version 11.0
[    28.954] (II) LoadModule: "fbdev"
[    28.954] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.954] (II) Module fbdev: vendor="X.Org Foundation"
[    28.954]     compiled for 1.11.3, module version = 0.4.2
[    28.954]     ABI class: X.Org Video Driver, version 11.0
[    28.954] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[    28.954] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[    28.954] (II) VESA: driver for VESA chipsets: vesa
[    28.955] (II) FBDEV: driver for framebuffer: fbdev
[    28.955] (++) using VT number 7

[    28.955] (WW) Falling back to old probe method for sis
[    28.955] (--) Assigning device section with no busID to primary device
[    28.955] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.955] (WW) Falling back to old probe method for fbdev
[    28.955] (II) Loading sub module "fbdevhw"
[    28.955] (II) LoadModule: "fbdevhw"
[    28.955] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.955] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.955]     compiled for 1.11.3, module version = 0.0.2
[    28.955]     ABI class: X.Org Video Driver, version 11.0
[    28.955] (II) Loading sub module "vbe"
[    28.955] (II) LoadModule: "vbe"
[    28.956] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    28.956] (II) Module vbe: vendor="X.Org Foundation"
[    28.956]     compiled for 1.11.3, module version = 1.1.0
[    28.956]     ABI class: X.Org Video Driver, version 11.0
[    28.956] (II) Loading sub module "int10"
[    28.956] (II) LoadModule: "int10"
[    28.956] (II) Loading /usr/lib/xorg/modules/libint10.so
[    28.956] (II) Module int10: vendor="X.Org Foundation"
[    28.956]     compiled for 1.11.3, module version = 1.0.0
[    28.956]     ABI class: X.Org Video Driver, version 11.0
[    28.956] (II) VESA(0): initializing int10
[    28.962] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    28.984] (II) VESA(0): VESA BIOS detected
[    28.984] (II) VESA(0): VESA VBE Version 3.0
[    28.984] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[    28.984] (II) VESA(0): VESA VBE OEM: SiS
[    28.984] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    28.984] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    28.984] (II) VESA(0): VESA VBE OEM Product: 6330
[    28.984] (II) VESA(0): VESA VBE OEM Product Rev: 3.74.10A
[    28.995] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.995] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    28.995] (==) VESA(0): RGB weight 888
[    28.995] (==) VESA(0): Default visual is TrueColor
[    28.995] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.995] (II) Loading sub module "ddc"
[    28.995] (II) LoadModule: "ddc"
[    28.995] (II) Module "ddc" already built-in
[    29.088] (II) VESA(0): VESA VBE DDC supported
[    29.088] (II) VESA(0): VESA VBE DDC Level none
[    29.088] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    29.121] (II) VESA(0): VESA VBE DDC read failed
[    29.121] (II) VESA(0): VESA VBE PanelID read failed
[    29.121] (II) VESA(0): Searching for matching VESA mode(s):
[    29.121] Mode: 11c (1280x768)
[    29.121]     ModeAttributes: 0x9f
[    29.121]     WinAAttributes: 0x7
[    29.121]     WinBAttributes: 0x0
[    29.121]     WinGranularity: 64
[    29.121]     WinSize: 64
[    29.121]     WinASegment: 0xa000
[    29.121]     WinBSegment: 0xa000
[    29.121]     WinFuncPtr: 0xc000877b
[    29.121]     BytesPerScanline: 1280
[    29.121]     XResolution: 1280
[    29.121]     YResolution: 768
[    29.121]     XCharSize: 8
[    29.121]     YCharSize: 16
[    29.121]     NumberOfPlanes: 1
[    29.121]     BitsPerPixel: 8
[    29.121]     NumberOfBanks: 1
[    29.121]     MemoryModel: 4
[    29.122]     BankSize: 0
[    29.122]     NumberOfImages: 7
[    29.122]     RedMaskSize: 0
[    29.122]     RedFieldPosition: 0
[    29.122]     GreenMaskSize: 0
[    29.122]     GreenFieldPosition: 0
[    29.122]     BlueMaskSize: 0
[    29.122]     BlueFieldPosition: 0
[    29.122]     RsvdMaskSize: 0
[    29.122]     RsvdFieldPosition: 0
[    29.122]     DirectColorModeInfo: 0
[    29.122]     PhysBasePtr: 0xc0000000
[    29.122]     LinBytesPerScanLine: 1280
[    29.122]     BnkNumberOfImagePages: 7
[    29.122]     LinNumberOfImagePages: 7
[    29.122]     LinRedMaskSize: 0
[    29.122]     LinRedFieldPosition: 0
[    29.122]     LinGreenMaskSize: 0
[    29.122]     LinGreenFieldPosition: 0
[    29.122]     LinBlueMaskSize: 0
[    29.122]     LinBlueFieldPosition: 0
[    29.122]     LinRsvdMaskSize: 0
[    29.122]     LinRsvdFieldPosition: 0
[    29.122]     MaxPixelClock: 0
[    29.122] Mode: 11d (1280x768)
[    29.122]     ModeAttributes: 0x9b
[    29.122]     WinAAttributes: 0x7
[    29.122]     WinBAttributes: 0x0
[    29.122]     WinGranularity: 64
[    29.122]     WinSize: 64
[    29.122]     WinASegment: 0xa000
[    29.122]     WinBSegment: 0xa000
[    29.122]     WinFuncPtr: 0xc000877b
[    29.122]     BytesPerScanline: 2560
[    29.122]     XResolution: 1280
[    29.122]     YResolution: 768
[    29.122]     XCharSize: 8
[    29.122]     YCharSize: 16
[    29.122]     NumberOfPlanes: 1
[    29.122]     BitsPerPixel: 16
[    29.122]     NumberOfBanks: 1
[    29.122]     MemoryModel: 6
[    29.122]     BankSize: 0
[    29.122]     NumberOfImages: 3
[    29.122]     RedMaskSize: 5
[    29.122]     RedFieldPosition: 11
[    29.122]     GreenMaskSize: 6
[    29.122]     GreenFieldPosition: 5
[    29.122]     BlueMaskSize: 5
[    29.122]     BlueFieldPosition: 0
[    29.122]     RsvdMaskSize: 0
[    29.122]     RsvdFieldPosition: 0
[    29.122]     DirectColorModeInfo: 0
[    29.122]     PhysBasePtr: 0xc0000000
[    29.122]     LinBytesPerScanLine: 2560
[    29.122]     BnkNumberOfImagePages: 3
[    29.122]     LinNumberOfImagePages: 3
[    29.122]     LinRedMaskSize: 5
[    29.122]     LinRedFieldPosition: 11
[    29.122]     LinGreenMaskSize: 6
[    29.122]     LinGreenFieldPosition: 5
[    29.122]     LinBlueMaskSize: 5
[    29.122]     LinBlueFieldPosition: 0
[    29.122]     LinRsvdMaskSize: 0
[    29.122]     LinRsvdFieldPosition: 0
[    29.122]     MaxPixelClock: 0
[    29.123] *Mode: 11e (1280x768)
[    29.123]     ModeAttributes: 0x9b
[    29.123]     WinAAttributes: 0x7
[    29.123]     WinBAttributes: 0x0
[    29.123]     WinGranularity: 64
[    29.123]     WinSize: 64
[    29.123]     WinASegment: 0xa000
[    29.123]     WinBSegment: 0xa000
[    29.123]     WinFuncPtr: 0xc000877b
[    29.123]     BytesPerScanline: 5120
[    29.123]     XResolution: 1280
[    29.123]     YResolution: 768
[    29.123]     XCharSize: 8
[    29.123]     YCharSize: 16
[    29.123]     NumberOfPlanes: 1
[    29.123]     BitsPerPixel: 32
[    29.123]     NumberOfBanks: 1
[    29.123]     MemoryModel: 6
[    29.123]     BankSize: 0
[    29.123]     NumberOfImages: 1
[    29.123]     RedMaskSize: 8
[    29.123]     RedFieldPosition: 16
[    29.123]     GreenMaskSize: 8
[    29.123]     GreenFieldPosition: 8
[    29.123]     BlueMaskSize: 8
[    29.123]     BlueFieldPosition: 0
[    29.123]     RsvdMaskSize: 8
[    29.123]     RsvdFieldPosition: 24
[    29.123]     DirectColorModeInfo: 0
[    29.123]     PhysBasePtr: 0xc0000000
[    29.123]     LinBytesPerScanLine: 5120
[    29.123]     BnkNumberOfImagePages: 1
[    29.123]     LinNumberOfImagePages: 1
[    29.123]     LinRedMaskSize: 8
[    29.123]     LinRedFieldPosition: 16
[    29.123]     LinGreenMaskSize: 8
[    29.123]     LinGreenFieldPosition: 8
[    29.123]     LinBlueMaskSize: 8
[    29.123]     LinBlueFieldPosition: 0
[    29.123]     LinRsvdMaskSize: 8
[    29.123]     LinRsvdFieldPosition: 24
[    29.123]     MaxPixelClock: 0
[    29.123] Mode: 101 (640x480)
[    29.123]     ModeAttributes: 0x9f
[    29.124]     WinAAttributes: 0x7
[    29.124]     WinBAttributes: 0x0
[    29.124]     WinGranularity: 64
[    29.124]     WinSize: 64
[    29.124]     WinASegment: 0xa000
[    29.124]     WinBSegment: 0xa000
[    29.124]     WinFuncPtr: 0xc000877b
[    29.124]     BytesPerScanline: 640
[    29.124]     XResolution: 640
[    29.124]     YResolution: 480
[    29.124]     XCharSize: 8
[    29.124]     YCharSize: 16
[    29.124]     NumberOfPlanes: 1
[    29.124]     BitsPerPixel: 8
[    29.124]     NumberOfBanks: 1
[    29.124]     MemoryModel: 4
[    29.124]     BankSize: 0
[    29.124]     NumberOfImages: 24
[    29.124]     RedMaskSize: 0
[    29.124]     RedFieldPosition: 0
[    29.124]     GreenMaskSize: 0
[    29.124]     GreenFieldPosition: 0
[    29.124]     BlueMaskSize: 0
[    29.124]     BlueFieldPosition: 0
[    29.124]     RsvdMaskSize: 0
[    29.124]     RsvdFieldPosition: 0
[    29.124]     DirectColorModeInfo: 0
[    29.124]     PhysBasePtr: 0xc0000000
[    29.124]     LinBytesPerScanLine: 640
[    29.124]     BnkNumberOfImagePages: 24
[    29.124]     LinNumberOfImagePages: 24
[    29.124]     LinRedMaskSize: 0
[    29.124]     LinRedFieldPosition: 0
[    29.124]     LinGreenMaskSize: 0
[    29.124]     LinGreenFieldPosition: 0
[    29.124]     LinBlueMaskSize: 0
[    29.124]     LinBlueFieldPosition: 0
[    29.124]     LinRsvdMaskSize: 0
[    29.124]     LinRsvdFieldPosition: 0
[    29.124]     MaxPixelClock: 0
[    29.124] Mode: 100 (640x400)
[    29.124]     ModeAttributes: 0x9f
[    29.124]     WinAAttributes: 0x7
[    29.124]     WinBAttributes: 0x0
[    29.124]     WinGranularity: 64
[    29.124]     WinSize: 64
[    29.124]     WinASegment: 0xa000
[    29.124]     WinBSegment: 0xa000
[    29.124]     WinFuncPtr: 0xc000877b
[    29.124]     BytesPerScanline: 640
[    29.124]     XResolution: 640
[    29.124]     YResolution: 400
[    29.124]     XCharSize: 8
[    29.124]     YCharSize: 16
[    29.124]     NumberOfPlanes: 1
[    29.124]     BitsPerPixel: 8
[    29.124]     NumberOfBanks: 1
[    29.124]     MemoryModel: 4
[    29.124]     BankSize: 0
[    29.124]     NumberOfImages: 31
[    29.124]     RedMaskSize: 0
[    29.124]     RedFieldPosition: 0
[    29.124]     GreenMaskSize: 0
[    29.124]     GreenFieldPosition: 0
[    29.124]     BlueMaskSize: 0
[    29.124]     BlueFieldPosition: 0
[    29.124]     RsvdMaskSize: 0
[    29.124]     RsvdFieldPosition: 0
[    29.124]     DirectColorModeInfo: 0
[    29.124]     PhysBasePtr: 0xc0000000
[    29.124]     LinBytesPerScanLine: 640
[    29.124]     BnkNumberOfImagePages: 31
[    29.125]     LinNumberOfImagePages: 31
[    29.125]     LinRedMaskSize: 0
[    29.125]     LinRedFieldPosition: 0
[    29.125]     LinGreenMaskSize: 0
[    29.125]     LinGreenFieldPosition: 0
[    29.125]     LinBlueMaskSize: 0
[    29.125]     LinBlueFieldPosition: 0
[    29.125]     LinRsvdMaskSize: 0
[    29.125]     LinRsvdFieldPosition: 0
[    29.125]     MaxPixelClock: 0
[    29.125] Mode: 103 (800x600)
[    29.125]     ModeAttributes: 0x9f
[    29.125]     WinAAttributes: 0x7
[    29.125]     WinBAttributes: 0x0
[    29.125]     WinGranularity: 64
[    29.125]     WinSize: 64
[    29.125]     WinASegment: 0xa000
[    29.125]     WinBSegment: 0xa000
[    29.125]     WinFuncPtr: 0xc000877b
[    29.125]     BytesPerScanline: 800
[    29.125]     XResolution: 800
[    29.125]     YResolution: 600
[    29.125]     XCharSize: 8
[    29.125]     YCharSize: 16
[    29.125]     NumberOfPlanes: 1
[    29.125]     BitsPerPixel: 8
[    29.125]     NumberOfBanks: 1
[    29.125]     MemoryModel: 4
[    29.125]     BankSize: 0
[    29.125]     NumberOfImages: 15
[    29.125]     RedMaskSize: 0
[    29.125]     RedFieldPosition: 0
[    29.125]     GreenMaskSize: 0
[    29.125]     GreenFieldPosition: 0
[    29.125]     BlueMaskSize: 0
[    29.125]     BlueFieldPosition: 0
[    29.125]     RsvdMaskSize: 0
[    29.125]     RsvdFieldPosition: 0
[    29.125]     DirectColorModeInfo: 0
[    29.125]     PhysBasePtr: 0xc0000000
[    29.125]     LinBytesPerScanLine: 800
[    29.125]     BnkNumberOfImagePages: 15
[    29.125]     LinNumberOfImagePages: 15
[    29.125]     LinRedMaskSize: 0
[    29.125]     LinRedFieldPosition: 0
[    29.125]     LinGreenMaskSize: 0
[    29.125]     LinGreenFieldPosition: 0
[    29.125]     LinBlueMaskSize: 0
[    29.125]     LinBlueFieldPosition: 0
[    29.125]     LinRsvdMaskSize: 0
[    29.125]     LinRsvdFieldPosition: 0
[    29.125]     MaxPixelClock: 0
[    29.126] Mode: 104 (1024x768)
[    29.126]     ModeAttributes: 0x1f
[    29.126]     WinAAttributes: 0x7
[    29.126]     WinBAttributes: 0x0
[    29.126]     WinGranularity: 64
[    29.126]     WinSize: 64
[    29.126]     WinASegment: 0xa000
[    29.126]     WinBSegment: 0xa000
[    29.126]     WinFuncPtr: 0xc000877b
[    29.126]     BytesPerScanline: 128
[    29.126]     XResolution: 1024
[    29.126]     YResolution: 768
[    29.126]     XCharSize: 8
[    29.126]     YCharSize: 16
[    29.126]     NumberOfPlanes: 4
[    29.126]     BitsPerPixel: 4
[    29.126]     NumberOfBanks: 1
[    29.126]     MemoryModel: 3
[    29.126]     BankSize: 0
[    29.126]     NumberOfImages: 15
[    29.126]     RedMaskSize: 0
[    29.126]     RedFieldPosition: 0
[    29.126]     GreenMaskSize: 0
[    29.126]     GreenFieldPosition: 0
[    29.126]     BlueMaskSize: 0
[    29.126]     BlueFieldPosition: 0
[    29.126]     RsvdMaskSize: 0
[    29.126]     RsvdFieldPosition: 0
[    29.126]     DirectColorModeInfo: 0
[    29.126]     PhysBasePtr: 0xc0000000
[    29.126]     LinBytesPerScanLine: 128
[    29.126]     BnkNumberOfImagePages: 15
[    29.126]     LinNumberOfImagePages: 15
[    29.126]     LinRedMaskSize: 0
[    29.126]     LinRedFieldPosition: 0
[    29.126]     LinGreenMaskSize: 0
[    29.126]     LinGreenFieldPosition: 0
[    29.126]     LinBlueMaskSize: 0
[    29.126]     LinBlueFieldPosition: 0
[    29.126]     LinRsvdMaskSize: 0
[    29.126]     LinRsvdFieldPosition: 0
[    29.126]     MaxPixelClock: 0
[    29.126] Mode: 105 (1024x768)
[    29.126]     ModeAttributes: 0x9f
[    29.126]     WinAAttributes: 0x7
[    29.126]     WinBAttributes: 0x0
[    29.126]     WinGranularity: 64
[    29.126]     WinSize: 64
[    29.126]     WinASegment: 0xa000
[    29.126]     WinBSegment: 0xa000
[    29.126]     WinFuncPtr: 0xc000877b
[    29.126]     BytesPerScanline: 1024
[    29.126]     XResolution: 1024
[    29.126]     YResolution: 768
[    29.126]     XCharSize: 8
[    29.126]     YCharSize: 16
[    29.126]     NumberOfPlanes: 1
[    29.126]     BitsPerPixel: 8
[    29.126]     NumberOfBanks: 1
[    29.126]     MemoryModel: 4
[    29.126]     BankSize: 0
[    29.126]     NumberOfImages: 9
[    29.126]     RedMaskSize: 0
[    29.126]     RedFieldPosition: 0
[    29.126]     GreenMaskSize: 0
[    29.126]     GreenFieldPosition: 0
[    29.126]     BlueMaskSize: 0
[    29.127]     BlueFieldPosition: 0
[    29.127]     RsvdMaskSize: 0
[    29.127]     RsvdFieldPosition: 0
[    29.127]     DirectColorModeInfo: 0
[    29.127]     PhysBasePtr: 0xc0000000
[    29.127]     LinBytesPerScanLine: 1024
[    29.127]     BnkNumberOfImagePages: 9
[    29.127]     LinNumberOfImagePages: 9
[    29.127]     LinRedMaskSize: 0
[    29.127]     LinRedFieldPosition: 0
[    29.127]     LinGreenMaskSize: 0
[    29.127]     LinGreenFieldPosition: 0
[    29.127]     LinBlueMaskSize: 0
[    29.127]     LinBlueFieldPosition: 0
[    29.127]     LinRsvdMaskSize: 0
[    29.127]     LinRsvdFieldPosition: 0
[    29.127]     MaxPixelClock: 0
[    29.127] Mode: 10d (320x200)
[    29.127]     ModeAttributes: 0x9b
[    29.127]     WinAAttributes: 0x7
[    29.127]     WinBAttributes: 0x0
[    29.127]     WinGranularity: 64
[    29.127]     WinSize: 64
[    29.127]     WinASegment: 0xa000
[    29.127]     WinBSegment: 0xa000
[    29.127]     WinFuncPtr: 0xc000877b
[    29.127]     BytesPerScanline: 640
[    29.127]     XResolution: 320
[    29.127]     YResolution: 200
[    29.127]     XCharSize: 8
[    29.127]     YCharSize: 8
[    29.127]     NumberOfPlanes: 1
[    29.127]     BitsPerPixel: 15
[    29.127]     NumberOfBanks: 1
[    29.127]     MemoryModel: 6
[    29.127]     BankSize: 0
[    29.127]     NumberOfImages: 63
[    29.127]     RedMaskSize: 5
[    29.127]     RedFieldPosition: 10
[    29.127]     GreenMaskSize: 5
[    29.127]     GreenFieldPosition: 5
[    29.127]     BlueMaskSize: 5
[    29.127]     BlueFieldPosition: 0
[    29.127]     RsvdMaskSize: 0
[    29.127]     RsvdFieldPosition: 0
[    29.127]     DirectColorModeInfo: 0
[    29.127]     PhysBasePtr: 0xc0000000
[    29.127]     LinBytesPerScanLine: 640
[    29.127]     BnkNumberOfImagePages: 63
[    29.127]     LinNumberOfImagePages: 63
[    29.127]     LinRedMaskSize: 5
[    29.127]     LinRedFieldPosition: 10
[    29.127]     LinGreenMaskSize: 5
[    29.127]     LinGreenFieldPosition: 5
[    29.127]     LinBlueMaskSize: 5
[    29.128]     LinBlueFieldPosition: 0
[    29.128]     LinRsvdMaskSize: 0
[    29.128]     LinRsvdFieldPosition: 0
[    29.128]     MaxPixelClock: 0
[    29.128] Mode: 10e (320x200)
[    29.128]     ModeAttributes: 0x9b
[    29.128]     WinAAttributes: 0x7
[    29.128]     WinBAttributes: 0x0
[    29.128]     WinGranularity: 64
[    29.128]     WinSize: 64
[    29.128]     WinASegment: 0xa000
[    29.128]     WinBSegment: 0xa000
[    29.128]     WinFuncPtr: 0xc000877b
[    29.128]     BytesPerScanline: 640
[    29.128]     XResolution: 320
[    29.128]     YResolution: 200
[    29.128]     XCharSize: 8
[    29.128]     YCharSize: 8
[    29.128]     NumberOfPlanes: 1
[    29.128]     BitsPerPixel: 16
[    29.128]     NumberOfBanks: 1
[    29.128]     MemoryModel: 6
[    29.128]     BankSize: 0
[    29.128]     NumberOfImages: 63
[    29.128]     RedMaskSize: 5
[    29.128]     RedFieldPosition: 11
[    29.128]     GreenMaskSize: 6
[    29.128]     GreenFieldPosition: 5
[    29.128]     BlueMaskSize: 5
[    29.128]     BlueFieldPosition: 0
[    29.128]     RsvdMaskSize: 0
[    29.128]     RsvdFieldPosition: 0
[    29.128]     DirectColorModeInfo: 0
[    29.128]     PhysBasePtr: 0xc0000000
[    29.128]     LinBytesPerScanLine: 640
[    29.128]     BnkNumberOfImagePages: 63
[    29.128]     LinNumberOfImagePages: 63
[    29.128]     LinRedMaskSize: 5
[    29.128]     LinRedFieldPosition: 11
[    29.128]     LinGreenMaskSize: 6
[    29.128]     LinGreenFieldPosition: 5
[    29.128]     LinBlueMaskSize: 5
[    29.128]     LinBlueFieldPosition: 0
[    29.128]     LinRsvdMaskSize: 0
[    29.128]     LinRsvdFieldPosition: 0
[    29.128]     MaxPixelClock: 0
[    29.129] Mode: 110 (640x480)
[    29.129]     ModeAttributes: 0x9b
[    29.129]     WinAAttributes: 0x7
[    29.129]     WinBAttributes: 0x0
[    29.129]     WinGranularity: 64
[    29.129]     WinSize: 64
[    29.129]     WinASegment: 0xa000
[    29.129]     WinBSegment: 0xa000
[    29.129]     WinFuncPtr: 0xc000877b
[    29.129]     BytesPerScanline: 1280
[    29.129]     XResolution: 640
[    29.129]     YResolution: 480
[    29.129]     XCharSize: 8
[    29.129]     YCharSize: 16
[    29.129]     NumberOfPlanes: 1
[    29.129]     BitsPerPixel: 15
[    29.129]     NumberOfBanks: 1
[    29.129]     MemoryModel: 6
[    29.129]     BankSize: 0
[    29.129]     NumberOfImages: 11
[    29.129]     RedMaskSize: 5
[    29.129]     RedFieldPosition: 10
[    29.129]     GreenMaskSize: 5
[    29.129]     GreenFieldPosition: 5
[    29.129]     BlueMaskSize: 5
[    29.129]     BlueFieldPosition: 0
[    29.129]     RsvdMaskSize: 0
[    29.129]     RsvdFieldPosition: 0
[    29.129]     DirectColorModeInfo: 0
[    29.129]     PhysBasePtr: 0xc0000000
[    29.129]     LinBytesPerScanLine: 1280
[    29.129]     BnkNumberOfImagePages: 11
[    29.129]     LinNumberOfImagePages: 11
[    29.129]     LinRedMaskSize: 5
[    29.129]     LinRedFieldPosition: 10
[    29.129]     LinGreenMaskSize: 5
[    29.129]     LinGreenFieldPosition: 5
[    29.129]     LinBlueMaskSize: 5
[    29.129]     LinBlueFieldPosition: 0
[    29.129]     LinRsvdMaskSize: 0
[    29.129]     LinRsvdFieldPosition: 0
[    29.129]     MaxPixelClock: 0
[    29.130] Mode: 111 (640x480)
[    29.130]     ModeAttributes: 0x9b
[    29.130]     WinAAttributes: 0x7
[    29.130]     WinBAttributes: 0x0
[    29.130]     WinGranularity: 64
[    29.130]     WinSize: 64
[    29.130]     WinASegment: 0xa000
[    29.130]     WinBSegment: 0xa000
[    29.130]     WinFuncPtr: 0xc000877b
[    29.130]     BytesPerScanline: 1280
[    29.130]     XResolution: 640
[    29.130]     YResolution: 480
[    29.130]     XCharSize: 8
[    29.130]     YCharSize: 16
[    29.130]     NumberOfPlanes: 1
[    29.130]     BitsPerPixel: 16
[    29.130]     NumberOfBanks: 1
[    29.130]     MemoryModel: 6
[    29.130]     BankSize: 0
[    29.130]     NumberOfImages: 11
[    29.130]     RedMaskSize: 5
[    29.130]     RedFieldPosition: 11
[    29.130]     GreenMaskSize: 6
[    29.130]     GreenFieldPosition: 5
[    29.130]     BlueMaskSize: 5
[    29.130]     BlueFieldPosition: 0
[    29.130]     RsvdMaskSize: 0
[    29.130]     RsvdFieldPosition: 0
[    29.130]     DirectColorModeInfo: 0
[    29.130]     PhysBasePtr: 0xc0000000
[    29.130]     LinBytesPerScanLine: 1280
[    29.130]     BnkNumberOfImagePages: 11
[    29.130]     LinNumberOfImagePages: 11
[    29.130]     LinRedMaskSize: 5
[    29.130]     LinRedFieldPosition: 11
[    29.130]     LinGreenMaskSize: 6
[    29.130]     LinGreenFieldPosition: 5
[    29.130]     LinBlueMaskSize: 5
[    29.130]     LinBlueFieldPosition: 0
[    29.130]     LinRsvdMaskSize: 0
[    29.130]     LinRsvdFieldPosition: 0
[    29.130]     MaxPixelClock: 0
[    29.130] Mode: 113 (800x600)
[    29.130]     ModeAttributes: 0x9b
[    29.130]     WinAAttributes: 0x7
[    29.130]     WinBAttributes: 0x0
[    29.130]     WinGranularity: 64
[    29.130]     WinSize: 64
[    29.130]     WinASegment: 0xa000
[    29.130]     WinBSegment: 0xa000
[    29.130]     WinFuncPtr: 0xc000877b
[    29.130]     BytesPerScanline: 1600
[    29.130]     XResolution: 800
[    29.130]     YResolution: 600
[    29.130]     XCharSize: 8
[    29.130]     YCharSize: 16
[    29.130]     NumberOfPlanes: 1
[    29.130]     BitsPerPixel: 15
[    29.130]     NumberOfBanks: 1
[    29.130]     MemoryModel: 6
[    29.130]     BankSize: 0
[    29.130]     NumberOfImages: 7
[    29.130]     RedMaskSize: 5
[    29.130]     RedFieldPosition: 10
[    29.130]     GreenMaskSize: 5
[    29.131]     GreenFieldPosition: 5
[    29.131]     BlueMaskSize: 5
[    29.131]     BlueFieldPosition: 0
[    29.131]     RsvdMaskSize: 0
[    29.131]     RsvdFieldPosition: 0
[    29.131]     DirectColorModeInfo: 0
[    29.131]     PhysBasePtr: 0xc0000000
[    29.131]     LinBytesPerScanLine: 1600
[    29.131]     BnkNumberOfImagePages: 7
[    29.131]     LinNumberOfImagePages: 7
[    29.131]     LinRedMaskSize: 5
[    29.131]     LinRedFieldPosition: 10
[    29.131]     LinGreenMaskSize: 5
[    29.131]     LinGreenFieldPosition: 5
[    29.131]     LinBlueMaskSize: 5
[    29.131]     LinBlueFieldPosition: 0
[    29.131]     LinRsvdMaskSize: 0
[    29.131]     LinRsvdFieldPosition: 0
[    29.131]     MaxPixelClock: 0
[    29.131] Mode: 114 (800x600)
[    29.131]     ModeAttributes: 0x9b
[    29.131]     WinAAttributes: 0x7
[    29.131]     WinBAttributes: 0x0
[    29.131]     WinGranularity: 64
[    29.131]     WinSize: 64
[    29.131]     WinASegment: 0xa000
[    29.131]     WinBSegment: 0xa000
[    29.131]     WinFuncPtr: 0xc000877b
[    29.131]     BytesPerScanline: 1600
[    29.131]     XResolution: 800
[    29.131]     YResolution: 600
[    29.131]     XCharSize: 8
[    29.131]     YCharSize: 16
[    29.131]     NumberOfPlanes: 1
[    29.131]     BitsPerPixel: 16
[    29.131]     NumberOfBanks: 1
[    29.131]     MemoryModel: 6
[    29.131]     BankSize: 0
[    29.131]     NumberOfImages: 7
[    29.131]     RedMaskSize: 5
[    29.131]     RedFieldPosition: 11
[    29.131]     GreenMaskSize: 6
[    29.131]     GreenFieldPosition: 5
[    29.131]     BlueMaskSize: 5
[    29.131]     BlueFieldPosition: 0
[    29.131]     RsvdMaskSize: 0
[    29.131]     RsvdFieldPosition: 0
[    29.131]     DirectColorModeInfo: 0
[    29.131]     PhysBasePtr: 0xc0000000
[    29.131]     LinBytesPerScanLine: 1600
[    29.131]     BnkNumberOfImagePages: 7
[    29.131]     LinNumberOfImagePages: 7
[    29.131]     LinRedMaskSize: 5
[    29.131]     LinRedFieldPosition: 11
[    29.131]     LinGreenMaskSize: 6
[    29.131]     LinGreenFieldPosition: 5
[    29.131]     LinBlueMaskSize: 5
[    29.131]     LinBlueFieldPosition: 0
[    29.131]     LinRsvdMaskSize: 0
[    29.131]     LinRsvdFieldPosition: 0
[    29.131]     MaxPixelClock: 0
[    29.132] Mode: 116 (1024x768)
[    29.132]     ModeAttributes: 0x9b
[    29.132]     WinAAttributes: 0x7
[    29.132]     WinBAttributes: 0x0
[    29.132]     WinGranularity: 64
[    29.132]     WinSize: 64
[    29.132]     WinASegment: 0xa000
[    29.132]     WinBSegment: 0xa000
[    29.132]     WinFuncPtr: 0xc000877b
[    29.132]     BytesPerScanline: 2048
[    29.132]     XResolution: 1024
[    29.132]     YResolution: 768
[    29.132]     XCharSize: 8
[    29.132]     YCharSize: 16
[    29.132]     NumberOfPlanes: 1
[    29.132]     BitsPerPixel: 15
[    29.132]     NumberOfBanks: 1
[    29.132]     MemoryModel: 6
[    29.132]     BankSize: 0
[    29.132]     NumberOfImages: 4
[    29.132]     RedMaskSize: 5
[    29.132]     RedFieldPosition: 10
[    29.132]     GreenMaskSize: 5
[    29.132]     GreenFieldPosition: 5
[    29.132]     BlueMaskSize: 5
[    29.132]     BlueFieldPosition: 0
[    29.132]     RsvdMaskSize: 0
[    29.132]     RsvdFieldPosition: 0
[    29.132]     DirectColorModeInfo: 0
[    29.132]     PhysBasePtr: 0xc0000000
[    29.132]     LinBytesPerScanLine: 2048
[    29.132]     BnkNumberOfImagePages: 4
[    29.132]     LinNumberOfImagePages: 4
[    29.132]     LinRedMaskSize: 5
[    29.132]     LinRedFieldPosition: 10
[    29.132]     LinGreenMaskSize: 5
[    29.132]     LinGreenFieldPosition: 5
[    29.132]     LinBlueMaskSize: 5
[    29.132]     LinBlueFieldPosition: 0
[    29.132]     LinRsvdMaskSize: 0
[    29.132]     LinRsvdFieldPosition: 0
[    29.132]     MaxPixelClock: 0
[    29.133] Mode: 117 (1024x768)
[    29.133]     ModeAttributes: 0x9b
[    29.133]     WinAAttributes: 0x7
[    29.133]     WinBAttributes: 0x0
[    29.133]     WinGranularity: 64
[    29.133]     WinSize: 64
[    29.133]     WinASegment: 0xa000
[    29.133]     WinBSegment: 0xa000
[    29.133]     WinFuncPtr: 0xc000877b
[    29.133]     BytesPerScanline: 2048
[    29.133]     XResolution: 1024
[    29.133]     YResolution: 768
[    29.133]     XCharSize: 8
[    29.133]     YCharSize: 16
[    29.133]     NumberOfPlanes: 1
[    29.133]     BitsPerPixel: 16
[    29.133]     NumberOfBanks: 1
[    29.133]     MemoryModel: 6
[    29.133]     BankSize: 0
[    29.133]     NumberOfImages: 4
[    29.133]     RedMaskSize: 5
[    29.133]     RedFieldPosition: 11
[    29.133]     GreenMaskSize: 6
[    29.133]     GreenFieldPosition: 5
[    29.133]     BlueMaskSize: 5
[    29.133]     BlueFieldPosition: 0
[    29.133]     RsvdMaskSize: 0
[    29.133]     RsvdFieldPosition: 0
[    29.133]     DirectColorModeInfo: 0
[    29.133]     PhysBasePtr: 0xc0000000
[    29.133]     LinBytesPerScanLine: 2048
[    29.133]     BnkNumberOfImagePages: 4
[    29.133]     LinNumberOfImagePages: 4
[    29.133]     LinRedMaskSize: 5
[    29.133]     LinRedFieldPosition: 11
[    29.133]     LinGreenMaskSize: 6
[    29.133]     LinGreenFieldPosition: 5
[    29.133]     LinBlueMaskSize: 5
[    29.133]     LinBlueFieldPosition: 0
[    29.133]     LinRsvdMaskSize: 0
[    29.133]     LinRsvdFieldPosition: 0
[    29.133]     MaxPixelClock: 0
[    29.134] Mode: 127 (320x240)
[    29.134]     ModeAttributes: 0x9f
[    29.134]     WinAAttributes: 0x7
[    29.134]     WinBAttributes: 0x0
[    29.134]     WinGranularity: 64
[    29.134]     WinSize: 64
[    29.134]     WinASegment: 0xa000
[    29.134]     WinBSegment: 0xa000
[    29.134]     WinFuncPtr: 0xc000877b
[    29.134]     BytesPerScanline: 320
[    29.134]     XResolution: 320
[    29.134]     YResolution: 240
[    29.134]     XCharSize: 8
[    29.134]     YCharSize: 8
[    29.134]     NumberOfPlanes: 1
[    29.134]     BitsPerPixel: 8
[    29.134]     NumberOfBanks: 1
[    29.134]     MemoryModel: 4
[    29.134]     BankSize: 0
[    29.134]     NumberOfImages: 63
[    29.134]     RedMaskSize: 0
[    29.134]     RedFieldPosition: 0
[    29.134]     GreenMaskSize: 0
[    29.134]     GreenFieldPosition: 0
[    29.134]     BlueMaskSize: 0
[    29.134]     BlueFieldPosition: 0
[    29.134]     RsvdMaskSize: 0
[    29.134]     RsvdFieldPosition: 0
[    29.134]     DirectColorModeInfo: 0
[    29.134]     PhysBasePtr: 0xc0000000
[    29.134]     LinBytesPerScanLine: 320
[    29.134]     BnkNumberOfImagePages: 63
[    29.134]     LinNumberOfImagePages: 63
[    29.134]     LinRedMaskSize: 0
[    29.134]     LinRedFieldPosition: 0
[    29.134]     LinGreenMaskSize: 0
[    29.134]     LinGreenFieldPosition: 0
[    29.134]     LinBlueMaskSize: 0
[    29.134]     LinBlueFieldPosition: 0
[    29.134]     LinRsvdMaskSize: 0
[    29.134]     LinRsvdFieldPosition: 0
[    29.134]     MaxPixelClock: 0
[    29.134] Mode: 128 (400x300)
[    29.134]     ModeAttributes: 0x9f
[    29.134]     WinAAttributes: 0x7
[    29.134]     WinBAttributes: 0x0
[    29.134]     WinGranularity: 64
[    29.134]     WinSize: 64
[    29.135]     WinASegment: 0xa000
[    29.135]     WinBSegment: 0xa000
[    29.135]     WinFuncPtr: 0xc000877b
[    29.135]     BytesPerScanline: 400
[    29.135]     XResolution: 400
[    29.135]     YResolution: 300
[    29.135]     XCharSize: 8
[    29.135]     YCharSize: 8
[    29.135]     NumberOfPlanes: 1
[    29.135]     BitsPerPixel: 8
[    29.135]     NumberOfBanks: 1
[    29.135]     MemoryModel: 4
[    29.135]     BankSize: 0
[    29.135]     NumberOfImages: 63
[    29.135]     RedMaskSize: 0
[    29.135]     RedFieldPosition: 0
[    29.135]     GreenMaskSize: 0
[    29.135]     GreenFieldPosition: 0
[    29.135]     BlueMaskSize: 0
[    29.135]     BlueFieldPosition: 0
[    29.135]     RsvdMaskSize: 0
[    29.135]     RsvdFieldPosition: 0
[    29.135]     DirectColorModeInfo: 0
[    29.135]     PhysBasePtr: 0xc0000000
[    29.135]     LinBytesPerScanLine: 400
[    29.135]     BnkNumberOfImagePages: 63
[    29.135]     LinNumberOfImagePages: 63
[    29.135]     LinRedMaskSize: 0
[    29.135]     LinRedFieldPosition: 0
[    29.135]     LinGreenMaskSize: 0
[    29.135]     LinGreenFieldPosition: 0
[    29.135]     LinBlueMaskSize: 0
[    29.135]     LinBlueFieldPosition: 0
[    29.135]     LinRsvdMaskSize: 0
[    29.135]     LinRsvdFieldPosition: 0
[    29.135]     MaxPixelClock: 0
[    29.135] Mode: 129 (512x384)
[    29.135]     ModeAttributes: 0x9f
[    29.135]     WinAAttributes: 0x7
[    29.135]     WinBAttributes: 0x0
[    29.135]     WinGranularity: 64
[    29.135]     WinSize: 64
[    29.135]     WinASegment: 0xa000
[    29.135]     WinBSegment: 0xa000
[    29.135]     WinFuncPtr: 0xc000877b
[    29.135]     BytesPerScanline: 512
[    29.135]     XResolution: 512
[    29.135]     YResolution: 384
[    29.135]     XCharSize: 8
[    29.135]     YCharSize: 8
[    29.135]     NumberOfPlanes: 1
[    29.135]     BitsPerPixel: 8
[    29.135]     NumberOfBanks: 1
[    29.135]     MemoryModel: 4
[    29.135]     BankSize: 0
[    29.135]     NumberOfImages: 41
[    29.135]     RedMaskSize: 0
[    29.135]     RedFieldPosition: 0
[    29.135]     GreenMaskSize: 0
[    29.135]     GreenFieldPosition: 0
[    29.135]     BlueMaskSize: 0
[    29.135]     BlueFieldPosition: 0
[    29.135]     RsvdMaskSize: 0
[    29.135]     RsvdFieldPosition: 0
[    29.135]     DirectColorModeInfo: 0
[    29.135]     PhysBasePtr: 0xc0000000
[    29.135]     LinBytesPerScanLine: 512
[    29.135]     BnkNumberOfImagePages: 41
[    29.135]     LinNumberOfImagePages: 41
[    29.136]     LinRedMaskSize: 0
[    29.136]     LinRedFieldPosition: 0
[    29.136]     LinGreenMaskSize: 0
[    29.136]     LinGreenFieldPosition: 0
[    29.136]     LinBlueMaskSize: 0
[    29.136]     LinBlueFieldPosition: 0
[    29.136]     LinRsvdMaskSize: 0
[    29.136]     LinRsvdFieldPosition: 0
[    29.136]     MaxPixelClock: 0
[    29.136] Mode: 12a (320x240)
[    29.136]     ModeAttributes: 0x9b
[    29.136]     WinAAttributes: 0x7
[    29.136]     WinBAttributes: 0x0
[    29.136]     WinGranularity: 64
[    29.136]     WinSize: 64
[    29.136]     WinASegment: 0xa000
[    29.136]     WinBSegment: 0xa000
[    29.136]     WinFuncPtr: 0xc000877b
[    29.136]     BytesPerScanline: 640
[    29.136]     XResolution: 320
[    29.136]     YResolution: 240
[    29.136]     XCharSize: 8
[    29.136]     YCharSize: 8
[    29.136]     NumberOfPlanes: 1
[    29.136]     BitsPerPixel: 16
[    29.136]     NumberOfBanks: 1
[    29.136]     MemoryModel: 6
[    29.136]     BankSize: 0
[    29.136]     NumberOfImages: 41
[    29.136]     RedMaskSize: 5
[    29.136]     RedFieldPosition: 11
[    29.136]     GreenMaskSize: 6
[    29.136]     GreenFieldPosition: 5
[    29.136]     BlueMaskSize: 5
[    29.136]     BlueFieldPosition: 0
[    29.136]     RsvdMaskSize: 0
[    29.136]     RsvdFieldPosition: 0
[    29.136]     DirectColorModeInfo: 0
[    29.136]     PhysBasePtr: 0xc0000000
[    29.136]     LinBytesPerScanLine: 640
[    29.136]     BnkNumberOfImagePages: 41
[    29.136]     LinNumberOfImagePages: 41
[    29.136]     LinRedMaskSize: 5
[    29.136]     LinRedFieldPosition: 11
[    29.136]     LinGreenMaskSize: 6
[    29.136]     LinGreenFieldPosition: 5
[    29.136]     LinBlueMaskSize: 5
[    29.136]     LinBlueFieldPosition: 0
[    29.136]     LinRsvdMaskSize: 0
[    29.136]     LinRsvdFieldPosition: 0
[    29.136]     MaxPixelClock: 0
[    29.137] Mode: 12b (400x300)
[    29.137]     ModeAttributes: 0x9b
[    29.137]     WinAAttributes: 0x7
[    29.137]     WinBAttributes: 0x0
[    29.137]     WinGranularity: 64
[    29.137]     WinSize: 64
[    29.137]     WinASegment: 0xa000
[    29.137]     WinBSegment: 0xa000
[    29.137]     WinFuncPtr: 0xc000877b
[    29.137]     BytesPerScanline: 800
[    29.137]     XResolution: 400
[    29.137]     YResolution: 300
[    29.137]     XCharSize: 8
[    29.137]     YCharSize: 8
[    29.137]     NumberOfPlanes: 1
[    29.137]     BitsPerPixel: 16
[    29.137]     NumberOfBanks: 1
[    29.137]     MemoryModel: 6
[    29.137]     BankSize: 0
[    29.137]     NumberOfImages: 31
[    29.137]     RedMaskSize: 5
[    29.137]     RedFieldPosition: 11
[    29.137]     GreenMaskSize: 6
[    29.137]     GreenFieldPosition: 5
[    29.137]     BlueMaskSize: 5
[    29.137]     BlueFieldPosition: 0
[    29.137]     RsvdMaskSize: 0
[    29.137]     RsvdFieldPosition: 0
[    29.137]     DirectColorModeInfo: 0
[    29.137]     PhysBasePtr: 0xc0000000
[    29.137]     LinBytesPerScanLine: 800
[    29.137]     BnkNumberOfImagePages: 31
[    29.137]     LinNumberOfImagePages: 31
[    29.137]     LinRedMaskSize: 5
[    29.137]     LinRedFieldPosition: 11
[    29.137]     LinGreenMaskSize: 6
[    29.137]     LinGreenFieldPosition: 5
[    29.137]     LinBlueMaskSize: 5
[    29.137]     LinBlueFieldPosition: 0
[    29.137]     LinRsvdMaskSize: 0
[    29.137]     LinRsvdFieldPosition: 0
[    29.137]     MaxPixelClock: 0
[    29.138] Mode: 12c (512x384)
[    29.138]     ModeAttributes: 0x9b
[    29.138]     WinAAttributes: 0x7
[    29.138]     WinBAttributes: 0x0
[    29.138]     WinGranularity: 64
[    29.138]     WinSize: 64
[    29.138]     WinASegment: 0xa000
[    29.138]     WinBSegment: 0xa000
[    29.138]     WinFuncPtr: 0xc000877b
[    29.138]     BytesPerScanline: 1024
[    29.138]     XResolution: 512
[    29.138]     YResolution: 384
[    29.138]     XCharSize: 8
[    29.138]     YCharSize: 8
[    29.138]     NumberOfPlanes: 1
[    29.138]     BitsPerPixel: 16
[    29.138]     NumberOfBanks: 1
[    29.138]     MemoryModel: 6
[    29.138]     BankSize: 0
[    29.138]     NumberOfImages: 20
[    29.138]     RedMaskSize: 5
[    29.138]     RedFieldPosition: 11
[    29.138]     GreenMaskSize: 6
[    29.138]     GreenFieldPosition: 5
[    29.138]     BlueMaskSize: 5
[    29.138]     BlueFieldPosition: 0
[    29.138]     RsvdMaskSize: 0
[    29.138]     RsvdFieldPosition: 0
[    29.138]     DirectColorModeInfo: 0
[    29.138]     PhysBasePtr: 0xc0000000
[    29.138]     LinBytesPerScanLine: 1024
[    29.138]     BnkNumberOfImagePages: 20
[    29.138]     LinNumberOfImagePages: 20
[    29.138]     LinRedMaskSize: 5
[    29.138]     LinRedFieldPosition: 11
[    29.138]     LinGreenMaskSize: 6
[    29.138]     LinGreenFieldPosition: 5
[    29.138]     LinBlueMaskSize: 5
[    29.138]     LinBlueFieldPosition: 0
[    29.138]     LinRsvdMaskSize: 0
[    29.138]     LinRsvdFieldPosition: 0
[    29.138]     MaxPixelClock: 0
[    29.138] Mode: 12d (320x200)
[    29.138]     ModeAttributes: 0x9f
[    29.138]     WinAAttributes: 0x7
[    29.138]     WinBAttributes: 0x0
[    29.138]     WinGranularity: 64
[    29.138]     WinSize: 64
[    29.138]     WinASegment: 0xa000
[    29.138]     WinBSegment: 0xa000
[    29.138]     WinFuncPtr: 0xc000877b
[    29.138]     BytesPerScanline: 320
[    29.138]     XResolution: 320
[    29.138]     YResolution: 200
[    29.138]     XCharSize: 8
[    29.138]     YCharSize: 8
[    29.139]     NumberOfPlanes: 1
[    29.139]     BitsPerPixel: 8
[    29.139]     NumberOfBanks: 1
[    29.139]     MemoryModel: 4
[    29.139]     BankSize: 0
[    29.139]     NumberOfImages: 127
[    29.139]     RedMaskSize: 0
[    29.139]     RedFieldPosition: 0
[    29.139]     GreenMaskSize: 0
[    29.139]     GreenFieldPosition: 0
[    29.139]     BlueMaskSize: 0
[    29.139]     BlueFieldPosition: 0
[    29.139]     RsvdMaskSize: 0
[    29.139]     RsvdFieldPosition: 0
[    29.139]     DirectColorModeInfo: 0
[    29.139]     PhysBasePtr: 0xc0000000
[    29.139]     LinBytesPerScanLine: 320
[    29.139]     BnkNumberOfImagePages: 127
[    29.139]     LinNumberOfImagePages: 127
[    29.139]     LinRedMaskSize: 0
[    29.139]     LinRedFieldPosition: 0
[    29.139]     LinGreenMaskSize: 0
[    29.139]     LinGreenFieldPosition: 0
[    29.139]     LinBlueMaskSize: 0
[    29.139]     LinBlueFieldPosition: 0
[    29.139]     LinRsvdMaskSize: 0
[    29.139]     LinRsvdFieldPosition: 0
[    29.139]     MaxPixelClock: 0
[    29.139] Mode: 131 (640x400)
[    29.139]     ModeAttributes: 0x9b
[    29.139]     WinAAttributes: 0x7
[    29.139]     WinBAttributes: 0x0
[    29.139]     WinGranularity: 64
[    29.139]     WinSize: 64
[    29.139]     WinASegment: 0xa000
[    29.139]     WinBSegment: 0xa000
[    29.139]     WinFuncPtr: 0xc000877b
[    29.139]     BytesPerScanline: 1280
[    29.139]     XResolution: 640
[    29.139]     YResolution: 400
[    29.139]     XCharSize: 8
[    29.139]     YCharSize: 16
[    29.139]     NumberOfPlanes: 1
[    29.139]     BitsPerPixel: 16
[    29.139]     NumberOfBanks: 1
[    29.139]     MemoryModel: 6
[    29.139]     BankSize: 0
[    29.139]     NumberOfImages: 15
[    29.139]     RedMaskSize: 5
[    29.139]     RedFieldPosition: 11
[    29.139]     GreenMaskSize: 6
[    29.139]     GreenFieldPosition: 5
[    29.139]     BlueMaskSize: 5
[    29.139]     BlueFieldPosition: 0
[    29.139]     RsvdMaskSize: 0
[    29.139]     RsvdFieldPosition: 0
[    29.139]     DirectColorModeInfo: 0
[    29.139]     PhysBasePtr: 0xc0000000
[    29.139]     LinBytesPerScanLine: 1280
[    29.139]     BnkNumberOfImagePages: 15
[    29.139]     LinNumberOfImagePages: 15
[    29.139]     LinRedMaskSize: 5
[    29.139]     LinRedFieldPosition: 11
[    29.140]     LinGreenMaskSize: 6
[    29.140]     LinGreenFieldPosition: 5
[    29.140]     LinBlueMaskSize: 5
[    29.140]     LinBlueFieldPosition: 0
[    29.140]     LinRsvdMaskSize: 0
[    29.140]     LinRsvdFieldPosition: 0
[    29.140]     MaxPixelClock: 0
[    29.140] *Mode: 112 (640x480)
[    29.140]     ModeAttributes: 0x9b
[    29.140]     WinAAttributes: 0x7
[    29.140]     WinBAttributes: 0x0
[    29.140]     WinGranularity: 64
[    29.140]     WinSize: 64
[    29.140]     WinASegment: 0xa000
[    29.140]     WinBSegment: 0xa000
[    29.140]     WinFuncPtr: 0xc000877b
[    29.140]     BytesPerScanline: 2560
[    29.140]     XResolution: 640
[    29.140]     YResolution: 480
[    29.140]     XCharSize: 8
[    29.140]     YCharSize: 16
[    29.140]     NumberOfPlanes: 1
[    29.140]     BitsPerPixel: 32
[    29.140]     NumberOfBanks: 1
[    29.140]     MemoryModel: 6
[    29.140]     BankSize: 0
[    29.140]     NumberOfImages: 5
[    29.140]     RedMaskSize: 8
[    29.140]     RedFieldPosition: 16
[    29.140]     GreenMaskSize: 8
[    29.140]     GreenFieldPosition: 8
[    29.140]     BlueMaskSize: 8
[    29.140]     BlueFieldPosition: 0
[    29.140]     RsvdMaskSize: 8
[    29.140]     RsvdFieldPosition: 24
[    29.140]     DirectColorModeInfo: 0
[    29.140]     PhysBasePtr: 0xc0000000
[    29.140]     LinBytesPerScanLine: 2560
[    29.140]     BnkNumberOfImagePages: 5
[    29.140]     LinNumberOfImagePages: 5
[    29.140]     LinRedMaskSize: 8
[    29.140]     LinRedFieldPosition: 16
[    29.140]     LinGreenMaskSize: 8
[    29.140]     LinGreenFieldPosition: 8
[    29.140]     LinBlueMaskSize: 8
[    29.140]     LinBlueFieldPosition: 0
[    29.140]     LinRsvdMaskSize: 8
[    29.140]     LinRsvdFieldPosition: 24
[    29.140]     MaxPixelClock: 0
[    29.141] *Mode: 115 (800x600)
[    29.141]     ModeAttributes: 0x9b
[    29.141]     WinAAttributes: 0x7
[    29.141]     WinBAttributes: 0x0
[    29.141]     WinGranularity: 64
[    29.141]     WinSize: 64
[    29.141]     WinASegment: 0xa000
[    29.141]     WinBSegment: 0xa000
[    29.141]     WinFuncPtr: 0xc000877b
[    29.141]     BytesPerScanline: 3200
[    29.141]     XResolution: 800
[    29.141]     YResolution: 600
[    29.141]     XCharSize: 8
[    29.141]     YCharSize: 16
[    29.141]     NumberOfPlanes: 1
[    29.141]     BitsPerPixel: 32
[    29.141]     NumberOfBanks: 1
[    29.141]     MemoryModel: 6
[    29.141]     BankSize: 0
[    29.141]     NumberOfImages: 3
[    29.141]     RedMaskSize: 8
[    29.141]     RedFieldPosition: 16
[    29.141]     GreenMaskSize: 8
[    29.141]     GreenFieldPosition: 8
[    29.141]     BlueMaskSize: 8
[    29.141]     BlueFieldPosition: 0
[    29.141]     RsvdMaskSize: 8
[    29.141]     RsvdFieldPosition: 24
[    29.141]     DirectColorModeInfo: 0
[    29.141]     PhysBasePtr: 0xc0000000
[    29.141]     LinBytesPerScanLine: 3200
[    29.141]     BnkNumberOfImagePages: 3
[    29.141]     LinNumberOfImagePages: 3
[    29.141]     LinRedMaskSize: 8
[    29.141]     LinRedFieldPosition: 16
[    29.141]     LinGreenMaskSize: 8
[    29.141]     LinGreenFieldPosition: 8
[    29.141]     LinBlueMaskSize: 8
[    29.141]     LinBlueFieldPosition: 0
[    29.141]     LinRsvdMaskSize: 8
[    29.141]     LinRsvdFieldPosition: 24
[    29.141]     MaxPixelClock: 0
[    29.142] *Mode: 118 (1024x768)
[    29.142]     ModeAttributes: 0x9b
[    29.142]     WinAAttributes: 0x7
[    29.142]     WinBAttributes: 0x0
[    29.142]     WinGranularity: 64
[    29.142]     WinSize: 64
[    29.142]     WinASegment: 0xa000
[    29.142]     WinBSegment: 0xa000
[    29.142]     WinFuncPtr: 0xc000877b
[    29.142]     BytesPerScanline: 4096
[    29.142]     XResolution: 1024
[    29.142]     YResolution: 768
[    29.142]     XCharSize: 8
[    29.142]     YCharSize: 16
[    29.142]     NumberOfPlanes: 1
[    29.142]     BitsPerPixel: 32
[    29.142]     NumberOfBanks: 1
[    29.142]     MemoryModel: 6
[    29.142]     BankSize: 0
[    29.142]     NumberOfImages: 1
[    29.142]     RedMaskSize: 8
[    29.142]     RedFieldPosition: 16
[    29.142]     GreenMaskSize: 8
[    29.142]     GreenFieldPosition: 8
[    29.142]     BlueMaskSize: 8
[    29.142]     BlueFieldPosition: 0
[    29.142]     RsvdMaskSize: 8
[    29.142]     RsvdFieldPosition: 24
[    29.142]     DirectColorModeInfo: 0
[    29.142]     PhysBasePtr: 0xc0000000
[    29.142]     LinBytesPerScanLine: 4096
[    29.142]     BnkNumberOfImagePages: 1
[    29.142]     LinNumberOfImagePages: 1
[    29.142]     LinRedMaskSize: 8
[    29.142]     LinRedFieldPosition: 16
[    29.142]     LinGreenMaskSize: 8
[    29.142]     LinGreenFieldPosition: 8
[    29.142]     LinBlueMaskSize: 8
[    29.142]     LinBlueFieldPosition: 0
[    29.142]     LinRsvdMaskSize: 8
[    29.142]     LinRsvdFieldPosition: 24
[    29.142]     MaxPixelClock: 0
[    29.143] Mode: 102 (800x600)
[    29.143]     ModeAttributes: 0x1f
[    29.143]     WinAAttributes: 0x7
[    29.143]     WinBAttributes: 0x0
[    29.143]     WinGranularity: 64
[    29.143]     WinSize: 64
[    29.143]     WinASegment: 0xa000
[    29.143]     WinBSegment: 0xa000
[    29.143]     WinFuncPtr: 0xc000877b
[    29.143]     BytesPerScanline: 100
[    29.143]     XResolution: 800
[    29.143]     YResolution: 600
[    29.143]     XCharSize: 8
[    29.143]     YCharSize: 16
[    29.143]     NumberOfPlanes: 4
[    29.143]     BitsPerPixel: 4
[    29.143]     NumberOfBanks: 1
[    29.143]     MemoryModel: 3
[    29.143]     BankSize: 0
[    29.143]     NumberOfImages: 31
[    29.143]     RedMaskSize: 0
[    29.143]     RedFieldPosition: 0
[    29.143]     GreenMaskSize: 0
[    29.143]     GreenFieldPosition: 0
[    29.143]     BlueMaskSize: 0
[    29.143]     BlueFieldPosition: 0
[    29.143]     RsvdMaskSize: 0
[    29.143]     RsvdFieldPosition: 0
[    29.143]     DirectColorModeInfo: 0
[    29.143]     PhysBasePtr: 0xc0000000
[    29.143]     LinBytesPerScanLine: 100
[    29.143]     BnkNumberOfImagePages: 31
[    29.143]     LinNumberOfImagePages: 31
[    29.143]     LinRedMaskSize: 0
[    29.143]     LinRedFieldPosition: 0
[    29.143]     LinGreenMaskSize: 0
[    29.143]     LinGreenFieldPosition: 0
[    29.143]     LinBlueMaskSize: 0
[    29.143]     LinBlueFieldPosition: 0
[    29.143]     LinRsvdMaskSize: 0
[    29.143]     LinRsvdFieldPosition: 0
[    29.143]     MaxPixelClock: 0
[    29.143] 
[    29.143] (II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
[    29.143] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    29.143] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    29.143] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    29.143] (WW) VESA(0): Unable to estimate virtual size
[    29.143] (II) VESA(0): Not using built-in mode "1280x768" (no mode of this name)
[    29.143] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    29.143] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    29.143] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    29.143] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    29.143] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    29.143] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    29.143] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    29.143] (WW) VESA(0): Unable to estimate virtual size
[    29.143] (II) VESA(0): Not using built-in mode "1280x768" (hsync out of range)
[    29.143] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    29.143] (**) VESA(0): *Built-in mode "1024x768"
[    29.143] (**) VESA(0): *Built-in mode "800x600"
[    29.144] (**) VESA(0): *Built-in mode "640x480"
[    29.144] (==) VESA(0): DPI set to (96, 96)
[    29.144] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    29.144] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    29.144] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    29.144] (**) VESA(0): Using "Shadow Framebuffer"
[    29.144] (II) Loading sub module "shadow"
[    29.144] (II) LoadModule: "shadow"
[    29.144] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    29.144] (II) Module shadow: vendor="X.Org Foundation"
[    29.144]     compiled for 1.11.3, module version = 1.1.0
[    29.144]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.144] (II) Loading sub module "fb"
[    29.144] (II) LoadModule: "fb"
[    29.145] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.145] (II) Module fb: vendor="X.Org Foundation"
[    29.145]     compiled for 1.11.3, module version = 1.0.0
[    29.145]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.145] (II) UnloadModule: "sis"
[    29.145] (II) Unloading sis
[    29.145] (II) UnloadModule: "fbdev"
[    29.145] (II) Unloading fbdev
[    29.145] (II) UnloadModule: "fbdevhw"
[    29.145] (II) Unloading fbdevhw
[    29.145] (==) Depth 24 pixmap format is 32 bpp
[    29.145] (II) Loading sub module "int10"
[    29.145] (II) LoadModule: "int10"
[    29.145] (II) Loading /usr/lib/xorg/modules/libint10.so
[    29.145] (II) Module int10: vendor="X.Org Foundation"
[    29.145]     compiled for 1.11.3, module version = 1.0.0
[    29.145]     ABI class: X.Org Video Driver, version 11.0
[    29.145] (II) VESA(0): initializing int10
[    29.150] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    29.152] (II) VESA(0): VESA BIOS detected
[    29.152] (II) VESA(0): VESA VBE Version 3.0
[    29.152] (II) VESA(0): VESA VBE Total Mem: 262144 kB
[    29.152] (II) VESA(0): VESA VBE OEM: SiS
[    29.152] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    29.152] (II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    29.152] (II) VESA(0): VESA VBE OEM Product: 6330
[    29.152] (II) VESA(0): VESA VBE OEM Product Rev: 3.74.10A
[    29.185] (II) VESA(0): virtual address = 0xa6d96000,
    physical address = 0xc0000000, size = 268435456
[    29.195] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    29.286] (==) VESA(0): Default visual is TrueColor
[    29.286] (==) VESA(0): Backing store disabled
[    29.286] (==) VESA(0): DPMS enabled
[    29.286] (==) RandR enabled
[    29.287] (II) Initializing built-in extension Generic Event Extension
[    29.287] (II) Initializing built-in extension SHAPE
[    29.287] (II) Initializing built-in extension MIT-SHM
[    29.287] (II) Initializing built-in extension XInputExtension
[    29.287] (II) Initializing built-in extension XTEST
[    29.287] (II) Initializing built-in extension BIG-REQUESTS
[    29.287] (II) Initializing built-in extension SYNC
[    29.287] (II) Initializing built-in extension XKEYBOARD
[    29.287] (II) Initializing built-in extension XC-MISC
[    29.287] (II) Initializing built-in extension SECURITY
[    29.287] (II) Initializing built-in extension XINERAMA
[    29.287] (II) Initializing built-in extension XFIXES
[    29.287] (II) Initializing built-in extension RENDER
[    29.287] (II) Initializing built-in extension RANDR
[    29.287] (II) Initializing built-in extension COMPOSITE
[    29.287] (II) Initializing built-in extension DAMAGE
[    29.297] (II) AIGLX: Screen 0 is not DRI2 capable
[    29.297] (II) AIGLX: Screen 0 is not DRI capable
[    29.314] (II) AIGLX: Loaded and initialized swrast
[    29.314] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    29.333] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.338] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.338] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.338] (II) LoadModule: "evdev"
[    29.339] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.339] (II) Module evdev: vendor="X.Org Foundation"
[    29.339]     compiled for 1.11.3, module version = 2.7.0
[    29.339]     Module class: X.Org XInput Driver
[    29.339]     ABI class: X.Org XInput driver, version 16.0
[    29.339] (II) Using input driver 'evdev' for 'Power Button'
[    29.339] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.339] (**) Power Button: always reports core events
[    29.339] (**) evdev: Power Button: Device: "/dev/input/event3"
[    29.339] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.339] (--) evdev: Power Button: Found keys
[    29.339] (II) evdev: Power Button: Configuring as keyboard
[    29.339] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    29.339] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.339] (**) Option "xkb_rules" "evdev"
[    29.339] (**) Option "xkb_model" "pc105"
[    29.339] (**) Option "xkb_layout" "de"
[    29.345] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    29.346] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    29.346] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.346] (II) Using input driver 'evdev' for 'Video Bus'
[    29.346] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.346] (**) Video Bus: always reports core events
[    29.346] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    29.346] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.346] (--) evdev: Video Bus: Found keys
[    29.346] (II) evdev: Video Bus: Configuring as keyboard
[    29.346] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input5/event5"
[    29.346] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    29.346] (**) Option "xkb_rules" "evdev"
[    29.346] (**) Option "xkb_model" "pc105"
[    29.346] (**) Option "xkb_layout" "de"
[    29.347] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.348] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.348] (II) Using input driver 'evdev' for 'Power Button'
[    29.348] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.348] (**) Power Button: always reports core events
[    29.348] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.348] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.348] (--) evdev: Power Button: Found keys
[    29.348] (II) evdev: Power Button: Configuring as keyboard
[    29.348] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    29.348] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    29.348] (**) Option "xkb_rules" "evdev"
[    29.348] (**) Option "xkb_model" "pc105"
[    29.348] (**) Option "xkb_layout" "de"
[    29.349] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    29.349] (II) No input driver specified, ignoring this device.
[    29.349] (II) This device may have been added with another device file.
[    29.349] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    29.349] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.349] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.349] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.350] (**) Sleep Button: always reports core events
[    29.350] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    29.350] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    29.350] (--) evdev: Sleep Button: Found keys
[    29.350] (II) evdev: Sleep Button: Configuring as keyboard
[    29.350] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    29.350] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    29.350] (**) Option "xkb_rules" "evdev"
[    29.350] (**) Option "xkb_model" "pc105"
[    29.350] (**) Option "xkb_layout" "de"
[    29.351] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event6)
[    29.351] (II) No input driver specified, ignoring this device.
[    29.351] (II) This device may have been added with another device file.
[    29.351] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event7)
[    29.351] (II) No input driver specified, ignoring this device.
[    29.351] (II) This device may have been added with another device file.
[    29.352] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    29.352] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.352] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.352] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.352] (**) AT Translated Set 2 keyboard: always reports core events
[    29.352] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    29.352] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.352] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.352] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.352] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    29.352] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    29.352] (**) Option "xkb_rules" "evdev"
[    29.352] (**) Option "xkb_model" "pc105"
[    29.352] (**) Option "xkb_layout" "de"
[    29.353] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    29.353] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    29.353] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    29.353] (II) LoadModule: "synaptics"
[    29.354] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.354] (II) Module synaptics: vendor="X.Org Foundation"
[    29.354]     compiled for 1.11.3, module version = 1.6.2
[    29.354]     Module class: X.Org XInput Driver
[    29.354]     ABI class: X.Org XInput driver, version 16.0
[    29.354] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    29.354] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.354] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.354] (**) Option "Device" "/dev/input/event8"
[    29.416] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    29.416] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    29.416] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    29.416] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    29.416] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    29.416] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    29.416] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.416] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.444] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[    29.444] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    29.444] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    29.444] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    29.444] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    29.444] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    29.444] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    29.444] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    29.444] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    29.444] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.445] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    29.445] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    31.263] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    52.208] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    52.935] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    54.325] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    54.367] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    58.446] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[  1612.569] (II) Open ACPI successful (/var/run/acpid.socket)
[  1612.569] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[  1612.680] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1622.284] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[  2643.624] (II) Open ACPI successful (/var/run/acpid.socket)
[  2643.624] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[  2643.735] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  2668.035] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[  3159.618] (II) Open ACPI successful (/var/run/acpid.socket)
[  3159.618] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[  3159.727] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  3169.317] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[  7027.612] (II) Open ACPI successful (/var/run/acpid.socket)
[  7027.612] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[  7027.723] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  7366.880] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[  7588.610] (II) Open ACPI successful (/var/run/acpid.socket)
[  7588.610] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[  7588.722] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  7607.994] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[  7738.590] (II) Open ACPI successful (/var/run/acpid.socket)
[  7738.590] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[  7738.699] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  7776.333] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[ 10010.611] (II) Open ACPI successful (/var/run/acpid.socket)
[ 10010.611] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[ 10010.738] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 10030.515] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[ 10583.580] (II) Open ACPI successful (/var/run/acpid.socket)
[ 10583.580] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[ 10583.690] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 10598.102] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[ 11410.609] (II) Open ACPI successful (/var/run/acpid.socket)
[ 11410.609] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[ 11410.721] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 11428.749] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[ 11981.595] (II) Open ACPI successful (/var/run/acpid.socket)
[ 11981.596] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[ 11981.705] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 12003.001] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[ 17035.582] (II) Open ACPI successful (/var/run/acpid.socket)
[ 17035.582] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[ 17035.692] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 17065.003] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm

```
thank you

---

### Post by lin9 on 2012-11-25
please help

---

### Post by lin9 on 2012-11-26
help please ^^

---

### Post by cwsnyder on 2012-11-27
The only fix I found for the unable to get gamma problem was to change to another video driver, for example from nouveau to proprietary nVidia driver, or to a later driver.  Is this something you can try?

---

### Post by lin9 on 2012-11-30
thank you for help, 
uhhm what do you mean?
install an nvidea driver instead of the sis driver?

which one? do you have a link?


thank you

---

### Post by cwsnyder on 2012-11-30
It looks like the link here: [http://ubuntuforums.org/showpost.php?p=6983046&postcount=119](http://ubuntuforums.org/showpost.php?p=6983046&postcount=119) to a .deb file is the best link for a driver for your sis video system.  I don't know if this is the one installed on your system or not.  This goes back 3 years, but I haven't seen any newer solutions posted where I can google them.

---

### Post by lin9 on 2012-12-01
thank you, 

how do I install it?

---

### Post by ohnonot on 2012-12-01
i had an amilo (fijitsu, too) with a sis onboard card and i remeber there were minor issues with it...

@lin9:
people with more experience than myself have posted here.
you should do the things they ask for before posting, plus detailed description of what you changed, and answer their questions.

anyhow, first things frist:

- i could not find the post/thread you're refering to
- i'm not going to read a log-file with 1000+ lines so i still don't know what graphic card you have exactly. try hardinfo (install with the package manager of your choice) to find what kind of graphic card you have. make searches based on that info.

that said, it seems to me your problems got worse after you renamed yoyr xorg.conf to ...bak - so have you renamed it back? or are you using a different one now?

someone suggested you should replace ```
Driver "sisimedia"
``` with ```
Driver "sis"
``` but you didn't say if you actually tried that.

---

### Post by cwsnyder on 2012-12-01
If you download the file, find it in file manager and double click the file, Gdebi will open and guide you through the installation, I believe.

---

