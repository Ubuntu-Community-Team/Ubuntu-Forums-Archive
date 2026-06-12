---
title: "Asus X53B - can't install v 12.6 proprietary drivers"
date: 2012-08-12
forum: Hardware
---

### Post by azurehoney on 2012-08-12
[I have already submitted a bug report to amd, but it hasn't been helpful]("http://ati.cchtml.com/show_bug.cgi?id=498")

So I thought I would ask here. Maybe someone can suggest something, like kernel boot options or other similar tweaks.

Xorg.0.log
```
[    22.844] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    22.844] X Protocol Version 11, Revision 0
[    22.844] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    22.844] Current Operating System: Linux kohvi 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64
[    22.844] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=67e7ede7-6f34-4897-bb1e-8f293f57ddbd ro quiet splash vt.handoff=7
[    22.844] Build Date: 16 July 2012  08:06:31PM
[    22.844] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see http://www.ubuntu.com/support) 
[    22.844] Current version of pixman: 0.24.4
[    22.844] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.844] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.844] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 12 13:26:53 2012
[    22.864] (==) Using config file: "/etc/X11/xorg.conf"
[    22.864] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.908] (==) ServerLayout "aticonfig Layout"
[    22.908] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    22.908] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    22.909] (**) |   |-->Device "aticonfig-Device[0]-0"
[    22.909] (==) Automatically adding devices
[    22.909] (==) Automatically enabling devices
[    22.917] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.917] 	Entry deleted from font path.
[    22.917] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.917] 	Entry deleted from font path.
[    22.917] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.917] 	Entry deleted from font path.
[    22.932] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.932] 	Entry deleted from font path.
[    22.932] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.932] 	Entry deleted from font path.
[    22.955] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    22.955] 	Entry deleted from font path.
[    22.955] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    22.955] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    22.955] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.955] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.955] (II) Loader magic: 0x7f630683db00
[    22.955] (II) Module ABI versions:
[    22.955] 	X.Org ANSI C Emulation: 0.4
[    22.955] 	X.Org Video Driver: 11.0
[    22.955] 	X.Org XInput driver : 16.0
[    22.955] 	X.Org Server Extension : 6.0
[    22.958] (--) PCI:*(0:0:1:0) 1002:9806:1043:2108 rev 0, Mem @ 0xb0000000/268435456, 0xfeb00000/262144, I/O @ 0x0000f000/256
[    22.958] (--) PCI: (0:1:0:0) 1002:6760:1043:2108 rev 0, Mem @ 0xc0000000/268435456, 0xfea20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    22.958] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.958] (II) "extmod" will be loaded by default.
[    22.958] (II) "dbe" will be loaded by default.
[    22.958] (II) "glx" will be loaded by default.
[    22.958] (II) "record" will be loaded by default.
[    22.958] (II) "dri" will be loaded by default.
[    22.958] (II) "dri2" will be loaded by default.
[    22.958] (II) LoadModule: "extmod"
[    23.072] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.083] (II) Module extmod: vendor="X.Org Foundation"
[    23.083] 	compiled for 1.11.3, module version = 1.0.0
[    23.083] 	Module class: X.Org Server Extension
[    23.083] 	ABI class: X.Org Server Extension, version 6.0
[    23.083] (II) Loading extension MIT-SCREEN-SAVER
[    23.083] (II) Loading extension XFree86-VidModeExtension
[    23.083] (II) Loading extension XFree86-DGA
[    23.083] (II) Loading extension DPMS
[    23.083] (II) Loading extension XVideo
[    23.083] (II) Loading extension XVideo-MotionCompensation
[    23.083] (II) Loading extension X-Resource
[    23.083] (II) LoadModule: "dbe"
[    23.084] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.094] (II) Module dbe: vendor="X.Org Foundation"
[    23.094] 	compiled for 1.11.3, module version = 1.0.0
[    23.094] 	Module class: X.Org Server Extension
[    23.094] 	ABI class: X.Org Server Extension, version 6.0
[    23.094] (II) Loading extension DOUBLE-BUFFER
[    23.094] (II) LoadModule: "glx"
[    23.094] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    23.117] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    23.117] 	compiled for 6.9.0, module version = 1.0.0
[    23.117] (II) Loading extension GLX
[    23.117] (II) LoadModule: "record"
[    23.118] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.119] (II) Module record: vendor="X.Org Foundation"
[    23.119] 	compiled for 1.11.3, module version = 1.13.0
[    23.119] 	Module class: X.Org Server Extension
[    23.119] 	ABI class: X.Org Server Extension, version 6.0
[    23.119] (II) Loading extension RECORD
[    23.119] (II) LoadModule: "dri"
[    23.119] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.143] (II) Module dri: vendor="X.Org Foundation"
[    23.143] 	compiled for 1.11.3, module version = 1.0.0
[    23.143] 	ABI class: X.Org Server Extension, version 6.0
[    23.143] (II) Loading extension XFree86-DRI
[    23.143] (II) LoadModule: "dri2"
[    23.144] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.145] (II) Module dri2: vendor="X.Org Foundation"
[    23.145] 	compiled for 1.11.3, module version = 1.2.0
[    23.145] 	ABI class: X.Org Server Extension, version 6.0
[    23.145] (II) Loading extension DRI2
[    23.145] (II) LoadModule: "fglrx"
[    23.146] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    23.418] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    23.418] 	compiled for 1.4.99.906, module version = 8.98.2
[    23.418] 	Module class: X.Org Video Driver
[    23.422] (II) Loading sub module "fglrxdrm"
[    23.422] (II) LoadModule: "fglrxdrm"
[    23.423] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    23.442] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    23.442] 	compiled for 1.4.99.906, module version = 8.98.2
[    23.449] (II) AMD Proprietary Linux Driver Version Identifier:8.98.2
[    23.449] (II) AMD Proprietary Linux Driver Release Identifier: 8.98                                 
[    23.449] (II) AMD Proprietary Linux Driver Build Date: Jun 11 2012 11:57:59
[    23.449] (++) using VT number 7

[    23.449] (WW) Falling back to old probe method for fglrx
[    23.530] (II) PCS database file /etc/ati/amdpcsdb not found
[    23.530] (II)   Creating PCS database from initial defaults instead
[    23.574] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:0) found
[    23.574] (--) Chipset Supported AMD Graphics Processor (0x6760) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    23.590] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    23.590] (**) ChipID override: 0x9806
[    23.590] (**) Chipset Supported AMD Graphics Processor (0x9806) found
[    23.594] ukiDynamicMajor: failed to open /proc/ati/major
[    23.594] ukiDynamicMajor: failed to open /proc/ati/major
[    23.598] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    23.604] (II) AMD Video driver is signed
[    23.606] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    23.606] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    23.606] (II) fglrx(0): pEnt->device->identifier=0x7f63074aa9e0
[    23.606] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    23.609] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    23.609] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    23.609] (==) fglrx(0): Default visual is TrueColor
[    23.609] (**) fglrx(0): Option "DPMS" "true"
[    23.609] (==) fglrx(0): RGB weight 888
[    23.609] (II) fglrx(0): Using 8 bits per RGB 
[    23.609] (==) fglrx(0): Buffer Tiling is ON
[    23.610] (II) Loading sub module "fglrxdrm"
[    23.610] (II) LoadModule: "fglrxdrm"
[    23.611] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    23.611] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    23.611] 	compiled for 1.4.99.906, module version = 8.98.2
[    23.615] ukiDynamicMajor: failed to open /proc/ati/major
[    23.615] ukiDynamicMajor: failed to open /proc/ati/major
[    23.615] (**) fglrx(0): NoAccel = NO
[    23.615] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    23.615] (--) fglrx(0): Chipset: "AMD Radeon HD 6400M Series" (Chipset = 0x6760)
[    23.615] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x2108)
[    23.615] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    23.615] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    23.615] (--) fglrx(0): MMIO registers at 0xfea20000
[    23.615] (--) fglrx(0): I/O port at 0x0000e000
[    23.615] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    23.643] (II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
[    23.643] (EE) fglrx(0): Invalid video BIOS signature!
[    23.643] (EE) fglrx(0): GetBIOSParameter failed
[    23.643] (EE) fglrx(0): PreInitAdapter failed
[    23.643] (EE) fglrx(0): PreInit failed
[    23.643] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === end
[    23.643] (EE) fglrx(0): Failed shutdown interrupts. Error -9
[    23.647] (II) UnloadModule: "fglrx"
[    23.647] (II) Unloading fglrx
[    23.647] (II) UnloadModule: "fglrxdrm"
[    23.647] (II) Unloading fglrxdrm
[    23.647] (II) UnloadModule: "fglrxdrm"
[    23.647] (II) Unloading fglrxdrm
[    23.647] (EE) Screen(s) found, but none have a usable configuration.
[    23.647] 
Fatal server error:
[    23.647] no screens found
[    23.647] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    23.647] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    23.647] 
[    23.664]  ddxSigGiveUp: Closing log
[    23.664] Server terminated with error (1). Closing log file.
```

---

