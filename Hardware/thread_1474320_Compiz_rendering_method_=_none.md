---
title: "Compiz rendering method = none"
date: 2010-05-05
forum: Hardware
---

### Post by D.horse on 2010-05-05
I just upgraded from 9.10 to 10.4 and now with the fglrx drivers installed i am not able to get any 3d graphics.  doing a compiz-check gives me 
[PHP]Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3400 Series
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

lenny@lenny-laptop:~$ gedit /var/log/Xorg.0.log
[/PHP]

And Xorg.0.log reads as follows

[PHP]
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux lenny-laptop 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=fdcbdf09-f0e7-45d4-9ca0-2f739dd96f7c ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May  5 22:05:24 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "amdcccle Layout"
(**) |-->Screen "amdcccle-Screen[1]-0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "amdcccle-Device[1]-0"
(==) No monitor specified for screen "amdcccle-Screen[1]-0".
	Using a default monitor configuration.
(**) Option "Xinerama" "off"
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

(--) PCI:*(0:1:0:0) 1002:95c4:17aa:210e ATI Technologies Inc Mobility Radeon HD 3400 Series rev 0, Mem @ 0xd0000000/268435456, 0xcfff0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
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
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(WW) Warning, couldn't open module dri
(II) UnloadModule: "dri"
(EE) Failed to load module "dri" (module does not exist, 0)
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
	Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:29
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x95C4) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x9e964c0
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3400 Series" (Chipset = 0x95c4)
(--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x210e)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xcfff0000
(--) fglrx(0): I/O port at 0x00002000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.88
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M82
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(II) fglrx(0): Interrupt handler installed at IRQ 32.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: LCD on internal LVDS [lvds]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LEN  Model: 4033  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.569 redY: 0.332   greenX: 0.312 greenY: 0.544
(II) fglrx(0): blueX: 0.149 blueY: 0.132   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 101.6 MHz   Image Size:  303 x 190 mm
(II) fglrx(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1792 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 945 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 81.5 MHz   Image Size:  303 x 190 mm
(II) fglrx(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1760 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) fglrx(0): Unknown vendor-specific block f
(II) fglrx(0):  LTN141WD-L05
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0030ae334000000000
(II) fglrx(0): 	000f0103801e1378eacd7591554f8b26
(II) fglrx(0): 	21505400000001010101010101010101
(II) fglrx(0): 	010101010101b027a06051842d303020
(II) fglrx(0): 	36002fbe10000019d51fa04051841a30
(II) fglrx(0): 	302036002fbe100000190000000f0090
(II) fglrx(0): 	0a32900a281401004ca34244000000fe
(II) fglrx(0): 	004c544e31343157442d4c30350a0032
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output LVDS using monitor section 0-LVDS
(**) fglrx(0): Option "PreferredMode" "1440x900"
(**) fglrx(0): Option "Position" "0 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(**) fglrx(0): Option "TargetRefresh" "60"
(II) fglrx(0): Output DFP1 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output LVDS connected
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Using user preference for initial modes
(II) fglrx(0): Output LVDS using initial mode 1440x900
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Mobility Radeon HD 3400 Series has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing swlDriScreenInit
(II) fglrx(0): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiDynamicMajor: found major device number 251
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb7760000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.72.5
(II) fglrx(0):     Date: Apr  6 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [uki] removed 1 reserved context for kernel
(II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0xb7760000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,1440) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 6751
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(==) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 78
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 1.0.0
(EE) fglrx(0): XMM failed to open CMMQS connection.
(II) fglrx(0): XMM failed to initialize!
(II) fglrx(0): Enable composite support successfully
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): User Preference Output LVDS using refresh rate 60.0 Hz.
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
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
(II) AIGLX: Screen 0 is not DRI capable
(II) fglrx(0): Setting screen physical size to 380 x 238
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
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Integrated Camera (/dev/input/event6)
(**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
(**) Integrated Camera: always reports core events
(**) Integrated Camera: Device: "/dev/input/event6"
(II) Integrated Camera: Found keys
(II) Integrated Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event12"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event13)
(**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event13"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found relative axes
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(II) TPPS/2 IBM TrackPoint: initialized for relative axes.
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event7)
(**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
(**) ThinkPad Extra Buttons: always reports core events
(**) ThinkPad Extra Buttons: Device: "/dev/input/event7"
(II) ThinkPad Extra Buttons: Found keys
(II) ThinkPad Extra Buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments[/PHP]


Any ideas what the problem is or how i can fix it?

---

### Post by jocko on 2010-05-06
This is your problem:
```
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    **compiled for 1.7.1, [COLOR=Red]module version = 8.72.11[/COLOR]**
    Module class: X.Org Video Driver

<snip>

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
**[COLOR=Red](II) fglrx(0):     Version: 8.72.5[/COLOR]**
(II) fglrx(0):     Date: Apr  6 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [uki] removed 1 reserved context for kernel
(II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0xb7760000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

You appear to have a dri module from an older fglrx version than the rest of the driver. I have no idea how that could have happened, but try to remove every trace of fglrx by marking all packages with "fglrx" in their names for complete removal in synaptic. Then reinstall fglrx and reboot.

---

### Post by Pablo Somebody on 2010-05-08
I run Kubuntu on desktop with an Asus M3A-H/HDMI with onboard ATI HD3200. I've just upgraded to Lucid and had fglrx errors during the upgrade. Initially fglrx wasn't installed, which I eventually managed to do, but I am getting unusable graphical performance. 

I've noticed that I'm getting exactly the same error as above, with the mismatch on the kernel version with the DRI module. I've tried to completely purge fglrx, and reinstall it, but to no avail. Does anyone have any ideas?

---

### Post by StonedSidney on 2010-05-24
I have exactly the same problem as jocko, with exactly the same module version numbers.

Will try removing fglrx (again) and reinstalling from repos....

I got an error during the uninstall from Synaptic: E: fglrx: subprocess installed post-removal script returned error exit status 2

---

### Post by Yellow Pasque on 2010-05-25
> **StonedSidney said:**
> I have exactly the same problem as jocko, with exactly the same module version numbers.

Will try removing fglrx (again) and reinstalling from repos....

I got an error during the uninstall from Synaptic: E: fglrx: subprocess installed post-removal script returned error exit status 2
Follow this to reset your driver setup: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

If dpkg complains:
```
dpkg-divert: mismatch on package
when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx
```
Then run:
```
sudo dpkg-divert --remove /usr/lib/libGL.so.1.2
```
Then you can finish cleaning out the old driver install and reinstall fglrx again.

---

### Post by StonedSidney on 2010-05-27
> **Temüjin said:**
> Follow this to reset your driver setup: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

If dpkg complains:
```
dpkg-divert: mismatch on package
when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx
```
Then run:
```
sudo dpkg-divert --remove /usr/lib/libGL.so.1.2
```
Then you can finish cleaning out the old driver install and reinstall fglrx again.

Thanks, but I fixed it with instructions here: [http://ubuntuforums.org/showthread.php?p=9367327&posted=1#post9367327](http://ubuntuforums.org/showthread.php?p=9367327&posted=1#post9367327)

Clearly your link is a much cleaner solution though, and it hope it works for others (I don't want to test it right now :) )

---

