---
title: "Graphics driver problem - ATI Radeon 5830 on Ubuntu 10.10"
date: 2011-04-11
forum: Hardware
---

### Post by mellowcandle on 2011-04-11
Hi.
I have a problem.
I recently installed on a fresh partition Ubuntu 10.10.
I changed the graphics driver to ATI/AMD proprietary FGLRX graphic driver through the Additional Drivers menu.
but when I restart my PC, the gnome desktop doesn't show up.
when I manually run it (startx)
I get a segmentation fault.

I included the log created, has anyone encountered such a thing ?
I really want to make use of the benefits of my graphics card...

```
[    21.086] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    21.086] X Protocol Version 11, Revision 0
[    21.086] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    21.086] Current Operating System: Linux gombotz-System-Product-Name 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686
[    21.086] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=ac641512-7e59-422e-96cc-b4fd8fc5f66c ro quiet splash
[    21.086] Build Date: 09 January 2011  12:14:58PM
[    21.086] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    21.086] Current version of pixman: 0.18.4
[    21.086] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.086] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.086] (==) Log file: "/var/log/Xorg.5.log", Time: Mon Apr 11 19:19:34 2011
[    21.087] (==) Using config file: "/etc/X11/xorg.conf"
[    21.087] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.087] (==) No Layout section.  Using the first Screen section.
[    21.087] (**) |-->Screen "Default Screen" (0)
[    21.087] (**) |   |-->Monitor "<default monitor>"
[    21.087] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    21.087] (**) |   |-->Device "Default Device"
[    21.087] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    21.087] (==) Automatically adding devices
[    21.087] (==) Automatically enabling devices
[    21.087] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.087] 	Entry deleted from font path.
[    21.087] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.087] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.087] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.087] (II) Loader magic: 0x81f9b00
[    21.087] (II) Module ABI versions:
[    21.087] 	X.Org ANSI C Emulation: 0.4
[    21.087] 	X.Org Video Driver: 8.0
[    21.087] 	X.Org XInput driver : 11.0
[    21.087] 	X.Org Server Extension : 4.0
[    21.088] (--) PCI:*(0:1:0:0) 1002:689e:174b:e140 rev 0, Mem @ 0xc0000000/268435456, 0xff6e0000/131072, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    21.088] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.088] (II) "extmod" will be loaded by default.
[    21.088] (II) "dbe" will be loaded by default.
[    21.088] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    21.088] (II) "record" will be loaded by default.
[    21.088] (II) "dri" will be loaded by default.
[    21.088] (II) "dri2" will be loaded by default.
[    21.088] (II) LoadModule: "glx"
[    21.089] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    21.089] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    21.089] 	compiled for 7.6.0, module version = 1.0.0
[    21.089] (II) Loading extension GLX
[    21.089] (II) LoadModule: "extmod"
[    21.090] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.090] (II) Module extmod: vendor="X.Org Foundation"
[    21.090] 	compiled for 1.9.0, module version = 1.0.0
[    21.090] 	Module class: X.Org Server Extension
[    21.090] 	ABI class: X.Org Server Extension, version 4.0
[    21.090] (II) Loading extension MIT-SCREEN-SAVER
[    21.090] (II) Loading extension XFree86-VidModeExtension
[    21.090] (II) Loading extension XFree86-DGA
[    21.090] (II) Loading extension DPMS
[    21.090] (II) Loading extension XVideo
[    21.090] (II) Loading extension XVideo-MotionCompensation
[    21.090] (II) Loading extension X-Resource
[    21.090] (II) LoadModule: "dbe"
[    21.090] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.090] (II) Module dbe: vendor="X.Org Foundation"
[    21.090] 	compiled for 1.9.0, module version = 1.0.0
[    21.090] 	Module class: X.Org Server Extension
[    21.090] 	ABI class: X.Org Server Extension, version 4.0
[    21.090] (II) Loading extension DOUBLE-BUFFER
[    21.090] (II) LoadModule: "record"
[    21.091] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.091] (II) Module record: vendor="X.Org Foundation"
[    21.091] 	compiled for 1.9.0, module version = 1.13.0
[    21.091] 	Module class: X.Org Server Extension
[    21.091] 	ABI class: X.Org Server Extension, version 4.0
[    21.091] (II) Loading extension RECORD
[    21.091] (II) LoadModule: "dri"
[    21.091] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.092] (II) Module dri: vendor="X.Org Foundation"
[    21.092] 	compiled for 1.9.0, module version = 1.0.0
[    21.092] 	ABI class: X.Org Server Extension, version 4.0
[    21.092] (II) Loading extension XFree86-DRI
[    21.092] (II) LoadModule: "dri2"
[    21.092] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.092] (II) Module dri2: vendor="X.Org Foundation"
[    21.092] 	compiled for 1.9.0, module version = 1.2.0
[    21.092] 	ABI class: X.Org Server Extension, version 4.0
[    21.092] (II) Loading extension DRI2
[    21.092] (II) LoadModule: "fglrx"
[    21.092] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    21.106] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    21.106] 	compiled for 1.4.99.906, module version = 8.78.30
[    21.106] 	Module class: X.Org Video Driver
[    21.106] (II) Loading sub module "fglrxdrm"
[    21.106] (II) LoadModule: "fglrxdrm"
[    21.106] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    21.106] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    21.106] 	compiled for 1.8.99.905, module version = 8.78.30
[    21.106] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    21.106] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    21.106] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[    21.106] (--) using VT number 8

[    21.112] (WW) Falling back to old probe method for fglrx
[    21.114] (II) Loading PCS database from /etc/ati/amdpcsdb
[    21.114] (--) Assigning device section with no busID to primary device
[    21.114] (--) Chipset Supported AMD Graphics Processor (0x689E) found
[    21.114] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    21.114] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    21.114] (II) AMD Video driver is signed
[    21.115] (II) fglrx(0): pEnt->device->identifier=0x8f92488
[    21.115] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    21.115] (II) Loading sub module "vgahw"
[    21.115] (II) LoadModule: "vgahw"
[    21.115] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    21.115] (II) Module vgahw: vendor="X.Org Foundation"
[    21.115] 	compiled for 1.9.0, module version = 0.1.0
[    21.115] 	ABI class: X.Org Video Driver, version 8.0
[    21.115] (II) fglrx(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    21.115] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    21.115] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.115] (==) fglrx(0): Default visual is TrueColor
[    21.115] (==) fglrx(0): RGB weight 888
[    21.115] (II) fglrx(0): Using 8 bits per RGB 
[    21.115] (==) fglrx(0): Buffer Tiling is ON
[    21.115] (II) Loading sub module "fglrxdrm"
[    21.115] (II) LoadModule: "fglrxdrm"
[    21.115] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    21.117] ukiDynamicMajor: found major device number 250
[    21.117] ukiDynamicMajor: found major device number 250
[    21.117] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    21.117] ukiOpenDevice: node name is /dev/ati/card0
[    21.117] ukiOpenDevice: open result is 11, (OK)
[    21.117] ukiOpenByBusid: ukiOpenMinor returns 11
[    21.117] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    21.117] (==) fglrx(0): NoAccel = NO
[    21.117] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    21.117] (--) fglrx(0): Chipset: "ATI Radeon HD 5800 Series  " (Chipset = 0x689e)
[    21.117] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0xe140)
[    21.117] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    21.117] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    21.117] (--) fglrx(0): MMIO registers at 0xff6e0000
[    21.117] (--) fglrx(0): I/O port at 0x00009000
[    21.117] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    21.117] (II) fglrx(0): AC Adapter is used
[    21.125] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    21.191] (II) Loading sub module "vbe"
[    21.191] (II) LoadModule: "vbe"
[    21.191] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    21.191] (II) Module vbe: vendor="X.Org Foundation"
[    21.191] 	compiled for 1.9.0, module version = 1.1.0
[    21.191] 	ABI class: X.Org Video Driver, version 8.0
[    21.191] (II) fglrx(0): VESA BIOS detected
[    21.191] (II) fglrx(0): VESA VBE Version 3.0
[    21.191] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    21.191] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    21.191] (II) fglrx(0): VESA VBE OEM Software Rev: 12.20
[    21.191] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    21.191] (II) fglrx(0): VESA VBE OEM Product: CYPRESS
[    21.191] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    21.232] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    21.232] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    21.232] (II) fglrx(0): PCIE card detected
[    21.232] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    21.232] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    21.234] (II) fglrx(0): Using adapter: 1:0.0.
[    21.365] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    21.459] (II) fglrx(0): Interrupt handler installed at IRQ 47.
[    21.459] (II) fglrx(0): RandR 1.2 support is enabled!
[    21.459] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    21.459] (==) fglrx(0): Center Mode is disabled 
[    21.459] (II) Loading sub module "fb"
[    21.459] (II) LoadModule: "fb"
[    21.459] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.460] (II) Module fb: vendor="X.Org Foundation"
[    21.460] 	compiled for 1.9.0, module version = 1.0.0
[    21.460] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.460] (==) fglrx(0): Active stereo disabled
[    21.460] (II) Loading sub module "ddc"
[    21.460] (II) LoadModule: "ddc"
[    21.460] (II) Module "ddc" already built-in
[    21.565] 
Backtrace:
[    21.565] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80ef31b]
[    21.565] 1: /usr/bin/X (0x8048000+0x5d00d) [0x80a500d]
[    21.565] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x17c40c]
[    21.566] 3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (amdPcsEngine_Command+0x1ec) [0x16db3bc]
[    21.566] 4: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (amdPcsCommand+0x87) [0x16db057]
[    21.566] 5: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xilPcsCommand+0x53) [0x12c38f3]
[    21.566] 6: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (MCIL_SetRegistrykey+0xdc) [0x12d332c]
[    21.566] 7: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZNK14DalSwBaseClass19WritePersistentDataEPKcPvj+0x6a) [0x1519b6a]
[    21.567] 8: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN4Dal214EnableInstanceEP14_DAL_INIT_INFO+0x63) [0x150ea73]
[    21.567] 9: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (DALEnableInstance+0xa4) [0x138f254]
[    21.567] 10: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDalDisplayEnableDAL+0x1a3) [0x12ca4a3]
[    21.567] 11: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xilDisplayAdaptorCreate+0x76) [0x12c7496]
[    21.567] 12: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_x760_atiddxDisplayPreInit+0x93c) [0x12b857c]
[    21.567] 13: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_x760_atiddxPreInit+0x9fb) [0x1288f9b]
[    21.567] 14: /usr/bin/X (InitOutput+0x900) [0x80adf10]
[    21.567] 15: /usr/bin/X (0x8048000+0x1a41b) [0x806241b]
[    21.567] 16: /lib/libc.so.6 (__libc_start_main+0xe7) [0xcc6ce7]
[    21.567] 17: /usr/bin/X (0x8048000+0x1a1b1) [0x80621b1]
[    21.567] Segmentation fault at address 0x2d7c4815
[    21.567] 
Caught signal 11 (Segmentation fault). Server aborting
[    21.567] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    21.567] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[    21.567] 
[    21.572]  ddxSigGiveUp: Closing log

```

---

### Post by Yellow Pasque on 2011-04-11
I would purge that fglrx version [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

and use the latest: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

