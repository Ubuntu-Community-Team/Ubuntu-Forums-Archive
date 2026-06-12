---
title: "Having trouble with compiz on my intel integrated computer"
date: 2009-05-30
forum: Hardware
---

### Post by swr12 on 2009-05-30
Hello,

I'm having problems with compiz on my desktop computer. When my computer is using Compiz the title bar to all my windows is missing. Desktop cube, Animations, etc. all work fine. I have looked everywhere for someone with a similar problem in the forums, but have come up empty handed.

possibly related to this problem is that the area around my cursor seems to not be refreshing correctly.

My computer is using the Intel Xorg driver. The only changes I have made to my xorg.conf where to manually set my monitor HorizSync and VertRefresh since for some reason they are not automatically detected. I also set the Virtual screen to 1024x768 which is my displays native resolution to prevent xorg from using to large of a resolution.

Xorg.0.log:

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux user-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 30 14:25:16 2009
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

(--) PCI:*(0@0:1:0) Intel Corporation 82810 (CGC) Chipset Graphics Controller rev 3, Mem @ 0xf8000000/67108864, 0xf4000000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:01:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(**) intel(0): Depth 16, (--) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
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
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel(R) 810, Intel(R) 815 Chipset Video BIOS
(II) intel(0): VESA VBE OEM Software Rev: 36.56
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(R) 810, Intel(R) 815 Chipset
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level none
(II) intel(0): VESA VBE DDC transfer in appr. 0 sec.
(II) intel(0): VESA VBE DDC read failed
(--) intel(0): Chipset: "i810"
(--) intel(0): Linear framebuffer at 0xF8000000
(--) intel(0): IO registers at addr 0xF4000000
(II) intel(0): Kernel reported 51712 total, 1 used
(II) intel(0): I810CheckAvailableMemory: 206844k available
(==) intel(0): Will alloc AGP framebuffer: 24576 kByte
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) intel(0): Configured Monitor: Using hsync range of 30.00-60.00 kHz
(II) intel(0): Configured Monitor: Using vrefresh range of 58.00-75.00 Hz
(II) intel(0): Clock range:   9.50 to 163.00 MHz
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (width too large for virtual size)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(**) intel(0): Virtual size is 1024x768 (pitch 1024)
(**) intel(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) intel(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) intel(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) intel(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) intel(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) intel(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) intel(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) intel(0): page flipping disabled
(II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:01.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmGetBusid returned ''
(II) [drm] loaded kernel module for "i810" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer handle = 0xf8000000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [drm] Registers = 0xf4000000
(II) intel(0): [agp] dcacheHandle : 0x0
(II) intel(0): [agp] GART: no dcache memory found
(II) intel(0): [agp] Bound backbuffer memory
(II) intel(0): [agp] Bound depthbuffer memory
(II) intel(0): [agp] Bound System Texture Memory
(II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
(II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
(II) intel(0): Adding 768 scanlines for pixmap caching
(II) intel(0): Allocated Scratch Memory
(II) intel(0): [dri] Buffer map : 13fb000
(II) intel(0): [drm] added 256 4096 byte DMA buffers
(II) intel(0): [drm] Init v1.4 interface.
(II) intel(0): [drm] dma control initialized, using IRQ -22
(II) intel(0): [dri] visual configs initialized.
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Setting dot clock to 78.7 MHz [ 0x50 0x17 0x20 ] [ 82 25 2 ]
(II) intel(0): chose watermark 0x2210e000: (tab.freq 78.8)
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		24 128x128 slots
		6 256x256 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): DPMS enabled
(II) intel(0): [DRI] installation complete
(II) intel(0): Direct rendering enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:01.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/i810_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0

```
My specs are as follows
Graphics - Intel i810e
Processor - 800 Mhz Celeron
Memmory - 256 MB
Ubuntu version 9.04

Thank you for reading and please post any suggestions

---

### Post by swr12 on 2009-06-02
I think that this problem may be related to the xorg driver. Is the one provided with Ubuntu the best or is their a better one? If the one provided with Ubuntu is the best is their some option that I could use to get it to work better?

This problem only shows up on my home computer (On my laptop I don't run into any of these problems) and it showed up right after doing a fresh install of ubuntu 9.04 since compiz runs by default. If I switch to Metacity the title bars (actually a better description would be the title bars and window borders) come back and the mouse cursor problem goes away. I have taken a picture of my desktop to show the problems.

I would really like to be able to use desktop cube, but I can't keep using my computer with out window title bars and borders.

please post any suggestions
thank you

---

