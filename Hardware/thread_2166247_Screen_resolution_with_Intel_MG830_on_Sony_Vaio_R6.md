---
title: "Screen resolution with Intel MG830 on Sony Vaio R600"
date: 2013-08-08
forum: Hardware
---

### Post by MRNyLph on 2013-08-08
I'm new to Ubuntu but after hearing about it of late thought it would be an ideal way to resurrect an old Sony Vaio R600 laptop (also known as a V505) into something useable again.  This laptop has an Intel 830mg onboard graphics controller.

The DVD drive on it has given up so I ended up installing over the network.  Initially, Ubuntu 12.04 seemed a bit too much for the specs of the computer so reinstalled with Lubuntu.

Lubuntu seems to run quite nicely, except I've never been able to get the screen above 680x480 resolution.  I'm booting with 'nomodeset' from the Grub menu, otherwise I end up with just a black screen, albeit the backlight is still illuminated.

With nomodeset, I'm able to logon but from there cannot change the screen resolution.  I've tried using Xrandr with a nomodeline from cvt and a slightly different one from PowerStrip which I ran on the remaining Windows XP partition.

I've tried adjusting Xorg.conf too without any real success, although did manage to achieve a TTY session opening up in the correct resolution (1024x768), but then when switching back to X it would just go back to 680x480.

I've tried downloading drivers from Intel but that didn't seem to change anything.  It must be 6 weeks now I've been trying to get this sorted, from everything I've found on Google, but without any real progress, so now I'm asking for help, as I'm almost at the point of giving up unfortunately.  Below is the xorg.log, thanks in advance for your assistance.


```
[ 1145.026] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  1145.026] X Protocol Version 11, Revision 0
[  1145.026] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[  1145.026] Current Operating System: Linux SonyR600L 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:21:10 UTC 2013 i686
[  1145.026] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-51-generic root=UUID=f8d913ac-2748-471d-82e8-e918cc5c4261 ro quiet splash nomodeset
[  1145.027] Build Date: 11 April 2013  01:04:30PM
[  1145.027] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1145.027] Current version of pixman: 0.24.4
[  1145.027]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  1145.027] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1145.027] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  8 14:13:35 2013
[  1145.027] (==) Using config file: "/etc/X11/xorg.conf"
[  1145.027] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1145.048] (==) ServerLayout "X.org Configured"
[  1145.048] (**) |-->Screen "Screen0" (0)
[  1145.048] (**) |   |-->Monitor "Monitor0"
[  1145.048] (**) |   |-->Device "Card0"
[  1145.048] (**) |-->Screen "Screen1" (1)
[  1145.048] (**) |   |-->Monitor "Monitor1"
[  1145.049] (**) |   |-->Device "Card1"
[  1145.049] (**) |-->Screen "Screen2" (2)
[  1145.049] (**) |   |-->Monitor "Monitor2"
[  1145.049] (**) |   |-->Device "Card2"
[  1145.049] (**) |-->Screen "Screen3" (3)
[  1145.049] (**) |   |-->Monitor "Monitor3"
[  1145.050] (**) |   |-->Device "Card3"
[  1145.050] (**) |-->Input Device "Mouse0"
[  1145.050] (**) |-->Input Device "Keyboard0"
[  1145.050] (==) Automatically adding devices
[  1145.050] (==) Automatically enabling devices
[  1145.050] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1145.050]     Entry deleted from font path.
[  1145.050] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1145.050]     Entry deleted from font path.
[  1145.050] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1145.050]     Entry deleted from font path.
[  1145.050] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1145.050]     Entry deleted from font path.
[  1145.050] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1145.050]     Entry deleted from font path.
[  1145.050] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  1145.050]     Entry deleted from font path.
[  1145.050] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1145.051]     Entry deleted from font path.
[  1145.051] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1145.051]     Entry deleted from font path.
[  1145.051] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1145.051]     Entry deleted from font path.
[  1145.051] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1145.051]     Entry deleted from font path.
[  1145.051] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1145.051]     Entry deleted from font path.
[  1145.051] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  1145.051]     Entry deleted from font path.
[  1145.051] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  1145.051] (**) ModulePath set to "/usr/lib/xorg/modules"
[  1145.051] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  1145.051] (WW) Disabling Mouse0
[  1145.051] (WW) Disabling Keyboard0
[  1145.051] (II) Loader magic: 0xbcc5a0
[  1145.051] (II) Module ABI versions:
[  1145.051]     X.Org ANSI C Emulation: 0.4
[  1145.051]     X.Org Video Driver: 11.0
[  1145.051]     X.Org XInput driver : 16.0
[  1145.051]     X.Org Server Extension : 6.0
[  1145.052] (--) PCI:*(0:0:2:0) 8086:3577:104d:8100 rev 4, Mem @ 0xe8000000/134217728, 0xe0000000/524288
[  1145.052] (--) PCI: (0:0:2:1) 8086:3577:104d:8100 rev 0, Mem @ 0xf0000000/134217728, 0xe0080000/524288
[  1145.053] (II) Open ACPI successful (/var/run/acpid.socket)
[  1145.053] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[  1145.053] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[  1145.053] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  1145.053] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[  1145.053] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[  1145.053] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[  1145.054] (II) LoadModule: "extmod"
[  1145.054] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1145.054] (II) Module extmod: vendor="X.Org Foundation"
[  1145.054]     compiled for 1.11.3, module version = 1.0.0
[  1145.055]     Module class: X.Org Server Extension
[  1145.055]     ABI class: X.Org Server Extension, version 6.0
[  1145.055] (II) Loading extension MIT-SCREEN-SAVER
[  1145.055] (II) Loading extension XFree86-VidModeExtension
[  1145.055] (II) Loading extension XFree86-DGA
[  1145.055] (II) Loading extension DPMS
[  1145.055] (II) Loading extension XVideo
[  1145.055] (II) Loading extension XVideo-MotionCompensation
[  1145.055] (II) Loading extension X-Resource
[  1145.055] (II) LoadModule: "glx"
[  1145.055] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1145.055] (II) Module glx: vendor="X.Org Foundation"
[  1145.055]     compiled for 1.11.3, module version = 1.0.0
[  1145.055]     ABI class: X.Org Server Extension, version 6.0
[  1145.055] (==) AIGLX enabled
[  1145.055] (II) Loading extension GLX
[  1145.055] (II) LoadModule: "dri"
[  1145.056] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1145.088] (II) Module dri: vendor="X.Org Foundation"
[  1145.088]     compiled for 1.11.3, module version = 1.0.0
[  1145.088]     ABI class: X.Org Server Extension, version 6.0
[  1145.088] (II) Loading extension XFree86-DRI
[  1145.088] (II) LoadModule: "dri2"
[  1145.088] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1145.089] (II) Module dri2: vendor="X.Org Foundation"
[  1145.089]     compiled for 1.11.3, module version = 1.2.0
[  1145.089]     ABI class: X.Org Server Extension, version 6.0
[  1145.089] (II) Loading extension DRI2
[  1145.089] (II) LoadModule: "dbe"
[  1145.089] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1145.089] (II) Module dbe: vendor="X.Org Foundation"
[  1145.089]     compiled for 1.11.3, module version = 1.0.0
[  1145.089]     Module class: X.Org Server Extension
[  1145.089]     ABI class: X.Org Server Extension, version 6.0
[  1145.089] (II) Loading extension DOUBLE-BUFFER
[  1145.089] (II) LoadModule: "record"
[  1145.090] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1145.090] (II) Module record: vendor="X.Org Foundation"
[  1145.090]     compiled for 1.11.3, module version = 1.13.0
[  1145.090]     Module class: X.Org Server Extension
[  1145.090]     ABI class: X.Org Server Extension, version 6.0
[  1145.090] (II) Loading extension RECORD
[  1145.090] (II) LoadModule: "intel"
[  1145.090] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1145.098] (II) Module intel: vendor="X.Org Foundation"
[  1145.098]     compiled for 1.11.3, module version = 2.17.0
[  1145.098]     Module class: X.Org Video Driver
[  1145.098]     ABI class: X.Org Video Driver, version 11.0
[  1145.098] (II) LoadModule: "fbdev"
[  1145.099] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1145.099] (II) Module fbdev: vendor="X.Org Foundation"
[  1145.099]     compiled for 1.11.3, module version = 0.4.2
[  1145.099]     ABI class: X.Org Video Driver, version 11.0
[  1145.099] (II) LoadModule: "vesa"
[  1145.099] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1145.099] (II) Module vesa: vendor="X.Org Foundation"
[  1145.100]     compiled for 1.11.3, module version = 2.3.0
[  1145.100]     Module class: X.Org Video Driver
[  1145.100]     ABI class: X.Org Video Driver, version 11.0
[  1145.100] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[  1145.101] (II) FBDEV: driver for framebuffer: fbdev
[  1145.101] (II) VESA: driver for VESA chipsets: vesa
[  1145.101] (++) using VT number 7


[  1145.110] (II) Loading sub module "fbdevhw"
[  1145.110] (II) LoadModule: "fbdevhw"
[  1145.111] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1145.111] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1145.111]     compiled for 1.11.3, module version = 0.0.2
[  1145.111]     ABI class: X.Org Video Driver, version 11.0
[  1145.111] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1145.111] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1145.111] (EE) open /dev/fb0: No such file or directory
[  1145.111] (WW) Falling back to old probe method for fbdev
[  1145.112] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1145.112] (II) Loading sub module "vbe"
[  1145.112] (II) LoadModule: "vbe"
[  1145.112] (II) Loading /usr/lib/xorg/modules/libvbe.so
[  1145.112] (II) Module vbe: vendor="X.Org Foundation"
[  1145.112]     compiled for 1.11.3, module version = 1.1.0
[  1145.113]     ABI class: X.Org Video Driver, version 11.0
[  1145.113] (II) Loading sub module "int10"
[  1145.113] (II) LoadModule: "int10"
[  1145.113] (II) Loading /usr/lib/xorg/modules/libint10.so
[  1145.113] (II) Module int10: vendor="X.Org Foundation"
[  1145.113]     compiled for 1.11.3, module version = 1.0.0
[  1145.113]     ABI class: X.Org Video Driver, version 11.0
[  1145.113] (II) VESA(1): initializing int10
[  1145.118] (II) VESA(1): Bad V_BIOS checksum
[  1145.119] (II) VESA(1): Primary V_BIOS segment is: 0xc000
[  1145.119] (II) VESA(1): VESA BIOS detected
[  1145.119] (II) VESA(1): VESA VBE Version 3.0
[  1145.119] (II) VESA(1): VESA VBE Total Mem: 832 kB
[  1145.119] (II) VESA(1): VESA VBE OEM: Almador Graphics Chip Accelerated VGA BIOS
[  1145.119] (II) VESA(1): VESA VBE OEM Software Rev: 1.0
[  1145.119] (II) VESA(1): VESA VBE OEM Vendor: Intel Corporation
[  1145.119] (II) VESA(1): VESA VBE OEM Product: Almador Graphics Controller
[  1145.119] (II) VESA(1): VESA VBE OEM Product Rev: Hardware Version 0.0
[  1145.145] (==) VESA(1): Depth 16, (--) framebuffer bpp 16
[  1145.146] (==) VESA(1): RGB weight 565
[  1145.146] (==) VESA(1): Default visual is TrueColor
[  1145.146] (==) VESA(1): Using gamma correction (1.0, 1.0, 1.0)
[  1145.146] (II) Loading sub module "ddc"
[  1145.146] (II) LoadModule: "ddc"
[  1145.146] (II) Module "ddc" already built-in
[  1145.197] (II) VESA(1): VESA VBE DDC supported
[  1145.197] (II) VESA(1): VESA VBE DDC Level none
[  1145.197] (II) VESA(1): VESA VBE DDC transfer in appr. 0 sec.
[  1145.247] (II) VESA(1): VESA VBE DDC read failed
[  1145.247] (II) VESA(1): VESA VBE PanelID read successfully
[  1145.247] (II) VESA(1): PanelID returned panel resolution 1024x768
[  1145.247] (II) VESA(1): Searching for matching VESA mode(s):
[  1145.249] Mode: 107 (1280x1024)
[  1145.249]     ModeAttributes: 0x9a
[  1145.249]     WinAAttributes: 0x7
[  1145.249]     WinBAttributes: 0x0
[  1145.249]     WinGranularity: 64
[  1145.249]     WinSize: 64
[  1145.250]     WinASegment: 0xa000
[  1145.250]     WinBSegment: 0x0
[  1145.250]     WinFuncPtr: 0xc0006175
[  1145.250]     BytesPerScanline: 1280
[  1145.250]     XResolution: 1280
[  1145.250]     YResolution: 1024
[  1145.250]     XCharSize: 8
[  1145.250]     YCharSize: 16
[  1145.250]     NumberOfPlanes: 1
[  1145.250]     BitsPerPixel: 8
[  1145.250]     NumberOfBanks: 1
[  1145.250]     MemoryModel: 4
[  1145.250]     BankSize: 0
[  1145.250]     NumberOfImages: 0
[  1145.250]     RedMaskSize: 0
[  1145.250]     RedFieldPosition: 0
[  1145.250]     GreenMaskSize: 0
[  1145.250]     GreenFieldPosition: 0
[  1145.250]     BlueMaskSize: 0
[  1145.250]     BlueFieldPosition: 0
[  1145.250]     RsvdMaskSize: 0
[  1145.250]     RsvdFieldPosition: 0
[  1145.250]     DirectColorModeInfo: 0
[  1145.250]     PhysBasePtr: 0xe8000000
[  1145.250]     LinBytesPerScanLine: 1280
[  1145.250]     BnkNumberOfImagePages: 0
[  1145.250]     LinNumberOfImagePages: 0
[  1145.250]     LinRedMaskSize: 0
[  1145.250]     LinRedFieldPosition: 0
[  1145.251]     LinGreenMaskSize: 0
[  1145.251]     LinGreenFieldPosition: 0
[  1145.251]     LinBlueMaskSize: 0
[  1145.251]     LinBlueFieldPosition: 0
[  1145.251]     LinRsvdMaskSize: 0
[  1145.251]     LinRsvdFieldPosition: 0
[  1145.251]     MaxPixelClock: 230000000
[  1145.253] Mode: 112 (640x480)
[  1145.253]     ModeAttributes: 0x9a
[  1145.253]     WinAAttributes: 0x7
[  1145.253]     WinBAttributes: 0x0
[  1145.253]     WinGranularity: 64
[  1145.253]     WinSize: 64
[  1145.253]     WinASegment: 0xa000
[  1145.253]     WinBSegment: 0x0
[  1145.253]     WinFuncPtr: 0xc0006175
[  1145.253]     BytesPerScanline: 2560
[  1145.253]     XResolution: 640
[  1145.253]     YResolution: 480
[  1145.254]     XCharSize: 8
[  1145.254]     YCharSize: 16
[  1145.254]     NumberOfPlanes: 1
[  1145.254]     BitsPerPixel: 32
[  1145.254]     NumberOfBanks: 1
[  1145.254]     MemoryModel: 6
[  1145.254]     BankSize: 0
[  1145.254]     NumberOfImages: 0
[  1145.254]     RedMaskSize: 8
[  1145.254]     RedFieldPosition: 16
[  1145.254]     GreenMaskSize: 8
[  1145.254]     GreenFieldPosition: 8
[  1145.254]     BlueMaskSize: 8
[  1145.254]     BlueFieldPosition: 0
[  1145.254]     RsvdMaskSize: 8
[  1145.254]     RsvdFieldPosition: 24
[  1145.254]     DirectColorModeInfo: 0
[  1145.254]     PhysBasePtr: 0xe8000000
[  1145.254]     LinBytesPerScanLine: 2560
[  1145.254]     BnkNumberOfImagePages: 0
[  1145.254]     LinNumberOfImagePages: 0
[  1145.254]     LinRedMaskSize: 8
[  1145.254]     LinRedFieldPosition: 16
[  1145.254]     LinGreenMaskSize: 8
[  1145.254]     LinGreenFieldPosition: 8
[  1145.254]     LinBlueMaskSize: 8
[  1145.254]     LinBlueFieldPosition: 0
[  1145.254]     LinRsvdMaskSize: 8
[  1145.254]     LinRsvdFieldPosition: 24
[  1145.254]     MaxPixelClock: 230000000
[  1145.257] Mode: 115 (800x600)
[  1145.257]     ModeAttributes: 0x9a
[  1145.257]     WinAAttributes: 0x7
[  1145.257]     WinBAttributes: 0x0
[  1145.257]     WinGranularity: 64
[  1145.257]     WinSize: 64
[  1145.257]     WinASegment: 0xa000
[  1145.257]     WinBSegment: 0x0
[  1145.257]     WinFuncPtr: 0xc0006175
[  1145.257]     BytesPerScanline: 3200
[  1145.257]     XResolution: 800
[  1145.257]     YResolution: 600
[  1145.257]     XCharSize: 8
[  1145.257]     YCharSize: 16
[  1145.257]     NumberOfPlanes: 1
[  1145.257]     BitsPerPixel: 32
[  1145.257]     NumberOfBanks: 1
[  1145.257]     MemoryModel: 6
[  1145.258]     BankSize: 0
[  1145.258]     NumberOfImages: 0
[  1145.258]     RedMaskSize: 8
[  1145.258]     RedFieldPosition: 16
[  1145.258]     GreenMaskSize: 8
[  1145.258]     GreenFieldPosition: 8
[  1145.258]     BlueMaskSize: 8
[  1145.258]     BlueFieldPosition: 0
[  1145.258]     RsvdMaskSize: 8
[  1145.258]     RsvdFieldPosition: 24
[  1145.258]     DirectColorModeInfo: 0
[  1145.258]     PhysBasePtr: 0xe8000000
[  1145.258]     LinBytesPerScanLine: 3200
[  1145.258]     BnkNumberOfImagePages: 0
[  1145.258]     LinNumberOfImagePages: 0
[  1145.258]     LinRedMaskSize: 8
[  1145.258]     LinRedFieldPosition: 16
[  1145.258]     LinGreenMaskSize: 8
[  1145.258]     LinGreenFieldPosition: 8
[  1145.258]     LinBlueMaskSize: 8
[  1145.258]     LinBlueFieldPosition: 0
[  1145.258]     LinRsvdMaskSize: 8
[  1145.258]     LinRsvdFieldPosition: 24
[  1145.258]     MaxPixelClock: 230000000
[  1145.260] Mode: 116 (1024x768)
[  1145.260]     ModeAttributes: 0x9a
[  1145.261]     WinAAttributes: 0x7
[  1145.261]     WinBAttributes: 0x0
[  1145.261]     WinGranularity: 64
[  1145.261]     WinSize: 64
[  1145.261]     WinASegment: 0xa000
[  1145.261]     WinBSegment: 0x0
[  1145.261]     WinFuncPtr: 0xc0006175
[  1145.261]     BytesPerScanline: 2048
[  1145.261]     XResolution: 1024
[  1145.261]     YResolution: 768
[  1145.261]     XCharSize: 8
[  1145.261]     YCharSize: 16
[  1145.261]     NumberOfPlanes: 1
[  1145.261]     BitsPerPixel: 15
[  1145.261]     NumberOfBanks: 1
[  1145.261]     MemoryModel: 6
[  1145.261]     BankSize: 0
[  1145.261]     NumberOfImages: 0
[  1145.261]     RedMaskSize: 5
[  1145.261]     RedFieldPosition: 10
[  1145.261]     GreenMaskSize: 5
[  1145.261]     GreenFieldPosition: 5
[  1145.261]     BlueMaskSize: 5
[  1145.261]     BlueFieldPosition: 0
[  1145.261]     RsvdMaskSize: 0
[  1145.261]     RsvdFieldPosition: 0
[  1145.261]     DirectColorModeInfo: 0
[  1145.261]     PhysBasePtr: 0xe8000000
[  1145.261]     LinBytesPerScanLine: 2048
[  1145.262]     BnkNumberOfImagePages: 0
[  1145.262]     LinNumberOfImagePages: 0
[  1145.262]     LinRedMaskSize: 5
[  1145.262]     LinRedFieldPosition: 10
[  1145.262]     LinGreenMaskSize: 5
[  1145.262]     LinGreenFieldPosition: 5
[  1145.262]     LinBlueMaskSize: 5
[  1145.262]     LinBlueFieldPosition: 0
[  1145.262]     LinRsvdMaskSize: 0
[  1145.262]     LinRsvdFieldPosition: 0
[  1145.262]     MaxPixelClock: 230000000
[  1145.264] Mode: 117 (1024x768)
[  1145.264]     ModeAttributes: 0x9a
[  1145.264]     WinAAttributes: 0x7
[  1145.264]     WinBAttributes: 0x0
[  1145.264]     WinGranularity: 64
[  1145.264]     WinSize: 64
[  1145.264]     WinASegment: 0xa000
[  1145.264]     WinBSegment: 0x0
[  1145.264]     WinFuncPtr: 0xc0006175
[  1145.264]     BytesPerScanline: 2048
[  1145.264]     XResolution: 1024
[  1145.264]     YResolution: 768
[  1145.264]     XCharSize: 8
[  1145.265]     YCharSize: 16
[  1145.265]     NumberOfPlanes: 1
[  1145.265]     BitsPerPixel: 16
[  1145.265]     NumberOfBanks: 1
[  1145.265]     MemoryModel: 6
[  1145.265]     BankSize: 0
[  1145.265]     NumberOfImages: 0
[  1145.265]     RedMaskSize: 5
[  1145.265]     RedFieldPosition: 11
[  1145.265]     GreenMaskSize: 6
[  1145.265]     GreenFieldPosition: 5
[  1145.265]     BlueMaskSize: 5
[  1145.265]     BlueFieldPosition: 0
[  1145.265]     RsvdMaskSize: 0
[  1145.265]     RsvdFieldPosition: 0
[  1145.265]     DirectColorModeInfo: 0
[  1145.265]     PhysBasePtr: 0xe8000000
[  1145.265]     LinBytesPerScanLine: 2048
[  1145.265]     BnkNumberOfImagePages: 0
[  1145.265]     LinNumberOfImagePages: 0
[  1145.265]     LinRedMaskSize: 5
[  1145.265]     LinRedFieldPosition: 11
[  1145.265]     LinGreenMaskSize: 6
[  1145.265]     LinGreenFieldPosition: 5
[  1145.265]     LinBlueMaskSize: 5
[  1145.265]     LinBlueFieldPosition: 0
[  1145.265]     LinRsvdMaskSize: 0
[  1145.265]     LinRsvdFieldPosition: 0
[  1145.265]     MaxPixelClock: 230000000
[  1145.268] Mode: 118 (1024x768)
[  1145.268]     ModeAttributes: 0x9a
[  1145.268]     WinAAttributes: 0x7
[  1145.268]     WinBAttributes: 0x0
[  1145.268]     WinGranularity: 64
[  1145.268]     WinSize: 64
[  1145.268]     WinASegment: 0xa000
[  1145.268]     WinBSegment: 0x0
[  1145.268]     WinFuncPtr: 0xc0006175
[  1145.268]     BytesPerScanline: 4096
[  1145.268]     XResolution: 1024
[  1145.268]     YResolution: 768
[  1145.268]     XCharSize: 8
[  1145.268]     YCharSize: 16
[  1145.268]     NumberOfPlanes: 1
[  1145.268]     BitsPerPixel: 32
[  1145.269]     NumberOfBanks: 1
[  1145.269]     MemoryModel: 6
[  1145.269]     BankSize: 0
[  1145.269]     NumberOfImages: 0
[  1145.269]     RedMaskSize: 8
[  1145.269]     RedFieldPosition: 16
[  1145.269]     GreenMaskSize: 8
[  1145.269]     GreenFieldPosition: 8
[  1145.269]     BlueMaskSize: 8
[  1145.269]     BlueFieldPosition: 0
[  1145.269]     RsvdMaskSize: 8
[  1145.269]     RsvdFieldPosition: 24
[  1145.269]     DirectColorModeInfo: 0
[  1145.269]     PhysBasePtr: 0xe8000000
[  1145.269]     LinBytesPerScanLine: 4096
[  1145.269]     BnkNumberOfImagePages: 0
[  1145.269]     LinNumberOfImagePages: 0
[  1145.269]     LinRedMaskSize: 8
[  1145.269]     LinRedFieldPosition: 16
[  1145.269]     LinGreenMaskSize: 8
[  1145.269]     LinGreenFieldPosition: 8
[  1145.269]     LinBlueMaskSize: 8
[  1145.269]     LinBlueFieldPosition: 0
[  1145.269]     LinRsvdMaskSize: 8
[  1145.269]     LinRsvdFieldPosition: 24
[  1145.269]     MaxPixelClock: 230000000
[  1145.272] Mode: 11a (1280x1024)
[  1145.272]     ModeAttributes: 0x9a
[  1145.272]     WinAAttributes: 0x7
[  1145.272]     WinBAttributes: 0x0
[  1145.272]     WinGranularity: 64
[  1145.272]     WinSize: 64
[  1145.272]     WinASegment: 0xa000
[  1145.272]     WinBSegment: 0x0
[  1145.272]     WinFuncPtr: 0xc0006175
[  1145.272]     BytesPerScanline: 2560
[  1145.272]     XResolution: 1280
[  1145.272]     YResolution: 1024
[  1145.272]     XCharSize: 8
[  1145.272]     YCharSize: 16
[  1145.272]     NumberOfPlanes: 1
[  1145.272]     BitsPerPixel: 16
[  1145.272]     NumberOfBanks: 1
[  1145.272]     MemoryModel: 6
[  1145.272]     BankSize: 0
[  1145.272]     NumberOfImages: 0
[  1145.272]     RedMaskSize: 5
[  1145.272]     RedFieldPosition: 11
[  1145.272]     GreenMaskSize: 6
[  1145.272]     GreenFieldPosition: 5
[  1145.272]     BlueMaskSize: 5
[  1145.272]     BlueFieldPosition: 0
[  1145.272]     RsvdMaskSize: 0
[  1145.272]     RsvdFieldPosition: 0
[  1145.273]     DirectColorModeInfo: 0
[  1145.273]     PhysBasePtr: 0xe8000000
[  1145.273]     LinBytesPerScanLine: 2560
[  1145.273]     BnkNumberOfImagePages: 0
[  1145.273]     LinNumberOfImagePages: 0
[  1145.273]     LinRedMaskSize: 5
[  1145.273]     LinRedFieldPosition: 11
[  1145.273]     LinGreenMaskSize: 6
[  1145.273]     LinGreenFieldPosition: 5
[  1145.273]     LinBlueMaskSize: 5
[  1145.273]     LinBlueFieldPosition: 0
[  1145.273]     LinRsvdMaskSize: 0
[  1145.273]     LinRsvdFieldPosition: 0
[  1145.273]     MaxPixelClock: 230000000
[  1145.276] Mode: 11b (1280x1024)
[  1145.276]     ModeAttributes: 0x9a
[  1145.276]     WinAAttributes: 0x7
[  1145.276]     WinBAttributes: 0x0
[  1145.276]     WinGranularity: 64
[  1145.276]     WinSize: 64
[  1145.276]     WinASegment: 0xa000
[  1145.276]     WinBSegment: 0x0
[  1145.276]     WinFuncPtr: 0xc0006175
[  1145.276]     BytesPerScanline: 5120
[  1145.276]     XResolution: 1280
[  1145.276]     YResolution: 1024
[  1145.276]     XCharSize: 8
[  1145.276]     YCharSize: 16
[  1145.276]     NumberOfPlanes: 1
[  1145.276]     BitsPerPixel: 32
[  1145.276]     NumberOfBanks: 1
[  1145.276]     MemoryModel: 6
[  1145.276]     BankSize: 0
[  1145.276]     NumberOfImages: 0
[  1145.276]     RedMaskSize: 8
[  1145.276]     RedFieldPosition: 16
[  1145.276]     GreenMaskSize: 8
[  1145.276]     GreenFieldPosition: 8
[  1145.276]     BlueMaskSize: 8
[  1145.276]     BlueFieldPosition: 0
[  1145.276]     RsvdMaskSize: 8
[  1145.276]     RsvdFieldPosition: 24
[  1145.276]     DirectColorModeInfo: 0
[  1145.277]     PhysBasePtr: 0xe8000000
[  1145.277]     LinBytesPerScanLine: 5120
[  1145.277]     BnkNumberOfImagePages: 0
[  1145.277]     LinNumberOfImagePages: 0
[  1145.277]     LinRedMaskSize: 8
[  1145.277]     LinRedFieldPosition: 16
[  1145.277]     LinGreenMaskSize: 8
[  1145.277]     LinGreenFieldPosition: 8
[  1145.277]     LinBlueMaskSize: 8
[  1145.277]     LinBlueFieldPosition: 0
[  1145.277]     LinRsvdMaskSize: 8
[  1145.277]     LinRsvdFieldPosition: 24
[  1145.277]     MaxPixelClock: 230000000
[  1145.279] Mode: 101 (640x480)
[  1145.279]     ModeAttributes: 0x9b
[  1145.279]     WinAAttributes: 0x7
[  1145.279]     WinBAttributes: 0x0
[  1145.279]     WinGranularity: 64
[  1145.279]     WinSize: 64
[  1145.279]     WinASegment: 0xa000
[  1145.279]     WinBSegment: 0x0
[  1145.279]     WinFuncPtr: 0xc0006175
[  1145.279]     BytesPerScanline: 640
[  1145.279]     XResolution: 640
[  1145.279]     YResolution: 480
[  1145.279]     XCharSize: 8
[  1145.279]     YCharSize: 16
[  1145.279]     NumberOfPlanes: 1
[  1145.279]     BitsPerPixel: 8
[  1145.279]     NumberOfBanks: 1
[  1145.279]     MemoryModel: 4
[  1145.279]     BankSize: 0
[  1145.279]     NumberOfImages: 1
[  1145.279]     RedMaskSize: 0
[  1145.279]     RedFieldPosition: 0
[  1145.279]     GreenMaskSize: 0
[  1145.280]     GreenFieldPosition: 0
[  1145.280]     BlueMaskSize: 0
[  1145.280]     BlueFieldPosition: 0
[  1145.280]     RsvdMaskSize: 0
[  1145.280]     RsvdFieldPosition: 0
[  1145.280]     DirectColorModeInfo: 0
[  1145.280]     PhysBasePtr: 0xe8000000
[  1145.280]     LinBytesPerScanLine: 640
[  1145.280]     BnkNumberOfImagePages: 1
[  1145.280]     LinNumberOfImagePages: 1
[  1145.280]     LinRedMaskSize: 0
[  1145.280]     LinRedFieldPosition: 0
[  1145.280]     LinGreenMaskSize: 0
[  1145.280]     LinGreenFieldPosition: 0
[  1145.280]     LinBlueMaskSize: 0
[  1145.280]     LinBlueFieldPosition: 0
[  1145.280]     LinRsvdMaskSize: 0
[  1145.280]     LinRsvdFieldPosition: 0
[  1145.280]     MaxPixelClock: 230000000
[  1145.282] Mode: 103 (800x600)
[  1145.282]     ModeAttributes: 0x9b
[  1145.282]     WinAAttributes: 0x7
[  1145.282]     WinBAttributes: 0x0
[  1145.282]     WinGranularity: 64
[  1145.282]     WinSize: 64
[  1145.282]     WinASegment: 0xa000
[  1145.282]     WinBSegment: 0x0
[  1145.282]     WinFuncPtr: 0xc0006175
[  1145.282]     BytesPerScanline: 800
[  1145.283]     XResolution: 800
[  1145.283]     YResolution: 600
[  1145.283]     XCharSize: 8
[  1145.283]     YCharSize: 16
[  1145.283]     NumberOfPlanes: 1
[  1145.283]     BitsPerPixel: 8
[  1145.283]     NumberOfBanks: 1
[  1145.283]     MemoryModel: 4
[  1145.283]     BankSize: 0
[  1145.283]     NumberOfImages: 0
[  1145.283]     RedMaskSize: 0
[  1145.283]     RedFieldPosition: 0
[  1145.283]     GreenMaskSize: 0
[  1145.283]     GreenFieldPosition: 0
[  1145.283]     BlueMaskSize: 0
[  1145.283]     BlueFieldPosition: 0
[  1145.283]     RsvdMaskSize: 0
[  1145.283]     RsvdFieldPosition: 0
[  1145.283]     DirectColorModeInfo: 0
[  1145.283]     PhysBasePtr: 0xe8000000
[  1145.283]     LinBytesPerScanLine: 800
[  1145.283]     BnkNumberOfImagePages: 0
[  1145.283]     LinNumberOfImagePages: 0
[  1145.283]     LinRedMaskSize: 0
[  1145.283]     LinRedFieldPosition: 0
[  1145.283]     LinGreenMaskSize: 0
[  1145.283]     LinGreenFieldPosition: 0
[  1145.283]     LinBlueMaskSize: 0
[  1145.283]     LinBlueFieldPosition: 0
[  1145.283]     LinRsvdMaskSize: 0
[  1145.284]     LinRsvdFieldPosition: 0
[  1145.284]     MaxPixelClock: 230000000
[  1145.285] Mode: 105 (1024x768)
[  1145.285]     ModeAttributes: 0x9b
[  1145.285]     WinAAttributes: 0x7
[  1145.286]     WinBAttributes: 0x0
[  1145.286]     WinGranularity: 64
[  1145.286]     WinSize: 64
[  1145.286]     WinASegment: 0xa000
[  1145.286]     WinBSegment: 0x0
[  1145.286]     WinFuncPtr: 0xc0006175
[  1145.286]     BytesPerScanline: 1024
[  1145.286]     XResolution: 1024
[  1145.286]     YResolution: 768
[  1145.286]     XCharSize: 8
[  1145.286]     YCharSize: 16
[  1145.286]     NumberOfPlanes: 1
[  1145.286]     BitsPerPixel: 8
[  1145.286]     NumberOfBanks: 1
[  1145.286]     MemoryModel: 4
[  1145.286]     BankSize: 0
[  1145.286]     NumberOfImages: 0
[  1145.286]     RedMaskSize: 0
[  1145.286]     RedFieldPosition: 0
[  1145.286]     GreenMaskSize: 0
[  1145.286]     GreenFieldPosition: 0
[  1145.286]     BlueMaskSize: 0
[  1145.286]     BlueFieldPosition: 0
[  1145.286]     RsvdMaskSize: 0
[  1145.286]     RsvdFieldPosition: 0
[  1145.286]     DirectColorModeInfo: 0
[  1145.286]     PhysBasePtr: 0xe8000000
[  1145.286]     LinBytesPerScanLine: 1024
[  1145.286]     BnkNumberOfImagePages: 0
[  1145.286]     LinNumberOfImagePages: 0
[  1145.287]     LinRedMaskSize: 0
[  1145.287]     LinRedFieldPosition: 0
[  1145.287]     LinGreenMaskSize: 0
[  1145.287]     LinGreenFieldPosition: 0
[  1145.287]     LinBlueMaskSize: 0
[  1145.287]     LinBlueFieldPosition: 0
[  1145.287]     LinRsvdMaskSize: 0
[  1145.287]     LinRsvdFieldPosition: 0
[  1145.287]     MaxPixelClock: 230000000
[  1145.289] *Mode: 111 (640x480)
[  1145.289]     ModeAttributes: 0x9b
[  1145.289]     WinAAttributes: 0x7
[  1145.289]     WinBAttributes: 0x0
[  1145.289]     WinGranularity: 64
[  1145.289]     WinSize: 64
[  1145.289]     WinASegment: 0xa000
[  1145.289]     WinBSegment: 0x0
[  1145.289]     WinFuncPtr: 0xc0006175
[  1145.289]     BytesPerScanline: 1280
[  1145.289]     XResolution: 640
[  1145.289]     YResolution: 480
[  1145.289]     XCharSize: 8
[  1145.289]     YCharSize: 16
[  1145.289]     NumberOfPlanes: 1
[  1145.289]     BitsPerPixel: 16
[  1145.289]     NumberOfBanks: 1
[  1145.290]     MemoryModel: 6
[  1145.290]     BankSize: 0
[  1145.290]     NumberOfImages: 0
[  1145.290]     RedMaskSize: 5
[  1145.290]     RedFieldPosition: 11
[  1145.290]     GreenMaskSize: 6
[  1145.290]     GreenFieldPosition: 5
[  1145.290]     BlueMaskSize: 5
[  1145.290]     BlueFieldPosition: 0
[  1145.290]     RsvdMaskSize: 0
[  1145.290]     RsvdFieldPosition: 0
[  1145.290]     DirectColorModeInfo: 0
[  1145.290]     PhysBasePtr: 0xe8000000
[  1145.290]     LinBytesPerScanLine: 1280
[  1145.290]     BnkNumberOfImagePages: 0
[  1145.290]     LinNumberOfImagePages: 0
[  1145.290]     LinRedMaskSize: 5
[  1145.290]     LinRedFieldPosition: 11
[  1145.290]     LinGreenMaskSize: 6
[  1145.290]     LinGreenFieldPosition: 5
[  1145.290]     LinBlueMaskSize: 5
[  1145.290]     LinBlueFieldPosition: 0
[  1145.290]     LinRsvdMaskSize: 0
[  1145.290]     LinRsvdFieldPosition: 0
[  1145.290]     MaxPixelClock: 230000000
[  1145.292] Mode: 114 (800x600)
[  1145.292]     ModeAttributes: 0x9a
[  1145.292]     WinAAttributes: 0x7
[  1145.293]     WinBAttributes: 0x0
[  1145.293]     WinGranularity: 64
[  1145.293]     WinSize: 64
[  1145.293]     WinASegment: 0xa000
[  1145.293]     WinBSegment: 0x0
[  1145.293]     WinFuncPtr: 0xc0006175
[  1145.293]     BytesPerScanline: 1600
[  1145.293]     XResolution: 800
[  1145.293]     YResolution: 600
[  1145.293]     XCharSize: 8
[  1145.293]     YCharSize: 16
[  1145.293]     NumberOfPlanes: 1
[  1145.293]     BitsPerPixel: 16
[  1145.293]     NumberOfBanks: 1
[  1145.293]     MemoryModel: 6
[  1145.293]     BankSize: 0
[  1145.293]     NumberOfImages: 0
[  1145.293]     RedMaskSize: 5
[  1145.293]     RedFieldPosition: 11
[  1145.293]     GreenMaskSize: 6
[  1145.293]     GreenFieldPosition: 5
[  1145.293]     BlueMaskSize: 5
[  1145.293]     BlueFieldPosition: 0
[  1145.293]     RsvdMaskSize: 0
[  1145.293]     RsvdFieldPosition: 0
[  1145.293]     DirectColorModeInfo: 0
[  1145.293]     PhysBasePtr: 0xe8000000
[  1145.293]     LinBytesPerScanLine: 1600
[  1145.293]     BnkNumberOfImagePages: 0
[  1145.293]     LinNumberOfImagePages: 0
[  1145.294]     LinRedMaskSize: 5
[  1145.294]     LinRedFieldPosition: 11
[  1145.294]     LinGreenMaskSize: 6
[  1145.294]     LinGreenFieldPosition: 5
[  1145.294]     LinBlueMaskSize: 5
[  1145.294]     LinBlueFieldPosition: 0
[  1145.294]     LinRsvdMaskSize: 0
[  1145.294]     LinRsvdFieldPosition: 0
[  1145.294]     MaxPixelClock: 230000000
[  1145.294] 
[  1145.294] (II) VESA(1): Total Memory: 13 64KB banks (832kB)
[  1145.294] (II) VESA(1): Monitor3: Using hsync range of 29.37-47.30 kHz
[  1145.294] (II) VESA(1): Monitor3: Using vrefresh range of 56.00-59.87 Hz
[  1145.294] (WW) VESA(1): Unable to estimate virtual size
[  1145.294] (II) VESA(1): Not using built-in mode "640x480" (no mode of this name)
[  1145.294] (WW) VESA(1): No valid modes left. Trying less strict filter...
[  1145.294] (II) VESA(1): Monitor3: Using hsync range of 29.37-47.30 kHz
[  1145.294] (II) VESA(1): Monitor3: Using vrefresh range of 56.00-59.87 Hz
[  1145.294] (WW) VESA(1): Unable to estimate virtual size
[  1145.294] (--) VESA(1): Virtual size is 640x480 (pitch 640)
[  1145.294] (**) VESA(1): *Built-in mode "640x480"
[  1145.295] (==) VESA(1): DPI set to (96, 96)
[  1145.295] (II) VESA(1): Attempting to use 60Hz refresh for mode "640x480" (111)
[  1145.295] (**) VESA(1): Using "Shadow Framebuffer"
[  1145.295] (II) Loading sub module "shadow"
[  1145.295] (II) LoadModule: "shadow"
[  1145.296] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  1145.296] (II) Module shadow: vendor="X.Org Foundation"
[  1145.296]     compiled for 1.11.3, module version = 1.1.0
[  1145.296]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1145.296] (II) Loading sub module "fb"
[  1145.296] (II) LoadModule: "fb"
[  1145.297] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1145.297] (II) Module fb: vendor="X.Org Foundation"
[  1145.297]     compiled for 1.11.3, module version = 1.0.0
[  1145.297]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1145.297] (II) UnloadModule: "fbdev"
[  1145.298] (II) Unloading fbdev
[  1145.298] (II) UnloadModule: "fbdevhw"
[  1145.298] (II) Unloading fbdevhw
[  1145.298] (II) Loading sub module "int10"
[  1145.298] (II) LoadModule: "int10"
[  1145.298] (II) Loading /usr/lib/xorg/modules/libint10.so
[  1145.298] (II) Module int10: vendor="X.Org Foundation"
[  1145.298]     compiled for 1.11.3, module version = 1.0.0
[  1145.298]     ABI class: X.Org Video Driver, version 11.0
[  1145.298] (II) VESA(0): initializing int10
[  1145.304] (II) VESA(0): Bad V_BIOS checksum
[  1145.304] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[  1145.304] (II) VESA(0): VESA BIOS detected
[  1145.304] (II) VESA(0): VESA VBE Version 3.0
[  1145.304] (II) VESA(0): VESA VBE Total Mem: 832 kB
[  1145.304] (II) VESA(0): VESA VBE OEM: Almador Graphics Chip Accelerated VGA BIOS
[  1145.305] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[  1145.305] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[  1145.305] (II) VESA(0): VESA VBE OEM Product: Almador Graphics Controller
[  1145.305] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[  1145.305] (II) VESA(0): virtual address = 0xb745f000,
    physical address = 0xe8000000, size = 851968
[  1147.261] (II) VESA(0): Setting up VESA Mode 0x111 (640x480)
[  1147.403] (==) VESA(0): Default visual is TrueColor
[  1147.403] (==) VESA(0): Backing store disabled
[  1147.404] (==) VESA(0): DPMS enabled
[  1147.404] (==) RandR enabled
[  1147.404] (II) Initializing built-in extension Generic Event Extension
[  1147.404] (II) Initializing built-in extension SHAPE
[  1147.404] (II) Initializing built-in extension MIT-SHM
[  1147.404] (II) Initializing built-in extension XInputExtension
[  1147.404] (II) Initializing built-in extension XTEST
[  1147.404] (II) Initializing built-in extension BIG-REQUESTS
[  1147.404] (II) Initializing built-in extension SYNC
[  1147.404] (II) Initializing built-in extension XKEYBOARD
[  1147.404] (II) Initializing built-in extension XC-MISC
[  1147.404] (II) Initializing built-in extension SECURITY
[  1147.404] (II) Initializing built-in extension XINERAMA
[  1147.404] (II) Initializing built-in extension XFIXES
[  1147.404] (II) Initializing built-in extension RENDER
[  1147.404] (II) Initializing built-in extension RANDR
[  1147.404] (II) Initializing built-in extension COMPOSITE
[  1147.404] (II) Initializing built-in extension DAMAGE
[  1147.427] (II) AIGLX: Screen 0 is not DRI2 capable
[  1147.427] (II) AIGLX: Screen 0 is not DRI capable
[  1147.492] (II) AIGLX: Loaded and initialized swrast
[  1147.492] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  1147.537] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1147.547] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[  1147.547] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1147.547] (II) LoadModule: "evdev"
[  1147.547] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1147.548] (II) Module evdev: vendor="X.Org Foundation"
[  1147.548]     compiled for 1.11.3, module version = 2.7.0
[  1147.548]     Module class: X.Org XInput Driver
[  1147.548]     ABI class: X.Org XInput driver, version 16.0
[  1147.548] (II) Using input driver 'evdev' for 'Video Bus'
[  1147.548] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1147.548] (**) Video Bus: always reports core events
[  1147.548] (**) evdev: Video Bus: Device: "/dev/input/event3"
[  1147.548] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  1147.548] (--) evdev: Video Bus: Found keys
[  1147.548] (II) evdev: Video Bus: Configuring as keyboard
[  1147.548] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input3/event3"
[  1147.548] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[  1147.548] (**) Option "xkb_rules" "evdev"
[  1147.549] (**) Option "xkb_model" "pc105"
[  1147.549] (**) Option "xkb_layout" "gb"
[  1147.549] (**) Option "xkb_variant" "extd"
[  1147.555] (II) XKB: reuse xkmfile /var/lib/xkb/server-75ECC1FC73DAECCA7C11B68297E66B9B8E3B1F31.xkm
[  1147.558] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event4)
[  1147.558] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[  1147.558] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[  1147.558] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1147.558] (**) Sony Vaio Keys: always reports core events
[  1147.558] (**) evdev: Sony Vaio Keys: Device: "/dev/input/event4"
[  1147.558] (--) evdev: Sony Vaio Keys: Vendor 0x104d Product 0
[  1147.558] (--) evdev: Sony Vaio Keys: Found keys
[  1147.559] (II) evdev: Sony Vaio Keys: Configuring as keyboard
[  1147.559] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:09/SNY6001:00/input/input4/event4"
[  1147.559] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD, id 7)
[  1147.559] (**) Option "xkb_rules" "evdev"
[  1147.559] (**) Option "xkb_model" "pc105"
[  1147.559] (**) Option "xkb_layout" "gb"
[  1147.559] (**) Option "xkb_variant" "extd"
[  1147.560] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1147.561] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1147.561] (II) Using input driver 'evdev' for 'Power Button'
[  1147.561] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1147.561] (**) Power Button: always reports core events
[  1147.561] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1147.561] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1147.561] (--) evdev: Power Button: Found keys
[  1147.561] (II) evdev: Power Button: Configuring as keyboard
[  1147.561] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[  1147.561] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[  1147.561] (**) Option "xkb_rules" "evdev"
[  1147.561] (**) Option "xkb_model" "pc105"
[  1147.561] (**) Option "xkb_layout" "gb"
[  1147.561] (**) Option "xkb_variant" "extd"
[  1147.563] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  1147.563] (II) No input driver specified, ignoring this device.
[  1147.563] (II) This device may have been added with another device file.
[  1147.564] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1147.564] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1147.564] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1147.564] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1147.564] (**) AT Translated Set 2 keyboard: always reports core events
[  1147.564] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1147.564] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1147.564] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1147.564] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1147.564] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  1147.564] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[  1147.564] (**) Option "xkb_rules" "evdev"
[  1147.564] (**) Option "xkb_model" "pc105"
[  1147.564] (**) Option "xkb_layout" "gb"
[  1147.564] (**) Option "xkb_variant" "extd"
[  1147.566] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
[  1147.566] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[  1147.566] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[  1147.566] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1147.566] (**) PS/2 Mouse: always reports core events
[  1147.566] (**) evdev: PS/2 Mouse: Device: "/dev/input/event6"
[  1147.566] (--) evdev: PS/2 Mouse: Vendor 0x2 Product 0x8
[  1147.566] (--) evdev: PS/2 Mouse: Found 3 mouse buttons
[  1147.566] (--) evdev: PS/2 Mouse: Found relative axes
[  1147.566] (--) evdev: PS/2 Mouse: Found x and y relative axes
[  1147.566] (II) evdev: PS/2 Mouse: Configuring as mouse
[  1147.567] (**) evdev: PS/2 Mouse: YAxisMapping: buttons 4 and 5
[  1147.567] (**) evdev: PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1147.567] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[  1147.567] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE, id 10)
[  1147.567] (II) evdev: PS/2 Mouse: initialized for relative axes.
[  1147.567] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[  1147.567] (**) PS/2 Mouse: (accel) acceleration profile 0
[  1147.567] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[  1147.567] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[  1147.568] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[  1147.568] (II) No input driver specified, ignoring this device.
[  1147.568] (II) This device may have been added with another device file.
[  1147.569] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
[  1147.569] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[  1147.569] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[  1147.569] (II) LoadModule: "synaptics"
[  1147.569] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1147.570] (II) Module synaptics: vendor="X.Org Foundation"
[  1147.570]     compiled for 1.11.3, module version = 1.6.2
[  1147.570]     Module class: X.Org XInput Driver
[  1147.570]     ABI class: X.Org XInput driver, version 16.0
[  1147.570] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[  1147.570] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1147.570] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[  1147.570] (**) Option "Device" "/dev/input/event7"
[  1147.570] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[  1147.570] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[  1147.570] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[  1147.570] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[  1147.570] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[  1147.570] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[  1147.570] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[  1147.570] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[  1147.570] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[  1147.570] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[  1147.570] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 11)
[  1147.571] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[  1147.571] (**) synaptics: AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[  1147.571] (**) synaptics: AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[  1147.571] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[  1147.571] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[  1147.571] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[  1147.571] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[  1147.571] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[  1147.572] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[  1147.572] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[  1147.577] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event5)
[  1147.577] (II) No input driver specified, ignoring this device.
[  1147.577] (II) This device may have been added with another device file.
[  1147.577] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse0)
[  1147.577] (II) No input driver specified, ignoring this device.
[  1147.577] (II) This device may have been added with another device file.

```

---

### Post by gordintoronto on 2013-08-08
Is this Lubuntu 12.04? The latest version of Lubuntu needs more than 512 MB of memory to install properly. (In my experience, the results are a variety of semi-random disasters.)

What video adapter? (Command lspci, look for the line which includes "VGA.")

---

### Post by MRNyLph on 2013-08-09
Thank you for getting back to me. Yes, it is Lubuntu 12.04; the installation seemed to go without incident and Lubuntu runs infinitely better than Windows XP, it's just the screen resolution issue.  I did upgrade it to 512Mb of RAM back in the day from the original 256Mb.

Anyway, here is the LSPCI result:-

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics
 Controller] (rev 04)

Thanks again

---

### Post by gordintoronto on 2013-08-10
I wish I could help you. When I Googled Intel  82830 lubuntu, I got a lot of hits, one of them might be useful to you.

---

### Post by MRNyLph on 2013-08-31
I tried Googling Intel 82830 lubuntu and came up with one page that said the 82830 chipset hasn't been supported since Ubuntu 10.04; so installed version 10.04 and it seems to work really well.  Even though we didn't solve the problem, thanks for the signposting, I'm most obliged.

---

### Post by gordintoronto on 2013-08-31
I'm glad you have a solution, but I'm concerned that you are using a somewhat unsupported version of Ubuntu. Since the server version will be supported until April, 2015, I think you will receive security updates, but no application updates. But I could be wrong.

---

