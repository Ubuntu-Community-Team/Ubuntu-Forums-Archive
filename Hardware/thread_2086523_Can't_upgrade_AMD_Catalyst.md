---
title: "Can't upgrade AMD Catalyst"
date: 2012-11-21
forum: Hardware
---

### Post by isecore on 2012-11-21
For whatever reason, my displays flicker A LOT after upgrading to 12.10. So I added the X-Edgers PPA to try to upgrade the AMD proprietery driver. Added it, aptitude installed all the upgraded packages - yet somehow inexplicably I'm still stuck on 11.8 Catalyst even though it claims to have installed 12.8.

The jerky and flickery displays persist as well, giving me nausea and making the experience most unpleasant.

Any ideas how to solve this?

---

### Post by isecore on 2012-11-21
Here's a video I shot with my phone demonstrating the jitters, jerks and glitches.

[http://www.youtube.com/watch?v=oa7dg_EKvP0](http://www.youtube.com/watch?v=oa7dg_EKvP0)

---

### Post by Yellow Pasque on 2012-11-21
Post your /var/log/Xorg.0.log
Often, the AMD/Catlayst Control GUI shows an older version even after you've upgraded.

---

### Post by isecore on 2012-11-22
Here ya go. I browsed through it and could see references to fglrx module being compiled September 2012 or something, but it's really early here so I could be mistaken in my sleepy haze ;)

And also, assuming that it's running the proper 12.8 Catalyst, the tearing and flickering is still extremely annoying.

```
[    26.229] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    26.230] X Protocol Version 11, Revision 0
[    26.230] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    26.230] Current Operating System: Linux dragula 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64
[    26.230] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-19-generic root=/dev/mapper/dragula-root ro quiet splash vt.handoff=7
[    26.230] Build Date: 20 September 2012  11:55:20AM
[    26.230] xorg-server 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz (For technical support please see http://www.ubuntu.com/support) 
[    26.230] Current version of pixman: 0.26.0
[    26.230] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.230] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.230] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 21 21:49:00 2012
[    26.230] (==) Using config file: "/etc/X11/xorg.conf"
[    26.230] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.230] (==) ServerLayout "amdcccle Layout"
[    26.230] (**) |-->Screen "amdcccle-Screen[1]-0" (0)
[    26.230] (**) |   |-->Monitor "<default monitor>"
[    26.230] (**) |   |-->Device "amdcccle-Device[1]-0"
[    26.230] (==) No monitor specified for screen "amdcccle-Screen[1]-0".
	Using a default monitor configuration.
[    26.230] (==) Automatically adding devices
[    26.230] (==) Automatically enabling devices
[    26.230] (==) Automatically adding GPU devices
[    26.230] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.230] 	Entry deleted from font path.
[    26.230] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.230] 	Entry deleted from font path.
[    26.230] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.230] 	Entry deleted from font path.
[    26.230] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.230] 	Entry deleted from font path.
[    26.230] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.230] 	Entry deleted from font path.
[    26.230] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.230] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.230] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.230] (II) Loader magic: 0x7f95ce88fc40
[    26.230] (II) Module ABI versions:
[    26.230] 	X.Org ANSI C Emulation: 0.4
[    26.230] 	X.Org Video Driver: 13.0
[    26.230] 	X.Org XInput driver : 18.0
[    26.230] 	X.Org Server Extension : 7.0
[    26.231] (--) PCI:*(0:1:0:0) 1002:6898:1682:2961 rev 0, Mem @ 0xd0000000/268435456, 0xfdfc0000/131072, I/O @ 0x0000ae00/256, BIOS @ 0x????????/131072
[    26.231] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.231] Initializing built-in extension Generic Event Extension
[    26.231] Initializing built-in extension SHAPE
[    26.231] Initializing built-in extension MIT-SHM
[    26.231] Initializing built-in extension XInputExtension
[    26.231] Initializing built-in extension XTEST
[    26.231] Initializing built-in extension BIG-REQUESTS
[    26.232] Initializing built-in extension SYNC
[    26.232] Initializing built-in extension XKEYBOARD
[    26.232] Initializing built-in extension XC-MISC
[    26.232] Initializing built-in extension SECURITY
[    26.232] Initializing built-in extension XINERAMA
[    26.232] Initializing built-in extension XFIXES
[    26.232] Initializing built-in extension RENDER
[    26.232] Initializing built-in extension RANDR
[    26.232] Initializing built-in extension COMPOSITE
[    26.232] Initializing built-in extension DAMAGE
[    26.232] Initializing built-in extension MIT-SCREEN-SAVER
[    26.232] Initializing built-in extension DOUBLE-BUFFER
[    26.232] Initializing built-in extension RECORD
[    26.232] Initializing built-in extension DPMS
[    26.232] Initializing built-in extension X-Resource
[    26.232] Initializing built-in extension XVideo
[    26.232] Initializing built-in extension XVideo-MotionCompensation
[    26.232] Initializing built-in extension XFree86-VidModeExtension
[    26.232] Initializing built-in extension XFree86-DGA
[    26.232] Initializing built-in extension XFree86-DRI
[    26.232] Initializing built-in extension DRI2
[    26.232] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    26.232] (II) LoadModule: "glx"
[    26.232] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    26.232] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    26.232] 	compiled for 6.9.0, module version = 1.0.0
[    26.232] Loading extension GLX
[    26.232] (II) LoadModule: "fglrx"
[    26.267] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    26.277] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    26.277] 	compiled for 1.4.99.906, module version = 9.0.2
[    26.277] 	Module class: X.Org Video Driver
[    26.278] (II) Loading sub module "fglrxdrm"
[    26.278] (II) LoadModule: "fglrxdrm"
[    26.278] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    26.278] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    26.278] 	compiled for 1.4.99.906, module version = 9.0.2
[    26.278] (II) AMD Proprietary Linux Driver Version Identifier:9.00.2
[    26.278] (II) AMD Proprietary Linux Driver Release Identifier: 9.00.11                              
[    26.278] (II) AMD Proprietary Linux Driver Build Date: Sep 20 2012 11:56:16
[    26.278] (++) using VT number 7

[    26.278] (WW) Falling back to old probe method for fglrx
[    26.283] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    26.295] ukiDynamicMajor: found major device number 249
[    26.295] ukiDynamicMajor: found major device number 249
[    26.295] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    26.295] ukiOpenDevice: node name is /dev/ati/card0
[    26.295] ukiOpenDevice: open result is 10, (OK)
[    26.443] ukiOpenByBusid: ukiOpenMinor returns 10
[    26.443] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    26.472] (--) Chipset Supported AMD Graphics Processor (0x6898) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:5:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:7:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:9:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    26.473] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    26.473] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    26.473] (II) AMD Video driver is signed
[    26.473] (II) fglrx(0): pEnt->device->identifier=0x7f95cedc0d70
[    26.473] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[    26.473] (II) Loading sub module "vgahw"
[    26.473] (II) LoadModule: "vgahw"
[    26.555] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    26.555] (II) Module vgahw: vendor="X.Org Foundation"
[    26.555] 	compiled for 1.13.0, module version = 0.1.0
[    26.555] 	ABI class: X.Org Video Driver, version 13.0
[    26.555] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    26.555] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    26.555] (==) fglrx(0): Default visual is TrueColor
[    26.555] (==) fglrx(0): RGB weight 888
[    26.555] (II) fglrx(0): Using 8 bits per RGB 
[    26.555] (==) fglrx(0): Buffer Tiling is ON
[    26.555] (II) Loading sub module "fglrxdrm"
[    26.555] (II) LoadModule: "fglrxdrm"
[    26.555] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    26.555] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    26.555] 	compiled for 1.4.99.906, module version = 9.0.2
[    26.566] ukiDynamicMajor: found major device number 249
[    26.566] ukiDynamicMajor: found major device number 249
[    26.566] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    26.566] ukiOpenDevice: node name is /dev/ati/card0
[    26.566] ukiOpenDevice: open result is 13, (OK)
[    26.566] ukiOpenByBusid: ukiOpenMinor returns 13
[    26.566] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    26.566] (**) fglrx(0): NoAccel = NO
[    26.566] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    26.566] (--) fglrx(0): Chipset: "ATI Radeon HD 5800 Series" (Chipset = 0x6898)
[    26.566] (--) fglrx(0): (PciSubVendor = 0x1682, PciSubDevice = 0x2961)
[    26.566] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    26.566] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    26.566] (--) fglrx(0): MMIO registers at 0xfdfc0000
[    26.566] (--) fglrx(0): I/O port at 0x0000ae00
[    26.566] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    26.572] (II) fglrx(0): AC Adapter is used
[    26.575] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    26.575] (II) Loading sub module "vbe"
[    26.575] (II) LoadModule: "vbe"
[    26.575] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    26.575] (II) Module vbe: vendor="X.Org Foundation"
[    26.575] 	compiled for 1.13.0, module version = 1.1.0
[    26.575] 	ABI class: X.Org Video Driver, version 13.0
[    26.575] (II) fglrx(0): VESA BIOS detected
[    26.575] (II) fglrx(0): VESA VBE Version 3.0
[    26.575] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    26.575] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    26.575] (II) fglrx(0): VESA VBE OEM Software Rev: 12.19
[    26.575] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    26.575] (II) fglrx(0): VESA VBE OEM Product: CYPRESS
[    26.575] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    26.575] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    26.575] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    26.575] (II) fglrx(0): PCIE card detected
[    26.575] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    26.575] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    26.575] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    26.575] (II) fglrx(0): RandR 1.2 support is enabled!
[    26.575] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    26.576] (==) fglrx(0): Center Mode is disabled 
[    26.576] (II) Loading sub module "fb"
[    26.576] (II) LoadModule: "fb"
[    26.576] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.576] (II) Module fb: vendor="X.Org Foundation"
[    26.576] 	compiled for 1.13.0, module version = 1.0.0
[    26.576] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.576] (II) Loading sub module "ddc"
[    26.576] (II) LoadModule: "ddc"
[    26.576] (II) Module "ddc" already built-in
[    26.778] (II) fglrx(0): Output DFP1 has no monitor section
[    26.778] (II) fglrx(0): Output DFP2 using monitor section 0-DFP2
[    26.778] (**) fglrx(0): Option "PreferredMode" "1920x1080"
[    26.778] (**) fglrx(0): Option "Position" "0 0"
[    26.778] (**) fglrx(0): Option "Disable" "false"
[    26.778] (**) fglrx(0): Option "Rotate" "normal"
[    26.778] (**) fglrx(0): Option "TargetRefresh" "60"
[    26.778] (II) fglrx(0): Output DFP3 has no monitor section
[    26.778] (II) fglrx(0): Output DFP4 using monitor section 0-DFP4
[    26.778] (**) fglrx(0): Option "PreferredMode" "1680x1050"
[    26.778] (**) fglrx(0): Option "Position" "1920 0"
[    26.778] (**) fglrx(0): Option "Disable" "false"
[    26.778] (**) fglrx(0): Option "Rotate" "normal"
[    26.778] (**) fglrx(0): Option "TargetRefresh" "60"
[    26.778] (II) fglrx(0): Output CRT1 has no monitor section
[    26.778] (II) fglrx(0): Output CRT2 has no monitor section
[    26.778] (II) Loading sub module "ddc"
[    26.778] (II) LoadModule: "ddc"
[    26.778] (II) Module "ddc" already built-in
[    26.778] (II) fglrx(0): Connected Display0: DFP2
[    26.778] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    26.778] (II) fglrx(0): Connected Display1: DFP4
[    26.778] (II) fglrx(0):  Display1: Failed to get EDID information. 
[    26.779] (II) fglrx(0): EDID for output DFP1
[    26.779] (II) fglrx(0): EDID for output DFP2
[    26.779] (II) fglrx(0): Manufacturer: SAM  Model: 7d6  Serial#: 808465465
[    26.779] (II) fglrx(0): Year: 2011  Week: 31
[    26.779] (II) fglrx(0): EDID Version: 1.3
[    26.779] (II) fglrx(0): Digital Display Input
[    26.779] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    26.779] (II) fglrx(0): Gamma: 2.20
[    26.779] (II) fglrx(0): DPMS capabilities: Off
[    26.779] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.779] (II) fglrx(0): First detailed timing is preferred mode
[    26.779] (II) fglrx(0): redX: 0.631 redY: 0.351   greenX: 0.334 greenY: 0.615
[    26.779] (II) fglrx(0): blueX: 0.157 blueY: 0.051   whiteX: 0.312 whiteY: 0.329
[    26.779] (II) fglrx(0): Supported established timings:
[    26.779] (II) fglrx(0): 720x400@70Hz
[    26.779] (II) fglrx(0): 640x480@60Hz
[    26.780] (II) fglrx(0): 640x480@67Hz
[    26.780] (II) fglrx(0): 640x480@72Hz
[    26.780] (II) fglrx(0): 640x480@75Hz
[    26.780] (II) fglrx(0): 800x600@56Hz
[    26.780] (II) fglrx(0): 800x600@60Hz
[    26.780] (II) fglrx(0): 800x600@72Hz
[    26.780] (II) fglrx(0): 800x600@75Hz
[    26.780] (II) fglrx(0): 832x624@75Hz
[    26.780] (II) fglrx(0): 1024x768@60Hz
[    26.780] (II) fglrx(0): 1024x768@70Hz
[    26.780] (II) fglrx(0): 1024x768@75Hz
[    26.780] (II) fglrx(0): 1280x1024@75Hz
[    26.780] (II) fglrx(0): 1152x864@75Hz
[    26.780] (II) fglrx(0): Manufacturer's mask: 0
[    26.780] (II) fglrx(0): Supported standard timings:
[    26.780] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    26.780] (II) fglrx(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    26.780] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    26.780] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    26.780] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    26.780] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    26.780] (II) fglrx(0): #6: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    26.780] (II) fglrx(0): #7: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    26.780] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    26.780] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    26.780] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    26.780] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    26.780] (II) fglrx(0): Ranges: V min: 50 V max: 75 Hz, H min: 31 H max: 81 kHz, PixClock max 175 MHz
[    26.780] (II) fglrx(0): Monitor name: SMS24A350H
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    26.780] (II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    26.780] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    26.780] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    26.780] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 74.2 MHz   Image Size:  531 x 299 mm
[    26.780] (II) fglrx(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    26.780] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    26.780] (II) fglrx(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    26.780] (II) fglrx(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 27.0 MHz   Image Size:  531 x 299 mm
[    26.780] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    26.780] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    26.780] (II) fglrx(0): Number of EDID sections to follow: 1
[    26.780] (II) fglrx(0): EDID (in hex):
[    26.780] (II) fglrx(0): 	00ffffffffffff004c2dd60739343030
[    26.780] (II) fglrx(0): 	1f15010380351e782aba41a159559d28
[    26.780] (II) fglrx(0): 	0d5054bfef80714f8100814081809500
[    26.780] (II) fglrx(0): 	950fa940b300023a801871382d40582c
[    26.780] (II) fglrx(0): 	4500132b2100001e011d007251d01e20
[    26.780] (II) fglrx(0): 	6e285500132b2100001e000000fd0032
[    26.780] (II) fglrx(0): 	4b1f5111000a202020202020000000fc
[    26.780] (II) fglrx(0): 	00534d53323441333530480a20200163
[    26.780] (II) fglrx(0): Printing probed modes for output DFP2
[    26.780] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz UeP)
[    26.780] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    26.780] (II) fglrx(0): Modeline "1920x1080"x60.0   74.25  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.8 kHz e)
[    26.780] (II) fglrx(0): Modeline "1920x1080"x50.0   74.25  1920 2448 2492 2640  1080 1085 1095 1125 interlace +hsync +vsync (28.1 kHz e)
[    26.780] (II) fglrx(0): Modeline "1920x1080"x59.9   74.18  1920 2008 2052 2200  1080 1085 1095 1125 interlace +hsync +vsync (33.7 kHz e)
[    26.780] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    26.780] (II) fglrx(0): Modeline "1776x1000"x59.9  148.35  1776 1864 1908 2200  1000 1004 1009 1125 +hsync +vsync (67.4 kHz ez)
[    26.780] (II) fglrx(0): Modeline "1776x1000"x50.0   74.25  1776 2304 2348 2640  1000 1005 1015 1125 interlace +hsync +vsync (28.1 kHz ez)
[    26.780] (II) fglrx(0): Modeline "1776x1000"x59.9   74.18  1776 1864 1908 2200  1000 1005 1015 1125 interlace +hsync +vsync (33.7 kHz ez)
[    26.780] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    26.780] (II) fglrx(0): Modeline "1400x1050"x60.0  162.00  1400 1664 1856 2160  1050 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1600x900"x60.0  162.00  1600 1664 1856 2160  900 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1360x1024"x60.0  162.00  1360 1664 1856 2160  1024 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    26.780] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x800"x50.0  148.50  1280 2448 2492 2640  800 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    26.780] (II) fglrx(0): Modeline "1152x864"x50.0  148.50  1152 2448 2492 2640  864 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1152x864"x59.9  148.35  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    26.780] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    26.780] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    26.780] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    26.780] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    26.780] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    26.780] (II) fglrx(0): Modeline "1152x648"x59.9   74.18  1152 1262 1302 1650  648 653 658 750 +hsync +vsync (45.0 kHz ez)
[    26.780] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    26.780] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    26.780] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    26.780] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "720x576"x59.9  148.35  720 2008 2052 2200  576 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    26.780] (II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    26.780] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    26.780] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.780] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    26.780] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz e)
[    26.780] (II) fglrx(0): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz e)
[    26.780] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    26.780] (II) fglrx(0): EDID for output DFP3
[    26.780] (II) fglrx(0): EDID for output DFP4
[    26.780] (II) fglrx(0): Manufacturer: SAM  Model: 27f  Serial#: 1296380466
[    26.780] (II) fglrx(0): Year: 2008  Week: 22
[    26.780] (II) fglrx(0): EDID Version: 1.3
[    26.780] (II) fglrx(0): Digital Display Input
[    26.780] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    26.780] (II) fglrx(0): Gamma: 2.20
[    26.780] (II) fglrx(0): DPMS capabilities: Off
[    26.780] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.780] (II) fglrx(0): First detailed timing is preferred mode
[    26.780] (II) fglrx(0): redX: 0.644 redY: 0.333   greenX: 0.286 greenY: 0.603
[    26.780] (II) fglrx(0): blueX: 0.152 blueY: 0.079   whiteX: 0.313 whiteY: 0.329
[    26.780] (II) fglrx(0): Supported established timings:
[    26.780] (II) fglrx(0): 720x400@70Hz
[    26.780] (II) fglrx(0): 640x480@60Hz
[    26.780] (II) fglrx(0): 640x480@67Hz
[    26.780] (II) fglrx(0): 640x480@72Hz
[    26.780] (II) fglrx(0): 640x480@75Hz
[    26.780] (II) fglrx(0): 800x600@56Hz
[    26.780] (II) fglrx(0): 800x600@60Hz
[    26.780] (II) fglrx(0): 800x600@72Hz
[    26.780] (II) fglrx(0): 800x600@75Hz
[    26.780] (II) fglrx(0): 832x624@75Hz
[    26.780] (II) fglrx(0): 1024x768@60Hz
[    26.780] (II) fglrx(0): 1024x768@70Hz
[    26.780] (II) fglrx(0): 1024x768@75Hz
[    26.780] (II) fglrx(0): 1280x1024@75Hz
[    26.780] (II) fglrx(0): 1152x864@75Hz
[    26.780] (II) fglrx(0): Manufacturer's mask: 0
[    26.780] (II) fglrx(0): Supported standard timings:
[    26.780] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    26.780] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    26.780] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    26.780] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    26.780] (II) fglrx(0): Supported detailed timing:
[    26.780] (II) fglrx(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
[    26.780] (II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    26.781] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    26.781] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    26.781] (II) fglrx(0): Monitor name: SyncMaster
[    26.781] (II) fglrx(0): Serial No: H9XQ530291
[    26.781] (II) fglrx(0): EDID (in hex):
[    26.781] (II) fglrx(0): 	00ffffffffffff004c2d7f023232454d
[    26.781] (II) fglrx(0): 	16120103802f1e782ad515a455499a27
[    26.781] (II) fglrx(0): 	145054bfef80b30081808140714f0101
[    26.781] (II) fglrx(0): 	0101010101017c2e90a0601a1e403020
[    26.781] (II) fglrx(0): 	3600da281100001a000000fd00384b1e
[    26.781] (II) fglrx(0): 	510e000a202020202020000000fc0053
[    26.781] (II) fglrx(0): 	796e634d61737465720a2020000000ff
[    26.781] (II) fglrx(0): 	00483958513533303239310a20200049
[    26.781] (II) fglrx(0): Printing probed modes for output DFP4
[    26.781] (II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz UeP)
[    26.781] (II) fglrx(0): Modeline "1400x1050"x60.0  119.00  1400 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    26.781] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1728 1760 1840  900 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    26.781] (II) fglrx(0): Modeline "1360x1024"x60.0  119.00  1360 1728 1760 1840  1024 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    26.781] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    26.781] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    26.781] (II) fglrx(0): Modeline "1440x900"x60.0  119.00  1440 1728 1760 1840  900 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    26.781] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    26.781] (II) fglrx(0): Modeline "1280x800"x60.0  108.00  1280 1376 1488 1800  800 961 964 1000 +hsync +vsync (60.0 kHz e)
[    26.781] (II) fglrx(0): Modeline "1152x864"x60.0  119.00  1152 1728 1760 1840  864 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    26.781] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    26.781] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1376 1488 1800  768 961 964 1000 +hsync +vsync (60.0 kHz e)
[    26.781] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1376 1488 1800  720 961 964 1000 +hsync +vsync (60.0 kHz e)
[    26.781] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    26.781] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    26.781] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    26.781] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    26.781] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    26.781] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    26.781] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    26.781] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    26.781] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz e)
[    26.781] (II) fglrx(0): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz e)
[    26.781] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    26.781] (II) fglrx(0): EDID for output CRT1
[    26.781] (II) fglrx(0): EDID for output CRT2
[    26.781] (II) fglrx(0): Output DFP1 disconnected
[    26.781] (II) fglrx(0): Output DFP2 connected
[    26.781] (II) fglrx(0): Output DFP3 disconnected
[    26.781] (II) fglrx(0): Output DFP4 connected
[    26.781] (II) fglrx(0): Output CRT1 disconnected
[    26.781] (II) fglrx(0): Output CRT2 disconnected
[    26.781] (II) fglrx(0): Using user preference for initial modes
[    26.781] (II) fglrx(0): Output DFP2 using initial mode 1920x1080
[    26.781] (II) fglrx(0): Output DFP4 using initial mode 1680x1050
[    26.781] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.781] (II) fglrx(0): DPI set to (96, 96)
[    26.781] (II) fglrx(0): Eyefinity capable adapter detected.
[    26.781] (II) fglrx(0): Adapter ATI Radeon HD 5800 Series has 6 configurable heads and 2 displays connected.
[    26.781] (==) fglrx(0):  PseudoColor visuals disabled
[    26.781] (II) Loading sub module "ramdac"
[    26.781] (II) LoadModule: "ramdac"
[    26.781] (II) Module "ramdac" already built-in
[    26.781] (==) fglrx(0): NoDRI = NO
[    26.781] (==) fglrx(0): Capabilities: 0x00000000
[    26.781] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    26.781] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    26.781] (==) fglrx(0): UseFastTLS=0
[    26.781] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    26.781] (--) Depth 24 pixmap format is 32 bpp
[    26.785] Loading extension ATIFGLRXDRI
[    26.785] (II) fglrx(0): doing swlDriScreenInit
[    26.785] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    26.785] ukiDynamicMajor: found major device number 249
[    26.785] ukiDynamicMajor: found major device number 249
[    26.785] ukiDynamicMajor: found major device number 249
[    26.785] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    26.785] ukiOpenDevice: node name is /dev/ati/card0
[    26.786] ukiOpenDevice: open result is 14, (OK)
[    26.786] ukiOpenByBusid: ukiOpenMinor returns 14
[    26.786] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    26.786] (II) fglrx(0): [uki] DRM interface version 1.0
[    26.786] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    26.786] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    26.786] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f95ce458000
[    26.786] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    26.786] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    26.786] (II) fglrx(0): swlDriScreenInit done
[    26.786] (II) fglrx(0): Kernel Module Version Information:
[    26.786] (II) fglrx(0):     Name: fglrx
[    26.786] (II) fglrx(0):     Version: 9.0.2
[    26.786] (II) fglrx(0):     Date: Sep 20 2012
[    26.786] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    26.786] (II) fglrx(0): Kernel Module version matches driver.
[    26.786] (II) fglrx(0): Kernel Module Build Time Information:
[    26.786] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.5.0-19-generic
[    26.786] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    26.786] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    26.786] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    26.786] (II) fglrx(0): [uki] register handle = 0x00004000
[    26.787] (II) fglrx(0): DRI initialization successfull
[    26.787] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01ab8000
[    26.787] (==) fglrx(0): Backing store disabled
[    26.787] Loading extension FGLRXEXTENSION
[    26.787] (==) fglrx(0): DPMS enabled
[    26.787] (II) fglrx(0): Initialized in-driver Xinerama extension
[    26.787] (**) fglrx(0): Textured Video is enabled.
[    26.787] (II) LoadModule: "glesx"
[    26.787] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    26.788] (II) Module glesx: vendor="X.Org Foundation"
[    26.788] 	compiled for 1.4.99.906, module version = 1.0.0
[    26.788] Loading extension GLESX
[    26.788] (II) fglrx(0): GLESX enableFlags = 592
[    26.788] (II) fglrx(0): GLESX is enabled
[    26.788] (II) LoadModule: "amdxmm"
[    26.788] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    26.788] (II) Module amdxmm: vendor="X.Org Foundation"
[    26.788] 	compiled for 1.4.99.906, module version = 2.0.0
[    26.811] Loading extension AMDXVOPL
[    26.811] Loading extension AMDXVBA
[    26.812] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    26.814] (II) fglrx(0): Enable composite support successfully
[    26.814] (II) fglrx(0): X context handle = 0x1
[    26.814] (II) fglrx(0): [DRI] installation complete
[    26.814] (==) fglrx(0): Silken mouse enabled
[    26.814] (==) fglrx(0): Using HW cursor of display infrastructure!
[    26.815] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.826] (II) fglrx(0): User Preference Output DFP2 using refresh rate 60.0 Hz.
[    26.878] (II) fglrx(0): User Preference Output DFP4 using refresh rate 60.0 Hz.
[    26.902] (--) RandR disabled
[    26.907] ukiDynamicMajor: found major device number 249
[    26.907] ukiDynamicMajor: found major device number 249
[    26.907] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    26.907] ukiOpenDevice: node name is /dev/ati/card0
[    26.907] ukiOpenDevice: open result is 15, (OK)
[    26.907] ukiOpenByBusid: ukiOpenMinor returns 15
[    26.907] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    26.977] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    27.004] (II) fglrx(0): Setting screen physical size to 952 x 285
[    27.012] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.014] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.014] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.014] (II) LoadModule: "evdev"
[    27.014] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.014] (II) Module evdev: vendor="X.Org Foundation"
[    27.014] 	compiled for 1.13.0, module version = 2.7.3
[    27.014] 	Module class: X.Org XInput Driver
[    27.014] 	ABI class: X.Org XInput driver, version 18.0
[    27.014] (II) Using input driver 'evdev' for 'Power Button'
[    27.014] (**) Power Button: always reports core events
[    27.014] (**) evdev: Power Button: Device: "/dev/input/event1"
[    27.014] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.014] (--) evdev: Power Button: Found keys
[    27.014] (II) evdev: Power Button: Configuring as keyboard
[    27.014] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    27.014] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.014] (**) Option "xkb_rules" "evdev"
[    27.014] (**) Option "xkb_model" "pc105"
[    27.014] (**) Option "xkb_layout" "se"
[    27.015] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    27.016] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.016] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.016] (II) Using input driver 'evdev' for 'Power Button'
[    27.016] (**) Power Button: always reports core events
[    27.016] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.016] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.016] (--) evdev: Power Button: Found keys
[    27.016] (II) evdev: Power Button: Configuring as keyboard
[    27.016] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    27.016] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    27.016] (**) Option "xkb_rules" "evdev"
[    27.016] (**) Option "xkb_model" "pc105"
[    27.016] (**) Option "xkb_layout" "se"
[    27.016] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event15)
[    27.016] (II) No input driver specified, ignoring this device.
[    27.016] (II) This device may have been added with another device file.
[    27.016] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event2)
[    27.017] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[    27.017] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[    27.017] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[    27.017] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event2"
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[    27.017] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[    27.017] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2/event2"
[    27.017] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 8)
[    27.017] (**) Option "xkb_rules" "evdev"
[    27.017] (**) Option "xkb_model" "pc105"
[    27.017] (**) Option "xkb_layout" "se"
[    27.017] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event3)
[    27.017] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[    27.017] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[    27.017] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[    27.017] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event3"
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Found 1 mouse buttons
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Found scroll wheel(s)
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Found relative axes
[    27.017] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing relative x/y axes to exist.
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Found absolute axes
[    27.017] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing absolute x/y axes to exist.
[    27.017] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[    27.017] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as mouse
[    27.017] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[    27.017] (II) evdev: Logitech Logitech Illuminated Keyboard: Adding scrollwheel support
[    27.017] (**) evdev: Logitech Logitech Illuminated Keyboard: YAxisMapping: buttons 4 and 5
[    27.017] (**) evdev: Logitech Logitech Illuminated Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.017] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3/event3"
[    27.017] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 9)
[    27.017] (**) Option "xkb_rules" "evdev"
[    27.017] (**) Option "xkb_model" "pc105"
[    27.017] (**) Option "xkb_layout" "se"
[    27.017] (II) evdev: Logitech Logitech Illuminated Keyboard: initialized for relative axes.
[    27.017] (WW) evdev: Logitech Logitech Illuminated Keyboard: ignoring absolute axes.
[    27.017] (**) Logitech Logitech Illuminated Keyboard: (accel) keeping acceleration scheme 1
[    27.017] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration profile 0
[    27.018] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration factor: 2.000
[    27.018] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration threshold: 4
[    27.018] (II) config/udev: Adding input device Logitech G500 (/dev/input/event4)
[    27.018] (**) Logitech G500: Applying InputClass "evdev pointer catchall"
[    27.018] (II) Using input driver 'evdev' for 'Logitech G500'
[    27.018] (**) Logitech G500: always reports core events
[    27.018] (**) evdev: Logitech G500: Device: "/dev/input/event4"
[    27.018] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[    27.018] (--) evdev: Logitech G500: Found 20 mouse buttons
[    27.018] (--) evdev: Logitech G500: Found scroll wheel(s)
[    27.018] (--) evdev: Logitech G500: Found relative axes
[    27.018] (--) evdev: Logitech G500: Found x and y relative axes
[    27.018] (II) evdev: Logitech G500: Configuring as mouse
[    27.018] (II) evdev: Logitech G500: Adding scrollwheel support
[    27.018] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[    27.018] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.018] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input7/event4"
[    27.018] (II) XINPUT: Adding extended input device "Logitech G500" (type: MOUSE, id 10)
[    27.018] (II) evdev: Logitech G500: initialized for relative axes.
[    27.018] (**) Logitech G500: (accel) keeping acceleration scheme 1
[    27.018] (**) Logitech G500: (accel) acceleration profile 0
[    27.018] (**) Logitech G500: (accel) acceleration factor: 2.000
[    27.018] (**) Logitech G500: (accel) acceleration threshold: 4
[    27.018] (II) config/udev: Adding input device Logitech G500 (/dev/input/mouse0)
[    27.018] (II) No input driver specified, ignoring this device.
[    27.018] (II) This device may have been added with another device file.
[    27.018] (II) config/udev: Adding input device Logitech G500 (/dev/input/event5)
[    27.018] (**) Logitech G500: Applying InputClass "evdev keyboard catchall"
[    27.018] (II) Using input driver 'evdev' for 'Logitech G500'
[    27.018] (**) Logitech G500: always reports core events
[    27.018] (**) evdev: Logitech G500: Device: "/dev/input/event5"
[    27.018] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[    27.018] (--) evdev: Logitech G500: Found 1 mouse buttons
[    27.018] (--) evdev: Logitech G500: Found scroll wheel(s)
[    27.018] (--) evdev: Logitech G500: Found relative axes
[    27.018] (II) evdev: Logitech G500: Forcing relative x/y axes to exist.
[    27.018] (--) evdev: Logitech G500: Found absolute axes
[    27.018] (II) evdev: Logitech G500: Forcing absolute x/y axes to exist.
[    27.018] (--) evdev: Logitech G500: Found keys
[    27.019] (II) evdev: Logitech G500: Configuring as mouse
[    27.019] (II) evdev: Logitech G500: Configuring as keyboard
[    27.019] (II) evdev: Logitech G500: Adding scrollwheel support
[    27.019] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[    27.019] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.019] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input8/event5"
[    27.019] (II) XINPUT: Adding extended input device "Logitech G500" (type: KEYBOARD, id 11)
[    27.019] (**) Option "xkb_rules" "evdev"
[    27.019] (**) Option "xkb_model" "pc105"
[    27.019] (**) Option "xkb_layout" "se"
[    27.019] (II) evdev: Logitech G500: initialized for relative axes.
[    27.019] (WW) evdev: Logitech G500: ignoring absolute axes.
[    27.019] (**) Logitech G500: (accel) keeping acceleration scheme 1
[    27.019] (**) Logitech G500: (accel) acceleration profile 0
[    27.019] (**) Logitech G500: (accel) acceleration factor: 2.000
[    27.019] (**) Logitech G500: (accel) acceleration threshold: 4
[    27.019] (II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/event6)
[    27.019] (II) No input driver specified, ignoring this device.
[    27.019] (II) This device may have been added with another device file.
[    27.019] (II) config/udev: Adding input device Logitech Logitech Dual Action (/dev/input/js0)
[    27.019] (II) No input driver specified, ignoring this device.
[    27.019] (II) This device may have been added with another device file.
[    27.019] (II) config/udev: Adding input device UVC Camera (046d:0825) (/dev/input/event16)
[    27.019] (**) UVC Camera (046d:0825): Applying InputClass "evdev keyboard catchall"
[    27.019] (II) Using input driver 'evdev' for 'UVC Camera (046d:0825)'
[    27.019] (**) UVC Camera (046d:0825): always reports core events
[    27.019] (**) evdev: UVC Camera (046d:0825): Device: "/dev/input/event16"
[    27.019] (--) evdev: UVC Camera (046d:0825): Vendor 0x46d Product 0x825
[    27.019] (--) evdev: UVC Camera (046d:0825): Found keys
[    27.019] (II) evdev: UVC Camera (046d:0825): Configuring as keyboard
[    27.019] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input18/event16"
[    27.019] (II) XINPUT: Adding extended input device "UVC Camera (046d:0825)" (type: KEYBOARD, id 12)
[    27.019] (**) Option "xkb_rules" "evdev"
[    27.019] (**) Option "xkb_model" "pc105"
[    27.020] (**) Option "xkb_layout" "se"
[    27.020] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event8)
[    27.020] (II) No input driver specified, ignoring this device.
[    27.020] (II) This device may have been added with another device file.
[    27.020] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event9)
[    27.020] (II) No input driver specified, ignoring this device.
[    27.020] (II) This device may have been added with another device file.
[    27.020] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event10)
[    27.020] (II) No input driver specified, ignoring this device.
[    27.020] (II) This device may have been added with another device file.
[    27.020] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event11)
[    27.020] (II) No input driver specified, ignoring this device.
[    27.020] (II) This device may have been added with another device file.
[    27.020] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event12)
[    27.020] (II) No input driver specified, ignoring this device.
[    27.020] (II) This device may have been added with another device file.
[    27.021] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event13)
[    27.021] (II) No input driver specified, ignoring this device.
[    27.021] (II) This device may have been added with another device file.
[    27.021] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event14)
[    27.021] (II) No input driver specified, ignoring this device.
[    27.021] (II) This device may have been added with another device file.
[    27.021] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[    27.021] (II) No input driver specified, ignoring this device.
[    27.021] (II) This device may have been added with another device file.
[    27.024] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    27.627] (II) fglrx(0): EDID vendor "SAM", prod id 639
[    27.627] (II) fglrx(0): Using EDID range info for horizontal sync
[    27.627] (II) fglrx(0): Using EDID range info for vertical refresh
[    27.627] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.627] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    27.627] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    27.627] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    27.627] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    27.627] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    27.627] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    27.627] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    27.627] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    27.627] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    27.627] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    27.627] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    27.627] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    27.627] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    27.627] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    27.627] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    27.627] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    27.627] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    27.627] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    28.708] (II) fglrx(0): EDID vendor "SAM", prod id 639
[    28.708] (II) fglrx(0): Using hsync ranges from config file
[    28.708] (II) fglrx(0): Using vrefresh ranges from config file
[    28.708] (II) fglrx(0): Printing DDC gathered Modelines:
[    28.708] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    28.708] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    28.708] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    28.708] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    28.708] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    28.708] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    28.708] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    28.708] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    28.708] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    28.708] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    28.708] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    28.708] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    28.708] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    28.708] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    28.708] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    28.708] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    28.708] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    28.708] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    46.883] (II) fglrx(0): EDID vendor "SAM", prod id 639
[    46.883] (II) fglrx(0): Using hsync ranges from config file
[    46.883] (II) fglrx(0): Using vrefresh ranges from config file
[    46.883] (II) fglrx(0): Printing DDC gathered Modelines:
[    46.883] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    46.883] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    46.883] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    46.883] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    46.883] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    46.883] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    46.883] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    46.883] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    46.883] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    46.883] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    46.883] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    46.883] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    46.883] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    46.883] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    46.883] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    46.883] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    46.883] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    46.883] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    47.166] (II) fglrx(0): EDID vendor "SAM", prod id 639
[    47.166] (II) fglrx(0): Using hsync ranges from config file
[    47.166] (II) fglrx(0): Using vrefresh ranges from config file
[    47.166] (II) fglrx(0): Printing DDC gathered Modelines:
[    47.166] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    47.166] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    47.166] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    47.166] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    47.166] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    47.166] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    47.166] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    47.166] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    47.166] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    47.166] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    47.166] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    47.166] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    47.166] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    47.166] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    47.166] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    47.166] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    47.166] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    47.166] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    48.061] (II) fglrx(0): EDID vendor "SAM", prod id 639
[    48.061] (II) fglrx(0): Using hsync ranges from config file
[    48.061] (II) fglrx(0): Using vrefresh ranges from config file
[    48.061] (II) fglrx(0): Printing DDC gathered Modelines:
[    48.061] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    48.061] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    48.061] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    48.061] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    48.061] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    48.061] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    48.061] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    48.061] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    48.061] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    48.061] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    48.061] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    48.061] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    48.061] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    48.061] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    48.061] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    48.061] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    48.061] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    48.061] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    48.353] (II) fglrx(0): EDID vendor "SAM", prod id 639
[    48.353] (II) fglrx(0): Using hsync ranges from config file
[    48.353] (II) fglrx(0): Using vrefresh ranges from config file
[    48.353] (II) fglrx(0): Printing DDC gathered Modelines:
[    48.353] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    48.353] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    48.353] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    48.353] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    48.353] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    48.353] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    48.353] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    48.353] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    48.353] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    48.353] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    48.353] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    48.353] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    48.353] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    48.353] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    48.353] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    48.353] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    48.353] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    48.353] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    65.933] (II) XKB: reuse xkmfile /var/lib/xkb/server-D88F7755FC03D159A7C2D06D644EF4934F12C75C.xkm
[   929.205] (II) XKB: reuse xkmfile /var/lib/xkb/server-D88F7755FC03D159A7C2D06D644EF4934F12C75C.xkm
[  1277.439] (II) fglrx(0): EDID vendor "SAM", prod id 639
[  1277.439] (II) fglrx(0): Using hsync ranges from config file
[  1277.439] (II) fglrx(0): Using vrefresh ranges from config file
[  1277.439] (II) fglrx(0): Printing DDC gathered Modelines:
[  1277.439] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[  1277.439] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1277.439] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1277.439] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1277.439] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1277.439] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1277.439] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1277.439] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1277.439] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1277.439] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1277.439] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1277.439] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1277.439] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1277.439] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1277.439] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1277.439] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1277.439] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1277.439] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  5924.779] (II) fglrx(0): EDID vendor "SAM", prod id 639
[  5924.779] (II) fglrx(0): Using hsync ranges from config file
[  5924.779] (II) fglrx(0): Using vrefresh ranges from config file
[  5924.779] (II) fglrx(0): Printing DDC gathered Modelines:
[  5924.779] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[  5924.779] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  5924.779] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  5924.779] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  5924.779] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  5924.779] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  5924.779] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  5924.779] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  5924.779] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  5924.779] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  5924.779] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  5924.779] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  5924.779] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  5924.780] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  5924.780] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  5924.780] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  5924.780] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  5924.780] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 39096.687] (II) fglrx(0): EDID vendor "SAM", prod id 639
[ 39096.687] (II) fglrx(0): Using hsync ranges from config file
[ 39096.687] (II) fglrx(0): Using vrefresh ranges from config file
[ 39096.687] (II) fglrx(0): Printing DDC gathered Modelines:
[ 39096.687] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[ 39096.687] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 39096.687] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)

```

---

