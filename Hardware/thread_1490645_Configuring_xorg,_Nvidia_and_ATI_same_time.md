---
title: "Configuring xorg, Nvidia and ATI same time"
date: 2010-05-22
forum: Hardware
---

### Post by tpls on 2010-05-22
I have installed on my computer ATI HD4200 pci-e(integrated on motherboard) and Geforce 6600 pci-e. Ati has attached one vga-tft display and hdmi-output to tv. Geforce has also one vga-tft, so I have now two monitors and one tv. With Windows 7 I can use all three displays same time, and I can get one huge desktop. Now I'd like to add same functionality on Ubuntu 10.04. How this is possible? I know this is not an easy trick, but I will be very very pleased if someone solves out this difficult situation.

I've tried to add Nvidia with vesa-drivers to my xorg.conf after ATI ccc had done changes on that file, but no luck. Ubuntu boots up with no errors, but the second screen (Nvidia with Acer 17" tft) doesn't show any signs of life :(

xorg.conf

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen	    1  "acer-screen" LeftOf "amdcccle-Screen[1]-0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1280x1024"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "acer"
EndSection

#Section "Device"
#	Identifier  "Default Device"
#	Driver      "fglrx"
#EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "gf6600"
	Driver      "vesa"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

#Section "Screen"
#	Identifier "Default Screen"
#	DefaultDepth     24
#EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "acer-screen"
	Device     "gf6600"
	Monitor    "acer"
	DefaultDepth     24
	SubSection "Display"
		Modes "1280x1024"
	EndSubSection
EndSection

```

/var/log/Xorg.0.log

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux intruder 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=6fd174de-444b-4da9-a0de-7e490dcd0ef0 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 22 21:29:03 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "amdcccle Layout"
(**) |-->Screen "amdcccle-Screen[1]-0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "amdcccle-Device[1]-0"
(==) No monitor specified for screen "amdcccle-Screen[1]-0".
	Using a default monitor configuration.
(**) |-->Screen "acer-screen" (1)
(**) |   |-->Monitor "acer"
(**) |   |-->Device "gf6600"
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
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:9710:1043:83a2 ATI Technologies Inc RS880 [Radeon HD 4200] rev 0, Mem @ 0xc0000000/268435456, 0xf7ff0000/65536, 0xf7e00000/1048576, I/O @ 0x0000c000/256
(--) PCI: (0:2:0:0) 10de:0141:196d:0000 nVidia Corporation NV43 [GeForce 6600] rev 162, Mem @ 0xf8000000/67108864, 0xd0000000/268435456, 0xfd000000/16777216, BIOS @ 0x????????/131072
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
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9710) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x2753060
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
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
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(--) fglrx(0): Chipset: "ATI Radeon HD 4200" (Chipset = 0x9710)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x83a2)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xf7ff0000
(--) fglrx(0): I/O port at 0x0000c000
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
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS880
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
(--) fglrx(0): Video RAM: 376832 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x17000000)
(II) fglrx(0): Interrupt handler installed at IRQ 28.
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
(II) fglrx(0): Connected Display0: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SNY  Model: 801  Serial#: 16843009
(II) fglrx(0): Year: 2008  Week: 1
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) fglrx(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) fglrx(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 74.2 MHz   Image Size:  1600 x 900 mm
(II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
(II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) fglrx(0): Monitor name: SONY TV
(II) fglrx(0): Ranges: V min: 48 V max: 62 Hz, H min: 14 H max: 48 kHz, PixClock max 90 MHz
(II) fglrx(0): Number of EDID sections to follow: 1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004dd9010801010101
(II) fglrx(0): 	0112010380a05a780a0dc9a057479827
(II) fglrx(0): 	12484c21080001010101010101010101
(II) fglrx(0): 	010101010101662150b051001b304070
(II) fglrx(0): 	360040846300001e011d007251d01e20
(II) fglrx(0): 	6e285500408463000018000000fc0053
(II) fglrx(0): 	4f4e592054560a2020202020000000fd
(II) fglrx(0): 	00303e0e3009000a2020202020200171
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: ACR  Model: ad29  Serial#: 1366296715
(II) fglrx(0): Year: 2005  Week: 17
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.07
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.293 greenY: 0.628
(II) fglrx(0): blueX: 0.141 blueY: 0.079   whiteX: 0.310 whiteY: 0.329
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) fglrx(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #5: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #6: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) fglrx(0): #7: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No: ETL2908061
(II) fglrx(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: Acer AL1912
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00047229ad8b087051
(II) fglrx(0): 	110f010368261e6b2ac315a4594ba024
(II) fglrx(0): 	144f54bfef00818f8180714f7140614f
(II) fglrx(0): 	6140454f4540302a009851002a403070
(II) fglrx(0): 	1300782d1100001e000000ff0045544c
(II) fglrx(0): 	323930383036310a2020000000fd0037
(II) fglrx(0): 	4b1e530e000a202020202020000000fc
(II) fglrx(0): 	004163657220414c313931320a20001d
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Output DFP2 using monitor section 0-DFP2
(**) fglrx(0): Option "PreferredMode" "1280x1024"
(**) fglrx(0): Option "Position" "0 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(**) fglrx(0): Option "TargetRefresh" "60"
(II) fglrx(0): Output CRT1 using monitor section 0-CRT1
(**) fglrx(0): Option "PreferredMode" "1280x1024"
(**) fglrx(0): Option "Position" "0 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(**) fglrx(0): Option "TargetRefresh" "60"
(II) fglrx(0): Output DFP2 connected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Using user preference for initial modes
(II) fglrx(0): Output DFP2 using initial mode 1280x1024
(II) fglrx(0): Output CRT1 using initial mode 1280x1024
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 4200 has 2 configurable heads and 2 displays connected.
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
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 16, (OK)
ukiOpenByBusid: ukiOpenMinor returns 16
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) fglrx(0): [uki] DRM interface version 1.0
(II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f1431c2e000
(II) fglrx(0): [uki] framebuffer handle = 0x3000
(II) fglrx(0): [uki] added 1 reserved context for kernel
(II) fglrx(0): swlDriScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.72.11
(II) fglrx(0):     Date: Apr  8 2010
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.32-22-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [uki] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd5fde000 FBMappedSize: 0x0101d000
(II) fglrx(0): Reserved 0x04000000 bytes of sideport memory for power saving
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,2200)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 280
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(==) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
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
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.7.1, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available
(II) fglrx(0): Enable composite support successfully
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): User Preference Output DFP2 using refresh rate 60.0 Hz.
(II) fglrx(0): User Preference Output CRT1 using refresh rate 60.0 Hz.
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
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:5:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 17, (OK)
ukiOpenByBusid: ukiOpenMinor returns 17
ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 338 x 270
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) XKB: reuse xkmfile /var/lib/xkb/server-F30D752BAEAAD4B8C79BE2C421539A0D3700902C.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) config/udev: Adding input device Microsoft Basic Optical Mouse (/dev/input/event3)
(**) Microsoft Basic Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Microsoft Basic Optical Mouse: always reports core events
(**) Microsoft Basic Optical Mouse: Device: "/dev/input/event3"
(II) Microsoft Basic Optical Mouse: Found 3 mouse buttons
(II) Microsoft Basic Optical Mouse: Found scroll wheel(s)
(II) Microsoft Basic Optical Mouse: Found relative axes
(II) Microsoft Basic Optical Mouse: Found x and y relative axes
(II) Microsoft Basic Optical Mouse: Configuring as mouse
(**) Microsoft Basic Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Microsoft Basic Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Basic Optical Mouse" (type: MOUSE)
(II) Microsoft Basic Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Microsoft Basic Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event4)
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: always reports core events
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event4"
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found keys
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) config/udev: Adding input device Microsft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/event5)
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev pointer catchall"
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: Applying InputClass "evdev keyboard catchall"
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: always reports core events
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: Device: "/dev/input/event5"
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found 9 mouse buttons
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found scroll wheel(s)
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found relative axes
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found x and y relative axes
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found absolute axes
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found x and y absolute axes
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Found keys
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Configuring as mouse
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: Configuring as keyboard
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: YAxisMapping: buttons 4 and 5
(**) Microsft Microsoft Wireless Optical Desktop® 2.10: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Optical Desktop® 2.10" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(II) Microsft Microsoft Wireless Optical Desktop® 2.10: initialized for relative axes.
(WW) Microsft Microsoft Wireless Optical Desktop® 2.10: ignoring absolute axes.
(II) config/udev: Adding input device Microsft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsft Microsoft Wireless Optical Desktop® 2.10 (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments

```

---

