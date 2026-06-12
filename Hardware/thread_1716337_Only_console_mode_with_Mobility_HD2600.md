---
title: "Only console mode with Mobility HD2600"
date: 2011-03-28
forum: Hardware
---

### Post by -Whity- on 2011-03-28
Hello :),

I'm trying to fix a problem with my laptop (ASUS X53Ka). I have 2 graphic-cards which I can switch in the BIOS (a shared-card ATI X1250 and ATI Mobility HD2600).

Ubuntu 10.10 runs with the X1250 perfect, but I can't connect an external monitor or beamer to the notebook - it only runs with the HD2600.

So, then I tried to start Ubuntu 10.10 with the HD2600, but the only thing i can reach, is the console mode!

I installed the newest catalyst treiber 11.2 from ATI Homepage, runned the installer and then typed "sudo aticonfig --initial" to create a xorg.conf. As I tried "startx" it said: "no screens found" (see Xorg.0.log-file).

Any ideas? Thanks :)

Here are my two files: xorg.conf and Xorg.0.log:

xorg.conf:
> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Xorg.0.log:
> [  1139.201] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  1139.202] X Protocol Version 11, Revision 0
[  1139.202] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[  1139.202] Current Operating System: Linux BIOS 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686
[  1139.202] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=380fec6b-4ab3-4193-9980-b5fd671421bb ro quiet splash
[  1139.203] Build Date: 09 January 2011  12:14:58PM
[  1139.203] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1139.203] Current version of pixman: 0.18.4
[  1139.203] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  1139.204] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1139.205] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 26 13:51:04 2011
[  1139.205] (==) Using config file: "/etc/X11/xorg.conf"
[  1139.206] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1139.207] (==) ServerLayout "aticonfig Layout"
[  1139.207] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[  1139.207] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[  1139.207] (**) |   |-->Device "aticonfig-Device[0]-0"
[  1139.207] (**) |-->Screen "aticonfig-Screen[0]-1" (1)
[  1139.207] (**) |   |-->Monitor "aticonfig-Monitor[0]-1"
[  1139.208] (**) |   |-->Device "aticonfig-Device[0]-1"
[  1139.208] (==) Automatically adding devices
[  1139.208] (==) Automatically enabling devices
[  1139.209] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1139.209] 	Entry deleted from font path.
[  1139.209] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1139.209] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1139.209] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1139.209] (II) Loader magic: 0x81f9b00
[  1139.209] (II) Module ABI versions:
[  1139.209] 	X.Org ANSI C Emulation: 0.4
[  1139.210] 	X.Org Video Driver: 8.0
[  1139.210] 	X.Org XInput driver : 11.0
[  1139.210] 	X.Org Server Extension : 4.0
[  1139.212] (--) PCI:*(0:1:0:0) 1002:9581:1043:1562 rev 0, Mem @ 0xfdff0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[  1139.212] (II) Open ACPI successful (/var/run/acpid.socket)
[  1139.212] (II) "extmod" will be loaded by default.
[  1139.212] (II) "dbe" will be loaded by default.
[  1139.212] (II) "glx" will be loaded by default.
[  1139.212] (II) "record" will be loaded by default.
[  1139.212] (II) "dri" will be loaded by default.
[  1139.212] (II) "dri2" will be loaded by default.
[  1139.212] (II) LoadModule: "extmod"
[  1139.215] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1139.215] (II) Module extmod: vendor="X.Org Foundation"
[  1139.215] 	compiled for 1.9.0, module version = 1.0.0
[  1139.215] 	Module class: X.Org Server Extension
[  1139.215] 	ABI class: X.Org Server Extension, version 4.0
[  1139.215] (II) Loading extension MIT-SCREEN-SAVER
[  1139.215] (II) Loading extension XFree86-VidModeExtension
[  1139.215] (II) Loading extension XFree86-DGA
[  1139.215] (II) Loading extension DPMS
[  1139.215] (II) Loading extension XVideo
[  1139.215] (II) Loading extension XVideo-MotionCompensation
[  1139.215] (II) Loading extension X-Resource
[  1139.215] (II) LoadModule: "dbe"
[  1139.217] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1139.217] (II) Module dbe: vendor="X.Org Foundation"
[  1139.217] 	compiled for 1.9.0, module version = 1.0.0
[  1139.217] 	Module class: X.Org Server Extension
[  1139.217] 	ABI class: X.Org Server Extension, version 4.0
[  1139.217] (II) Loading extension DOUBLE-BUFFER
[  1139.217] (II) LoadModule: "glx"
[  1139.218] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1139.219] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[  1139.219] 	compiled for 6.9.0, module version = 1.0.0
[  1139.220] (II) Loading extension GLX
[  1139.220] (II) LoadModule: "record"
[  1139.221] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1139.222] (II) Module record: vendor="X.Org Foundation"
[  1139.222] 	compiled for 1.9.0, module version = 1.13.0
[  1139.222] 	Module class: X.Org Server Extension
[  1139.222] 	ABI class: X.Org Server Extension, version 4.0
[  1139.222] (II) Loading extension RECORD
[  1139.222] (II) LoadModule: "dri"
[  1139.223] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1139.223] (II) Module dri: vendor="X.Org Foundation"
[  1139.223] 	compiled for 1.9.0, module version = 1.0.0
[  1139.223] 	ABI class: X.Org Server Extension, version 4.0
[  1139.223] (II) Loading extension XFree86-DRI
[  1139.224] (II) LoadModule: "dri2"
[  1139.225] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1139.225] (II) Module dri2: vendor="X.Org Foundation"
[  1139.225] 	compiled for 1.9.0, module version = 1.2.0
[  1139.225] 	ABI class: X.Org Server Extension, version 4.0
[  1139.225] (II) Loading extension DRI2
[  1139.225] (II) LoadModule: "fglrx"
[  1139.226] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[  1139.290] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[  1139.290] 	compiled for 1.4.99.906, module version = 8.82.8
[  1139.290] 	Module class: X.Org Video Driver
[  1139.291] (II) Loading sub module "fglrxdrm"
[  1139.291] (II) LoadModule: "fglrxdrm"
[  1139.292] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[  1139.292] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[  1139.292] 	compiled for 1.4.99.906, module version = 8.82.8
[  1139.292] (II) ATI Proprietary Linux Driver Version Identifier:8.82.8
[  1139.292] (II) ATI Proprietary Linux Driver Release Identifier: 8.821                                
[  1139.293] (II) ATI Proprietary Linux Driver Build Date: Jan 26 2011 17:20:30
[  1139.293] (--) using VT number 8

[  1139.302] (WW) Falling back to old probe method for fglrx
[  1139.329] (II) Loading PCS database from /etc/ati/amdpcsdb
[  1139.332] (--) Chipset Supported AMD Graphics Processor (0x9581) found
[  1139.332] (--) Chipset Supported AMD Graphics Processor (0x9581) found
[  1139.332] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[  1139.332] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[  1139.332] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
[  1139.332] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:5:0) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:6:0) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:3) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:4) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:5) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[  1139.333] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[  1139.334] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[  1139.334] (II) AMD Video driver is signed
[  1139.335] (II) fglrx(0): pEnt->device->identifier=0x881a898
[  1139.335] (II) fglrx(1): pEnt->device->identifier=0x881a898
[  1139.335] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[  1139.335] (II) Loading sub module "vgahw"
[  1139.335] (II) LoadModule: "vgahw"
[  1139.335] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[  1139.336] (II) Module vgahw: vendor="X.Org Foundation"
[  1139.336] 	compiled for 1.9.0, module version = 0.1.0
[  1139.336] 	ABI class: X.Org Video Driver, version 8.0
[  1139.336] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[  1139.336] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  1139.336] (==) fglrx(0): Default visual is TrueColor
[  1139.336] (**) fglrx(0): Option "DPMS" "true"
[  1139.336] (==) fglrx(0): RGB weight 888
[  1139.336] (II) fglrx(0): Using 8 bits per RGB 
[  1139.336] (==) fglrx(0): Buffer Tiling is ON
[  1139.336] (II) Loading sub module "fglrxdrm"
[  1139.336] (II) LoadModule: "fglrxdrm"
[  1139.336] (II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[  1139.534] ukiDynamicMajor: found major device number 249
[  1139.534] ukiDynamicMajor: found major device number 249
[  1139.534] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[  1139.534] ukiOpenDevice: node name is /dev/ati/card0
[  1139.534] ukiOpenDevice: open result is 12, (OK)
[  1139.534] ukiOpenByBusid: ukiOpenMinor returns 12
[  1139.534] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[  1139.534] (==) fglrx(0): NoAccel = NO
[  1139.534] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[  1139.534] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 2600" (Chipset = 0x9581)
[  1139.534] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x1562)
[  1139.534] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[  1139.534] (EE) fglrx(0): No valid linear framebuffer address
[  1139.534] (EE) fglrx(0): PreInitAdapter failed
[  1139.534] (EE) fglrx(0): PreInit failed
[  1139.534] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === end
[  1139.534] (II) fglrx(1): === [xdl_x760_atiddxPreInit] === begin
[  1139.534] (WW) fglrx(1): Quitting screen -- more screens specified than supported by current Adaptor.
[  1139.534] (II) fglrx(1): === [xdl_x760_atiddxPreInit] === end
[  1139.535] SetVBEMode failed
[  1139.535] (II) UnloadModule: "fglrx"
[  1139.535] (II) UnloadModule: "fglrxdrm"
[  1139.535] (II) UnloadModule: "vgahw"
[  1139.535] (II) Unloading /usr/lib/xorg/modules/libvgahw.so
[  1139.535] (II) UnloadModule: "fglrxdrm"
[  1139.535] (II) UnloadModule: "fglrx"
[  1139.535] (II) UnloadModule: "fglrxdrm"
[  1139.535] (EE) Screen(s) found, but none have a usable configuration.
[  1139.535] 
Fatal server error:
[  1139.535] no screens found
[  1139.535] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  1139.535] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1139.535] 
[  1139.543]  ddxSigGiveUp: Closing log

---

