---
title: "help with VIA driver xorg.conf"
date: 2009-10-31
forum: Hardware
---

### Post by kwagga on 2009-10-31
Hi guys,

Before I installed the via driver, ubuntu 9.10 was working fine, but I wanted composite effects. I installed the driver (As per official instructions) and it added several lines to xorg.conf, now my screen is black. If someone can maybe spot the problem, I would *GREATLY* appreciate it! :)

Xorg.log:
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux kwagga-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=f8508e04-a34d-438f-87b9-3c0d39e9be69 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 31 14:10:45 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(**) |-->Input Device "Mouse"
(**) |-->Input Device "Keyboard"
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
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse
(WW) Disabling Keyboard
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1106:3344:1734:10ae VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] rev 1, Mem @ 0xf0000000/67108864, 0xd1000000/16777216
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "via"
(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 5.74.86
	Module class: X.Org Video Driver
(II) via driver subversion: V86a-50937
(II) via: driver for VIA chipsets: P4M800PRO, CX700, K8M890, P4M890,
	P4M900, VX800, VX855
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "viavideo"
(II) LoadModule: "viavideo"
(WW) Warning, couldn't open module viavideo
(II) UnloadModule: "viavideo"
(EE) VIA: Failed to load module "viavideo" (module does not exist, 0)
(WW) VIA(0):  Couldn't open viavideo
(--) VIA(0): Chipset: "P4M800PRO"
(--) VIA(0): Chipset Rev.: 0
(**) VIA(0): Depth 24, (--) framebuffer bpp 32
(==) VIA(0): RGB weight 888
(==) VIA(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) VIA(0): VESA BIOS detected
(II) VIA(0): VESA VBE Version 3.0
(II) VIA(0): VESA VBE Total Mem: 65536 kB
(II) VIA(0): VESA VBE OEM: VIA P4N800 PRO

(II) VIA(0): VESA VBE OEM Software Rev: 1.0
(II) VIA(0): VESA VBE OEM Vendor: 
(II) VIA(0): VESA VBE OEM Product: 
(II) VIA(0): VESA VBE OEM Product Rev: 
(**) VIA(0): Option "AccelMethod" "EXA"
(**) VIA(0): Using EXA acceleration architecture.
(==) VIA(0): EXA composite acceleration enabled.
(II) VIA(0): MergedFB mode forced off.
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): VGA BIOS Version is = 0.13
(II) VIA(0): VGA BIOS Release Date Is: 2005/10/7
(==) VIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) VIA(0): videoram =  65536k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) VIA(0): I2C bus "I2C bus 1" initialized.
(II) VIA(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(==) VIA(0): DPI set to (96, 96)
(II) VIA(0): Output CRT using monitor section CRT
(**) VIA(0): Option "Enable" "true"
(II) VIA(0): Output DVI using monitor section DVI
(**) VIA(0): Option "Disable" "true"
(II) VIA(0): Output LCD using monitor section LCD
(**) VIA(0): Option "Disable" "true"
(II) VIA(0): Output TV using monitor section TV
(**) VIA(0): Option "Ignore" "true"
(II) VIA(0): Output HDMI using monitor section HDMI
(**) VIA(0): Option "Ignore" "true"
(II) VIA(0): Output CRT-2 using monitor section CRT-2
(**) VIA(0): Option "Ignore" "true"
(EE) VIA(0): Unknown EDID version 255
(EE) VIA(0): Unknown EDID version 0
(II) VIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x960" (hsync out of range)
(II) VIA(0): Not using default mode "1280x960" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) VIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) VIA(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) VIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) VIA(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) VIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) VIA(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) VIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) VIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) VIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "1440x900" (hsync out of range)
(II) VIA(0): Not using default mode "1600x1024" (hsync out of range)
(II) VIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) VIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) VIA(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) VIA(0): Not using default mode "1920x1080" (hsync out of range)
(II) VIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) VIA(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) VIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) VIA(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) VIA(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) VIA(0): Printing probed modes for output CRT
(II) VIA(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) VIA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) VIA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VIA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VIA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VIA(0): Output CRT enabled by config file
(II) VIA(0): Using fuzzy aspect match for initial modes
(II) VIA(0): Output CRT using initial mode 1152x864
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) VIA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VIA(0): [drm] Detect H2 chipset: 0001  chipid: 3344
(II) VIA(0): VIAModeInit
(II) VIA(0): VIASetDisplayPath is DuoView
(WW) VIA(0): Refresh rate setting in xorg.conf is not supported!!
(WW) VIA(0): Driver will try to find another refresh rate instead.
(II) VIA(0): into 3D initial...3Dinitial? 0
(II) VIA(0): H2 3D Engine has been initilized.
(II) VIA(0): VIAWriteMode exit:TVtype=1, TVScan=0
(II) VIA(0): VIAModeInit exit:TVtype=1, TVScan=0
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): EXA manager all the free FB when NO DRI
(**) VIA(0): Option "MigrationHeuristic" "greedy"
(II) EXA(0): Offscreen pixmap area of 59382752 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) VIA(0): Enable EXA Now
(II) VIA(0): [EXA] Trying to enable EXA acceleration.
(==) VIA(0): Backing store disabled
(==) VIA(0): Silken mouse enabled
(II) VIA(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) VIA(0): DPMS enabled
(II) VIA(0): direct rendering disabled
(II) IGA1 timing
HActive=1152, HSyncStart=1216, HSyncEnd=1336, HTotal=1520 
VActive=864, VSyncStart=865, VSyncEnd=868, VTotal=895
(--) RandR disabled
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
(II) VIA(0): Setting screen physical size to 304 x 228
(II) config/hal: Adding input device Video Bus
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event7"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event6"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) PS/2 Mouse: initialized for relative axes.
(EE) VIA(0): Unknown EDID version 0
(EE) VIA(0): Unknown EDID version 0
(II) VIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x960" (hsync out of range)
(II) VIA(0): Not using default mode "1280x960" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Printing probed modes for output CRT
(II) VIA(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) VIA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) VIA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VIA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VIA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(EE) VIA(0): Unknown EDID version 0
(EE) VIA(0): Unknown EDID version 0
(II) VIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x960" (hsync out of range)
(II) VIA(0): Not using default mode "1280x960" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Printing probed modes for output CRT
(II) VIA(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) VIA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) VIA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VIA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VIA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(EE) VIA(0): Unknown EDID version 0
(EE) VIA(0): Unknown EDID version 0
(II) VIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x960" (hsync out of range)
(II) VIA(0): Not using default mode "1280x960" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) VIA(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) VIA(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) VIA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) VIA(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) VIA(0): Printing probed modes for output CRT
(II) VIA(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) VIA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) VIA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VIA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VIA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VIA(0): Hqv0Saved.hqv_ctl:f51f232e
(II) Open ACPI successful (/var/run/acpid.socket)
(II) VIA(0): VIAModeInit
(II) VIA(0): VIASetDisplayPath is DuoView
(WW) VIA(0): Refresh rate setting in xorg.conf is not supported!!
(WW) VIA(0): Driver will try to find another refresh rate instead.
(II) VIA(0): into 3D initial...3Dinitial? 1
drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "via"
(EE) VIA(0): DRM open error 
(II) VIA(0): H2 3D Engine has been initilized.
(II) VIA(0): VIAWriteMode exit:TVtype=1, TVScan=0
(II) VIA(0): VIAModeInit exit:TVtype=1, TVScan=0
(II) IGA1 timing
HActive=1152, HSyncStart=1216, HSyncEnd=1336, HTotal=1520 
VActive=864, VSyncStart=865, VSyncEnd=868, VTotal=895
(II) VIA(0): Hqv0 hqv_ctl:f51f232e
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) Video Bus: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) PS/2 Mouse: Device reopened after 1 attempts.

```

xorg.conf [modified - all I added was Screen, because it was set to "virtual 2000 2000", as well as HorizSync & VertRefresh, it wasn't specified by default.]
```
Section "ServerLayout"
       Identifier	"Default Layout"
       Screen		"Default Screen"
       InputDevice	"Mouse"
       InputDevice	"Keyboard"
EndSection

Section "Files"
#     RgbPath      "/usr/local/share/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc/"
#     FontPath     "/usr/share/fonts/X11/TTF/"
#     FontPath     "/usr/share/fonts/X11/OTF"
#     FontPath     "/usr/share/fonts/X11/Type1/"
#     FontPath     "/usr/share/fonts/X11/100dpi/"
#     FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
       Identifier	"Keyboard"
       Driver		"kbd"
       Option		"XkbRules"	"xorg"
       Option		"XkbModel"	"pc105"
       Option		"XkbLayout"	"cn"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
        HorizSync 30.0 - 81.0
        VertRefresh 56.0 - 76.0
    Option "DPMS"
EndSection


Section "InputDevice"
       Identifier	"Mouse"
       Driver		"mouse"
       Option		"CorePointer"
EndSection

Section "Monitor"
       Identifier	"CRT"
       Option	"Enable"	"true"            
EndSection

Section "Monitor"
       Identifier	"LCD"
       Option	 "Disable"	"true"         
EndSection	

Section "Monitor"
       Identifier	"DVI"
       Option	 "Disable"	"true"
EndSection	

Section "Monitor"
       Identifier	"TV"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"HDMI"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"CRT-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"LCD-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"DVI-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"TV-2"
       Option	  "Ignore"	"true"
EndSection

Section "Device"
	#BusID "PCI:01:00:0"
	Driver 	"via"
	VendorName  	"VIA Tech"
	BoardName   	"via"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"		"EXA"
	Option		"MigrationHeuristic" "greedy"
EndSection

Section "Screen"
     DefaultDepth 24
    SubSection "Display"
        Depth 16
        Modes "1280x800" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1280x800" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
       Identifier       "Default Screen"
       Device           "Configured Video Device"
EndSection


Section "Module"
      Load  "glx"
      Load  "dri"
      Load  "extmod"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
	Option	"Composite"			"Enable"
EndSection

```

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

```

---

