---
title: "need openGL direct rendering, I can't enable it"
date: 2013-04-09
forum: Hardware
---

### Post by heWhoWearsAshes on 2013-04-09
I've installed steam, but it's complaining that there isn't openGL direct rendering. Searching google leads me to believe that there might be a problem using 32 bit graphics drivers - needed by the steam client - on 64 bit os. 

I'm relatively new to graphics stuff, please help.

---

### Post by Yellow Pasque on 2013-04-09
Post your /var/log/Xorg.0.log
(Use [ code ] tags)

---

### Post by heWhoWearsAshes on 2013-04-10
Ok, here you go:

```
[    33.068] X.Org X Server 1.11.3
Release Date: 2011-12-16
[    33.068] X Protocol Version 11, Revision 0
[    33.068] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    33.068] Current Operating System: Linux zombie 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64
[    33.068] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-40-generic root=UUID=e7881d84-e297-43bc-a846-02859771b7a4 ro quiet splash vt.handoff=7
[    33.068] Build Date: 27 February 2013  02:07:42AM
[    33.068] xorg-server 2:1.11.4-0ubuntu10.12 (For technical support please see http://www.ubuntu.com/support) 
[    33.068] Current version of pixman: 0.24.4
[    33.068] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    33.068] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.068] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  9 15:00:52 2013
[    33.069] (==) Using config file: "/etc/X11/xorg.conf"
[    33.069] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.069] (==) ServerLayout "aticonfig Layout"
[    33.069] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    33.069] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    33.069] (**) |   |-->Device "aticonfig-Device[0]-0"
[    33.069] (==) Automatically adding devices
[    33.069] (==) Automatically enabling devices
[    33.069] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.069] 	Entry deleted from font path.
[    33.069] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.069] 	Entry deleted from font path.
[    33.069] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.069] 	Entry deleted from font path.
[    33.069] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.069] 	Entry deleted from font path.
[    33.069] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.069] 	Entry deleted from font path.
[    33.114] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    33.114] 	Entry deleted from font path.
[    33.114] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    33.114] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.114] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.114] (II) Loader magic: 0x7f5c49114b00
[    33.114] (II) Module ABI versions:
[    33.114] 	X.Org ANSI C Emulation: 0.4
[    33.114] 	X.Org Video Driver: 11.0
[    33.114] 	X.Org XInput driver : 16.0
[    33.114] 	X.Org Server Extension : 6.0
[    33.115] (--) PCI:*(0:1:0:0) 1002:954f:1787:2008 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    33.115] (II) Open ACPI successful (/var/run/acpid.socket)
[    33.115] (II) "extmod" will be loaded by default.
[    33.115] (II) "dbe" will be loaded by default.
[    33.115] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    33.115] (II) "record" will be loaded by default.
[    33.115] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    33.115] (II) "dri2" will be loaded by default.
[    33.115] (II) LoadModule: "glx"
[    33.141] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    33.141] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    33.141] 	compiled for 6.9.0, module version = 1.0.0
[    33.141] (II) Loading extension GLX
[    33.141] (II) LoadModule: "dri"
[    33.156] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    33.156] (II) Module dri: vendor="X.Org Foundation"
[    33.156] 	compiled for 1.11.3, module version = 1.0.0
[    33.156] 	ABI class: X.Org Server Extension, version 6.0
[    33.156] (II) Loading extension XFree86-DRI
[    33.156] (II) LoadModule: "extmod"
[    33.157] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    33.157] (II) Module extmod: vendor="X.Org Foundation"
[    33.157] 	compiled for 1.11.3, module version = 1.0.0
[    33.157] 	Module class: X.Org Server Extension
[    33.157] 	ABI class: X.Org Server Extension, version 6.0
[    33.157] (II) Loading extension MIT-SCREEN-SAVER
[    33.157] (II) Loading extension XFree86-VidModeExtension
[    33.157] (II) Loading extension XFree86-DGA
[    33.157] (II) Loading extension DPMS
[    33.157] (II) Loading extension XVideo
[    33.157] (II) Loading extension XVideo-MotionCompensation
[    33.157] (II) Loading extension X-Resource
[    33.157] (II) LoadModule: "dbe"
[    33.157] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    33.157] (II) Module dbe: vendor="X.Org Foundation"
[    33.157] 	compiled for 1.11.3, module version = 1.0.0
[    33.157] 	Module class: X.Org Server Extension
[    33.157] 	ABI class: X.Org Server Extension, version 6.0
[    33.157] (II) Loading extension DOUBLE-BUFFER
[    33.157] (II) LoadModule: "record"
[    33.157] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    33.157] (II) Module record: vendor="X.Org Foundation"
[    33.157] 	compiled for 1.11.3, module version = 1.13.0
[    33.157] 	Module class: X.Org Server Extension
[    33.157] 	ABI class: X.Org Server Extension, version 6.0
[    33.158] (II) Loading extension RECORD
[    33.158] (II) LoadModule: "dri2"
[    33.158] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    33.158] (II) Module dri2: vendor="X.Org Foundation"
[    33.158] 	compiled for 1.11.3, module version = 1.2.0
[    33.158] 	ABI class: X.Org Server Extension, version 6.0
[    33.158] (II) Loading extension DRI2
[    33.158] (II) LoadModule: "fglrx"
[    33.158] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    33.174] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    33.174] 	compiled for 1.4.99.906, module version = 8.96.4
[    33.174] 	Module class: X.Org Video Driver
[    33.174] (II) Loading sub module "fglrxdrm"
[    33.174] (II) LoadModule: "fglrxdrm"
[    33.175] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    33.175] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    33.175] 	compiled for 1.4.99.906, module version = 8.96.4
[    33.175] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    33.175] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[    33.175] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:50
[    33.175] (++) using VT number 7


[    33.175] (WW) Falling back to old probe method for fglrx
[    33.179] (II) Loading PCS database from /etc/ati/amdpcsdb
[    33.180] (--) Chipset Supported AMD Graphics Processor (0x954F) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    33.180] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    33.180] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    33.180] (II) AMD Video driver is signed
[    33.180] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    33.180] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    33.180] (II) fglrx(0): pEnt->device->identifier=0x7f5c49af1d70
[    33.180] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    33.180] (II) Loading sub module "vgahw"
[    33.180] (II) LoadModule: "vgahw"
[    33.181] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    33.181] (II) Module vgahw: vendor="X.Org Foundation"
[    33.181] 	compiled for 1.11.3, module version = 0.1.0
[    33.181] 	ABI class: X.Org Video Driver, version 11.0
[    33.181] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    33.181] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    33.181] (==) fglrx(0): Default visual is TrueColor
[    33.181] (**) fglrx(0): Option "DPMS" "true"
[    33.181] (==) fglrx(0): RGB weight 888
[    33.181] (II) fglrx(0): Using 8 bits per RGB 
[    33.181] (==) fglrx(0): Buffer Tiling is ON
[    33.181] (II) Loading sub module "fglrxdrm"
[    33.181] (II) LoadModule: "fglrxdrm"
[    33.181] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    33.181] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    33.181] 	compiled for 1.4.99.906, module version = 8.96.4
[    33.183] ukiDynamicMajor: found major device number 250
[    33.183] ukiDynamicMajor: found major device number 250
[    33.183] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    33.183] ukiOpenDevice: node name is /dev/ati/card0
[    33.183] ukiOpenDevice: open result is 12, (OK)
[    33.183] ukiOpenByBusid: ukiOpenMinor returns 12
[    33.183] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    33.183] (**) fglrx(0): NoAccel = NO
[    33.183] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    33.183] (--) fglrx(0): Chipset: "ATI Radeon HD 4300/4500 Series" (Chipset = 0x954f)
[    33.183] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x2008)
[    33.183] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    33.183] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    33.183] (--) fglrx(0): MMIO registers at 0xfeaf0000
[    33.183] (--) fglrx(0): I/O port at 0x0000d000
[    33.183] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    33.255] (II) fglrx(0): AC Adapter is used
[    33.263] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    33.264] (II) Loading sub module "vbe"
[    33.264] (II) LoadModule: "vbe"
[    33.264] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    33.264] (II) Module vbe: vendor="X.Org Foundation"
[    33.264] 	compiled for 1.11.3, module version = 1.1.0
[    33.264] 	ABI class: X.Org Video Driver, version 11.0
[    33.264] (II) fglrx(0): VESA BIOS detected
[    33.264] (II) fglrx(0): VESA VBE Version 3.0
[    33.264] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    33.264] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    33.264] (II) fglrx(0): VESA VBE OEM Software Rev: 11.21
[    33.264] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    33.264] (II) fglrx(0): VESA VBE OEM Product: R-00
[    33.264] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    33.291] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    33.291] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
[    33.291] (II) fglrx(0): PCIE card detected
[    33.291] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    33.291] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    33.305] (II) fglrx(0): Using adapter: 1:0.0.
[    33.348] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    33.364] (II) fglrx(0): Interrupt handler installed at IRQ 44.
[    33.364] (II) fglrx(0): RandR 1.2 support is enabled!
[    33.364] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    33.364] (==) fglrx(0): Center Mode is disabled 
[    33.364] (II) Loading sub module "fb"
[    33.364] (II) LoadModule: "fb"
[    33.364] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.364] (II) Module fb: vendor="X.Org Foundation"
[    33.364] 	compiled for 1.11.3, module version = 1.0.0
[    33.364] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    33.364] (II) Loading sub module "ddc"
[    33.364] (II) LoadModule: "ddc"
[    33.364] (II) Module "ddc" already built-in
[    36.116] (II) fglrx(0): Finished Initialize PPLIB!
[    36.125] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    36.125] (II) fglrx(0): Output DFP2 has no monitor section
[    36.125] (II) fglrx(0): Output CRT1 has no monitor section
[    36.125] (II) fglrx(0): Output CRT2 has no monitor section
[    36.125] (II) Loading sub module "ddc"
[    36.125] (II) LoadModule: "ddc"
[    36.125] (II) Module "ddc" already built-in
[    36.125] (II) fglrx(0): Connected Display0: CRT2
[    36.125] (II) fglrx(0): Display0 EDID data ---------------------------
[    36.125] (II) fglrx(0): Manufacturer: SNY  Model: 2250  Serial#: 16843009
[    36.125] (II) fglrx(0): Year: 2005  Week: 4
[    36.125] (II) fglrx(0): EDID Version: 1.3
[    36.125] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    36.125] (II) fglrx(0): Sync:  Separate  Composite
[    36.125] (II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    36.125] (II) fglrx(0): Gamma: 2.20
[    36.125] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    36.125] (II) fglrx(0): First detailed timing is preferred mode
[    36.125] (II) fglrx(0): redX: 0.643 redY: 0.344   greenX: 0.304 greenY: 0.566
[    36.125] (II) fglrx(0): blueX: 0.141 blueY: 0.085   whiteX: 0.312 whiteY: 0.318
[    36.125] (II) fglrx(0): Supported established timings:
[    36.125] (II) fglrx(0): 720x400@70Hz
[    36.125] (II) fglrx(0): 640x480@60Hz
[    36.125] (II) fglrx(0): 800x600@60Hz
[    36.125] (II) fglrx(0): 1024x768@60Hz
[    36.125] (II) fglrx(0): Manufacturer's mask: 0
[    36.125] (II) fglrx(0): Supported detailed timing:
[    36.125] (II) fglrx(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    36.125] (II) fglrx(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    36.125] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    36.125] (II) fglrx(0): Ranges: V min: 57 V max: 63 Hz, H min: 28 H max: 49 kHz, PixClock max 95 MHz
[    36.125] (II) fglrx(0): Monitor name: SDM-HS53
[    36.125] (II) fglrx(0): Serial No: 0419510
[    36.125] (II) fglrx(0): EDID (in hex):
[    36.125] (II) fglrx(0): 	00ffffffffffff004dd9502201010101
[    36.125] (II) fglrx(0): 	040f01030c1e1778ea8c3ea4584d9124
[    36.125] (II) fglrx(0): 	154f51a1080001010101010101010101
[    36.125] (II) fglrx(0): 	01010101010164190040410026301888
[    36.125] (II) fglrx(0): 	360030e410000018000000fd00393f1c
[    36.125] (II) fglrx(0): 	3109000a202020202020000000fc0053
[    36.125] (II) fglrx(0): 	444d2d485335330a20202020000000ff
[    36.125] (II) fglrx(0): 	00303431393531300a202020202000d8
[    36.125] (II) fglrx(0): End of Display0 EDID data --------------------
[    36.165] (II) fglrx(0): EDID for output DFP1
[    36.165] (II) fglrx(0): EDID for output DFP2
[    36.165] (II) fglrx(0): EDID for output CRT1
[    36.165] (II) fglrx(0): EDID for output CRT2
[    36.165] (II) fglrx(0): Manufacturer: SNY  Model: 2250  Serial#: 16843009
[    36.165] (II) fglrx(0): Year: 2005  Week: 4
[    36.165] (II) fglrx(0): EDID Version: 1.3
[    36.165] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    36.165] (II) fglrx(0): Sync:  Separate  Composite
[    36.165] (II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    36.165] (II) fglrx(0): Gamma: 2.20
[    36.165] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    36.165] (II) fglrx(0): First detailed timing is preferred mode
[    36.165] (II) fglrx(0): redX: 0.643 redY: 0.344   greenX: 0.304 greenY: 0.566
[    36.165] (II) fglrx(0): blueX: 0.141 blueY: 0.085   whiteX: 0.312 whiteY: 0.318
[    36.165] (II) fglrx(0): Supported established timings:
[    36.165] (II) fglrx(0): 720x400@70Hz
[    36.165] (II) fglrx(0): 640x480@60Hz
[    36.165] (II) fglrx(0): 800x600@60Hz
[    36.165] (II) fglrx(0): 1024x768@60Hz
[    36.165] (II) fglrx(0): Manufacturer's mask: 0
[    36.165] (II) fglrx(0): Supported detailed timing:
[    36.165] (II) fglrx(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    36.165] (II) fglrx(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    36.165] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    36.165] (II) fglrx(0): Ranges: V min: 57 V max: 63 Hz, H min: 28 H max: 49 kHz, PixClock max 95 MHz
[    36.165] (II) fglrx(0): Monitor name: SDM-HS53
[    36.165] (II) fglrx(0): Serial No: 0419510
[    36.165] (II) fglrx(0): EDID (in hex):
[    36.165] (II) fglrx(0): 	00ffffffffffff004dd9502201010101
[    36.165] (II) fglrx(0): 	040f01030c1e1778ea8c3ea4584d9124
[    36.165] (II) fglrx(0): 	154f51a1080001010101010101010101
[    36.165] (II) fglrx(0): 	01010101010164190040410026301888
[    36.165] (II) fglrx(0): 	360030e410000018000000fd00393f1c
[    36.165] (II) fglrx(0): 	3109000a202020202020000000fc0053
[    36.165] (II) fglrx(0): 	444d2d485335330a20202020000000ff
[    36.165] (II) fglrx(0): 	00303431393531300a202020202000d8
[    36.165] (II) fglrx(0): Printing probed modes for output CRT2
[    36.165] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    36.165] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    36.165] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    36.165] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    36.165] (II) fglrx(0): Output DFP1 disconnected
[    36.165] (II) fglrx(0): Output DFP2 disconnected
[    36.165] (II) fglrx(0): Output CRT1 disconnected
[    36.165] (II) fglrx(0): Output CRT2 connected
[    36.165] (II) fglrx(0): Using exact sizes for initial modes
[    36.165] (II) fglrx(0): Output CRT2 using initial mode 1024x768
[    36.165] (II) fglrx(0): DPI set to (96, 96)
[    36.165] (II) fglrx(0): Adapter ATI Radeon HD 4300/4500 Series has 2 configurable heads and 1 displays connected.
[    36.165] (==) fglrx(0):  PseudoColor visuals disabled
[    36.165] (II) Loading sub module "ramdac"
[    36.165] (II) LoadModule: "ramdac"
[    36.165] (II) Module "ramdac" already built-in
[    36.165] (==) fglrx(0): NoDRI = NO
[    36.165] (==) fglrx(0): Capabilities: 0x00000000
[    36.165] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    36.165] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    36.165] (==) fglrx(0): UseFastTLS=0
[    36.165] (==) fglrx(0): BlockSignalsOnLock=1
[    36.165] (--) Depth 24 pixmap format is 32 bpp
[    36.166] (II) Loading extension ATIFGLRXDRI
[    36.166] (II) fglrx(0): doing swlDriScreenInit
[    36.166] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    36.166] ukiDynamicMajor: found major device number 250
[    36.166] ukiDynamicMajor: found major device number 250
[    36.166] ukiDynamicMajor: found major device number 250
[    36.166] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    36.166] ukiOpenDevice: node name is /dev/ati/card0
[    36.166] ukiOpenDevice: open result is 17, (OK)
[    36.166] ukiOpenByBusid: ukiOpenMinor returns 17
[    36.166] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    36.166] (II) fglrx(0): [uki] DRM interface version 1.0
[    36.166] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    36.166] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    36.166] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f5c48d04000
[    36.166] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    36.166] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    36.166] (II) fglrx(0): swlDriScreenInit done
[    36.166] (II) fglrx(0): Kernel Module Version Information:
[    36.166] (II) fglrx(0):     Name: fglrx
[    36.166] (II) fglrx(0):     Version: 8.96.4
[    36.166] (II) fglrx(0):     Date: Mar 12 2012
[    36.166] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    36.166] (II) fglrx(0): Kernel Module version matches driver.
[    36.166] (II) fglrx(0): Kernel Module Build Time Information:
[    36.166] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-40-generic
[    36.166] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    36.166] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    36.166] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    36.166] (II) fglrx(0): [uki] register handle = 0x00004000
[    36.180] (II) fglrx(0): DRI initialization successfull
[    36.180] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[    36.181] (==) fglrx(0): Backing store disabled
[    36.181] (II) Loading extension FGLRXEXTENSION
[    36.181] (**) fglrx(0): DPMS enabled
[    36.181] (II) fglrx(0): Initialized in-driver Xinerama extension
[    36.181] (**) fglrx(0): Textured Video is enabled.
[    36.181] (II) LoadModule: "glesx"
[    36.181] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    36.182] (II) Module glesx: vendor="X.Org Foundation"
[    36.182] 	compiled for 1.4.99.906, module version = 1.0.0
[    36.182] (II) Loading extension GLESX
[    36.182] (II) fglrx(0): GLESX enableFlags = 528
[    36.182] (II) fglrx(0): GLESX is enabled
[    36.182] (II) LoadModule: "amdxmm"
[    36.182] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    36.182] (II) Module amdxmm: vendor="X.Org Foundation"
[    36.182] 	compiled for 1.4.99.906, module version = 2.0.0
[    36.182] (II) Loading extension AMDXVOPL
[    36.182] (II) Loading extension AMDXVBA
[    36.183] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    36.185] (II) fglrx(0): Enable composite support successfully
[    36.185] (WW) fglrx(0): Option "VendorName" is not used
[    36.185] (WW) fglrx(0): Option "ModelName" is not used
[    36.185] (II) fglrx(0): X context handle = 0x1
[    36.185] (II) fglrx(0): [DRI] installation complete
[    36.185] (==) fglrx(0): Silken mouse enabled
[    36.185] (==) fglrx(0): Using HW cursor of display infrastructure!
[    36.186] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    36.258] (--) RandR disabled
[    36.258] (II) Initializing built-in extension Generic Event Extension
[    36.258] (II) Initializing built-in extension SHAPE
[    36.258] (II) Initializing built-in extension MIT-SHM
[    36.258] (II) Initializing built-in extension XInputExtension
[    36.258] (II) Initializing built-in extension XTEST
[    36.258] (II) Initializing built-in extension BIG-REQUESTS
[    36.258] (II) Initializing built-in extension SYNC
[    36.258] (II) Initializing built-in extension XKEYBOARD
[    36.258] (II) Initializing built-in extension XC-MISC
[    36.258] (II) Initializing built-in extension SECURITY
[    36.258] (II) Initializing built-in extension XINERAMA
[    36.258] (II) Initializing built-in extension XFIXES
[    36.258] (II) Initializing built-in extension RENDER
[    36.258] (II) Initializing built-in extension RANDR
[    36.258] (II) Initializing built-in extension COMPOSITE
[    36.258] (II) Initializing built-in extension DAMAGE
[    36.273] ukiDynamicMajor: found major device number 250
[    36.273] ukiDynamicMajor: found major device number 250
[    36.273] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    36.273] ukiOpenDevice: node name is /dev/ati/card0
[    36.273] ukiOpenDevice: open result is 19, (OK)
[    36.273] ukiOpenByBusid: ukiOpenMinor returns 19
[    36.273] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    36.349] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    36.349] (II) fglrx(0): Enable the clock gating!
[    36.349] (II) fglrx(0): Setting screen physical size to 270 x 203
[    36.356] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.359] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    36.359] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.359] (II) LoadModule: "evdev"
[    36.359] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.359] (II) Module evdev: vendor="X.Org Foundation"
[    36.359] 	compiled for 1.11.3, module version = 2.7.0
[    36.359] 	Module class: X.Org XInput Driver
[    36.359] 	ABI class: X.Org XInput driver, version 16.0
[    36.359] (II) Using input driver 'evdev' for 'Power Button'
[    36.359] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.359] (**) Power Button: always reports core events
[    36.359] (**) evdev: Power Button: Device: "/dev/input/event1"
[    36.359] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.359] (--) evdev: Power Button: Found keys
[    36.359] (II) evdev: Power Button: Configuring as keyboard
[    36.359] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    36.359] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    36.359] (**) Option "xkb_rules" "evdev"
[    36.359] (**) Option "xkb_model" "pc105"
[    36.359] (**) Option "xkb_layout" "us"
[    36.359] (**) Option "xkb_variant" "intl"
[    36.361] (II) XKB: reuse xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[    36.361] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    36.361] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.361] (II) Using input driver 'evdev' for 'Power Button'
[    36.361] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.361] (**) Power Button: always reports core events
[    36.362] (**) evdev: Power Button: Device: "/dev/input/event0"
[    36.362] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.362] (--) evdev: Power Button: Found keys
[    36.362] (II) evdev: Power Button: Configuring as keyboard
[    36.362] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    36.362] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    36.362] (**) Option "xkb_rules" "evdev"
[    36.362] (**) Option "xkb_model" "pc105"
[    36.362] (**) Option "xkb_layout" "us"
[    36.362] (**) Option "xkb_variant" "intl"
[    36.362] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event13)
[    36.362] (II) No input driver specified, ignoring this device.
[    36.362] (II) This device may have been added with another device file.
[    36.362] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event4)
[    36.362] (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    36.362] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Wireless Mouse'
[    36.362] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.362] (**) MOSART Semi. 2.4G Wireless Mouse: always reports core events
[    36.362] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: Device: "/dev/input/event4"
[    36.362] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Vendor 0x62a Product 0x3270
[    36.362] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found 9 mouse buttons
[    36.362] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found scroll wheel(s)
[    36.362] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found relative axes
[    36.362] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found x and y relative axes
[    36.362] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Configuring as mouse
[    36.362] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Adding scrollwheel support
[    36.362] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: YAxisMapping: buttons 4 and 5
[    36.362] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.362] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4/event4"
[    36.362] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Wireless Mouse" (type: MOUSE, id 8)
[    36.362] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: initialized for relative axes.
[    36.363] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) keeping acceleration scheme 1
[    36.363] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration profile 0
[    36.363] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration factor: 2.000
[    36.363] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration threshold: 4
[    36.363] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/mouse1)
[    36.363] (II) No input driver specified, ignoring this device.
[    36.363] (II) This device may have been added with another device file.
[    36.363] (II) config/udev: Adding input device MLK 2.4GHz Wireless Optical Mouse (/dev/input/event3)
[    36.363] (**) MLK 2.4GHz Wireless Optical Mouse: Applying InputClass "evdev pointer catchall"
[    36.363] (**) MLK 2.4GHz Wireless Optical Mouse: Applying InputClass "evdev keyboard catchall"
[    36.363] (II) Using input driver 'evdev' for 'MLK 2.4GHz Wireless Optical Mouse'
[    36.363] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.363] (**) MLK 2.4GHz Wireless Optical Mouse: always reports core events
[    36.363] (**) evdev: MLK 2.4GHz Wireless Optical Mouse: Device: "/dev/input/event3"
[    36.363] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Vendor 0x4fc Product 0x538
[    36.363] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found 9 mouse buttons
[    36.363] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found scroll wheel(s)
[    36.363] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found relative axes
[    36.363] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found x and y relative axes
[    36.363] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found absolute axes
[    36.363] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Forcing absolute x/y axes to exist.
[    36.363] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found keys
[    36.363] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Configuring as mouse
[    36.363] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Configuring as keyboard
[    36.363] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Adding scrollwheel support
[    36.363] (**) evdev: MLK 2.4GHz Wireless Optical Mouse: YAxisMapping: buttons 4 and 5
[    36.363] (**) evdev: MLK 2.4GHz Wireless Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.363] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3/event3"
[    36.363] (II) XINPUT: Adding extended input device "MLK 2.4GHz Wireless Optical Mouse" (type: KEYBOARD, id 9)
[    36.363] (**) Option "xkb_rules" "evdev"
[    36.363] (**) Option "xkb_model" "pc105"
[    36.363] (**) Option "xkb_layout" "us"
[    36.363] (**) Option "xkb_variant" "intl"
[    36.363] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: initialized for relative axes.
[    36.363] (WW) evdev: MLK 2.4GHz Wireless Optical Mouse: ignoring absolute axes.
[    36.364] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) keeping acceleration scheme 1
[    36.364] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) acceleration profile 0
[    36.364] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) acceleration factor: 2.000
[    36.364] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) acceleration threshold: 4
[    36.364] (II) config/udev: Adding input device MLK 2.4GHz Wireless Optical Mouse (/dev/input/mouse0)
[    36.364] (II) No input driver specified, ignoring this device.
[    36.364] (II) This device may have been added with another device file.
[    36.364] (II) config/udev: Adding input device HDA ATI SB Line-Out CLFE (/dev/input/event10)
[    36.364] (II) No input driver specified, ignoring this device.
[    36.364] (II) This device may have been added with another device file.
[    36.364] (II) config/udev: Adding input device HDA ATI SB Line-Out Surround (/dev/input/event11)
[    36.364] (II) No input driver specified, ignoring this device.
[    36.364] (II) This device may have been added with another device file.
[    36.364] (II) config/udev: Adding input device HDA ATI SB Line-Out Front (/dev/input/event12)
[    36.364] (II) No input driver specified, ignoring this device.
[    36.364] (II) This device may have been added with another device file.
[    36.364] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event5)
[    36.364] (II) No input driver specified, ignoring this device.
[    36.364] (II) This device may have been added with another device file.
[    36.365] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[    36.365] (II) No input driver specified, ignoring this device.
[    36.365] (II) This device may have been added with another device file.
[    36.365] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event7)
[    36.365] (II) No input driver specified, ignoring this device.
[    36.365] (II) This device may have been added with another device file.
[    36.365] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event8)
[    36.365] (II) No input driver specified, ignoring this device.
[    36.365] (II) This device may have been added with another device file.
[    36.365] (II) config/udev: Adding input device HDA ATI SB Line-Out Side (/dev/input/event9)
[    36.365] (II) No input driver specified, ignoring this device.
[    36.365] (II) This device may have been added with another device file.
[    36.365] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    36.365] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    36.365] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    36.365] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.365] (**) AT Translated Set 2 keyboard: always reports core events
[    36.365] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    36.365] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    36.365] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    36.365] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    36.365] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    36.365] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    36.365] (**) Option "xkb_rules" "evdev"
[    36.365] (**) Option "xkb_model" "pc105"
[    36.365] (**) Option "xkb_layout" "us"
[    36.365] (**) Option "xkb_variant" "intl"
[    36.499] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    37.276] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[    37.276] (II) fglrx(0): Using EDID range info for horizontal sync
[    37.276] (II) fglrx(0): Using EDID range info for vertical refresh
[    37.276] (II) fglrx(0): Printing DDC gathered Modelines:
[    37.276] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    37.276] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    37.276] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    37.276] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    38.343] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[    38.343] (II) fglrx(0): Using hsync ranges from config file
[    38.343] (II) fglrx(0): Using vrefresh ranges from config file
[    38.343] (II) fglrx(0): Printing DDC gathered Modelines:
[    38.343] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    38.343] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    38.343] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    38.343] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    68.181] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[    68.181] (II) fglrx(0): Using hsync ranges from config file
[    68.181] (II) fglrx(0): Using vrefresh ranges from config file
[    68.181] (II) fglrx(0): Printing DDC gathered Modelines:
[    68.181] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    68.181] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    68.181] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    68.181] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    71.172] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[    71.172] (II) fglrx(0): Using hsync ranges from config file
[    71.172] (II) fglrx(0): Using vrefresh ranges from config file
[    71.172] (II) fglrx(0): Printing DDC gathered Modelines:
[    71.172] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    71.172] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    71.172] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    71.172] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    71.907] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[    71.907] (II) fglrx(0): Using hsync ranges from config file
[    71.907] (II) fglrx(0): Using vrefresh ranges from config file
[    71.907] (II) fglrx(0): Printing DDC gathered Modelines:
[    71.907] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    71.907] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    71.907] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    71.907] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    74.559] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[    74.559] (II) fglrx(0): Using hsync ranges from config file
[    74.559] (II) fglrx(0): Using vrefresh ranges from config file
[    74.559] (II) fglrx(0): Printing DDC gathered Modelines:
[    74.559] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    74.559] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    74.559] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    74.559] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    75.705] (II) XKB: reuse xkmfile /var/lib/xkb/server-D8278742E1FF7238DDD8602D24FE4364B072AF32.xkm
[    92.150] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[    92.150] (II) fglrx(0): Using hsync ranges from config file
[    92.150] (II) fglrx(0): Using vrefresh ranges from config file
[    92.150] (II) fglrx(0): Printing DDC gathered Modelines:
[    92.150] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    92.150] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    92.150] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    92.150] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1136.872] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[  1136.872] (II) fglrx(0): Using hsync ranges from config file
[  1136.872] (II) fglrx(0): Using vrefresh ranges from config file
[  1136.872] (II) fglrx(0): Printing DDC gathered Modelines:
[  1136.872] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1136.872] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1136.872] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1136.872] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  4248.649] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[  4248.649] (II) fglrx(0): Using hsync ranges from config file
[  4248.649] (II) fglrx(0): Using vrefresh ranges from config file
[  4248.649] (II) fglrx(0): Printing DDC gathered Modelines:
[  4248.649] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4248.649] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4248.649] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4248.649] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[ 14334.616] (II) config/udev: removing device MLK 2.4GHz Wireless Optical Mouse
[ 14334.657] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Close
[ 14334.663] (II) UnloadModule: "evdev"
[ 14334.663] (II) Unloading evdev
[ 14335.338] (II) config/udev: Adding input device MLK 2.4GHz Wireless Optical Mouse (/dev/input/mouse0)
[ 14335.338] (II) No input driver specified, ignoring this device.
[ 14335.338] (II) This device may have been added with another device file.
[ 14335.387] (II) config/udev: Adding input device MLK 2.4GHz Wireless Optical Mouse (/dev/input/event3)
[ 14335.387] (**) MLK 2.4GHz Wireless Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 14335.387] (**) MLK 2.4GHz Wireless Optical Mouse: Applying InputClass "evdev keyboard catchall"
[ 14335.387] (II) Using input driver 'evdev' for 'MLK 2.4GHz Wireless Optical Mouse'
[ 14335.387] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 14335.531] (**) MLK 2.4GHz Wireless Optical Mouse: always reports core events
[ 14335.531] (**) evdev: MLK 2.4GHz Wireless Optical Mouse: Device: "/dev/input/event3"
[ 14335.561] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Vendor 0x4fc Product 0x538
[ 14335.561] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found 9 mouse buttons
[ 14335.561] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found scroll wheel(s)
[ 14335.561] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found relative axes
[ 14335.561] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found x and y relative axes
[ 14335.561] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found absolute axes
[ 14335.561] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Forcing absolute x/y axes to exist.
[ 14335.561] (--) evdev: MLK 2.4GHz Wireless Optical Mouse: Found keys
[ 14335.561] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Configuring as mouse
[ 14335.561] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Configuring as keyboard
[ 14335.561] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: Adding scrollwheel support
[ 14335.561] (**) evdev: MLK 2.4GHz Wireless Optical Mouse: YAxisMapping: buttons 4 and 5
[ 14335.561] (**) evdev: MLK 2.4GHz Wireless Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 14335.562] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input14/event3"
[ 14335.562] (II) XINPUT: Adding extended input device "MLK 2.4GHz Wireless Optical Mouse" (type: KEYBOARD, id 9)
[ 14335.562] (**) Option "xkb_rules" "evdev"
[ 14335.562] (**) Option "xkb_model" "pc105"
[ 14335.562] (**) Option "xkb_layout" "us"
[ 14335.562] (**) Option "xkb_variant" "intl"
[ 14335.562] (II) evdev: MLK 2.4GHz Wireless Optical Mouse: initialized for relative axes.
[ 14335.562] (WW) evdev: MLK 2.4GHz Wireless Optical Mouse: ignoring absolute axes.
[ 14335.562] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) keeping acceleration scheme 1
[ 14335.562] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) acceleration profile 0
[ 14335.562] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) acceleration factor: 2.000
[ 14335.562] (**) MLK 2.4GHz Wireless Optical Mouse: (accel) acceleration threshold: 4
[ 15351.587] (II) fglrx(0): EDID vendor "SNY", prod id 8784
[ 15351.588] (II) fglrx(0): Using hsync ranges from config file
[ 15351.588] (II) fglrx(0): Using vrefresh ranges from config file
[ 15351.588] (II) fglrx(0): Printing DDC gathered Modelines:
[ 15351.588] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 15351.588] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 15351.588] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 15351.588] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
```

---

### Post by Yellow Pasque on 2013-04-10
AMD dropped support for RadeonHD 4xxx series in the proprietary fglrx/Catalyst driver. Your options:
1) Go back to Ubuntu 12.04, where you can still use fglrx/Catalyst legacy release
2) Use open-source driver
3) Use the following PPA to downgrade the X server and allow you to use fglrx/Catalyst legacy with Ubuntu >= 12.10: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

#1 is probably the best option if your primary interest is Steam gaming. #3 is a hackish approach and may cause package management issues in the future, but a lot of folks are using it. Make sure you remove the current fglrx package if you go that route (you need the fglrx-legacy package that the PPA provides).

---

### Post by heWhoWearsAshes on 2013-04-11
I *am *using 12.04. What about #2? Is that not a good option? And where would I get it?

---

### Post by Yellow Pasque on 2013-04-12
Sorry, I misread your log (saw X 1.13 instead of 1.11.3 and assumed you were using Quantal).

IIRC, AMD did fix some Steam OpenGL detection bugs with Catalyst 13-1 Legacy driver. You can install that using the makson96 PPA I linked to in my last post:
```
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
auso apt-get purge fglrx
sudo apt-get install fglrx-legacy
```

---

### Post by heWhoWearsAshes on 2013-04-13
Then I'd enable it with jockey like usual?

---

### Post by heWhoWearsAshes on 2013-04-13
Okay. I've installed the legacy drivers, but I still don't have direct rendering. When the client starts, a dialog box tells me that direct rendering is disabled (just the same way it would before I installed the legacy drivers), but the client actually shows up. So one victory there.

But, when I try to play a game, it tells me "Could not find required OpenGL entry point 'glColorMaskIndexedEXT'! Either your video card is unsupported, or your OpenGL driver needs to be updated."

What does that mean? What should I do?

---

### Post by heWhoWearsAshes on 2013-04-16
Bump

---

