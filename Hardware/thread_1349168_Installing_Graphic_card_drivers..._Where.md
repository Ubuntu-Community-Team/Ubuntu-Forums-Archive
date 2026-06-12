---
title: "Installing Graphic card drivers... Where?"
date: 2009-12-08
forum: Hardware
---

### Post by Nylo on 2009-12-08
I have the NeoGraphic 256AV drivers sitting on my desktop in a zip file.  Problem is I do not know where to put/install them so Karmic can detect them.  Im trying to get back to my 1024x768 res that I had before I updated.

---

### Post by Yellow Pasque on 2009-12-08
The driver is pre-installed: [http://packages.ubuntu.com/karmic/xserver-xorg-video-neomagic](http://packages.ubuntu.com/karmic/xserver-xorg-video-neomagic) . I'd guess that you need to adjust xorg.conf because of poor autodetection of display settings.

Post/pastebin your /var/log/Xorg.0.log file

---

### Post by Nylo on 2009-12-08
> **Temüjin said:**
> The driver is pre-installed: [http://packages.ubuntu.com/karmic/xserver-xorg-video-neomagic](http://packages.ubuntu.com/karmic/xserver-xorg-video-neomagic) . I'd guess that you need to adjust xorg.conf because of poor autodetection of display settings.

Post/pastebin your /var/log/Xorg.0.log file

Here's your request.  

BTW. 9.10 Karmic does not use Xorg.conf...  Its gone.  I have tried to install it many ways but to know avail.

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu007 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=184cea4a-c540-43cc-a962-d4a34440c8d3 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  8 00:59:20 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10c8:0005:1028:0005 Neomagic Corporation NM2200 [MagicGraph 256AV] rev 32, Mem @ 0xf6000000/16777216, 0xfe400000/4194304, 0xfeb00000/1048576
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default neomagic Device 0"
		Driver	"neomagic"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default neomagic Screen 0"
		Device	"Builtin Default neomagic Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default neomagic Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default neomagic Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default neomagic Device 0"
(==) No monitor specified for screen "Builtin Default neomagic Screen 0".
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
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "neomagic"
(II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.2.3
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
(II) NEOMAGIC: Driver for Neomagic chipsets: neo2070, neo2090, neo2093,
	neo2097, neo2160, neo2200, neo2230, neo2360, neo2380
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for neomagic
(--) Assigning device section with no busID to primary device
(--) Chipset neo2200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
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
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) NEOMAGIC(0): Chipset is a MagicMedia 256AV (NM2200)
(II) NEOMAGIC(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) NEOMAGIC(0): Panel is a 800x600 color TFT display
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
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
(II) NEOMAGIC(0): initializing int10
(II) NEOMAGIC(0): Primary V_BIOS segment is: 0xc000
(II) NEOMAGIC(0): VESA BIOS detected
(II) NEOMAGIC(0): VESA VBE Version 2.0
(II) NEOMAGIC(0): VESA VBE Total Mem: 2496 kB
(II) NEOMAGIC(0): VESA VBE OEM: MagicGraph 256 AV 48K
(II) NEOMAGIC(0): VESA VBE OEM Software Rev: 1.15
(II) NEOMAGIC(0): VESA VBE OEM Vendor: NeoMagic
(II) NEOMAGIC(0): VESA VBE OEM Product: MagicMedia 256 AV
(II) NEOMAGIC(0): VESA VBE OEM Product Rev: 01.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NEOMAGIC(0): VESA VBE DDC supported
(II) NEOMAGIC(0): VESA VBE DDC Level none
(II) NEOMAGIC(0): VESA VBE DDC transfer in appr. 0 sec.
(II) NEOMAGIC(0): VESA VBE DDC read failed
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) NEOMAGIC(0): I2C bus "I2C bus" initialized.
(II) NEOMAGIC(0): I2C device "I2C bus:E-EDID segment register" registered at address 0x60.
(II) NEOMAGIC(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(--) NEOMAGIC(0): No DDC signal
(II) NEOMAGIC(0): Creating default Display subsection in Screen section
	"Builtin Default neomagic Screen 0" for depth/fbbpp 16/16
(==) NEOMAGIC(0): Depth 16, (--) framebuffer bpp 16
(==) NEOMAGIC(0): RGB weight 565
(==) NEOMAGIC(0): Default visual is TrueColor
(==) NEOMAGIC(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NEOMAGIC(0): Internal LCD only display mode
(==) NEOMAGIC(0): using linear mode
(**) NEOMAGIC(0): using PCI Burst mode
(**) NEOMAGIC(0): Option StrangeLockups set: disabling some acceleration
(--) NEOMAGIC(0): FB base address is set at 0xF6000000.
(--) NEOMAGIC(0): MMIO base address is set at 0xFE400000.
(--) NEOMAGIC(0): MMIO base address2 is set at 0xFEB00000.
(--) NEOMAGIC(0): VideoRAM: 2560 kByte
(--) NEOMAGIC(0): Max Clock: 110000 kHz
(--) NEOMAGIC(0): Using hsync range matching panel size: 28.00-38.52 kHz
(--) NEOMAGIC(0): Using vsync range for panel: 55.00-65.00 kHz
(II) NEOMAGIC(0): <default monitor>: Using hsync range of 28.00-38.52 kHz
(II) NEOMAGIC(0): <default monitor>: Using vrefresh range of 55.00-65.00 Hz
(WW) NEOMAGIC(0): Unable to estimate virtual size
(II) NEOMAGIC(0): Clock range:  11.00 to 110.00 MHz
(II) NEOMAGIC(0): Removing mode (640x350) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "640x350" (unknown reason)
(II) NEOMAGIC(0): Removing mode (320x175) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "320x175" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x400) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "640x400" (unknown reason)
(II) NEOMAGIC(0): Removing mode (320x200) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "320x200" (unknown reason)
(II) NEOMAGIC(0): Removing mode (720x400) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "720x400" (unknown reason)
(II) NEOMAGIC(0): Removing mode (360x200) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "360x200" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "640x480" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "320x240" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "640x480" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "320x240" (vrefresh out of range)
(II) NEOMAGIC(0): Not using default mode "640x480" (hsync out of range)
(II) NEOMAGIC(0): Not using default mode "320x240" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "800x600" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "800x600" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "800x600" (hsync out of range)
(II) NEOMAGIC(0): Removing mode (400x300) that won't display properly on LCD
(II) NEOMAGIC(0): Not using default mode "400x300" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1024x768" (unknown reason)
(II) NEOMAGIC(0): Removing mode (512x384) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1024x768" (unknown reason)
(II) NEOMAGIC(0): Removing mode (512x384) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1024x768" (unknown reason)
(II) NEOMAGIC(0): Removing mode (512x384) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1024x768) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1024x768" (unknown reason)
(II) NEOMAGIC(0): Removing mode (512x384) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "512x384" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1152x864" (unknown reason)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1280x960) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1280x960" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x480) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "640x480" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (640x480) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "640x480" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1280x1024) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1280x1024" (unknown reason)
(II) NEOMAGIC(0): Removing mode (640x512) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "640x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (640x512) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "640x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (640x512) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "640x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "896x672" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "928x696" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (832x624) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "832x624" (unknown reason)
(II) NEOMAGIC(0): Removing mode (416x312) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "416x312" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1152x864" (unknown reason)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1152x864" (unknown reason)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Removing mode (1152x864) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "1152x864" (unknown reason)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Removing mode (576x432) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "576x432" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1360x768" (width requires unsupported line pitch)
(II) NEOMAGIC(0): Removing mode (680x384) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "680x384" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1360x768" (width requires unsupported line pitch)
(II) NEOMAGIC(0): Removing mode (680x384) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "680x384" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "700x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1440x900" (width requires unsupported line pitch)
(II) NEOMAGIC(0): Removing mode (720x450) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "720x450" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) NEOMAGIC(0): Removing mode (800x512) larger than the LCD panel (800x600)
(II) NEOMAGIC(0): Not using default mode "800x512" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "840x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "840x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "840x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "840x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "840x525" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1920x1080" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x540" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x600" (unknown reason)
(II) NEOMAGIC(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NEOMAGIC(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) NEOMAGIC(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NEOMAGIC(0): Virtual size is 800x600 (pitch 800)
(**) NEOMAGIC(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NEOMAGIC(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NEOMAGIC(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NEOMAGIC(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NEOMAGIC(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NEOMAGIC(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NEOMAGIC(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NEOMAGIC(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NEOMAGIC(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
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
(II) NEOMAGIC(0): Stretching disabled
(II) NEOMAGIC(0): Using linear framebuffer at: 0xF6000000
(--) NEOMAGIC(0): 1661440 bytes off-screen memory available
(II) NEOMAGIC(0): Using H/W Cursor.
(II) NEOMAGIC(0): Using 424 scanlines of offscreen memory 
(II) NEOMAGIC(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		18 128x128 slots
(II) NEOMAGIC(0): Acceleration  Initialized
(==) NEOMAGIC(0): Backing store disabled
(==) NEOMAGIC(0): Silken mouse enabled
(II) NEOMAGIC(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event5"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
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
```

---

### Post by Yellow Pasque on 2009-12-08
```
gksu gedit /etc/X11/xorg.conf
```
Paste this (if you can find more specific values for "horizsync" and "vertrefresh" for your display, then use those values)
```
Section "Device"
	Identifier "Configured Video Device"
	Busid "PCI:1:0:0"
	Driver "neomagic"
	Screen 0
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
	Vendorname "Generic LCD Display"
	Modelname "LCD Panel 1024x768"
	Horizsync 31.5-48.0
	Vertrefresh 56.0 - 65.0
	Option "PreferredMode" "1024x768@60"
	Gamma 1.0
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
	Defaultdepth 24
	SubSection "Display"
		Depth 24
		Virtual 1024 768
		Modes "1024x768@60" "800x600@60" "640x480@60"
	EndSubSection
EndSection
```
Save. Reboot. If it doesn't work, paste the new Xorg log file, so we can see why.

---

### Post by Nylo on 2009-12-08
> **Temüjin said:**
> ```
gksu gedit /etc/X11/xorg.conf
```
Paste this (if you can find more specific values for "horizsync" and "vertrefresh" for your display, then use those values)
```
Section "Device"
	Identifier "Configured Video Device"
	Busid "PCI:1:0:0"
	Driver "neomagic"
	Screen 0
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
	Vendorname "Generic LCD Display"
	Modelname "LCD Panel 1024x768"
	Horizsync 31.5-48.0
	Vertrefresh 56.0 - 65.0
	Option "PreferredMode" "1024x768@60"
	Gamma 1.0
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
	Defaultdepth 24
	SubSection "Display"
		Depth 24
		Virtual 1024 768
		Modes "1024x768@60" "800x600@60" "640x480@60"
	EndSubSection
EndSection
```
Save. Reboot. If it doesn't work, paste the new Xorg log file, so we can see why.

After your directions my laptop just keeps rebooting over and over.  Once I get to the desktop it starts the "tty ubuntu007 login:" then goes to the graphical login after which it goes back to "tty ubuntu007 Login:.

Went to Recovery Mode, "drop root to shell," and tried to access Xorg.conf/Xorg.log.  Results were, Command Not Found, or Permission Denied.

---

