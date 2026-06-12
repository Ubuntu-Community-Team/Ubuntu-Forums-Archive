---
title: "X Config Problem after upgrade to Jaunty"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Chester.carey on 2009-04-24
Hi,
 
I did a net upgrade on my laptop to Jaunty. Grub boots fine, though the spalsh screen is now at finer resolution than before the upgrade. When the gui should load, it flickers a few times, like it's probing the resolution or trying to configure. Ultimately it just sits at a black screen. ctrl-alt-f(any number) does not get me to a shell.
 
If I go to recovery mode from grub I get a few options, only 2 take me to a shell as best I can tell and both ask for a root password, which I don't have as ubuntu has no root. I am at a remote location so I don't have the CD. 
 
If I can get to a shell I think I can reconfigure X, but I can't figure out how to get to a shell.
 
Help?

---

### Post by tomdkat on 2009-04-24
I'm seeing the same "flicker" and black screen behavior as you.  I've seen this with an old PCI video card with a GeForce2 MX-200 chipset and an old PCI ATI video card with a Mach64 chipset.

In both cases, when I drop to a root shell after booting in recovery mode, the reason for the black screen is X can't find a video mode it can use that the monitor will accept. I've seen this in /var/log/Xorg.0.log.  My original problem involves an ATI Radeon XPRESS 200 video card and colored garbage once X starts.

As for the root password, I haven't been prompted for a password so I'm not sure why you are.

Peace...

---

### Post by Chester.carey on 2009-04-24
How do you drop to a root shell? From the menu that comes up or is there a key sequence that will do this?
 
Anyone else have it drop them to a prompt for root password?

---

### Post by irv on 2009-04-24
> **Chester.carey said:**
> How do you drop to a root shell? From the menu that comes up or is there a key sequence that will do this?
 
Anyone else have it drop them to a prompt for root password?
Just as the grub menu is loading hit [ESC] key and start in the recovery mode. when the menu comes up you can go to start in prompt with network. when you are asked for the root password it is the password you gave yourself on the install. Once at the prompt you can just type in your commands.
If you find the solution to this problem with the video please post the fix so others can use it.

---

### Post by bobonthenet on 2009-04-24
Same problem here, someone has got to have the solution.

---

### Post by zsoltl on 2009-04-25
Similar here! After upgrading to Jaunty and restarting the system Xorg can't find any mode that would fit my screen(1024x768 on a five year old Acer Aspire laptop). The splash screen is indeed finer but shifted from the center of the screen. However, I do have proper access to shell. Any ideas? Do I have to start messing with xorg.conf?
Here is the Xorg.0.log file:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux zsolt-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 25 09:53:43 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
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

(--) PCI:*(0@1:0:0) VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] rev 1, Mem @ 0xf0000000/67108864, 0xd1000000/16777216
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
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.5.99.902, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
	K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800
(II) Primary Device is: PCI 01@00:00:0
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to http://www.openchrome.org/.
(!!) (development build, compiled on Fri Feb 13 08:34:27 2009)
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) CHROME(0): Depth 24, (--) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: KM400/KN400
(--) CHROME(0): Chipset revision: 3
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options.
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Reading config file...
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): Shadow framebuffer is disabled.
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be disabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xd1000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xd1200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(--) CHROME(0): Detected Acer Aspire 135x.
(II) CHROME(0): Detected MemClk 4
(II) CHROME(0): ViaGetMemoryBandwidth
(II) CHROME(0): Detected TV standard: PAL.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:E-EDID segment register" registered at address 0x60.
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): Enabling panel from PCI-subsystem ID information.
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaCH7xxxDetect
(II) CHROME(0): I2C device "I2C bus 3:CH7xxx" registered at address 0xEA.
(--) CHROME(0): Detected Chrontel CH7019B LVDS Transmitter/TV Encoder
(II) CHROME(0): ViaTVInit
(II) CHROME(0): ViaCH7xxxInit
(II) CHROME(0): CH7xxxSave
(II) CHROME(0): CH7xxxSave
(II) CHROME(0): CH7xxxDACDetect
(--) CHROME(0): CH7xxx: Nothing connected.
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x02
(II) CHROME(0): ViaOutputsSelect: Panel.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.lo to 29.677456
(II) CHROME(0): ViaModesMonitorFixup - Adjusted HSync.hi to 74.904167
(II) CHROME(0): Generic Monitor: Using hsync range of 29.68-74.90 kHz
(II) CHROME(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(WW) CHROME(0): Unable to estimate virtual size
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): VIAGetPanelSize
(II) CHROME(0): VIAGetPanelSizeFromDDCv1
(II) CHROME(0): I2C device "I2C bus 2:E-EDID segment register" registered at address 0x60.
(II) CHROME(0): I2C device "I2C bus 2:ddc2" registered at address 0xA0.
(II) CHROME(0): Manufacturer: LGP  Model: 657  Serial#: 0
(II) CHROME(0): Year: 1990  Week: 0
(II) CHROME(0): EDID Version: 1.3
(II) CHROME(0): Digital Display Input
(II) CHROME(0): Max Image Size [cm]: horiz.: 30  vert.: 22
(II) CHROME(0): Gamma: 2.20
(II) CHROME(0): No DPMS capabilities specified
(II) CHROME(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) CHROME(0): First detailed timing is preferred mode
(II) CHROME(0): redX: 0.587 redY: 0.343   greenX: 0.320 greenY: 0.529
(II) CHROME(0): blueX: 0.158 blueY: 0.140   whiteX: 0.312 whiteY: 0.328
(II) CHROME(0): Manufacturer's mask: 0
(II) CHROME(0): Supported additional Video Mode:
(II) CHROME(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) CHROME(0): h_active: 1024  h_sync: 1048  h_sync_end 1696 h_blank_end 1344 h_border: 0
(II) CHROME(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(WW) CHROME(0): Unknown vendor-specific block 0
(WW) CHROME(0): Unknown vendor-specific block 0
(WW) CHROME(0): Unknown vendor-specific block 0
(II) CHROME(0): EDID (in hex):
(II) CHROME(0): 	00ffffffffffff0030f0570600000000
(II) CHROME(0): 	00000103801e16780a72b09657528728
(II) CHROME(0): 	23505400000001010101010101010101
(II) CHROME(0): 	01010101010164190040410026301888
(II) CHROME(0): 	362030e4100000180000000000000000
(II) CHROME(0): 	0000000000000000000000000000004c
(II) CHROME(0): 	475068696c6970734c43440a00000000
(II) CHROME(0): 	004c503135305830382d413300000006
(II) CHROME(0): EDID vendor "LGP", prod id 1623
(II) CHROME(0): VIAGetPanelSizeFromEDID
(II) CHROME(0): VIAGetPanelSizeFromDDCv1: (1024x768)
(II) CHROME(0): Using panel at 800x600.
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x350" (unknown reason)
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x400" (unknown reason)
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "720x400" (unknown reason)
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
(II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x960" (unknown reason)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (148500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x960" (unknown reason)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (157500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (162000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (175500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (189000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (202500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (229500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1792x1344 (204800)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1792x1344" (unknown reason)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1856x1392 (218300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1856x1392" (unknown reason)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "832x624" (unknown reason)
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (119650)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (121500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (143470)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (72000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1360x768" (unknown reason)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (84750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1360x768" (unknown reason)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (122000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (145060)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (155800)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1400x1050" (horizontal sync too wide)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (179260)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (106500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1440x900" (unknown reason)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1024 (103125)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1600x1024" (unknown reason)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (119000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1680x1050" (unknown reason)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (146250)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1680x1050" (unknown reason)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (174000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1680x1050" (unknown reason)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (187000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1680x1050" (unknown reason)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (214750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1680x1050" (unknown reason)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1080 (138500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1920x1080" (unknown reason)
(II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1200 (154000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1920x1200" (unknown reason)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25312)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 640x480
(II) CHROME(0): ViaGetResolutionIndex: 0
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "640x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 720x480 (26591)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 720x480
(II) CHROME(0): ViaGetResolutionIndex: 12
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "720x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 720x576 (32663)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 720x576
(II) CHROME(0): ViaGetResolutionIndex: 13
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "720x576" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 800x480 (40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 800x480
(II) CHROME(0): ViaGetResolutionIndex: 17
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "800x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 800x600 (39822)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 800x600
(II) CHROME(0): ViaGetResolutionIndex: 1
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "800x600" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 848x480 (33750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 848x480
(II) CHROME(0): ViaGetResolutionIndex: 10
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "848x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 856x480 (31704)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 856x480
(II) CHROME(0): ViaGetResolutionIndex: 15
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "856x480" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1024x512 (41164)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1024x512
(II) CHROME(0): ViaGetResolutionIndex: 14
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1024x512" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1024x576 (46981)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1024x576
(II) CHROME(0): ViaGetResolutionIndex: 16
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1024x576" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1024x600 (48960)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1024x600
(II) CHROME(0): Panel does not support this resolution: 1024x600
(II) CHROME(0): Not using default mode "1024x600" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65028)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1024x768
(II) CHROME(0): ViaGetResolutionIndex: 2
(II) CHROME(0): ViaPanelGetIndex:Match Debug: 2 == 0)
(II) CHROME(0): ViaPanelGetIndex:Match Debug: 2 == 1)
(II) CHROME(0): ViaPanelGetIndex:Match Debug: 2 == 2)
(II) CHROME(0): ViaPanelGetIndex:Match Debug: 2 == 3)
(II) CHROME(0): ViaPanelGetIndex:Match Debug: 2 == 4)
(II) CHROME(0): ViaPanelGetIndex:Match Debug: 2 == 5)
(II) CHROME(0): ViaPanelGetIndex:Match Debug: 2 == 6)
(II) CHROME(0): ViaPanelGetIndex: Unable to match PanelSize with an lcdTable entry.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81613)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1152x864
(II) CHROME(0): ViaGetResolutionIndex: 3
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1152x864" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1280x768 (81135)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1280x768
(II) CHROME(0): ViaGetResolutionIndex: 7
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1280x768" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1280x720 (74600)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1280x720
(II) CHROME(0): Panel does not support this resolution: 1280x720
(II) CHROME(0): Not using default mode "1280x720" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108280)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1280x960
(II) CHROME(0): ViaGetResolutionIndex: 8
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1280x960" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108280)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1280x1024
(II) CHROME(0): ViaGetResolutionIndex: 4
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1280x1024" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (85500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1360x768" (horizontal sync too wide)
(II) CHROME(0): ViaValidMode: Validating 1366x768 (85860)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1366x768
(II) CHROME(0): Panel does not support this resolution: 1366x768
(II) CHROME(0): Not using default mode "1366x768" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (122726)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1400x1050
(II) CHROME(0): ViaGetResolutionIndex: 11
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1400x1050" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (106470)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1440x900
(II) CHROME(0): Panel does not support this resolution: 1440x900
(II) CHROME(0): Not using default mode "1440x900" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (161793)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1600x1200
(II) CHROME(0): ViaGetResolutionIndex: 5
(II) CHROME(0): ViaPanelGetIndex: Non-native resolutions are broken.
(II) CHROME(0): Not using default mode "1600x1200" (unknown reason)
(II) CHROME(0): ViaValidMode: Validating 1920x1080 (172900)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaGetResolutionIndex: Looking for 1920x1080
(II) CHROME(0): Panel does not support this resolution: 1920x1080
(II) CHROME(0): Not using default mode "1920x1080" (unknown reason)
(WW) CHROME(0): Mode pool is empty
(EE) CHROME(0): No valid modes found
(II) CHROME(0): VIAFreeRec
(II) CHROME(0): I2C device "I2C bus 3:CH7019B" removed.
(II) CHROME(0): VIAUnmapMem
(II) CHROME(0): VIAFreeScreen
(II) CHROME(0): VIAFreeRec
(II) UnloadModule: "openchrome"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

---

### Post by irv on 2009-04-25
I don't know if this will help, but look at this Thread:
[http://ubuntuforums.org/showthread.php?t=1135141&page=3]("http://ubuntuforums.org/showthread.php?t=1135141&page=3")

---

### Post by YankeeTransplant on 2009-04-25
I'm also having this issue (flicker than black screen, no tty console access) after doing a dist upgrade from 8.10. I'm running with x64 arch.

---

### Post by ukch on 2009-05-05
I have the same problem - old Acer Aspire laptop (1355LC) with Via chipset, and no X, although I can get to the terminal login with Alt-F1 without problems. Restoring a previous backup of my xorg.conf does not solve the problems, even if I restore from xorg.conf.failsafe. Please someone find a solution to this problem soon, as I really can't stand the thought of being stuck with Windows!

---

### Post by irv on 2009-05-05
> **ukch said:**
> I have the same problem - old Acer Aspire laptop (1355LC) with Via chipset, and no X, although I can get to the terminal login with Alt-F1 without problems. Restoring a previous backup of my xorg.conf does not solve the problems, even if I restore from xorg.conf.failsafe. Please someone find a solution to this problem soon, as I really can't stand the thought of being stuck with Windows!

Did you try the thread I had posted above?
[http://ubuntuforums.org/showthread.php?t=1135141&page=3]("http://ubuntuforums.org/showthread.php?t=1135141&page=3") 
To see it this helps.

---

### Post by bobonthenet on 2009-05-06
irv, your advice on that other thread worked for me.  I forgot to post back here.  Thanks a ton for your help.

---

### Post by ukch on 2009-05-06
Afraid I haven't been so lucky. I have tried removing the fglrx driver, but it wasn't installed. Then I tried removing xserver-xorg and reinstalling, as suggested by **akse** but that changed nothing. Looking back on that thread, I'm not sure there's been anyone with this particular problem (ie. VIA chipset and no X at all) who's been able to solve it.

---

### Post by irv on 2009-05-06
> **ukch said:**
> Afraid I haven't been so lucky. I have tried removing the fglrx driver, but it wasn't installed. Then I tried removing xserver-xorg and reinstalling, as suggested by **akse** but that changed nothing. Looking back on that thread, I'm not sure there's been anyone with this particular problem (ie. VIA chipset and no X at all) who's been able to solve it.
Have you tried the xfix on the recovery menu in grub?

---

### Post by ukch on 2009-05-06
Yes, I have tried that. It doesn't appear to do anything particularly useful.

I am going to try to install the latest snapshot of the Openchrome and/or Unichrome drivers and see if that helps any. Unless anyone knows an easier way to fix the problem, of course?

---

### Post by ukch on 2009-05-06
It turns out that the latest snapshot of Openchrome is already installed, so I tried to roll back to the previous stable version that came with Intrepid, but the problem is exactly the same. At this point I really have no more ideas as to what could be the source of the problem.

---

### Post by ukch on 2009-05-07
I have come across a partial (and let's be honest, a bit of a hacky) fix. Basically, I removed xserver-xorg (and all of its dependencies) and installed the current versions from Debian Sid instead, proving that the problem is one with one of the X packages themselves and not with the Openchrome drivers. Everything seems to be fine now, but who knows what problems I will encounter further along the line, especially when it comes time to upgrade something!

---

### Post by irv on 2009-05-07
> **ukch said:**
> I have come across a partial (and let's be honest, a bit of a hacky) fix. Basically, I removed xserver-xorg (and all of its dependencies) and installed the current versions from Debian Sid instead, proving that the problem is one with one of the X packages themselves and not with the Openchrome drivers. Everything seems to be fine now, but who knows what problems I will encounter further along the line, especially when it comes time to upgrade something!

I had some problems with wicd. Once I got it fixed, I when ito Synaptic Package Manager selected it went to the package menu and locked it. Maybe you should do the same with xserver-xorg so it won't get over written if you do some updates. Just a thought.

---

### Post by ukch on 2009-05-08
It seems to be OK, as it's actually a newer version than the Ubuntu one. What I'm more concerned about is the couple of libraries I had to update as well. Currently, everything seems to be working fine though, so fingers crossed everything'll be OK until the next Ubuntu release, by which time they'll hopefully have fixed whatever was causing the error in the first place.

---

### Post by irv on 2009-05-08
> **ukch said:**
> It seems to be OK, as it's actually a newer version than the Ubuntu one. What I'm more concerned about is the couple of libraries I had to update as well. Currently, everything seems to be working fine though, so fingers crossed everything'll be OK until the next Ubuntu release, by which time they'll hopefully have fixed whatever was causing the error in the first place.

To be safe you could backup the libraries so if there was a problem with an update you could revert back to them. Again, just a thought.

---

### Post by thorax695 on 2009-05-13
I have the exact same problem, but my computer is an Everex StepNote NM3900W. It uses the OpenChrome driver and has a maximum screen resolution of 1280x800.

Maybe I'll try installing the xorg packages from Debian Sid...

---

### Post by blackzafiro on 2009-05-14
> **ukch said:**
> I have come across a partial (and let's be honest, a bit of a hacky) fix. Basically, I removed xserver-xorg (and all of its dependencies) and installed the current versions from Debian Sid instead, proving that the problem is one with one of the X packages themselves and not with the Openchrome drivers....

Sorry for my ignorance but... how do you do that?  Used apt-get remove ...? Add Sid repos... or dowload the package?

Cheers

---

### Post by ukch on 2009-05-14
OK. I'll do a step-by-step of what I did, just because there were a couple of odd surprises. I'm doing this from memory, so there may be a couple of errors - please let me know if anything doesn't work as expected.

First of all, you want to run the command
```
sudo apt-get remove xserver-xorg
sudo dpkg -r --ignore-depends=hal hal
```
This should remove the xserver and all of its dependencies, plus the *hal* package as it caused me a bit of trouble.

Next, make a backup of your /etc/apt/sources.list file and replace it with the one line
```
deb http://ftp.debian.org/debian/ sid main contrib non-free
```
Then run *sudo apt-get update*.

Next, install the new versions of the xserver, the hal and all dependent libraries:
```
sudo apt-get install hal xserver-xorg xserver-xorg-video-all
```

After this, restore your original sources.list file and run *sudo apt-get update* again.

Now, there is a particular problem with the packages *xserver-xorg* and *hal* in that (for various reasons) the Debian versions of these packages are incompatible with the currenct version of Ubuntu, so you need to remove these two new packages and replace them with the original Ubuntu versions:
```
sudo dpkg -r --ignore-depends=hal hal
sudo dpkg -r --ignore-dependencies=xserver-xorg xserver-xorg
sudo apt-get install hal xserver-xorg
```
This ought to remove just these two packages, then reinstall the Ubuntu versions. Then, to test whether everything works OK, run
```
startx
```
If everything seems to be OK, then just run ```
sudo service gdm restart
```
(or if you're running kubuntu, substitute gdm for kdm)

I hope this post was helpful to you!

---

### Post by blackzafiro on 2009-05-15
Wow, amazing, thank you very much for the very detail guide.  I have learned a lot today :D.

Also, I found a less dangerous way to solve the problem:

Install [http://launchpadlibrarian.net/26710878/xserver-xorg-video-openchrome_0.2.903%2Bsvn741-1_i386.deb](http://launchpadlibrarian.net/26710878/xserver-xorg-video-openchrome_0.2.903%2Bsvn741-1_i386.deb)

It is meant to be used for karmic, but it made my jaunty desktop appear :KS.

Thanks a lot!!!

---

### Post by thorax695 on 2009-05-16
I found an even simpler solution in my case from [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/182778"). Here's what I added to my Screen section in my xorg.conf:

```
Section "Screen"
   Identifier   "Default Screen"
   Monitor      "Configured Monitor"
   Device       "Configured Video Device"
[COLOR=Red]   SubSection "Display"
      Virtual 1280 800
   EndSubSection
[/COLOR]EndSection
```

---

