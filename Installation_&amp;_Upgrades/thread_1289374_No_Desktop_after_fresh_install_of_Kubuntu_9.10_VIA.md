---
title: "No Desktop after fresh install of Kubuntu 9.10 VIA Chipset"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by rmannon on 2009-10-12
Hi all

I installed 9.10 yesterday and have lost my ability to get to a desktop.  During the boot from the live cd the kde splash screen would go through it's paces a few times before giving me a desktop.  But once it got to the desktop it was fine.  The install went smoothly.  After reboot the box would go to the login screen and after I entered my user name and password it would just go to the login screen again.  I did a ctrl+alt+f1 to get a login prompt and did an apt-get update and then an apt-get upgrade, but still no desktop.  I am using a VIA chip with the openchrome driver.  I dont see any errors in the Xorg.0.log but I assume it's the 3D rendering thats crashing the desktop.  How the heck to I turn off the rendering?  

If you need to see my logs or other files I will post them tonight when I get home from work.  Thanks for all your help.

---

### Post by rmannon on 2009-10-12
I reinstalled Kubuntu and after the system finally booted to a gui.  but it got stuck in a loop in the kde splash screen until i opened the dvd drive.  Wha??  I don't know why that finally let it boot to a gui.  so anyway here is my xorg.log: 


	Information			Driver	"vesa"
	Information		EndSection
	Information		Section "Screen"
	Information			Identifier	"Builtin Default vesa Screen 0"
	Information			Device	"Builtin Default vesa Device 0"
	Information		EndSection
	Information		Section "Device"
	Information			Identifier	"Builtin Default fbdev Device 0"
	Information			Driver	"fbdev"
	Information		EndSection
	Information		Section "Screen"
	Information			Identifier	"Builtin Default fbdev Screen 0"
	Information			Device	"Builtin Default fbdev Device 0"
	Information		EndSection
	Information		Section "ServerLayout"
	Information			Identifier	"Builtin Default Layout"
	Information			Screen	"Builtin Default openchrome Screen 0"
	Information			Screen	"Builtin Default vesa Screen 0"
	Information			Screen	"Builtin Default fbdev Screen 0"
	Information		EndSection
	Default setting	--- End of built-in configuration ---
	Default setting	ServerLayout "Builtin Default Layout"
	From config file	|-->Screen "Builtin Default openchrome Screen 0" (0)
	From config file	|   |-->Monitor "<default monitor>"
	From config file	|   |-->Device "Builtin Default openchrome Device 0"
	Default setting	No monitor specified for screen "Builtin Default openchrome Screen 0".
	Information		Using a default monitor configuration.
	From config file	|-->Screen "Builtin Default vesa Screen 0" (1)
	From config file	|   |-->Monitor "<default monitor>"
	From config file	|   |-->Device "Builtin Default vesa Device 0"
	Default setting	No monitor specified for screen "Builtin Default vesa Screen 0".
	Information		Using a default monitor configuration.
	From config file	|-->Screen "Builtin Default fbdev Screen 0" (2)
	From config file	|   |-->Monitor "<default monitor>"
	From config file	|   |-->Device "Builtin Default fbdev Device 0"
	Default setting	No monitor specified for screen "Builtin Default fbdev Screen 0".
	Information		Using a default monitor configuration.
	Default setting	Automatically adding devices
	Default setting	Automatically enabling devices
	Warning	The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Information		Entry deleted from font path.
	Default setting	FontPath set to:
	Information		/usr/share/fonts/X11/misc,
	Information		/usr/share/fonts/X11/100dpi/:unscaled,
	Information		/usr/share/fonts/X11/75dpi/:unscaled,
	Information		/usr/share/fonts/X11/Type1,
	Information		/usr/share/fonts/X11/100dpi,
	Information		/usr/share/fonts/X11/75dpi,
	Information		/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	Information		built-ins
	Default setting	ModulePath set to "/usr/lib/xorg/modules"
	Information	Cannot locate a core pointer device.
	Information	Cannot locate a core keyboard device.
	Information	The server relies on HAL to provide the list of input devices.
	Information		If no devices become available, reconfigure HAL or disable AllowEmptyInput.
	Information	Open ACPI successful (/var/run/acpid.socket)
	Information	System resource ranges:
	Information		[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information	LoadModule: "extmod"
	Information	Loading /usr/lib/xorg/modules/extensions//libextmod.so
	Information	Module extmod: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.0.0
	Information		Module class: X.Org Server Extension
	Information		ABI class: X.Org Server Extension, version 2.0
	Information	Loading extension MIT-SCREEN-SAVER
	Information	Loading extension XFree86-VidModeExtension
	Information	Loading extension XFree86-DGA
	Information	Loading extension DPMS
	Information	Loading extension XVideo
	Information	Loading extension XVideo-MotionCompensation
	Information	Loading extension X-Resource
	Information	LoadModule: "dbe"
	Information	Loading /usr/lib/xorg/modules/extensions//libdbe.so
	Information	Module dbe: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.0.0
	Information		Module class: X.Org Server Extension
	Information		ABI class: X.Org Server Extension, version 2.0
	Information	Loading extension DOUBLE-BUFFER
	Information	LoadModule: "glx"
	Information	Loading /usr/lib/xorg/modules/extensions//libglx.so
	Information	Module glx: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.0.0
	Information		ABI class: X.Org Server Extension, version 2.0
	Default setting	AIGLX enabled
	Information	Loading extension GLX
	Information	LoadModule: "record"
	Information	Loading /usr/lib/xorg/modules/extensions//librecord.so
	Information	Module record: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.13.0
	Information		Module class: X.Org Server Extension
	Information		ABI class: X.Org Server Extension, version 2.0
	Information	Loading extension RECORD
	Information	LoadModule: "dri"
	Information	Loading /usr/lib/xorg/modules/extensions//libdri.so
	Information	Module dri: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.0.0
	Information		ABI class: X.Org Server Extension, version 2.0
	Information	Loading extension XFree86-DRI
	Information	LoadModule: "dri2"
	Information	Loading /usr/lib/xorg/modules/extensions//libdri2.so
	Information	Module dri2: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.1.0
	Information		ABI class: X.Org Server Extension, version 2.0
	Information	Loading extension DRI2
	Information	LoadModule: "openchrome"
	Information	Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
	Information	Module openchrome: vendor="http://openchrome.org/"
	Information		compiled for 1.6.1.901, module version = 0.2.903
	Information		Module class: X.Org Video Driver
	Information		ABI class: X.Org Video Driver, version 5.0
	Information	LoadModule: "vesa"
	Information	Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
	Information	Module vesa: vendor="X.Org Foundation"
	Information		compiled for 1.6.3, module version = 2.2.1
	Information		Module class: X.Org Video Driver
	Information		ABI class: X.Org Video Driver, version 5.0
	Information	LoadModule: "fbdev"
	Information	Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
	Information	Module fbdev: vendor="X.Org Foundation"
	Information		compiled for 1.6.0, module version = 0.4.0
	Information		ABI class: X.Org Video Driver, version 5.0
	Information	OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	Information		K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
	Information		K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800, VX855
	Information	VESA: driver for VESA chipsets: vesa
	Information	FBDEV: driver for framebuffer: fbdev
	Information	Primary Device is: PCI 01@00:00:0
	Notice	VIA Technologies does not support this driver in any way.
	Notice	For support, please refer to [http://www.openchrome.org/](http://www.openchrome.org/).
	Notice	(development build, compiled on Mon Jul 27 22:22:51 2009)
	Warning	Falling back to old probe method for vesa
	Warning	Falling back to old probe method for fbdev
	Information	Loading sub module "fbdevhw"
	Information	LoadModule: "fbdevhw"
	Information	Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
	Information	Module fbdevhw: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 0.0.2
	Information		ABI class: X.Org Video Driver, version 5.0
	Error	open /dev/fb0: No such file or directory
	Information	resource ranges after probing:
	Information		[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information	CHROME(0): VIAPreInit
	Information	Loading sub module "vgahw"
	Information	LoadModule: "vgahw"
	Information	Loading /usr/lib/xorg/modules//libvgahw.so
	Information	Module vgahw: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 0.1.0
	Information		ABI class: X.Org Video Driver, version 5.0
	Information	CHROME(0): VIAGetRec
	Information	CHROME(0): Creating default Display subsection in Screen section
	Information		"Builtin Default openchrome Screen 0" for depth/fbbpp 24/32
	Default setting	CHROME(0): Depth 24, (--) framebuffer bpp 32
	Default setting	CHROME(0): RGB weight 888
	Default setting	CHROME(0): Default visual is TrueColor
	Probed	CHROME(0): Chipset: K8M800/K8N800
	Probed	CHROME(0): Chipset revision: 0
	Probed	CHROME(0): Probed amount of VideoRAM = 65536 kB
	Information	CHROME(0): Setting up default chipset options.
	Information	CHROME(0): VIASetupDefaultOptions
	Information	CHROME(0): Reading config file...
	Information	CHROME(0): Starting to parse config file options...
	Default setting	CHROME(0): Shadow framebuffer is disabled.
	Default setting	CHROME(0): Hardware acceleration is enabled.
	Default setting	CHROME(0): Using XAA acceleration architecture.
	Default setting	CHROME(0): Using hardware two-color cursors and software full-color cursors.
	Default setting	CHROME(0): GPU virtual command queue will be enabled.
	Default setting	CHROME(0): DRI IRQ will be disabled if DRI is enabled.
	Default setting	CHROME(0): AGP DMA will be enabled if DRI is enabled.
	Default setting	CHROME(0): AGP DMA will be used for 2D acceleration.
	Default setting	CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
	Default setting	CHROME(0): Will not enable VBE modes.
	Default setting	CHROME(0): VBE VGA register save & restore will not be used
	Information		if VBE modes are enabled.
	Default setting	CHROME(0): Xv Bandwidth check is enabled.
	Default setting	CHROME(0): Will not impose a limit on video RAM reserved for DRI.
	Default setting	CHROME(0): Will try to allocate 32768 kB of AGP memory.
	Default setting	CHROME(0): Digital output bus width is 12 bits.
	Default setting	CHROME(0): DVI Center is disabled.
	Default setting	CHROME(0): Panel size is not selected from config file.
	Default setting	CHROME(0): Panel will not be forced.
	Default setting	CHROME(0): TV dotCrawl is disabled.
	Default setting	CHROME(0): TV deflicker is set to 0.
	Default setting	CHROME(0): No default TV type is set.
	Default setting	CHROME(0): No default TV output signal type is set.
	Information	CHROME(0): VIAMapMMIO
	Probed	CHROME(0): mapping MMIO @ 0xec000000 with size 0x9000
	Probed	CHROME(0): mapping BitBlt MMIO @ 0xec200000 with size 0x200000
	Information	CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
	Default setting	CHROME(0): Will not print VGA registers.
	Default setting	CHROME(0): Will not scan I2C buses.
	Information	CHROME(0): ...Finished parsing config file options.
	Error	CHROME(0): Unknown Card-Ids (3108|147B|1421); please report to [email]openchrome-users@openchrome.org[/email]
	Information	CHROME(0): Detected MemClk 6
	Information	CHROME(0): ViaGetMemoryBandwidth
	Information	CHROME(0): Detected TV standard: NTSC.
	Default setting	CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
	Information	Loading sub module "i2c"
	Information	LoadModule: "i2c"
	Information	Module "i2c" already built-in
	Information	CHROME(0): ViaI2CInit
	Information	CHROME(0): ViaI2CBus1Init
	Information	CHROME(0): I2C bus "I2C bus 1" initialized.
	Information	CHROME(0): ViaI2cBus2Init
	Information	CHROME(0): I2C bus "I2C bus 2" initialized.
	Information	CHROME(0): ViaI2CBus3Init
	Information	CHROME(0): I2C bus "I2C bus 3" initialized.
	Information	Loading sub module "ddc"
	Information	LoadModule: "ddc"
	Information	Module "ddc" already built-in
	Information	CHROME(0): I2C device "I2C bus 1:E-EDID segment register" registered at address 0x60.
	Information	CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
	Information	CHROME(0): Manufacturer: DEL  Model: a00a  Serial#: 1111638618
	Information	CHROME(0): Year: 2004  Week: 7
	Information	CHROME(0): EDID Version: 1.3
	Information	CHROME(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
	Information	CHROME(0): Sync:  Separate
	Information	CHROME(0): Max Image Size [cm]: horiz.: 34  vert.: 27
	Information	CHROME(0): Gamma: 2.20
	Information	CHROME(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
	Information	CHROME(0): First detailed timing is preferred mode
	Information	CHROME(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
	Information	CHROME(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
	Information	CHROME(0): Supported established timings:
	Information	CHROME(0): 720x400@70Hz
	Information	CHROME(0): 640x480@60Hz
	Information	CHROME(0): 640x480@75Hz
	Information	CHROME(0): 800x600@60Hz
	Information	CHROME(0): 800x600@75Hz
	Information	CHROME(0): 1024x768@60Hz
	Information	CHROME(0): 1024x768@75Hz
	Information	CHROME(0): 1280x1024@75Hz
	Information	CHROME(0): Manufacturer's mask: 0
	Information	CHROME(0): Supported standard timings:
	Information	CHROME(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
	Information	CHROME(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
	Information	CHROME(0): Supported detailed timing:
	Information	CHROME(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
	Information	CHROME(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
	Information	CHROME(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
	Information	CHROME(0): Serial No: J180642DBBBZ
	Information	CHROME(0): Monitor name: DELL E172FP
	Information	CHROME(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 140 MHz
	Information	CHROME(0): EDID (in hex):
	Information	CHROME(0): 	00ffffffffffff0010ac0aa05a424242
	Information	CHROME(0): 	070e010368221b78eac5c6a3574a9c23
	Information	CHROME(0): 	124f54a54b00714f8180010101010101
	Information	CHROME(0): 	010101010101302a009851002a403070
	Information	CHROME(0): 	1300520e1100001e000000ff004a3138
	Information	CHROME(0): 	30363432444242425a0a000000fc0044
	Information	CHROME(0): 	454c4c204531373246500a20000000fd
	Information	CHROME(0): 	00384c1f500e000a20202020202000e1
	Information	CHROME(0): EDID vendor "DEL", prod id 40970
	Information	CHROME(0): Using EDID range info for horizontal sync
	Information	CHROME(0): Using EDID range info for vertical refresh
	Information	CHROME(0): Printing DDC gathered Modelines:
	Information	CHROME(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	Information	CHROME(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
	Information	CHROME(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
	Information	CHROME(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
	Information	CHROME(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
	Information	CHROME(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
	Information	CHROME(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
	Information	CHROME(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
	Information	CHROME(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
	Information	CHROME(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
	Information	CHROME(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	Information	CHROME(0): ViaOutputsDetect
	Information	CHROME(0): VIATVDetect
	Information	CHROME(0): ViaOutputsSelect
	Information	CHROME(0): ViaOutputsSelect: X Configuration: 0x00
	Information	CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x00
	Information	CHROME(0): ViaOutputsSelect: CRT.
	Information	CHROME(0): ViaModesAttach
	Information	CHROME(0): <default monitor>: Using hsync range of 31.00-80.00 kHz
	Information	CHROME(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
	Information	CHROME(0): <default monitor>: Using maximum pixel clock of 140.00 MHz
	Information	CHROME(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
	Information	CHROME(0): Clock range:  20.00 to 230.00 MHz
	Information	CHROME(0): ViaValidMode: Validating 640x350 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "640x350" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 640x400 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "640x400" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 720x400 (35500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "720x400" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 640x480 (25175)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 640x480 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 640x480 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 640x480 (36000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "640x480" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 800x600 (36000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 800x600 (40000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 800x600 (50000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 800x600 (49500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 800x600 (56300)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "800x600" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (44900)
	Information	CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
	Information	CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (65000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (75000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (78750)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (94500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "1024x768" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1280x960 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1280x960 (148500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "1280x960" (hsync out of range)
	Information	CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (157500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "1280x1024" (hsync out of range)
	Information	CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 832x624 (57284)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (81620)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (96770)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (104990)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (119650)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (121500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
	Information	CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (143470)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): Not using default mode "1152x864" (hsync out of range)
	Information	CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1440x900" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1600x1024" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1920x1080" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1920x1200" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
	Information	CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (40000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 640x480 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 640x480 (25175)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 720x400 (28320)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (78750)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (65000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (49500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1280x960 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (108000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (104990)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (96770)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1152x864 (81620)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (78750)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (65000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (78750)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (75000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 1024x768 (65000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 832x624 (57284)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (49500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (40000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (49500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (50000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (40000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 800x600 (36000)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 640x480 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 640x480 (25175)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 640x480 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 640x480 (31500)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 640x480 (25175)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Information	CHROME(0): ViaValidMode: Validating 720x400 (28320)
	Information	CHROME(0): ViaFirstCRTCModeValid
	Probed	CHROME(0): Virtual size is 1280x1024 (pitch 1280)
	From config file	CHROME(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
	Information	CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	From config file	CHROME(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
	From config file	CHROME(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
	Information	CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	From config file	CHROME(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
	From config file	CHROME(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
	Information	CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	From config file	CHROME(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
	Information	CHROME(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
	From config file	CHROME(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
	From config file	CHROME(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
	From config file	CHROME(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
	From config file	CHROME(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
	Information	CHROME(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
	From config file	CHROME(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
	Information	CHROME(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
	From config file	CHROME(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
	From config file	CHROME(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
	Information	CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
	From config file	CHROME(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
	From config file	CHROME(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
	Information	CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
	From config file	CHROME(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
	Information	CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
	From config file	CHROME(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
	Information	CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
	From config file	CHROME(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
	From config file	CHROME(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
	Information	CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
	From config file	CHROME(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
	From config file	CHROME(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
	Information	CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
	From config file	CHROME(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
	Information	CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
	From config file	CHROME(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
	Information	CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
	From config file	CHROME(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
	From config file	CHROME(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
	Information	CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
	From config file	CHROME(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
	Information	CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
	From config file	CHROME(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
	Information	CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
	From config file	CHROME(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
	Information	CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
	From config file	CHROME(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
	Information	CHROME(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
	From config file	CHROME(0): Display dimensions: (340, 270) mm
	From config file	CHROME(0): DPI set to (95, 96)
	Information	Loading sub module "fb"
	Information	LoadModule: "fb"
	Information	Loading /usr/lib/xorg/modules//libfb.so
	Information	Module fb: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.0.0
	Information		ABI class: X.Org ANSI C Emulation, version 0.4
	Information	Loading sub module "xaa"
	Information	LoadModule: "xaa"
	Information	Loading /usr/lib/xorg/modules//libxaa.so
	Information	Module xaa: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 1.2.1
	Information		ABI class: X.Org Video Driver, version 5.0
	Information	Loading sub module "ramdac"
	Information	LoadModule: "ramdac"
	Information	Module "ramdac" already built-in
	Information	CHROME(0): VIAUnmapMem
	Information	UnloadModule: "vesa"
	Information	Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
	Information	UnloadModule: "fbdev"
	Information	Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
	Information	UnloadModule: "fbdevhw"
	Information	Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
	Probed	Depth 24 pixmap format is 32 bpp
	Information	do I need RAC?  No, I don't.
	Information	resource ranges after preInit:
	Information		[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	Information		[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	Information		[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	Information		[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	Information		[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information		[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	Information		[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	Information	CHROME(0): VIAScreenInit
	Information	CHROME(0): VIAMapFB
	Probed	CHROME(0): mapping framebuffer @ 0xe8000000 with size 0x4000000
	Probed	CHROME(0): Frame buffer start: 0x7f8e19338000, free start: 0x500000 end: 0x4000000
	Information	CHROME(0): VIAMapMMIO
	Probed	CHROME(0): mapping MMIO @ 0xec000000 with size 0x9000
	Probed	CHROME(0): mapping BitBlt MMIO @ 0xec200000 with size 0x200000
	Information	CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
	Information	CHROME(0): VIASave
	Information	CHROME(0): Primary
	Information	CHROME(0): Crtc...
	Information	CHROME(0): TVSave...
	Information	CHROME(0): VIAWriteMode
	Information	CHROME(0): ViaModePrimary
	Information	CHROME(0): Name: 1280x1024
	Information	CHROME(0): Clock: 108000
	Information	CHROME(0): VRefresh: 60.019741
	Information	CHROME(0): HSync: 63.981041
	Information	CHROME(0): HDisplay: 1280
	Information	CHROME(0): HSyncStart: 1328
	Information	CHROME(0): HSyncEnd: 1440
	Information	CHROME(0): HTotal: 1688
	Information	CHROME(0): HSkew: 0
	Information	CHROME(0): VDisplay: 1024
	Information	CHROME(0): VSyncStart: 1025
	Information	CHROME(0): VSyncEnd: 1028
	Information	CHROME(0): VTotal: 1066
	Information	CHROME(0): VScan: 0
	Information	CHROME(0): Flags: 5
	Information	CHROME(0): CrtcHDisplay: 0x500
	Information	CHROME(0): CrtcHBlankStart: 0x500
	Information	CHROME(0): CrtcHSyncStart: 0x530
	Information	CHROME(0): CrtcHSyncEnd: 0x5a0
	Information	CHROME(0): CrtcHBlankEnd: 0x698
	Information	CHROME(0): CrtcHTotal: 0x698
	Information	CHROME(0): CrtcHSkew: 0x0
	Information	CHROME(0): CrtcVDisplay: 0x400
	Information	CHROME(0): CrtcVBlankStart: 0x400
	Information	CHROME(0): CrtcVSyncStart: 0x401
	Information	CHROME(0): CrtcVSyncEnd: 0x404
	Information	CHROME(0): CrtcVBlankEnd: 0x42a
	Information	CHROME(0): CrtcVTotal: 0x42a
	Information	CHROME(0): ViaFirstCRTCSetMode
	Information	CHROME(0): Setting up 1280x1024
	Information	CHROME(0): ViaTVPower: Off.
	Information	CHROME(0): ViaSetPrimaryFIFO
	Information	CHROME(0): ViaSetDotclock to 0x079089
	Information	CHROME(0): ViaSetUseExternalClock
	Information	CHROME(0): VIAAdjustFrame
	Information	CHROME(0): VIAAdjustFrame
	Information	CHROME(0): - Blanked
	Information	drmOpenDevice: node name is /dev/dri/card0
	Information	drmOpenDevice: open result is 11, (OK)
	Information	drmOpenDevice: node name is /dev/dri/card0
	Information	drmOpenDevice: open result is 11, (OK)
	Information	drmOpenByBusid: Searching for BusID PCI:1:0:0
	Information	drmOpenDevice: node name is /dev/dri/card0
	Information	drmOpenDevice: open result is 11, (OK)
	Information	drmOpenByBusid: drmOpenMinor returns 11
	Information	drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
	Information	[drm] DRM interface version 1.3
	Information	[drm] DRM open master succeeded.
	Information	CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
	Information	CHROME(0): [drm] framebuffer handle = 0xe8000000
	Information	CHROME(0): [drm] added 1 reserved context for kernel
	Information	CHROME(0): X context handle = 0x1
	Information	CHROME(0): [drm] installed DRM signal handler
	Information	CHROME(0): [dri] visual configs initialized.
	Information	CHROME(0): [drm] register handle = 0xec000000
	Information	CHROME(0): [drm] framebuffer handle = 0xe8000000
	Information	CHROME(0): [drm] mmio Registers = 0xec000000
	Information	CHROME(0): [dri] mmio mapped.
	Information	CHROME(0): - Visuals set up
	Information	CHROME(0): VIAInternalScreenInit
	Information	CHROME(0): - B & W
	Information	CHROME(0): CursorStart: 0x3fc0000
	Information	CHROME(0): Using 3072 lines for offscreen memory.
	Information	CHROME(0): Using XFree86 Acceleration Architecture (XAA)
	Information		Screen to screen bit blits
	Information		Solid filled rectangles
	Information		8x8 mono pattern filled rectangles
	Information		8x8 color pattern filled rectangles
	Information		Solid Lines
	Information		Dashed Lines
	Information		Setting up tile and stipple cache:
	Information			31 128x128 slots
	Information			24 256x256 slots
	Information			7 512x512 slots
	Information			32 8x8 color pattern slots
	Default setting	CHROME(0): Backing store disabled
	Information	CHROME(0): - Backing store set up
	Information	CHROME(0): - SW cursor set up
	Information	CHROME(0): VIAHWCursorInit
	Information	CHROME(0): - Def Color map set up
	Information	CHROME(0): VIALoadPalette
	Information	CHROME(0): - Palette loaded
	Information	CHROME(0): DPMS enabled
	Information	CHROME(0): - DPMS set up
	Information	CHROME(0): - Color maps etc. set up
	Information	CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0204
	Information	CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
	Information	CHROME(0): [drm] Trying to enable AGP fast writes.
	Information	CHROME(0): [drm] drmAgpEnabled succeeded
	Information	CHROME(0): [drm] agpAddr = 0xe0000000
	Information	CHROME(0): [drm] agpBase = (nil)
	Information	CHROME(0): [drm] agpAddr = 0xe0000000
	Information	CHROME(0): [drm] agpSize = 0x01e00000
	Information	CHROME(0): [drm] agp physical addr = 0x00000000
	Information	CHROME(0): [dri] Using AGP.
	Information	CHROME(0): [drm] Using 45864928 bytes for DRM memory heap.
	Information	CHROME(0): [dri] Frame buffer initialized.
	Information	CHROME(0): [DRI] installation complete
	Information	CHROME(0): [dri] Kernel data initialized.
	Information	CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
	Information	CHROME(0): direct rendering enabled
	Information	CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
	Information	CHROME(0): Using default xfree86 memcpy for video.
	Information	CHROME(0): [XvMC] Registering chromeXvMC.
	Information	CHROME(0): [XvMC] Initialized XvMC extension.
	Information	CHROME(0): - Done
	Default setting	RandR enabled
	Information	Initializing built-in extension Generic Event Extension
	Information	Initializing built-in extension SHAPE
	Information	Initializing built-in extension MIT-SHM
	Information	Initializing built-in extension XInputExtension
	Information	Initializing built-in extension XTEST
	Information	Initializing built-in extension BIG-REQUESTS
	Information	Initializing built-in extension SYNC
	Information	Initializing built-in extension XKEYBOARD
	Information	Initializing built-in extension XC-MISC
	Information	Initializing built-in extension SECURITY
	Information	Initializing built-in extension XINERAMA
	Information	Initializing built-in extension XFIXES
	Information	Initializing built-in extension RENDER
	Information	Initializing built-in extension RANDR
	Information	Initializing built-in extension COMPOSITE
	Information	Initializing built-in extension DAMAGE
	Information	AIGLX: Screen 0 is not DRI2 capable
	Information	drmOpenDevice: node name is /dev/dri/card0
	Information	drmOpenDevice: open result is 12, (OK)
	Information	drmOpenByBusid: Searching for BusID PCI:1:0:0
	Information	drmOpenDevice: node name is /dev/dri/card0
	Information	drmOpenDevice: open result is 12, (OK)
	Information	drmOpenByBusid: drmOpenMinor returns 12
	Information	drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
	Information	AIGLX: enabled GLX_SGI_make_current_read
	Information	AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
	Information	GLX: Initialized DRI GL provider for screen 0
	Information	config/hal: Adding input device AT Translated Set 2 keyboard
	Information	LoadModule: "evdev"
	Information	Loading /usr/lib/xorg/modules/input//evdev_drv.so
	Information	Module evdev: vendor="X.Org Foundation"
	Information		compiled for 1.6.4, module version = 2.2.5
	Information		Module class: X.Org XInput Driver
	Information		ABI class: X.Org XInput driver, version 4.0
	From config file	AT Translated Set 2 keyboard: always reports core events
	From config file	AT Translated Set 2 keyboard: Device: "/dev/input/event3"
	Information	AT Translated Set 2 keyboard: Found keys
	Information	AT Translated Set 2 keyboard: Configuring as keyboard
	Information	XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
	From config file	Option "xkb_rules" "evdev"
	From config file	Option "xkb_model" "pc105"
	From config file	Option "xkb_layout" "us"
	Information	config/hal: Adding input device Power Button
	From config file	Power Button: always reports core events
	From config file	Power Button: Device: "/dev/input/event1"
	Information	Power Button: Found keys
	Information	Power Button: Configuring as keyboard
	Information	XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
	From config file	Option "xkb_rules" "evdev"
	From config file	Option "xkb_model" "pc105"
	From config file	Option "xkb_layout" "us"
	Information	config/hal: Adding input device Power Button
	From config file	Power Button: always reports core events
	From config file	Power Button: Device: "/dev/input/event0"
	Information	Power Button: Found keys
	Information	Power Button: Configuring as keyboard
	Information	XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
	From config file	Option "xkb_rules" "evdev"
	From config file	Option "xkb_model" "pc105"
	From config file	Option "xkb_layout" "us"
	Information	config/hal: Adding input device Macintosh mouse button emulation
	From config file	Macintosh mouse button emulation: always reports core events
	From config file	Macintosh mouse button emulation: Device: "/dev/input/event2"
	Information	Macintosh mouse button emulation: Found 3 mouse buttons
	Information	Macintosh mouse button emulation: Found x and y relative axes
	Information	Macintosh mouse button emulation: Configuring as mouse
	From config file	Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
	From config file	Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
	Information	XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
	From config file	Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
	From config file	Macintosh mouse button emulation: (accel) filter chain progression: 2.00
	From config file	Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
	From config file	Macintosh mouse button emulation: (accel) set acceleration profile 0
	Information	Macintosh mouse button emulation: initialized for relative axes.
	Information	config/hal: Adding input device Kensington MIAB Optical
	From config file	Kensington MIAB Optical: always reports core events
	From config file	Kensington MIAB Optical: Device: "/dev/input/event4"
	Information	Kensington MIAB Optical: Found 3 mouse buttons
	Information	Kensington MIAB Optical: Found x and y relative axes
	Information	Kensington MIAB Optical: Found scroll wheel(s)
	Information	Kensington MIAB Optical: Configuring as mouse
	From config file	Kensington MIAB Optical: YAxisMapping: buttons 4 and 5
	From config file	Kensington MIAB Optical: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
	Information	XINPUT: Adding extended input device "Kensington MIAB Optical" (type: MOUSE)
	From config file	Kensington MIAB Optical: (accel) keeping acceleration scheme 1
	From config file	Kensington MIAB Optical: (accel) filter chain progression: 2.00
	From config file	Kensington MIAB Optical: (accel) filter stage 0: 20.00 ms
	From config file	Kensington MIAB Optical: (accel) set acceleration profile 0
	Information	Kensington MIAB Optical: initialized for relative axes.
	Information	Open ACPI successful (/var/run/acpid.socket)
	Information	Freed 0 (pool 0)
	Information	Fulfilled via DRI at 20976640
	Information	Freed 0 (pool 0)
	Information	Fulfilled via DRI at 21652480
	Information	Freed 20976640 (pool 2)
	Information	Freed 21652480 (pool 2)

---

### Post by rmannon on 2009-10-12
And Kernal log:

2009-10-12 18:31:17	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:19	ksmserver[8673]	segfault at 8 ip 00007f336255732b sp 00007f3358e9f638 error 4 in libQtDBus.so.4.5.2[7f3362516000+6f000]
2009-10-12 18:31:20	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:20	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:20	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:23	ksmserver[8849]	segfault at 8 ip 00007f1b0f5af32b sp 00007f1b05ef7638 error 4 in libQtDBus.so.4.5.2[7f1b0f56e000+6f000]
2009-10-12 18:31:23	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:23	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:23	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:26	ksmserver[9025]	segfault at 8 ip 00007f310de6232b sp 00007f31047aa638 error 4 in libQtDBus.so.4.5.2[7f310de21000+6f000]
2009-10-12 18:31:26	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:26	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:26	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:29	ksmserver[9201]	segfault at 8 ip 00007f2b62b6132b sp 00007f2b594a9638 error 4 in libQtDBus.so.4.5.2[7f2b62b20000+6f000]
2009-10-12 18:31:29	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:29	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:29	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:32	ksmserver[9377]	segfault at 8 ip 00007fd0afd5d32b sp 00007fd0a66a5638 error 4 in libQtDBus.so.4.5.2[7fd0afd1c000+6f000]
2009-10-12 18:31:32	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:32	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:32	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:35	ksmserver[9553]	segfault at 8 ip 00007f5a23e3a32b sp 00007f5a1a782638 error 4 in libQtDBus.so.4.5.2[7f5a23df9000+6f000]
2009-10-12 18:31:36	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:36	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:36	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:38	ksmserver[9729]	segfault at 8 ip 00007f6735a5332b sp 00007f672c39b638 error 4 in libQtDBus.so.4.5.2[7f6735a12000+6f000]
2009-10-12 18:31:39	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:39	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:39	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:41	ksmserver[9905]	segfault at 8 ip 00007f1647a5132b sp 00007f163e399638 error 4 in libQtDBus.so.4.5.2[7f1647a10000+6f000]
2009-10-12 18:31:42	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:42	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:42	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:44	ksmserver[10081]	segfault at 8 ip 00007f238c3d732b sp 00007f2382d1f638 error 4 in libQtDBus.so.4.5.2[7f238c396000+6f000]
2009-10-12 18:31:45	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:45	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:45	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:47	ksmserver[10257]	segfault at 8 ip 00007f40e743432b sp 00007f40ddd7c638 error 4 in libQtDBus.so.4.5.2[7f40e73f3000+6f000]
2009-10-12 18:31:48	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:48	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:48	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:51	ksmserver[10433]	segfault at 8 ip 00007f1c9471432b sp 00007f1c8b05c638 error 4 in libQtDBus.so.4.5.2[7f1c946d3000+6f000]
2009-10-12 18:31:51	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:51	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:51	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:54	ksmserver[10609]	segfault at 8 ip 00007f633b45b32b sp 00007f6331da3638 error 4 in libQtDBus.so.4.5.2[7f633b41a000+6f000]
2009-10-12 18:31:54	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:54	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:54	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:57	ksmserver[10785]	segfault at 8 ip 00007f6b36a5a32b sp 00007f6b2d3a2638 error 4 in libQtDBus.so.4.5.2[7f6b36a19000+6f000]
2009-10-12 18:31:57	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:31:57	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:31:57	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:00	ksmserver[10961]	segfault at 8 ip 00007f6da57ab32b sp 00007f6d9c0f3638 error 4 in libQtDBus.so.4.5.2[7f6da576a000+6f000]
2009-10-12 18:32:00	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:00	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:00	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:03	ksmserver[11137]	segfault at 8 ip 00007f5a63d6e32b sp 00007f5a5a6b6638 error 4 in libQtDBus.so.4.5.2[7f5a63d2d000+6f000]
2009-10-12 18:32:04	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:04	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:04	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:06	ksmserver[11313]	segfault at 8 ip 00007ffb5b8b032b sp 00007ffb521f8638 error 4 in libQtDBus.so.4.5.2[7ffb5b86f000+6f000]
2009-10-12 18:32:07	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:07	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:07	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:09	ksmserver[11489]	segfault at 8 ip 00007ffb8035b32b sp 00007ffb76ca3638 error 4 in libQtDBus.so.4.5.2[7ffb8031a000+6f000]
2009-10-12 18:32:10	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:10	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:10	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:12	ksmserver[11665]	segfault at 8 ip 00007fecd0b0a32b sp 00007fecc7452638 error 4 in libQtDBus.so.4.5.2[7fecd0ac9000+6f000]
2009-10-12 18:32:13	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:13	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:13	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:15	ksmserver[11841]	segfault at 8 ip 00007f38a28c132b sp 00007f3899209638 error 4 in libQtDBus.so.4.5.2[7f38a2880000+6f000]
2009-10-12 18:32:16	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:16	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:16	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:19	ksmserver[12017]	segfault at 8 ip 00007f830ccc332b sp 00007f830360b638 error 4 in libQtDBus.so.4.5.2[7f830cc82000+6f000]
2009-10-12 18:32:19	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:19	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:19	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:22	ksmserver[12193]	segfault at 8 ip 00007fcf3ca6032b sp 00007fcf333a8638 error 4 in libQtDBus.so.4.5.2[7fcf3ca1f000+6f000]
2009-10-12 18:32:22	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:22	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:22	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:25	ksmserver[12369]	segfault at 8 ip 00007f27bc11132b sp 00007f27b2a59638 error 4 in libQtDBus.so.4.5.2[7f27bc0d0000+6f000]
2009-10-12 18:32:25	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:25	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:25	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:28	ksmserver[12545]	segfault at 8 ip 00007f42d2f5932b sp 00007f42c98a1638 error 4 in libQtDBus.so.4.5.2[7f42d2f18000+6f000]
2009-10-12 18:32:29	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:29	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:29	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:31	ksmserver[12721]	segfault at 8 ip 00007fd0d363732b sp 00007fd0c9f7f638 error 4 in libQtDBus.so.4.5.2[7fd0d35f6000+6f000]
2009-10-12 18:32:32	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:32	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:32	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:34	ksmserver[12897]	segfault at 8 ip 00007f11f329932b sp 00007f11e9be1638 error 4 in libQtDBus.so.4.5.2[7f11f3258000+6f000]
2009-10-12 18:32:35	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:35	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:35	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:37	ksmserver[13073]	segfault at 8 ip 00007f5f1251932b sp 00007f5f08e61638 error 4 in libQtDBus.so.4.5.2[7f5f124d8000+6f000]
2009-10-12 18:32:38	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:38	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:38	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:40	ksmserver[13249]	segfault at 8 ip 00007ff347e3432b sp 00007ff33e77c638 error 4 in libQtDBus.so.4.5.2[7ff347df3000+6f000]
2009-10-12 18:32:41	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:41	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:41	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:43	ksmserver[13425]	segfault at 8 ip 00007f961507332b sp 00007f960b9bb638 error 4 in libQtDBus.so.4.5.2[7f9615032000+6f000]
2009-10-12 18:32:44	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:44	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:44	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:47	ksmserver[13601]	segfault at 8 ip 00007f40a2a9632b sp 00007f40993de638 error 4 in libQtDBus.so.4.5.2[7f40a2a55000+6f000]
2009-10-12 18:32:47	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:47	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:47	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:50	ksmserver[13777]	segfault at 8 ip 00007f1bbdbdf32b sp 00007f1bb4527638 error 4 in libQtDBus.so.4.5.2[7f1bbdb9e000+6f000]
2009-10-12 18:32:50	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:50	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:50	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:53	ksmserver[13953]	segfault at 8 ip 00007f37430ca32b sp 00007f3739a12638 error 4 in libQtDBus.so.4.5.2[7f3743089000+6f000]
2009-10-12 18:32:53	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:53	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:53	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:56	ksmserver[14129]	segfault at 8 ip 00007f21f720532b sp 00007f21edb4d638 error 4 in libQtDBus.so.4.5.2[7f21f71c4000+6f000]
2009-10-12 18:32:57	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:32:57	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:57	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:32:59	ksmserver[14305]	segfault at 8 ip 00007fd637fc832b sp 00007fd62e910638 error 4 in libQtDBus.so.4.5.2[7fd637f87000+6f000]
2009-10-12 18:33:00	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:00	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:00	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:02	ksmserver[14481]	segfault at 8 ip 00007f45c2ba532b sp 00007f45b94ed638 error 4 in libQtDBus.so.4.5.2[7f45c2b64000+6f000]
2009-10-12 18:33:03	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:03	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:03	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:05	ksmserver[14657]	segfault at 8 ip 00007f4fb7a7232b sp 00007f4fae3ba638 error 4 in libQtDBus.so.4.5.2[7f4fb7a31000+6f000]
2009-10-12 18:33:06	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:06	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:06	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:08	ksmserver[14833]	segfault at 8 ip 00007f4c1caab32b sp 00007f4c133f3638 error 4 in libQtDBus.so.4.5.2[7f4c1ca6a000+6f000]
2009-10-12 18:33:09	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:09	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:09	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:12	ksmserver[15009]	segfault at 8 ip 00007f8a05e7c32b sp 00007f89fc7c4638 error 4 in libQtDBus.so.4.5.2[7f8a05e3b000+6f000]
2009-10-12 18:33:12	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:12	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:12	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:15	ksmserver[15185]	segfault at 8 ip 00007f5c22b8932b sp 00007f5c194d1638 error 4 in libQtDBus.so.4.5.2[7f5c22b48000+6f000]
2009-10-12 18:33:15	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:15	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:15	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:18	ksmserver[15361]	segfault at 8 ip 00007feae647532b sp 00007feadcdbd638 error 4 in libQtDBus.so.4.5.2[7feae6434000+6f000]
2009-10-12 18:33:18	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:18	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:18	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:21	ksmserver[15537]	segfault at 8 ip 00007f8a9154632b sp 00007f8a87e8e638 error 4 in libQtDBus.so.4.5.2[7f8a91505000+6f000]
2009-10-12 18:33:21	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:21	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:21	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:24	ksmserver[15713]	segfault at 8 ip 00007feb58c0732b sp 00007feb4f54f638 error 4 in libQtDBus.so.4.5.2[7feb58bc6000+6f000]
2009-10-12 18:33:25	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:25	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:25	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:27	ksmserver[15889]	segfault at 8 ip 00007f2a4c67032b sp 00007f2a42fb8638 error 4 in libQtDBus.so.4.5.2[7f2a4c62f000+6f000]
2009-10-12 18:33:28	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:28	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:28	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:30	ksmserver[16065]	segfault at 8 ip 00007f21b42ae32b sp 00007f21aabf6638 error 4 in libQtDBus.so.4.5.2[7f21b426d000+6f000]
2009-10-12 18:33:31	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:31	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:31	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:33	ksmserver[16241]	segfault at 8 ip 00007fe081df932b sp 00007fe078741638 error 4 in libQtDBus.so.4.5.2[7fe081db8000+6f000]
2009-10-12 18:33:34	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:34	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:34	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:36	ksmserver[16417]	segfault at 8 ip 00007f318220032b sp 00007f3178b48638 error 4 in libQtDBus.so.4.5.2[7f31821bf000+6f000]
2009-10-12 18:33:37	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:37	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:37	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:40	ksmserver[16593]	segfault at 8 ip 00007f3045f3932b sp 00007f303c881638 error 4 in libQtDBus.so.4.5.2[7f3045ef8000+6f000]
2009-10-12 18:33:40	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:40	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:40	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:43	ksmserver[16769]	segfault at 8 ip 00007f3cc024a32b sp 00007f3cb6b92638 error 4 in libQtDBus.so.4.5.2[7f3cc0209000+6f000]
2009-10-12 18:33:43	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:43	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:43	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:46	ksmserver[16945]	segfault at 8 ip 00007ffd3265632b sp 00007ffd28f9e638 error 4 in libQtDBus.so.4.5.2[7ffd32615000+6f000]
2009-10-12 18:33:46	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:46	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:46	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:49	ksmserver[17121]	segfault at 8 ip 00007f9a2e67c32b sp 00007f9a24fc4638 error 4 in libQtDBus.so.4.5.2[7f9a2e63b000+6f000]
2009-10-12 18:33:49	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:49	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:49	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:52	ksmserver[17297]	segfault at 8 ip 00007fe51a12c32b sp 00007fe510a74638 error 4 in libQtDBus.so.4.5.2[7fe51a0eb000+6f000]
2009-10-12 18:33:53	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:53	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:53	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:55	ksmserver[17473]	segfault at 8 ip 00007f84d763432b sp 00007f84cdf7c638 error 4 in libQtDBus.so.4.5.2[7f84d75f3000+6f000]
2009-10-12 18:33:56	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:56	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:56	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:58	ksmserver[17649]	segfault at 8 ip 00007f1ba1f7932b sp 00007f1b988c1638 error 4 in libQtDBus.so.4.5.2[7f1ba1f38000+6f000]
2009-10-12 18:33:59	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:33:59	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:33:59	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:01	ksmserver[17825]	segfault at 8 ip 00007f28593e132b sp 00007f284fd29638 error 4 in libQtDBus.so.4.5.2[7f28593a0000+6f000]
2009-10-12 18:34:02	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:02	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:02	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:04	ksmserver[18001]	segfault at 8 ip 00007f3f9296532b sp 00007f3f892ad638 error 4 in libQtDBus.so.4.5.2[7f3f92924000+6f000]
2009-10-12 18:34:05	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:05	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:05	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:08	ksmserver[18177]	segfault at 8 ip 00007f2a2ba2b32b sp 00007f2a22373638 error 4 in libQtDBus.so.4.5.2[7f2a2b9ea000+6f000]
2009-10-12 18:34:08	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:08	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:08	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:11	ksmserver[18353]	segfault at 8 ip 00007f97d185732b sp 00007f97c819f638 error 4 in libQtDBus.so.4.5.2[7f97d1816000+6f000]
2009-10-12 18:34:11	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:11	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:11	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:14	ksmserver[18529]	segfault at 8 ip 00007f24c61cf32b sp 00007f24bcb17638 error 4 in libQtDBus.so.4.5.2[7f24c618e000+6f000]
2009-10-12 18:34:14	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:14	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:14	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:17	ksmserver[18705]	segfault at 8 ip 00007f657972332b sp 00007f657006b638 error 4 in libQtDBus.so.4.5.2[7f65796e2000+6f000]
2009-10-12 18:34:17	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:17	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:17	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:20	ksmserver[18881]	segfault at 8 ip 00007fdf2df7e32b sp 00007fdf248c6638 error 4 in libQtDBus.so.4.5.2[7fdf2df3d000+6f000]
2009-10-12 18:34:21	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:21	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:21	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:23	ksmserver[19057]	segfault at 8 ip 00007f1d009e532b sp 00007f1cf732d638 error 4 in libQtDBus.so.4.5.2[7f1d009a4000+6f000]
2009-10-12 18:34:24	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:24	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:24	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:26	ksmserver[19233]	segfault at 8 ip 00007f381137632b sp 00007f3807cbe638 error 4 in libQtDBus.so.4.5.2[7f3811335000+6f000]
2009-10-12 18:34:27	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:27	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:27	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:29	ksmserver[19409]	segfault at 8 ip 00007f05f4d5532b sp 00007f05eb69d638 error 4 in libQtDBus.so.4.5.2[7f05f4d14000+6f000]
2009-10-12 18:34:30	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:30	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:30	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:32	ksmserver[19585]	segfault at 8 ip 00007f97e6eec32b sp 00007f97dd834638 error 4 in libQtDBus.so.4.5.2[7f97e6eab000+6f000]
2009-10-12 18:34:33	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:33	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:33	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:36	ksmserver[19761]	segfault at 8 ip 00007fad0471232b sp 00007facfb05a638 error 4 in libQtDBus.so.4.5.2[7fad046d1000+6f000]
2009-10-12 18:34:36	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:36	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:36	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:39	ksmserver[19937]	segfault at 8 ip 00007f2bb528c32b sp 00007f2babbd4638 error 4 in libQtDBus.so.4.5.2[7f2bb524b000+6f000]
2009-10-12 18:34:39	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:39	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:39	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:42	ksmserver[20113]	segfault at 8 ip 00007f38a273432b sp 00007f389907c638 error 4 in libQtDBus.so.4.5.2[7f38a26f3000+6f000]
2009-10-12 18:34:42	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:42	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:42	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:45	ksmserver[20289]	segfault at 8 ip 00007fab710ab32b sp 00007fab679f3638 error 4 in libQtDBus.so.4.5.2[7fab7106a000+6f000]
2009-10-12 18:34:46	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:46	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:46	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:48	ksmserver[20465]	segfault at 8 ip 00007ffff144932b sp 00007fffe7e12638 error 4 in libQtDBus.so.4.5.2[7ffff1408000+6f000]
2009-10-12 18:34:49	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:49	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:49	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:51	ksmserver[20641]	segfault at 8 ip 00007f942457d32b sp 00007f941aec5638 error 4 in libQtDBus.so.4.5.2[7f942453c000+6f000]
2009-10-12 18:34:52	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:52	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:52	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:54	ksmserver[20817]	segfault at 8 ip 00007f15f227f32b sp 00007f15e8bc7638 error 4 in libQtDBus.so.4.5.2[7f15f223e000+6f000]
2009-10-12 18:34:55	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:55	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:55	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:57	ksmserver[20993]	segfault at 8 ip 00007f30c3af532b sp 00007f30ba43d638 error 4 in libQtDBus.so.4.5.2[7f30c3ab4000+6f000]
2009-10-12 18:34:58	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:34:58	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:34:58	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:00	ksmserver[21169]	segfault at 8 ip 00007f29d075832b sp 00007f29c70a0638 error 4 in libQtDBus.so.4.5.2[7f29d0717000+6f000]
2009-10-12 18:35:01	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:01	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:01	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:04	ksmserver[21345]	segfault at 8 ip 00007f3d7cef332b sp 00007f3d7383b638 error 4 in libQtDBus.so.4.5.2[7f3d7ceb2000+6f000]
2009-10-12 18:35:04	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:04	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:04	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:07	ksmserver[21521]	segfault at 8 ip 00007f5acc36232b sp 00007f5ac2caa638 error 4 in libQtDBus.so.4.5.2[7f5acc321000+6f000]
2009-10-12 18:35:07	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:07	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:07	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:10	ksmserver[21697]	segfault at 8 ip 00007f31d6fd032b sp 00007f31cd918638 error 4 in libQtDBus.so.4.5.2[7f31d6f8f000+6f000]
2009-10-12 18:35:10	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:10	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:10	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:13	ksmserver[21873]	segfault at 8 ip 00007f35739a032b sp 00007f356a2e8638 error 4 in libQtDBus.so.4.5.2[7f357395f000+6f000]
2009-10-12 18:35:14	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:14	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:14	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:16	ksmserver[22049]	segfault at 8 ip 00007fc21b3e432b sp 00007fc211d2c638 error 4 in libQtDBus.so.4.5.2[7fc21b3a3000+6f000]
2009-10-12 18:35:17	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:17	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:17	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:19	ksmserver[22225]	segfault at 8 ip 00007fcad19be32b sp 00007fcac8306638 error 4 in libQtDBus.so.4.5.2[7fcad197d000+6f000]
2009-10-12 18:35:20	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:20	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:20	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:22	ksmserver[22401]	segfault at 8 ip 00007f3e82d4932b sp 00007f3e79691638 error 4 in libQtDBus.so.4.5.2[7f3e82d08000+6f000]
2009-10-12 18:35:23	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:23	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:23	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:25	ksmserver[22577]	segfault at 8 ip 00007fb82197c32b sp 00007fb8182c4638 error 4 in libQtDBus.so.4.5.2[7fb82193b000+6f000]
2009-10-12 18:35:26	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:26	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:26	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:29	ksmserver[22753]	segfault at 8 ip 00007f4636bbb32b sp 00007f462d503638 error 4 in libQtDBus.so.4.5.2[7f4636b7a000+6f000]
2009-10-12 18:35:29	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:29	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:29	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:32	ksmserver[22929]	segfault at 8 ip 00007f337cc3f32b sp 00007f3373587638 error 4 in libQtDBus.so.4.5.2[7f337cbfe000+6f000]
2009-10-12 18:35:32	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:32	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:32	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:35	ksmserver[23105]	segfault at 8 ip 00007f9085e1a32b sp 00007f907c762638 error 4 in libQtDBus.so.4.5.2[7f9085dd9000+6f000]
2009-10-12 18:35:35	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:35	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:35	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:38	ksmserver[23281]	segfault at 8 ip 00007fa5f415a32b sp 00007fa5eaaa2638 error 4 in libQtDBus.so.4.5.2[7fa5f4119000+6f000]
2009-10-12 18:35:38	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:38	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:38	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:41	ksmserver[23457]	segfault at 8 ip 00007f928151032b sp 00007f9277e58638 error 4 in libQtDBus.so.4.5.2[7f92814cf000+6f000]
2009-10-12 18:35:42	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:42	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:42	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:44	ksmserver[23633]	segfault at 8 ip 00007f1f0623132b sp 00007f1efcb79638 error 4 in libQtDBus.so.4.5.2[7f1f061f0000+6f000]
2009-10-12 18:35:45	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:45	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:45	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:47	ksmserver[23809]	segfault at 8 ip 00007f896e51832b sp 00007f8964e60638 error 4 in libQtDBus.so.4.5.2[7f896e4d7000+6f000]
2009-10-12 18:35:48	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:48	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:48	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:50	ksmserver[23985]	segfault at 8 ip 00007ffb0ac6532b sp 00007ffb015ad638 error 4 in libQtDBus.so.4.5.2[7ffb0ac24000+6f000]
2009-10-12 18:35:51	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:51	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:51	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:53	ksmserver[24161]	segfault at 8 ip 00007ff806fe232b sp 00007ff7fd92a638 error 4 in libQtDBus.so.4.5.2[7ff806fa1000+6f000]
2009-10-12 18:35:54	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:54	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:54	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:57	ksmserver[24337]	segfault at 8 ip 00007f3b65e3732b sp 00007f3b5c77f638 error 4 in libQtDBus.so.4.5.2[7f3b65df6000+6f000]
2009-10-12 18:35:57	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:35:57	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:35:57	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:00	ksmserver[24513]	segfault at 8 ip 00007f9dba67532b sp 00007f9db0fbd638 error 4 in libQtDBus.so.4.5.2[7f9dba634000+6f000]
2009-10-12 18:36:00	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:00	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:00	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:03	ksmserver[24689]	segfault at 8 ip 00007fc53e2c632b sp 00007fc534c0e638 error 4 in libQtDBus.so.4.5.2[7fc53e285000+6f000]
2009-10-12 18:36:03	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:03	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:03	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:06	ksmserver[24865]	segfault at 8 ip 00007f576e8ab32b sp 00007f57651f3638 error 4 in libQtDBus.so.4.5.2[7f576e86a000+6f000]
2009-10-12 18:36:06	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:06	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:06	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:09	ksmserver[25041]	segfault at 8 ip 00007fc0922bf32b sp 00007fc088c07638 error 4 in libQtDBus.so.4.5.2[7fc09227e000+6f000]
2009-10-12 18:36:10	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:10	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:10	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:12	ksmserver[25217]	segfault at 8 ip 00007f9e3af8a32b sp 00007f9e318d2638 error 4 in libQtDBus.so.4.5.2[7f9e3af49000+6f000]
2009-10-12 18:36:13	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:13	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:13	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:15	ksmserver[25393]	segfault at 8 ip 00007f96f80ab32b sp 00007f96ee9f3638 error 4 in libQtDBus.so.4.5.2[7f96f806a000+6f000]
2009-10-12 18:36:16	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:16	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:16	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:18	ksmserver[25569]	segfault at 8 ip 00007ffba3a0932b sp 00007ffb9a351638 error 4 in libQtDBus.so.4.5.2[7ffba39c8000+6f000]
2009-10-12 18:36:19	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:19	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:19	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:21	ksmserver[25745]	segfault at 8 ip 00007f6db63db32b sp 00007f6dacd23638 error 4 in libQtDBus.so.4.5.2[7f6db639a000+6f000]
2009-10-12 18:36:22	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:22	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:22	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:25	ksmserver[25921]	segfault at 8 ip 00007f34869de32b sp 00007f347d326638 error 4 in libQtDBus.so.4.5.2[7f348699d000+6f000]
2009-10-12 18:36:25	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:25	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:25	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:28	ksmserver[26097]	segfault at 8 ip 00007f59f291532b sp 00007f59e925d638 error 4 in libQtDBus.so.4.5.2[7f59f28d4000+6f000]
2009-10-12 18:36:28	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:28	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:28	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:31	ksmserver[26273]	segfault at 8 ip 00007fabc90de32b sp 00007fabbfa26638 error 4 in libQtDBus.so.4.5.2[7fabc909d000+6f000]
2009-10-12 18:36:31	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:31	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:31	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:34	ksmserver[26449]	segfault at 8 ip 00007f01e2fd432b sp 00007f01d991c638 error 4 in libQtDBus.so.4.5.2[7f01e2f93000+6f000]
2009-10-12 18:36:35	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:35	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:35	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:37	ksmserver[26625]	segfault at 8 ip 00007f17956d732b sp 00007f178c01f638 error 4 in libQtDBus.so.4.5.2[7f1795696000+6f000]
2009-10-12 18:36:38	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:38	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:38	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:40	ksmserver[26801]	segfault at 8 ip 00007ffc7a9e932b sp 00007ffc71331638 error 4 in libQtDBus.so.4.5.2[7ffc7a9a8000+6f000]
2009-10-12 18:36:41	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:41	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:41	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:43	ksmserver[26977]	segfault at 8 ip 00007f5b8675a32b sp 00007f5b7d0a2638 error 4 in libQtDBus.so.4.5.2[7f5b86719000+6f000]
2009-10-12 18:36:44	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:44	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:44	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:46	ksmserver[27153]	segfault at 8 ip 00007fa66330232b sp 00007fa659c4a638 error 4 in libQtDBus.so.4.5.2[7fa6632c1000+6f000]
2009-10-12 18:36:47	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:47	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:47	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:50	ksmserver[27329]	segfault at 8 ip 00007f21690bb32b sp 00007f215fa03638 error 4 in libQtDBus.so.4.5.2[7f216907a000+6f000]
2009-10-12 18:36:50	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:50	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:50	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:53	ksmserver[27505]	segfault at 8 ip 00007feb735ea32b sp 00007feb69f32638 error 4 in libQtDBus.so.4.5.2[7feb735a9000+6f000]
2009-10-12 18:36:53	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:53	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:53	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:56	ksmserver[27681]	segfault at 8 ip 00007fcd6f9a232b sp 00007fcd662ea638 error 4 in libQtDBus.so.4.5.2[7fcd6f961000+6f000]
2009-10-12 18:36:56	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:56	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:56	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:59	ksmserver[27857]	segfault at 8 ip 00007f722280032b sp 00007f7219148638 error 4 in libQtDBus.so.4.5.2[7f72227bf000+6f000]
2009-10-12 18:36:59	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:36:59	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:36:59	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:02	ksmserver[28033]	segfault at 8 ip 00007f2dc855832b sp 00007f2dbeea0638 error 4 in libQtDBus.so.4.5.2[7f2dc8517000+6f000]
2009-10-12 18:37:03	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:03	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:03	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:05	ksmserver[28209]	segfault at 8 ip 00007faabc59332b sp 00007faab2edb638 error 4 in libQtDBus.so.4.5.2[7faabc552000+6f000]
2009-10-12 18:37:06	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:06	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:06	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:08	ksmserver[28385]	segfault at 8 ip 00007f6e5b5a532b sp 00007f6e51eed638 error 4 in libQtDBus.so.4.5.2[7f6e5b564000+6f000]
2009-10-12 18:37:09	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:09	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:09	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:11	ksmserver[28561]	segfault at 8 ip 00007fa10d96132b sp 00007fa1042a9638 error 4 in libQtDBus.so.4.5.2[7fa10d920000+6f000]
2009-10-12 18:37:12	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:12	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:12	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:14	ksmserver[28737]	segfault at 8 ip 00007faca7f8632b sp 00007fac9e8ce638 error 4 in libQtDBus.so.4.5.2[7faca7f45000+6f000]
2009-10-12 18:37:15	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:15	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:15	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:18	ksmserver[28913]	segfault at 8 ip 00007fb02635332b sp 00007fb01cc9b638 error 4 in libQtDBus.so.4.5.2[7fb026312000+6f000]
2009-10-12 18:37:18	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:18	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:18	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:21	ksmserver[29089]	segfault at 8 ip 00007f2e54d0732b sp 00007f2e4b64f638 error 4 in libQtDBus.so.4.5.2[7f2e54cc6000+6f000]
2009-10-12 18:37:21	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:21	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:21	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:24	ksmserver[29265]	segfault at 8 ip 00007fbdb7cd932b sp 00007fbdae621638 error 4 in libQtDBus.so.4.5.2[7fbdb7c98000+6f000]
2009-10-12 18:37:24	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:24	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:24	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:27	ksmserver[29441]	segfault at 8 ip 00007ff65b61a32b sp 00007ff651f62638 error 4 in libQtDBus.so.4.5.2[7ff65b5d9000+6f000]
2009-10-12 18:37:27	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:27	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:27	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:30	ksmserver[29617]	segfault at 8 ip 00007f402089a32b sp 00007f40171e2638 error 4 in libQtDBus.so.4.5.2[7f4020859000+6f000]
2009-10-12 18:37:31	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:31	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:31	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:33	ksmserver[29793]	segfault at 8 ip 00007f96dec9532b sp 00007f96d55dd638 error 4 in libQtDBus.so.4.5.2[7f96dec54000+6f000]
2009-10-12 18:37:34	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:34	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:34	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:36	ksmserver[29969]	segfault at 8 ip 00007f6dfeadf32b sp 00007f6df5427638 error 4 in libQtDBus.so.4.5.2[7f6dfea9e000+6f000]
2009-10-12 18:37:37	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:37	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:37	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:39	ksmserver[30145]	segfault at 8 ip 00007f28982ec32b sp 00007f288ec34638 error 4 in libQtDBus.so.4.5.2[7f28982ab000+6f000]
2009-10-12 18:37:40	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:40	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:40	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:42	ksmserver[30321]	segfault at 8 ip 00007faf1705232b sp 00007faf0d99a638 error 4 in libQtDBus.so.4.5.2[7faf17011000+6f000]
2009-10-12 18:37:43	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:43	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:43	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:46	ksmserver[30497]	segfault at 8 ip 00007f076f1c132b sp 00007f0765b09638 error 4 in libQtDBus.so.4.5.2[7f076f180000+6f000]
2009-10-12 18:37:46	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:46	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:46	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:49	ksmserver[30673]	segfault at 8 ip 00007fbdf53e432b sp 00007fbdebd2c638 error 4 in libQtDBus.so.4.5.2[7fbdf53a3000+6f000]
2009-10-12 18:37:49	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:49	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:49	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:52	ksmserver[30849]	segfault at 8 ip 00007fe0fabc532b sp 00007fe0f150d638 error 4 in libQtDBus.so.4.5.2[7fe0fab84000+6f000]
2009-10-12 18:37:52	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:52	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:52	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:55	ksmserver[31025]	segfault at 8 ip 00007f99bd84232b sp 00007f99b418a638 error 4 in libQtDBus.so.4.5.2[7f99bd801000+6f000]
2009-10-12 18:37:56	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:56	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:56	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:58	ksmserver[31201]	segfault at 8 ip 00007fdb2edf432b sp 00007fdb2573c638 error 4 in libQtDBus.so.4.5.2[7fdb2edb3000+6f000]
2009-10-12 18:37:59	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:37:59	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:37:59	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:01	ksmserver[31377]	segfault at 8 ip 00007f475dc8232b sp 00007f47545ca638 error 4 in libQtDBus.so.4.5.2[7f475dc41000+6f000]
2009-10-12 18:38:02	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:02	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:02	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:04	ksmserver[31553]	segfault at 8 ip 00007fef9c0a832b sp 00007fef929f0638 error 4 in libQtDBus.so.4.5.2[7fef9c067000+6f000]
2009-10-12 18:38:05	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:05	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:05	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:07	ksmserver[31729]	segfault at 8 ip 00007f980ad8332b sp 00007f98016cb638 error 4 in libQtDBus.so.4.5.2[7f980ad42000+6f000]
2009-10-12 18:38:08	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:08	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:08	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:11	ksmserver[31905]	segfault at 8 ip 00007f0a40fcf32b sp 00007f0a37917638 error 4 in libQtDBus.so.4.5.2[7f0a40f8e000+6f000]
2009-10-12 18:38:11	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:11	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:11	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:14	ksmserver[32081]	segfault at 8 ip 00007f30c159932b sp 00007f30b7ee1638 error 4 in libQtDBus.so.4.5.2[7f30c1558000+6f000]
2009-10-12 18:38:14	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:14	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:14	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:17	ksmserver[32257]	segfault at 8 ip 00007f2741f0f32b sp 00007f2738857638 error 4 in libQtDBus.so.4.5.2[7f2741ece000+6f000]
2009-10-12 18:38:17	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:17	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:17	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:20	ksmserver[32433]	segfault at 8 ip 00007f6c506ce32b sp 00007f6c47016638 error 4 in libQtDBus.so.4.5.2[7f6c5068d000+6f000]
2009-10-12 18:38:20	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:20	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:20	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:23	ksmserver[32609]	segfault at 8 ip 00007f600c22132b sp 00007f6002b69638 error 4 in libQtDBus.so.4.5.2[7f600c1e0000+6f000]
2009-10-12 18:38:24	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:24	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:24	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:26	ksmserver[317]	segfault at 8 ip 00007f3fbd3d032b sp 00007f3fb3d18638 error 4 in libQtDBus.so.4.5.2[7f3fbd38f000+6f000]
2009-10-12 18:38:27	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:27	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:27	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:29	ksmserver[500]	segfault at 8 ip 00007fde93d6d32b sp 00007fde8a6b5638 error 4 in libQtDBus.so.4.5.2[7fde93d2c000+6f000]
2009-10-12 18:38:30	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:30	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:30	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:32	ksmserver[683]	segfault at 8 ip 00007fb85231c32b sp 00007fb848c64638 error 4 in libQtDBus.so.4.5.2[7fb8522db000+6f000]
2009-10-12 18:38:33	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:33	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:33	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:35	ksmserver[865]	segfault at 8 ip 00007f86f1f0e32b sp 00007f86e8856638 error 4 in libQtDBus.so.4.5.2[7f86f1ecd000+6f000]
2009-10-12 18:38:36	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:36	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:36	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:39	ksmserver[1114]	segfault at 8 ip 00007f4f461e632b sp 00007f4f3cb2e638 error 4 in libQtDBus.so.4.5.2[7f4f461a5000+6f000]
2009-10-12 18:38:39	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:39	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:39	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:42	ksmserver[1294]	segfault at 8 ip 00007fce553e132b sp 00007fce4bd29638 error 4 in libQtDBus.so.4.5.2[7fce553a0000+6f000]
2009-10-12 18:38:42	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:42	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:42	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:45	ksmserver[1471]	segfault at 8 ip 00007fbff51f932b sp 00007fbfebb41638 error 4 in libQtDBus.so.4.5.2[7fbff51b8000+6f000]
2009-10-12 18:38:45	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:45	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:45	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:48	ksmserver[1647]	segfault at 8 ip 00007ffe7395032b sp 00007ffe6a298638 error 4 in libQtDBus.so.4.5.2[7ffe7390f000+6f000]
2009-10-12 18:38:48	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:48	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:48	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:51	ksmserver[1823]	segfault at 8 ip 00007fb7c24a632b sp 00007fb7b8dee638 error 4 in libQtDBus.so.4.5.2[7fb7c2465000+6f000]
2009-10-12 18:38:52	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:52	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:52	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:54	ksmserver[1999]	segfault at 8 ip 00007fe82434032b sp 00007fe81ac88638 error 4 in libQtDBus.so.4.5.2[7fe8242ff000+6f000]
2009-10-12 18:38:55	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:55	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:55	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:58	ksmserver[2175]	segfault at 8 ip 00007f1439cbd32b sp 00007f1430605638 error 4 in libQtDBus.so.4.5.2[7f1439c7c000+6f000]
2009-10-12 18:38:58	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:38:58	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:38:58	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:01	ksmserver[2351]	segfault at 8 ip 00007f22f8cc332b sp 00007f22ef60b638 error 4 in libQtDBus.so.4.5.2[7f22f8c82000+6f000]
2009-10-12 18:39:01	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:01	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:01	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:04	ksmserver[2527]	segfault at 8 ip 00007f2702e2132b sp 00007f26f9769638 error 4 in libQtDBus.so.4.5.2[7f2702de0000+6f000]
2009-10-12 18:39:04	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:04	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:04	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:07	ksmserver[2703]	segfault at 8 ip 00007f16ac4e732b sp 00007f16a2e2f638 error 4 in libQtDBus.so.4.5.2[7f16ac4a6000+6f000]
2009-10-12 18:39:07	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:07	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:07	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:10	ksmserver[2879]	segfault at 8 ip 00007ff2e2e0a32b sp 00007ff2d9752638 error 4 in libQtDBus.so.4.5.2[7ff2e2dc9000+6f000]
2009-10-12 18:39:11	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:11	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:11	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:13	ksmserver[3055]	segfault at 8 ip 00007feafade032b sp 00007feaf1728638 error 4 in libQtDBus.so.4.5.2[7feafad9f000+6f000]
2009-10-12 18:39:14	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:14	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:14	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:16	ksmserver[3234]	segfault at 8 ip 00007f113937232b sp 00007f112fcba638 error 4 in libQtDBus.so.4.5.2[7f1139331000+6f000]
2009-10-12 18:39:17	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:17	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:17	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:19	ksmserver[3410]	segfault at 8 ip 00007f6cb312e32b sp 00007f6ca9a76638 error 4 in libQtDBus.so.4.5.2[7f6cb30ed000+6f000]
2009-10-12 18:39:20	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:20	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:20	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:22	ksmserver[3586]	segfault at 8 ip 00007f0ce159232b sp 00007f0cd7eda638 error 4 in libQtDBus.so.4.5.2[7f0ce1551000+6f000]
2009-10-12 18:39:23	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:23	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:23	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:26	ksmserver[3762]	segfault at 8 ip 00007f0d5e8d232b sp 00007f0d5521a638 error 4 in libQtDBus.so.4.5.2[7f0d5e891000+6f000]
2009-10-12 18:39:26	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:26	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:26	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:29	ksmserver[3938]	segfault at 8 ip 00007ffe5f3c732b sp 00007ffe55d0f638 error 4 in libQtDBus.so.4.5.2[7ffe5f386000+6f000]
2009-10-12 18:39:29	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:29	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:29	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:32	ksmserver[4114]	segfault at 8 ip 00007f62ce3e932b sp 00007f62c4d31638 error 4 in libQtDBus.so.4.5.2[7f62ce3a8000+6f000]
2009-10-12 18:39:32	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:32	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:32	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:35	ksmserver[4290]	segfault at 8 ip 00007f0599d7532b sp 00007f05906bd638 error 4 in libQtDBus.so.4.5.2[7f0599d34000+6f000]
2009-10-12 18:39:36	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:36	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:36	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:38	ksmserver[4466]	segfault at 8 ip 00007fee710b732b sp 00007fee679ff638 error 4 in libQtDBus.so.4.5.2[7fee71076000+6f000]
2009-10-12 18:39:39	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:39	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:39	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:41	ksmserver[4643]	segfault at 8 ip 00007fadb27ab32b sp 00007fada90f3638 error 4 in libQtDBus.so.4.5.2[7fadb276a000+6f000]
2009-10-12 18:39:42	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:42	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:42	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:44	ksmserver[4819]	segfault at 8 ip 00007f178e7bb32b sp 00007f1785103638 error 4 in libQtDBus.so.4.5.2[7f178e77a000+6f000]
2009-10-12 18:39:45	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:45	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:45	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:47	ksmserver[4995]	segfault at 8 ip 00007f1506d6c32b sp 00007f14fd6b4638 error 4 in libQtDBus.so.4.5.2[7f1506d2b000+6f000]
2009-10-12 18:39:48	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:48	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:48	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:51	ksmserver[5171]	segfault at 8 ip 00007ff85e96232b sp 00007ff8552aa638 error 4 in libQtDBus.so.4.5.2[7ff85e921000+6f000]
2009-10-12 18:39:51	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:51	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:51	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:54	ksmserver[5347]	segfault at 8 ip 00007f1f46a8732b sp 00007f1f3d3cf638 error 4 in libQtDBus.so.4.5.2[7f1f46a46000+6f000]
2009-10-12 18:39:54	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:54	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:54	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:57	ksmserver[5524]	segfault at 8 ip 00007f2acfd3532b sp 00007f2ac667d638 error 4 in libQtDBus.so.4.5.2[7f2acfcf4000+6f000]
2009-10-12 18:39:57	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:39:57	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:39:57	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:00	ksmserver[5700]	segfault at 8 ip 00007f55c512532b sp 00007f55bba6d638 error 4 in libQtDBus.so.4.5.2[7f55c50e4000+6f000]
2009-10-12 18:40:00	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:00	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:00	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:03	ksmserver[5876]	segfault at 8 ip 00007f6509dac32b sp 00007f65006f4638 error 4 in libQtDBus.so.4.5.2[7f6509d6b000+6f000]
2009-10-12 18:40:04	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:04	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:04	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:06	ksmserver[6054]	segfault at 8 ip 00007f16dcb1632b sp 00007f16d345e638 error 4 in libQtDBus.so.4.5.2[7f16dcad5000+6f000]
2009-10-12 18:40:07	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:07	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:07	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:09	ksmserver[6230]	segfault at 8 ip 00007f64a1be932b sp 00007f6498531638 error 4 in libQtDBus.so.4.5.2[7f64a1ba8000+6f000]
2009-10-12 18:40:10	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:10	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:10	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:12	ksmserver[6406]	segfault at 8 ip 00007f8c2200a32b sp 00007f8c18952638 error 4 in libQtDBus.so.4.5.2[7f8c21fc9000+6f000]
2009-10-12 18:40:13	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:13	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:13	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:15	ksmserver[6582]	segfault at 8 ip 00007f357bfd332b sp 00007f357291b638 error 4 in libQtDBus.so.4.5.2[7f357bf92000+6f000]
2009-10-12 18:40:16	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:16	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:16	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:19	ksmserver[6758]	segfault at 8 ip 00007f6c355e632b sp 00007f6c2bf2e638 error 4 in libQtDBus.so.4.5.2[7f6c355a5000+6f000]
2009-10-12 18:40:19	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:19	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:19	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:22	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:22	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:22	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:25	ksmserver[7109]	segfault at 8 ip 00007f02e2a0232b sp 00007f02d934a638 error 4 in libQtDBus.so.4.5.2[7f02e29c1000+6f000]
2009-10-12 18:40:25	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:25	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:25	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:28	ksmserver[7285]	segfault at 8 ip 00007fe49639932b sp 00007fe48cce1638 error 4 in libQtDBus.so.4.5.2[7fe496358000+6f000]
2009-10-12 18:40:28	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:28	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:28	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:31	ksmserver[7461]	segfault at 8 ip 00007fb93ada232b sp 00007fb9316ea638 error 4 in libQtDBus.so.4.5.2[7fb93ad61000+6f000]
2009-10-12 18:40:31	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:31	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:31	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:34	ksmserver[7637]	segfault at 8 ip 00007fdca989132b sp 00007fdca01d9638 error 4 in libQtDBus.so.4.5.2[7fdca9850000+6f000]
2009-10-12 18:40:35	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:35	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:35	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:37	ksmserver[7813]	segfault at 8 ip 00007f0dc6fe832b sp 00007f0dbd930638 error 4 in libQtDBus.so.4.5.2[7f0dc6fa7000+6f000]
2009-10-12 18:40:38	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:38	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:38	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:40	ksmserver[7989]	segfault at 8 ip 00007f2976d4732b sp 00007f296d68f638 error 4 in libQtDBus.so.4.5.2[7f2976d06000+6f000]
2009-10-12 18:40:41	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:41	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:41	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:43	ksmserver[8165]	segfault at 8 ip 00007f2ae39d232b sp 00007f2ada31a638 error 4 in libQtDBus.so.4.5.2[7f2ae3991000+6f000]
2009-10-12 18:40:44	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:44	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:44	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:46	ksmserver[8341]	segfault at 8 ip 00007f8320ae332b sp 00007f831742b638 error 4 in libQtDBus.so.4.5.2[7f8320aa2000+6f000]
2009-10-12 18:40:47	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:47	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:47	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:50	ksmserver[8517]	segfault at 8 ip 00007fe7e57e032b sp 00007fe7dc128638 error 4 in libQtDBus.so.4.5.2[7fe7e579f000+6f000]
2009-10-12 18:40:50	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:50	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:50	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:53	ksmserver[8693]	segfault at 8 ip 00007fc87141f32b sp 00007fc867d67638 error 4 in libQtDBus.so.4.5.2[7fc8713de000+6f000]
2009-10-12 18:40:53	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:53	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:53	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:56	ksmserver[8869]	segfault at 8 ip 00007f02603de32b sp 00007f0256d26638 error 4 in libQtDBus.so.4.5.2[7f026039d000+6f000]
2009-10-12 18:40:56	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:56	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:56	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:59	ksmserver[9045]	segfault at 8 ip 00007f0baebb032b sp 00007f0ba54f8638 error 4 in libQtDBus.so.4.5.2[7f0baeb6f000+6f000]
2009-10-12 18:40:59	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:40:59	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:40:59	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:02	ksmserver[9221]	segfault at 8 ip 00007fc0d846932b sp 00007fc0cedb1638 error 4 in libQtDBus.so.4.5.2[7fc0d8428000+6f000]
2009-10-12 18:41:03	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:03	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:03	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:05	ksmserver[9397]	segfault at 8 ip 00007fe49a37332b sp 00007fe490cbb638 error 4 in libQtDBus.so.4.5.2[7fe49a332000+6f000]
2009-10-12 18:41:06	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:06	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:06	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:08	ksmserver[9573]	segfault at 8 ip 00007f87ece8732b sp 00007f87e37cf638 error 4 in libQtDBus.so.4.5.2[7f87ece46000+6f000]
2009-10-12 18:41:09	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:09	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:09	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:11	ksmserver[9749]	segfault at 8 ip 00007fcb6d55b32b sp 00007fcb63ea3638 error 4 in libQtDBus.so.4.5.2[7fcb6d51a000+6f000]
2009-10-12 18:41:12	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:12	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:12	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:14	ksmserver[9925]	segfault at 8 ip 00007f525fa1c32b sp 00007f5256364638 error 4 in libQtDBus.so.4.5.2[7f525f9db000+6f000]
2009-10-12 18:41:15	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:15	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:15	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:18	ksmserver[10101]	segfault at 8 ip 00007f98d7b7432b sp 00007f98ce4bc638 error 4 in libQtDBus.so.4.5.2[7f98d7b33000+6f000]
2009-10-12 18:41:18	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:18	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:18	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:21	ksmserver[10277]	segfault at 8 ip 00007fa833e1732b sp 00007fa82a75f638 error 4 in libQtDBus.so.4.5.2[7fa833dd6000+6f000]
2009-10-12 18:41:21	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:21	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:21	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:24	ksmserver[10453]	segfault at 8 ip 00007f8252c6832b sp 00007f82495b0638 error 4 in libQtDBus.so.4.5.2[7f8252c27000+6f000]
2009-10-12 18:41:24	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:24	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:24	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:27	ksmserver[10629]	segfault at 8 ip 00007f4ab7d7332b sp 00007f4aae6bb638 error 4 in libQtDBus.so.4.5.2[7f4ab7d32000+6f000]
2009-10-12 18:41:28	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:28	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:28	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:30	ksmserver[10805]	segfault at 8 ip 00007fa680a0532b sp 00007fa67734d638 error 4 in libQtDBus.so.4.5.2[7fa6809c4000+6f000]
2009-10-12 18:41:31	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:31	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:31	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:33	ksmserver[10981]	segfault at 8 ip 00007f8abf15732b sp 00007f8ab5a9f638 error 4 in libQtDBus.so.4.5.2[7f8abf116000+6f000]
2009-10-12 18:41:34	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:34	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:34	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:36	ksmserver[11157]	segfault at 8 ip 00007f1abd5ba32b sp 00007f1ab3f02638 error 4 in libQtDBus.so.4.5.2[7f1abd579000+6f000]
2009-10-12 18:41:37	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:37	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:37	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:39	ksmserver[11333]	segfault at 8 ip 00007f5685dca32b sp 00007f567c712638 error 4 in libQtDBus.so.4.5.2[7f5685d89000+6f000]
2009-10-12 18:41:40	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:40	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:40	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:43	ksmserver[11509]	segfault at 8 ip 00007f73d903632b sp 00007f73cf97e638 error 4 in libQtDBus.so.4.5.2[7f73d8ff5000+6f000]
2009-10-12 18:41:43	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:43	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:43	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:46	ksmserver[11685]	segfault at 8 ip 00007f4c5340132b sp 00007f4c49d49638 error 4 in libQtDBus.so.4.5.2[7f4c533c0000+6f000]
2009-10-12 18:41:46	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:46	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:46	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:49	ksmserver[11861]	segfault at 8 ip 00007fc26b53c32b sp 00007fc261e84638 error 4 in libQtDBus.so.4.5.2[7fc26b4fb000+6f000]
2009-10-12 18:41:49	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:49	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:49	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:52	ksmserver[12037]	segfault at 8 ip 00007f399a18132b sp 00007f3990ac9638 error 4 in libQtDBus.so.4.5.2[7f399a140000+6f000]
2009-10-12 18:41:52	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:52	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:52	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:55	ksmserver[12213]	segfault at 8 ip 00007f9aad61132b sp 00007f9aa3f59638 error 4 in libQtDBus.so.4.5.2[7f9aad5d0000+6f000]
2009-10-12 18:41:56	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:56	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:56	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:58	ksmserver[12389]	segfault at 8 ip 00007f22e37db32b sp 00007f22da123638 error 4 in libQtDBus.so.4.5.2[7f22e379a000+6f000]
2009-10-12 18:41:59	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:41:59	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:41:59	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:01	ksmserver[12565]	segfault at 8 ip 00007fac7d36332b sp 00007fac73cab638 error 4 in libQtDBus.so.4.5.2[7fac7d322000+6f000]
2009-10-12 18:42:02	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:02	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:02	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:04	ksmserver[12741]	segfault at 8 ip 00007f362b14032b sp 00007f3621a88638 error 4 in libQtDBus.so.4.5.2[7f362b0ff000+6f000]
2009-10-12 18:42:05	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:05	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:05	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:07	ksmserver[12917]	segfault at 8 ip 00007f3def2b632b sp 00007f3de5bfe638 error 4 in libQtDBus.so.4.5.2[7f3def275000+6f000]
2009-10-12 18:42:08	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:08	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:08	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:11	ksmserver[13093]	segfault at 8 ip 00007f468fc8a32b sp 00007f46865d2638 error 4 in libQtDBus.so.4.5.2[7f468fc49000+6f000]
2009-10-12 18:42:11	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:11	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:11	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:14	ksmserver[13269]	segfault at 8 ip 00007f43e2bb932b sp 00007f43d9501638 error 4 in libQtDBus.so.4.5.2[7f43e2b78000+6f000]
2009-10-12 18:42:14	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:14	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:14	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:17	ksmserver[13445]	segfault at 8 ip 00007f78da9fd32b sp 00007f78d1345638 error 4 in libQtDBus.so.4.5.2[7f78da9bc000+6f000]
2009-10-12 18:42:17	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:17	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:17	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:20	ksmserver[13621]	segfault at 8 ip 00007fcf9203732b sp 00007fcf8897f638 error 4 in libQtDBus.so.4.5.2[7fcf91ff6000+6f000]
2009-10-12 18:42:20	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:20	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:20	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:23	ksmserver[13797]	segfault at 8 ip 00007f9f2201d32b sp 00007f9f18965638 error 4 in libQtDBus.so.4.5.2[7f9f21fdc000+6f000]
2009-10-12 18:42:24	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:24	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:24	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:26	ksmserver[13973]	segfault at 8 ip 00007f892219432b sp 00007f8918adc638 error 4 in libQtDBus.so.4.5.2[7f8922153000+6f000]
2009-10-12 18:42:27	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:27	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:27	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:29	ksmserver[14149]	segfault at 8 ip 00007f620960a32b sp 00007f61fff52638 error 4 in libQtDBus.so.4.5.2[7f62095c9000+6f000]
2009-10-12 18:42:30	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:30	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:30	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:32	ksmserver[14325]	segfault at 8 ip 00007fdb673f232b sp 00007fdb5dd3a638 error 4 in libQtDBus.so.4.5.2[7fdb673b1000+6f000]
2009-10-12 18:42:33	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:33	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:33	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:36	ksmserver[14501]	segfault at 8 ip 00007f636a8fd32b sp 00007f6361245638 error 4 in libQtDBus.so.4.5.2[7f636a8bc000+6f000]
2009-10-12 18:42:36	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:36	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:36	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:39	ksmserver[14677]	segfault at 8 ip 00007f3fb15b632b sp 00007f3fa7efe638 error 4 in libQtDBus.so.4.5.2[7f3fb1575000+6f000]
2009-10-12 18:42:39	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:39	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:39	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:53	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:53	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:53	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:55	ksmserver[15102]	segfault at 8 ip 00007f7fe48d432b sp 00007f7fdb21c638 error 4 in libQtDBus.so.4.5.2[7f7fe4893000+6f000]
2009-10-12 18:42:56	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:56	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:56	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:58	ksmserver[15278]	segfault at 8 ip 00007f6a6b66032b sp 00007f6a61fa8638 error 4 in libQtDBus.so.4.5.2[7f6a6b61f000+6f000]
2009-10-12 18:42:59	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:42:59	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:42:59	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:01	ksmserver[15454]	segfault at 8 ip 00007fb3feb3b32b sp 00007fb3f5483638 error 4 in libQtDBus.so.4.5.2[7fb3feafa000+6f000]
2009-10-12 18:43:02	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:02	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:02	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:05	ksmserver[15630]	segfault at 8 ip 00007f0d3f52532b sp 00007f0d35e6d638 error 4 in libQtDBus.so.4.5.2[7f0d3f4e4000+6f000]
2009-10-12 18:43:05	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:05	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:05	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:08	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:08	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:08	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:11	ksmserver[15981]	segfault at 8 ip 00007f0e7ee6732b sp 00007f0e757af638 error 4 in libQtDBus.so.4.5.2[7f0e7ee26000+6f000]
2009-10-12 18:43:11	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:11	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:11	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:14	ksmserver[16157]	segfault at 8 ip 00007f50ec63432b sp 00007f50e2f7c638 error 4 in libQtDBus.so.4.5.2[7f50ec5f3000+6f000]
2009-10-12 18:43:14	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:14	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:14	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:17	ksmserver[16333]	segfault at 8 ip 00007fda778ee32b sp 00007fda6e236638 error 4 in libQtDBus.so.4.5.2[7fda778ad000+6f000]
2009-10-12 18:43:17	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:17	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:17	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:20	ksmserver[16509]	segfault at 8 ip 00007fbf45deb32b sp 00007fbf3c733638 error 4 in libQtDBus.so.4.5.2[7fbf45daa000+6f000]
2009-10-12 18:43:20	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:20	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:20	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:23	ksmserver[16685]	segfault at 8 ip 00007f3b5d48c32b sp 00007f3b53dd4638 error 4 in libQtDBus.so.4.5.2[7f3b5d44b000+6f000]
2009-10-12 18:43:24	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:24	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:24	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:26	ksmserver[16861]	segfault at 8 ip 00007f8606fa532b sp 00007f85fd8ed638 error 4 in libQtDBus.so.4.5.2[7f8606f64000+6f000]
2009-10-12 18:43:27	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:27	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:27	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:29	ksmserver[17037]	segfault at 8 ip 00007fe7295d032b sp 00007fe71ff18638 error 4 in libQtDBus.so.4.5.2[7fe72958f000+6f000]
2009-10-12 18:43:30	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:30	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:30	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:32	ksmserver[17213]	segfault at 8 ip 00007f8679b6b32b sp 00007f86704b3638 error 4 in libQtDBus.so.4.5.2[7f8679b2a000+6f000]
2009-10-12 18:43:33	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:33	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:33	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:35	ksmserver[17389]	segfault at 8 ip 00007fa953ee932b sp 00007fa94a831638 error 4 in libQtDBus.so.4.5.2[7fa953ea8000+6f000]
2009-10-12 18:43:36	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:36	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:36	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:39	ksmserver[17565]	segfault at 8 ip 00007f76f309232b sp 00007f76e99da638 error 4 in libQtDBus.so.4.5.2[7f76f3051000+6f000]
2009-10-12 18:43:39	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:39	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:39	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:42	ksmserver[17741]	segfault at 8 ip 00007f1eafdf032b sp 00007f1ea6738638 error 4 in libQtDBus.so.4.5.2[7f1eafdaf000+6f000]
2009-10-12 18:43:42	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:42	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:42	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:45	ksmserver[17917]	segfault at 8 ip 00007fd80863032b sp 00007fd7fef78638 error 4 in libQtDBus.so.4.5.2[7fd8085ef000+6f000]
2009-10-12 18:43:45	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:45	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:45	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:48	ksmserver[18093]	segfault at 8 ip 00007f32da23d32b sp 00007f32d0b85638 error 4 in libQtDBus.so.4.5.2[7f32da1fc000+6f000]
2009-10-12 18:43:49	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:49	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:49	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:51	ksmserver[18269]	segfault at 8 ip 00007fd00f1b132b sp 00007fd005af9638 error 4 in libQtDBus.so.4.5.2[7fd00f170000+6f000]
2009-10-12 18:43:52	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:52	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:52	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:54	ksmserver[18445]	segfault at 8 ip 00007feca095432b sp 00007fec9729c638 error 4 in libQtDBus.so.4.5.2[7feca0913000+6f000]
2009-10-12 18:43:55	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:55	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:55	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:57	ksmserver[18621]	segfault at 8 ip 00007fed8a71932b sp 00007fed81061638 error 4 in libQtDBus.so.4.5.2[7fed8a6d8000+6f000]
2009-10-12 18:43:58	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:43:58	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:58	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:44:00	ksmserver[18797]	segfault at 8 ip 00007f7dd6fb232b sp 00007f7dcd8fa638 error 4 in libQtDBus.so.4.5.2[7f7dd6f71000+6f000]
2009-10-12 18:44:01	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:44:01	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:44:01	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:44:04	ksmserver[18973]	segfault at 8 ip 00007f73634fa32b sp 00007f7359e42638 error 4 in libQtDBus.so.4.5.2[7f73634b9000+6f000]
2009-10-12 18:44:04	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:44:04	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:44:04	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:44:07	ksmserver[19149]	segfault at 8 ip 00007fa16862c32b sp 00007fa15ef74638 error 4 in libQtDBus.so.4.5.2[7fa1685eb000+6f000]
2009-10-12 18:44:07	agpgart-amd64 0000	0:00.0: AGP 3.0 bridge
2009-10-12 18:44:07	agpgart-amd64 0000	0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:44:07	pci 0000	1:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:57:31	usb 1-3	new high speed USB device using ehci_hcd and address 2
2009-10-12 18:57:31	usb 1-3	configuration #1 chosen from 1 choice
2009-10-12 18:57:32		Initializing USB Mass Storage driver...
2009-10-12 18:57:32	scsi4 	SCSI emulation for USB Mass Storage devices
2009-10-12 18:57:32	usbcore	registered new interface driver usb-storage
2009-10-12 18:57:32		USB Mass Storage support registered.
2009-10-12 18:57:32	usb-storage	device found at 2
2009-10-12 18:57:32	usb-storage	waiting for device to settle before scanning
2009-10-12 18:57:37	usb-storage	device scan complete
2009-10-12 18:57:37	scsi 4	:0:0: Direct-Access Generic USB SD Reader 0.00 PQ: 0 ANSI: 2
2009-10-12 18:57:37	sd 4	:0:0: Attached scsi generic sg4 type 0
2009-10-12 18:57:37	sd 4	:0:0: [sdd] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
2009-10-12 18:57:37	sd 4	:0:0: [sdd] Write Protect is off
2009-10-12 18:57:37	sd 4	:0:0: [sdd] Mode Sense: 03 00 00 00
2009-10-12 18:57:37	sd 4	:0:0: [sdd] Assuming drive cache: write through
2009-10-12 18:57:37	sd 4	:0:0: [sdd] Assuming drive cache: write through
2009-10-12 18:57:37	 sdd	sdd1
2009-10-12 18:57:37	sd 4	:0:0: [sdd] Assuming drive cache: write through
2009-10-12 18:57:37	sd 4	:0:0: [sdd] Attached SCSI removable disk
2009-10-12 19:03:30	usb 1-3	USB disconnect, address 2
2009-10-12 19:05:20		SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
2009-10-12 19:05:20		SGI XFS Quota Management subsystem
2009-10-12 19:05:20	JFS	nTxBlock = 7489, nTxLock = 59917
2009-10-12 19:05:20		NTFS driver 2.1.29 [Flags: R/O MODULE].
2009-10-12 19:05:20		QNX4 filesystem 0.2.3 registered.
2009-10-12 19:32:55	ksystemlog[27018]	segfault at 29 ip 00007fd7019c09c8 sp 00007fff8fefc300 error 4 in libQtGui.so.4.5.2[7fd7012d7000+972000]

---

### Post by zeronothing on 2009-10-12
if you just did a fresh install of the 9.10 beta you will probably need to update the system if you haven't already. There have been some kernal and xserver updates that might cure your problem. if you can try and reach the command line to do the update. see if you can hit "ctrl+alt+f2 to bring you down to the command line. you will probably need to login but after you do that you can execute the update command (hopefully you have network connectivity). so to do the update do

1.) sudo apt-get update

2.) sudo apt-get dist-upgrade

once you do the "dist-upgrade" this should start to download all of the need update packages to your system. once they are done downloading and installing restart your system and see what happens.

---

### Post by rmannon on 2009-10-13
Guess I should have stated that I did a apt-get update
and apt-get upgrade and the problem is still there.

---

### Post by rmannon on 2009-10-13
The problem still exists.  I think it has something to do with this:

2009-10-12 18:43:39 ksmserver[17565] segfault at 8 ip 00007f76f309232b sp 00007f76e99da638 error 4 in libQtDBus.so.4.5.2[7f76f3051000+6f000]
2009-10-12 18:43:39 agpgart-amd64 0000 0:00.0: AGP 3.0 bridge
2009-10-12 18:43:39 agpgart-amd64 0000 0:00.0: putting AGP V3 device into 8x mode
2009-10-12 18:43:39 pci 0000 1:00.0: putting AGP V3 device into 8x mode

and this is really odd:

lolo@Home-Box:~$ sudo apt-get install ksmserver
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ksmserver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdebase-workspace-data
E: Package ksmserver has no installation candidate
lolo@Home-Box:~$ sudo apt-get install kdebase-workspace-data
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdebase-workspace-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
lolo@Home-Box:~$

where is the ksmserver[17565] segfault comming from?

---

### Post by rmannon on 2009-10-16
I gave up on 9.10 and went back to 9.04.  It seems to be a bit more stable for me.  I tried installing KDE 4.3 last night and it hosed my desktop.  For some reason plasma would not put a background image on the desktop, it was nothing but grey and white squares and I could not change that.  Also none of the widgets that I had installed on the desktop showed up.  I think I'll give 9.10 a few weeks to calm down after the release before I try it again.  I also think there might be some issues with the openchrome driver but I cannot find anybody else having the same issues I am. I love KDE 4.3 on my laptop but it just wont install on my desktop.  I know that VIA chipsets are not the greatest but I am cheap and dont want to go buy another video card. That and my wife and kids are tired of me killing the "Home Computer". :)

---

### Post by sanjayak on 2009-11-01
I am having the same issue after install Kubuntu 9.10. X restart after login when the splash screen is going... I disabled 2D acceleration and now it works. But obviously screen rendering is very slow.

---

### Post by atreidae on 2009-11-05
Same issue, If i leave the machine long enough it will boot into KDE but stuff is slow.

Checking dmesg it appears the crash occurs when attempting to put the card into 8x mode 

"AGPpart-via 0000: 00: 00. 0 putting AGP V3 device into 8x mode"

Motherboard is a gigabyte GA-8VM800M-775 
Bios line is 11/10/2005-P4M800Pro-823-6A7L6G01C-00
running 1 GB of ddr
Hyperthreading is on
using the on-board graphics card.

---

### Post by atreidae on 2009-11-05
I threw an AGP card into the machine, worked a treat, definitely something to do with the onboard GFX card.
(i should have also pointed out, i had a similar issue after upgrading from 9.04 to 9.10, this particular case was a 9.10 fresh install)

---

