---
title: "no displap after boot"
date: 2010-05-08
forum: Hardware
---

### Post by yoma819 on 2010-05-08
Dear all
i have a toshiba st-a10 touchscreen computer running ubuntu 9.10 that simply refuses to display any gui past boot.
/etc/x11/xorg.conf does not exist however i am getting a display on an external monitor!
can anyone advise me as to what to do next?
cheers
yoma

---

### Post by yoma819 on 2010-05-08
update
have tried ubuntu 10.04 and instead of a blank screen i now get colours and lots of flickering!
if its any help the graphics card is via unichrome igp!
works fine on ext monitor still
cheers
yoma

---

### Post by dino99 on 2010-05-08
need xserver-xorg-video-openchrom be installed and activated (system admin hardware driver)

more details into .xsession-errors
and : system admin log viewer (xorg.0.log)

by default Lucid dont need xorg.conf, but if you need it for custom config:

sudo X -configure

[http://www.via.com.tw/en/support/drivers.jsp](http://www.via.com.tw/en/support/drivers.jsp)

---

### Post by yoma819 on 2010-05-08
thank you 
will try this as soon as ubuntu 10.04 has installed
cheers

---

### Post by yoma819 on 2010-05-08
xserver-xorg-video-openchrome is installed and i assume active
screen is full of lines
how do i get the lopgs up for you?
cheers
yoma

---

### Post by dino99 on 2010-05-08
*** and i assume active ****  ;)

you may check: system admin hardware driver

**** more details into .xsession-errors ( /home, unhide it with menu)
and : system admin log viewer (xorg.0.log) ****

look at "warnings" and "errors" into these files

**** into synaptic, install the "toshiba" packages: toshset, toshutils and fnfxd; and: xserver-xorg-input-evtouch, xserver-xorg-input-tslib

then reboot (cold boot, ie power off)

---

### Post by yoma819 on 2010-05-08
code from xord.0.log
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux shop-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=65bfb71e-d298-4ed0-9776-1a0b34c6db01 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May  8 14:14:07 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1106:3344:1106:3344 VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] rev 1, Mem @ 0xf4000000/67108864, 0xfb000000/16777216, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched openchrome as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.7.5, module version = 0.2.904
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
	K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800/VX820,
	VX855/VX875
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to http://www.openchrome.org/.
(!!) (development build, compiled on Mon Mar 22 20:33:42 2010)
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) CHROME(0): Depth 24, (--) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: VM800/P4M800Pro/VN800/CN700
(--) CHROME(0): Chipset revision: 0
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
(==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
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
(==) CHROME(0): No default TV output port is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfb000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfb200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(WW) CHROME(0): Manufacturer plainly copied main PCI IDs to subsystem/card IDs.
(--) CHROME(0): Detected VIA VT3344 (VM800) - EPIA EN. Card-Ids (1106|3344)
(II) CHROME(0): Detected MemClk 7
(II) CHROME(0): ViaGetMemoryBandwidth. Memory type: 7
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
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): I2C device "I2C bus 1:DDC control interface" registered at address 0x6E.
(II) CHROME(0): Manufacturer: NUL  Model: 1  Serial#: 1
(II) CHROME(0): Year: 2002  Week: 32
(II) CHROME(0): EDID Version: 1.3
(II) CHROME(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) CHROME(0): Sync:  Separate
(II) CHROME(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) CHROME(0): Gamma: 1.00
(II) CHROME(0): DPMS capabilities: StandBy Suspend; RGB/Color Display
(II) CHROME(0): First detailed timing is preferred mode
(II) CHROME(0): redX: 0.609 redY: 0.352   greenX: 0.303 greenY: 0.550
(II) CHROME(0): blueX: 0.148 blueY: 0.128   whiteX: 0.305 whiteY: 0.342
(II) CHROME(0): Supported established timings:
(II) CHROME(0): 720x400@70Hz
(II) CHROME(0): 640x480@60Hz
(II) CHROME(0): 640x480@72Hz
(II) CHROME(0): 640x480@75Hz
(II) CHROME(0): 800x600@56Hz
(II) CHROME(0): 800x600@60Hz
(II) CHROME(0): 800x600@72Hz
(II) CHROME(0): 800x600@75Hz
(II) CHROME(0): 1024x768@60Hz
(II) CHROME(0): 1024x768@70Hz
(II) CHROME(0): 1024x768@75Hz
(II) CHROME(0): 1280x1024@75Hz
(II) CHROME(0): Manufacturer's mask: 0
(II) CHROME(0): Supported standard timings:
(II) CHROME(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) CHROME(0): Supported detailed timing:
(II) CHROME(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) CHROME(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) CHROME(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) CHROME(0):  
(II) CHROME(0):  
(II) CHROME(0): Monitor name: 
(II) CHROME(0): EDID (in hex):
(II) CHROME(0): 	00ffffffffffff003aac010001000000
(II) CHROME(0): 	200c010308221b00ca0b329c5a4d8c26
(II) CHROME(0): 	204e57afcf0081800101010101010101
(II) CHROME(0): 	010101010101302a009851002a403070
(II) CHROME(0): 	1300520e1100001e000000fe000a2020
(II) CHROME(0): 	20202020202020202020000000fe000a
(II) CHROME(0): 	202020202020202020202020000000fc
(II) CHROME(0): 	000a20202020202020202020202000d6
(II) CHROME(0): EDID vendor "NUL", prod id 1
(II) CHROME(0): Printing DDC gathered Modelines:
(II) CHROME(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) CHROME(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) CHROME(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): VIATVDetect
(WW) CHROME(0): This device is supposed to have a TV encoder, but we are unable to detect it (support missing?).
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x03
(II) CHROME(0): ViaOutputsSelect: CRT.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): <default monitor>: Using hsync range of 31.47-79.98 kHz
(II) CHROME(0): <default monitor>: Using vrefresh range of 56.25-75.03 Hz
(II) CHROME(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x400 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 35500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 56300)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 44900)
(II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 94500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1024x768" (vrefresh out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 148500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 157500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (Clock: 57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 119650)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 121500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (vrefresh out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 143470)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1360x768" (width too large for virtual size)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1440x900" (width too large for virtual size)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 28320)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 108000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 104990)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 96770)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 81620)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 832x624 (Clock: 57284)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 28320)
(II) CHROME(0): ViaFirstCRTCModeValid
(--) CHROME(0): Virtual size is 1280x1024 (pitch 1280)
(**) CHROME(0): *Driver mode "1280x1024": 108.0 MHz (scaled from 2.3 MHz), 64.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) CHROME(0): *Driver mode "1280x1024": 135.0 MHz (scaled from 2.8 MHz), 80.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) CHROME(0): *Default mode "1280x1024": 135.0 MHz (scaled from 2.8 MHz), 80.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) CHROME(0): *Default mode "1280x1024": 108.0 MHz (scaled from 2.3 MHz), 64.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) CHROME(0): *Default mode "1280x960": 108.0 MHz (scaled from 2.3 MHz), 60.0 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Default mode "1152x864": 108.0 MHz (scaled from 2.3 MHz), 67.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) CHROME(0): *Default mode "1152x864": 105.0 MHz (scaled from 2.2 MHz), 67.6 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) CHROME(0): *Default mode "1152x864": 96.8 MHz (scaled from 2.0 MHz), 63.0 kHz, 70.0 Hz
(II) CHROME(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) CHROME(0): *Default mode "1152x864": 81.6 MHz (scaled from 1.7 MHz), 53.7 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) CHROME(0): *Driver mode "1024x768": 78.8 MHz (scaled from 1.7 MHz), 60.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Driver mode "1024x768": 75.0 MHz (scaled from 1.6 MHz), 56.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) CHROME(0): *Driver mode "1024x768": 65.0 MHz (scaled from 1.4 MHz), 48.4 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) CHROME(0): *Default mode "1024x768": 78.8 MHz (scaled from 1.7 MHz), 60.0 kHz, 75.0 Hz
(II) CHROME(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) CHROME(0): *Default mode "1024x768": 75.0 MHz (scaled from 1.6 MHz), 56.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) CHROME(0): *Default mode "1024x768": 65.0 MHz (scaled from 1.4 MHz), 48.4 kHz, 60.0 Hz
(II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) CHROME(0): *Default mode "832x624": 57.3 MHz (scaled from 1.2 MHz), 49.7 kHz, 74.6 Hz
(II) CHROME(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) CHROME(0): *Driver mode "800x600": 49.5 MHz (scaled from 1.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 50.0 MHz (scaled from 1.1 MHz), 48.1 kHz, 72.2 Hz
(II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) CHROME(0): *Driver mode "800x600": 40.0 MHz (scaled from 0.8 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Driver mode "800x600": 36.0 MHz (scaled from 0.8 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Default mode "800x600": 49.5 MHz (scaled from 1.0 MHz), 46.9 kHz, 75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) CHROME(0): *Default mode "800x600": 50.0 MHz (scaled from 1.1 MHz), 48.1 kHz, 72.2 Hz
(II) CHROME(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 0.8 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 0.8 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from 0.7 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from 0.7 MHz), 37.9 kHz, 72.8 Hz
(II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) CHROME(0): *Driver mode "640x480": 25.2 MHz (scaled from 0.5 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from 0.7 MHz), 37.5 kHz, 75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) CHROME(0): *Default mode "640x480": 31.5 MHz (scaled from 0.7 MHz), 37.9 kHz, 72.8 Hz
(II) CHROME(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from 0.5 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) CHROME(0): *Driver mode "720x400": 28.3 MHz (scaled from 0.6 MHz), 31.5 kHz, 70.1 Hz
(II) CHROME(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) CHROME(0): Display dimensions: (340, 270) mm
(**) CHROME(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xf4000000 with size 0x4000000
(--) CHROME(0): Frame buffer start: 0xb37a6000, free start: 0x500000 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfb000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfb200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
(II) CHROME(0): Non-Primary Adapter! saving VGA_SR_MODE only !!
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModeSet
(II) CHROME(0): Name: 1280x1024
(II) CHROME(0): Clock: 108000
(II) CHROME(0): VRefresh: 60.019741
(II) CHROME(0): HSync: 63.981041
(II) CHROME(0): HDisplay: 1280
(II) CHROME(0): HSyncStart: 1328
(II) CHROME(0): HSyncEnd: 1440
(II) CHROME(0): HTotal: 1688
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 1024
(II) CHROME(0): VSyncStart: 1025
(II) CHROME(0): VSyncEnd: 1028
(II) CHROME(0): VTotal: 1066
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x500
(II) CHROME(0): CrtcHBlankStart: 0x500
(II) CHROME(0): CrtcHSyncStart: 0x530
(II) CHROME(0): CrtcHSyncEnd: 0x5a0
(II) CHROME(0): CrtcHBlankEnd: 0x698
(II) CHROME(0): CrtcHTotal: 0x698
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x400
(II) CHROME(0): CrtcVBlankStart: 0x400
(II) CHROME(0): CrtcVSyncStart: 0x401
(II) CHROME(0): CrtcVSyncEnd: 0x404
(II) CHROME(0): CrtcVBlankEnd: 0x42a
(II) CHROME(0): CrtcVTotal: 0x42a
(II) CHROME(0): ViaDisplaySetStreamOnCRT
(II) CHROME(0): ViaDisplayEnableCRT
(II) CHROME(0): ViaModeFirstCRTC
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 1280x1024
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetDotclock to 0x079089
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): ViaDisplayDisableSimultaneous
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "via" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
(II) CHROME(0): [drm] framebuffer handle = 0xf4000000
(II) CHROME(0): [drm] added 1 reserved context for kernel
(II) CHROME(0): X context handle = 0x1
(II) CHROME(0): [drm] installed DRM signal handler
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [drm] register handle = 0xfb000000
(II) CHROME(0): [drm] framebuffer handle = 0xf4000000
(II) CHROME(0): [drm] mmio Registers = 0xfb000000
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): CursorStart: 0x3fc0000
(II) CHROME(0): Frame Buffer From (0,0) To (1280,4096)
(II) CHROME(0): Using 3072 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Image Writes
	Setting up tile and stipple cache:
		31 128x128 slots
		24 256x256 slots
		7 512x512 slots
		32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette: numColors: 256
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): - Palette loaded
(==) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0314
(II) CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
(II) CHROME(0): [drm] Trying to enable AGP fast writes.
(II) CHROME(0): [drm] drmAgpEnabled succeeded
(II) CHROME(0): [drm] agpAddr = 0xe8000000
(II) CHROME(0): [drm] agpBase = (nil)
(II) CHROME(0): [drm] agpAddr = 0xe8000000
(II) CHROME(0): [drm] agpSize = 0x01e00000
(II) CHROME(0): [drm] agp physical addr = 0x00000000
(II) CHROME(0): [dri] Using AGP.
(II) CHROME(0): [drm] Using 45864928 bytes for DRM memory heap.
(II) CHROME(0): [dri] Frame buffer initialized.
(II) CHROME(0): [DRI] installation complete
(II) CHROME(0): [dri] Kernel data initialized.
(II) CHROME(0): [drm] IRQ handler installed, using IRQ 16.
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): direct rendering enabled
(II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
Fulfilled via DRI at 20976640
(II) CHROME(0): Benchmarking video copy.  Less time is better.
(--) CHROME(0): Timed   libc YUV420 copy... 2677725. Throughput: 331.5 MiB/s.
(--) CHROME(0): Timed kernel YUV420 copy... 2639762. Throughput: 336.3 MiB/s.
(--) CHROME(0): Timed    SSE YUV420 copy... 1520285. Throughput: 583.9 MiB/s.
(--) CHROME(0): Timed    MMX YUV420 copy... 2242727. Throughput: 395.8 MiB/s.
(--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
(--) CHROME(0): Timed   MMX2 YUV420 copy... 1617700. Throughput: 548.8 MiB/s.
Freed 20976640 (pool 2)
(--) CHROME(0): Using SSE YUV42X copy for video.
(II) CHROME(0): [XvMC] Registering chromeXvMC.
(II) CHROME(0): [XvMC] Initialized XvMC extension.
(II) CHROME(0): - Done
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
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device   SCISSORS Keyboard (/dev/input/event4)
(**)   SCISSORS Keyboard: Applying InputClass "evdev keyboard catchall"
(**)   SCISSORS Keyboard: always reports core events
(**)   SCISSORS Keyboard: Device: "/dev/input/event4"
(II)   SCISSORS Keyboard: Found keys
(II)   SCISSORS Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  SCISSORS Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) CHROME(0): VIASwitchMode
(II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModeSet
(II) CHROME(0): Name: 800x600
(II) CHROME(0): Clock: 40000
(II) CHROME(0): VRefresh: 60.316540
(II) CHROME(0): HSync: 37.878788
(II) CHROME(0): HDisplay: 800
(II) CHROME(0): HSyncStart: 840
(II) CHROME(0): HSyncEnd: 968
(II) CHROME(0): HTotal: 1056
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 600
(II) CHROME(0): VSyncStart: 601
(II) CHROME(0): VSyncEnd: 605
(II) CHROME(0): VTotal: 628
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x320
(II) CHROME(0): CrtcHBlankStart: 0x320
(II) CHROME(0): CrtcHSyncStart: 0x348
(II) CHROME(0): CrtcHSyncEnd: 0x3c8
(II) CHROME(0): CrtcHBlankEnd: 0x420
(II) CHROME(0): CrtcHTotal: 0x420
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x258
(II) CHROME(0): CrtcVBlankStart: 0x258
(II) CHROME(0): CrtcVSyncStart: 0x259
(II) CHROME(0): CrtcVSyncEnd: 0x25d
(II) CHROME(0): CrtcVBlankEnd: 0x274
(II) CHROME(0): CrtcVTotal: 0x274
(II) CHROME(0): ViaDisplaySetStreamOnCRT
(II) CHROME(0): ViaDisplayEnableCRT
(II) CHROME(0): ViaModeFirstCRTC
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 800x600
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetDotclock to 0x0860cd
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): ViaDisplayDisableSimultaneous
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): VIALoadPalette: numColors: 256
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): VIAAdjustFrame 1x1
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): VIASwitchMode
(II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModeSet
(II) CHROME(0): Name: 1280x1024
(II) CHROME(0): Clock: 108000
(II) CHROME(0): VRefresh: 60.019741
(II) CHROME(0): HSync: 63.981041
(II) CHROME(0): HDisplay: 1280
(II) CHROME(0): HSyncStart: 1328
(II) CHROME(0): HSyncEnd: 1440
(II) CHROME(0): HTotal: 1688
(II) CHROME(0): HSkew: 0
(II) CHROME(0): VDisplay: 1024
(II) CHROME(0): VSyncStart: 1025
(II) CHROME(0): VSyncEnd: 1028
(II) CHROME(0): VTotal: 1066
(II) CHROME(0): VScan: 0
(II) CHROME(0): Flags: 5
(II) CHROME(0): CrtcHDisplay: 0x500
(II) CHROME(0): CrtcHBlankStart: 0x500
(II) CHROME(0): CrtcHSyncStart: 0x530
(II) CHROME(0): CrtcHSyncEnd: 0x5a0
(II) CHROME(0): CrtcHBlankEnd: 0x698
(II) CHROME(0): CrtcHTotal: 0x698
(II) CHROME(0): CrtcHSkew: 0x0
(II) CHROME(0): CrtcVDisplay: 0x400
(II) CHROME(0): CrtcVBlankStart: 0x400
(II) CHROME(0): CrtcVSyncStart: 0x401
(II) CHROME(0): CrtcVSyncEnd: 0x404
(II) CHROME(0): CrtcVBlankEnd: 0x42a
(II) CHROME(0): CrtcVTotal: 0x42a
(II) CHROME(0): ViaDisplaySetStreamOnCRT
(II) CHROME(0): ViaDisplayEnableCRT
(II) CHROME(0): ViaModeFirstCRTC
(II) CHROME(0): ViaFirstCRTCSetMode
(II) CHROME(0): Setting up 1280x1024
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetDotclock to 0x079089
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): ViaDisplayDisableSimultaneous
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): VIALoadPalette: numColors: 256
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIAAdjustFrame 0x0
(II) CHROME(0): VIAAdjustFrame 1x1
(II) CHROME(0): VIAAdjustFrame 0x0

```

---

### Post by dino99 on 2010-05-08
****(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to [http://www.openchrome.org/](http://www.openchrome.org/).
(!!) (development build, compiled on Mon Mar 22 20:33:42 2010)
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev

here is the problem (ww) you are using vesa instead openchrome

is that log after or before you ran X -configure ?

run into console: sudo update-pciids && update-usbids

sudo rm -f /etc/X11/xorg.conf

reboot

look again at xorg.0.log (only from the previous deleting, watch "time") and see if we have new errors or less

note: my previous post is updated

---

### Post by dino99 on 2010-05-08
if you still have no gui, then let us use more recent packages. Into synaptic, select repo tab and add this ppa: [COLOR="Blue"]ppa:ubuntu-x-swat/x-updates
[/COLOR]
validate, update and upgrade

then install a new kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

howto:
 in that strict order, by double clicking on the packages ( need gdebi to be installed):
** linux-source....all.deb
** linux-headers...all.deb
** linux-headers (choose i386 )
** linux-image (choose i386 )

then reboot with this kernel

---

