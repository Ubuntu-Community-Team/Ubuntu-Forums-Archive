---
title: "fglrx SLOW on main X, very fast on second X"
date: 2011-12-08
forum: Hardware
---

### Post by gcbzzzz on 2011-12-08
just installed 11.10, installed proprietary drivers. created xorg.conf with `aticonfig` and added some tweaks mentioned on this forum.

my X is slow. dragging a window is a pain! glxgears is in slow-mo (18fps)

if i run "xinit -- :1" and get a second X, everything is lightning fast. fgl_glxgears spin like crazy

why is that?

my box does have two cards. one in the CPU another dedicated (i think, may be both on the cpu)

lspci
```
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9648
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]
```

xorg device:
```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:0:1:0"
#ChipID  0x4144 # some cards (i.e. 9800SE, or partially broken) with reduced capabilities work fine accessing only parts of the hardware (by supplying the PCI ChipID of a lower end card, http://pci-ids.ucw.cz/read/PC/1002)
Option "AccelMethod" "EXA"  #either XAA or EXA. "EXA" is the default since Karmic. Try XAA with older cards if you have 2D issues.
Option "EnablePageFlip" "true" #only works with accelmethod "XAA"
Option "TripleBuffer"   "true" #This *might* help if you use something like Compiz and have slow video playback.
Option "ColorTiling" "true" #should improve 3D performance for newer cards with kernel >= 2.6.36
EndSection

```

---

### Post by gcbzzzz on 2011-12-08
xorg log for FIRST X

```
[    12.208] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    12.208] X Protocol Version 11, Revision 0
[    12.208] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    12.208] Current Operating System: Linux edge 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686
[    12.208] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=0000fd0a-08e7-4fe5-bb57-902c8a28211c ro acpi_osi=Linux nosplash xforcevesa nomodeset
[    12.208] Build Date: 19 October 2011  05:09:41AM
[    12.208] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    12.208] Current version of pixman: 0.22.2
[    12.208] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.208] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.208] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec  8 11:10:35 2011
[    12.208] (==) Using config file: "/etc/X11/xorg.conf"
[    12.208] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.209] (==) ServerLayout "aticonfig Layout"
[    12.209] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    12.209] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    12.209] (**) |   |-->Device "aticonfig-Device[0]-0"
[    12.209] (==) Automatically adding devices
[    12.209] (==) Automatically enabling devices
[    12.209] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.209] 	Entry deleted from font path.
[    12.209] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.209] 	Entry deleted from font path.
[    12.209] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.209] 	Entry deleted from font path.
[    12.209] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.209] 	Entry deleted from font path.
[    12.209] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.209] 	Entry deleted from font path.
[    12.209] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    12.209] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.209] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.209] (II) Loader magic: 0x823ada0
[    12.209] (II) Module ABI versions:
[    12.209] 	X.Org ANSI C Emulation: 0.4
[    12.209] 	X.Org Video Driver: 10.0
[    12.209] 	X.Org XInput driver : 12.3
[    12.209] 	X.Org Server Extension : 5.0
[    12.216] (--) PCI:*(0:0:1:0) 1002:9648:17aa:21eb rev 0, Mem @ 0xd0000000/268435456, 0xf0c00000/262144, I/O @ 0x00005000/256
[    12.216] (--) PCI: (0:1:0:0) 1002:6760:17aa:21eb rev 0, Mem @ 0xe0000000/268435456, 0xf0b00000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    12.216] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.216] (II) "extmod" will be loaded by default.
[    12.216] (II) "dbe" will be loaded by default.
[    12.216] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    12.216] (II) "record" will be loaded by default.
[    12.216] (II) "dri" will be loaded by default.
[    12.216] (II) "dri2" will be loaded by default.
[    12.216] (II) LoadModule: "glx"
[    12.217] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    12.217] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[    12.217] 	compiled for 6.9.0, module version = 1.0.0
[    12.217] (II) Loading extension GLX
[    12.217] (II) LoadModule: "extmod"
[    12.236] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.237] (II) Module extmod: vendor="X.Org Foundation"
[    12.237] 	compiled for 1.10.4, module version = 1.0.0
[    12.237] 	Module class: X.Org Server Extension
[    12.237] 	ABI class: X.Org Server Extension, version 5.0
[    12.237] (II) Loading extension MIT-SCREEN-SAVER
[    12.237] (II) Loading extension XFree86-VidModeExtension
[    12.237] (II) Loading extension XFree86-DGA
[    12.237] (II) Loading extension DPMS
[    12.237] (II) Loading extension XVideo
[    12.237] (II) Loading extension XVideo-MotionCompensation
[    12.237] (II) Loading extension X-Resource
[    12.237] (II) LoadModule: "dbe"
[    12.237] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.237] (II) Module dbe: vendor="X.Org Foundation"
[    12.237] 	compiled for 1.10.4, module version = 1.0.0
[    12.237] 	Module class: X.Org Server Extension
[    12.237] 	ABI class: X.Org Server Extension, version 5.0
[    12.237] (II) Loading extension DOUBLE-BUFFER
[    12.237] (II) LoadModule: "record"
[    12.237] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.238] (II) Module record: vendor="X.Org Foundation"
[    12.238] 	compiled for 1.10.4, module version = 1.13.0
[    12.238] 	Module class: X.Org Server Extension
[    12.238] 	ABI class: X.Org Server Extension, version 5.0
[    12.238] (II) Loading extension RECORD
[    12.238] (II) LoadModule: "dri"
[    12.238] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.238] (II) Module dri: vendor="X.Org Foundation"
[    12.238] 	compiled for 1.10.4, module version = 1.0.0
[    12.238] 	ABI class: X.Org Server Extension, version 5.0
[    12.238] (II) Loading extension XFree86-DRI
[    12.238] (II) LoadModule: "dri2"
[    12.239] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.239] (II) Module dri2: vendor="X.Org Foundation"
[    12.239] 	compiled for 1.10.4, module version = 1.2.0
[    12.239] 	ABI class: X.Org Server Extension, version 5.0
[    12.239] (II) Loading extension DRI2
[    12.239] (II) LoadModule: "fglrx"
[    12.239] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    12.261] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    12.261] 	compiled for 1.4.99.906, module version = 8.88.7
[    12.261] 	Module class: X.Org Video Driver
[    12.262] (II) Loading sub module "fglrxdrm"
[    12.262] (II) LoadModule: "fglrxdrm"
[    12.262] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    12.262] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    12.262] 	compiled for 1.4.99.906, module version = 8.88.7
[    12.262] (II) ATI Proprietary Linux Driver Version Identifier:8.88.7
[    12.262] (II) ATI Proprietary Linux Driver Release Identifier: 8.881                                
[    12.262] (II) ATI Proprietary Linux Driver Build Date: Jul 28 2011 17:03:52
[    12.262] (++) using VT number 7

[    12.262] (WW) Falling back to old probe method for fglrx
[    12.280] (II) Loading PCS database from /etc/ati/amdpcsdb
[    12.281] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found
[    12.281] (--) Chipset Supported AMD Graphics Processor (0x9648) found
[    12.282] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    12.282] (**) ChipID override: 0x6760
[    12.282] (**) Chipset Supported AMD Graphics Processor (0x6760) found
[    12.288] ukiDynamicMajor: found major device number 251
[    12.288] ukiDynamicMajor: found major device number 251
[    12.288] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    12.288] ukiOpenDevice: node name is /dev/ati/card0
[    12.288] ukiOpenDevice: open result is 11, (OK)
[    12.288] ukiOpenByBusid: ukiOpenMinor returns 11
[    12.288] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    12.289] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    12.290] (II) AMD Video driver is signed
[    12.290] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    12.290] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    12.290] (II) fglrx(0): pEnt->device->identifier=0x9acf208
[    12.292] (II) pEnt->device->identifier=(nil)
[    12.292] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    12.293] (II) Loading sub module "vgahw"
[    12.293] (II) LoadModule: "vgahw"
[    12.293] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    12.293] (II) Module vgahw: vendor="X.Org Foundation"
[    12.293] 	compiled for 1.10.4, module version = 0.1.0
[    12.293] 	ABI class: X.Org Video Driver, version 10.0
[    12.294] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    12.294] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.294] (==) fglrx(0): Default visual is TrueColor
[    12.294] (**) fglrx(0): Option "DPMS" "true"
[    12.294] (==) fglrx(0): RGB weight 888
[    12.294] (II) fglrx(0): Using 8 bits per RGB 
[    12.294] (==) fglrx(0): Buffer Tiling is ON
[    12.294] (II) Loading sub module "fglrxdrm"
[    12.294] (II) LoadModule: "fglrxdrm"
[    12.294] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    12.294] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    12.294] 	compiled for 1.4.99.906, module version = 8.88.7
[    12.297] ukiDynamicMajor: found major device number 251
[    12.297] ukiDynamicMajor: found major device number 251
[    12.297] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    12.297] ukiOpenDevice: node name is /dev/ati/card0
[    12.298] ukiOpenDevice: open result is 15, (OK)
[    12.298] ukiOpenByBusid: ukiOpenMinor returns 15
[    12.298] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    12.298] ukiDynamicMajor: found major device number 251
[    12.298] ukiDynamicMajor: found major device number 251
[    12.298] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    12.298] ukiOpenDevice: node name is /dev/ati/card0
[    12.298] ukiOpenDevice: open result is 16, (OK)
[    12.298] ukiOpenByBusid: ukiOpenMinor returns 16
[    12.298] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    12.298] ukiOpenDevice: node name is /dev/ati/card1
[    12.298] ukiOpenDevice: open result is 16, (OK)
[    12.298] ukiOpenByBusid: ukiOpenMinor returns 16
[    12.298] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.298] (==) fglrx(0): NoAccel = NO
[    12.298] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    12.298] (--) fglrx(0): Chipset: "AMD Radeon HD 6480G" (Chipset = 0x9648)
[    12.298] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x21eb)
[    12.298] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    12.298] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    12.298] (--) fglrx(0): MMIO registers at 0xf0c00000
[    12.298] (--) fglrx(0): I/O port at 0x00005000
[    12.298] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    12.299] (II) fglrx(0): ATIF platform detected
[    12.299] (II) fglrx(0): Battery is used
[    12.350] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    12.351] (II) Loading sub module "vbe"
[    12.351] (II) LoadModule: "vbe"
[    12.352] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    12.352] (II) Module vbe: vendor="X.Org Foundation"
[    12.352] 	compiled for 1.10.4, module version = 1.1.0
[    12.352] 	ABI class: X.Org Video Driver, version 10.0
[    12.352] (II) fglrx(0): VESA BIOS detected
[    12.352] (II) fglrx(0): VESA VBE Version 3.0
[    12.352] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    12.352] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    12.352] (II) fglrx(0): VESA VBE OEM Software Rev: 12.43
[    12.352] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    12.352] (II) fglrx(0): VESA VBE OEM Product: SUMO
[    12.352] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    12.364] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    12.364] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
[    12.364] (II) fglrx(0): PCIE card detected
[    12.364] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    12.364] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    12.367] (II) fglrx(0): PowerXpress is enabled for AMD platform.
[    12.368] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x21eb)
[    12.368] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    12.368] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    12.368] (--) fglrx(0): MMIO registers at 0xf0b00000
[    12.368] (--) fglrx(0): I/O port at 0x00004000
[    12.368] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    13.574] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    13.574] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    13.574] (II) fglrx(0): PCIE card detected
[    13.574] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    13.574] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    13.578] (II) fglrx(0): Using adapter: 0:1.0.
[    14.520] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    14.567] (II) fglrx(0): Interrupt handler installed at IRQ 49.
[    14.567] (II) fglrx(0): Using adapter: 1:0.0.
[    14.580] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    14.645] (II) fglrx(0): Interrupt handler installed at IRQ 50.
[    14.645] (II) fglrx(0): RandR 1.2 support is enabled!
[    14.645] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    14.645] (==) fglrx(0): Center Mode is disabled 
[    14.645] (II) Loading sub module "fb"
[    14.645] (II) LoadModule: "fb"
[    14.645] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.646] (II) Module fb: vendor="X.Org Foundation"
[    14.646] 	compiled for 1.10.4, module version = 1.0.0
[    14.646] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.646] (II) Loading sub module "ddc"
[    14.646] (II) LoadModule: "ddc"
[    14.646] (II) Module "ddc" already built-in
[    14.774] (II) fglrx(0): Finished Initialize PPLIB!
[    14.873] (WW) fglrx(0): Unable to register ADL handler for 0x00C00000
[    14.873] (II) fglrx(0): Finished Initialize PPLIB!
[    14.873] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    14.873] (II) fglrx(0): Output DFP1 has no monitor section
[    14.873] (II) fglrx(0): Output CRT1 has no monitor section
[    14.873] (II) Loading sub module "ddc"
[    14.873] (II) LoadModule: "ddc"
[    14.873] (II) Module "ddc" already built-in
[    14.874] (II) fglrx(0): Connected Display0: LVDS
[    14.874] (II) fglrx(0): Display0 EDID data ---------------------------
[    14.874] (II) fglrx(0): Manufacturer: SEC  Model: 304c  Serial#: 0
[    14.874] (II) fglrx(0): Year: 2010  Week: 0
[    14.874] (II) fglrx(0): EDID Version: 1.3
[    14.874] (II) fglrx(0): Digital Display Input
[    14.874] (II) fglrx(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    14.874] (II) fglrx(0): Gamma: 2.20
[    14.874] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    14.874] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.874] (II) fglrx(0): First detailed timing is preferred mode
[    14.874] (II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    14.874] (II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    14.874] (II) fglrx(0): Manufacturer's mask: 0
[    14.874] (II) fglrx(0): Supported detailed timing:
[    14.874] (II) fglrx(0): clock: 75.8 MHz   Image Size:  309 x 174 mm
[    14.874] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1598 h_border: 0
[    14.874] (II) fglrx(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
[    14.874] (II) fglrx(0): Unknown vendor-specific block f
[    14.874] (II) fglrx(0):  SAMSUNG
[    14.874] (II) fglrx(0):  LTN140AT20401
[    14.874] (II) fglrx(0): EDID (in hex):
[    14.874] (II) fglrx(0): 	00ffffffffffff004ca34c3000000000
[    14.874] (II) fglrx(0): 	00140103801f1178ea87f594574f8c27
[    14.874] (II) fglrx(0): 	27505400000001010101010101010101
[    14.874] (II) fglrx(0): 	010101010101971d56e8500016303020
[    14.874] (II) fglrx(0): 	250035ae100000190000000f00000000
[    14.874] (II) fglrx(0): 	000000000025d9066a00000000fe0053
[    14.874] (II) fglrx(0): 	414d53554e470a204ca34154000000fe
[    14.874] (II) fglrx(0): 	004c544e3134304154323034303100d0
[    14.874] (II) fglrx(0): End of Display0 EDID data --------------------
[    14.880] (II) fglrx(0): EDID for output LVDS
[    14.880] (II) fglrx(0): Manufacturer: SEC  Model: 304c  Serial#: 0
[    14.880] (II) fglrx(0): Year: 2010  Week: 0
[    14.880] (II) fglrx(0): EDID Version: 1.3
[    14.880] (II) fglrx(0): Digital Display Input
[    14.880] (II) fglrx(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    14.880] (II) fglrx(0): Gamma: 2.20
[    14.880] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    14.880] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.880] (II) fglrx(0): First detailed timing is preferred mode
[    14.880] (II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    14.880] (II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    14.880] (II) fglrx(0): Manufacturer's mask: 0
[    14.880] (II) fglrx(0): Supported detailed timing:
[    14.880] (II) fglrx(0): clock: 75.8 MHz   Image Size:  309 x 174 mm
[    14.880] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1598 h_border: 0
[    14.880] (II) fglrx(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
[    14.880] (II) fglrx(0): Unknown vendor-specific block f
[    14.880] (II) fglrx(0):  SAMSUNG
[    14.880] (II) fglrx(0):  LTN140AT20401
[    14.880] (II) fglrx(0): EDID (in hex):
[    14.880] (II) fglrx(0): 	00ffffffffffff004ca34c3000000000
[    14.880] (II) fglrx(0): 	00140103801f1178ea87f594574f8c27
[    14.880] (II) fglrx(0): 	27505400000001010101010101010101
[    14.880] (II) fglrx(0): 	010101010101971d56e8500016303020
[    14.880] (II) fglrx(0): 	250035ae100000190000000f00000000
[    14.880] (II) fglrx(0): 	000000000025d9066a00000000fe0053
[    14.880] (II) fglrx(0): 	414d53554e470a204ca34154000000fe
[    14.880] (II) fglrx(0): 	004c544e3134304154323034303100d0
[    14.880] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    14.880] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.880] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    14.880] (II) fglrx(0): Printing probed modes for output LVDS
[    14.880] (II) fglrx(0): Modeline "1366x768"x60.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    14.880] (II) fglrx(0): Modeline "1360x768"x60.0   75.75  1360 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    14.880] (II) fglrx(0): Modeline "1280x768"x60.0   75.75  1280 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    14.880] (II) fglrx(0): Modeline "1280x720"x60.0   75.75  1280 1414 1446 1598  720 770 775 790 -hsync -vsync (47.4 kHz)
[    14.880] (II) fglrx(0): Modeline "1024x768"x60.0   75.75  1024 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    14.881] (II) fglrx(0): Modeline "1024x600"x60.0   75.75  1024 1414 1446 1598  600 770 775 790 -hsync -vsync (47.4 kHz)
[    14.881] (II) fglrx(0): Modeline "800x600"x60.0   75.75  800 1414 1446 1598  600 770 775 790 -hsync -vsync (47.4 kHz)
[    14.881] (II) fglrx(0): Modeline "800x480"x60.0   75.75  800 1414 1446 1598  480 770 775 790 -hsync -vsync (47.4 kHz)
[    14.881] (II) fglrx(0): Modeline "640x480"x60.0   75.75  640 1414 1446 1598  480 770 775 790 -hsync -vsync (47.4 kHz)
[    14.881] (II) fglrx(0): EDID for output DFP1
[    14.881] (II) fglrx(0): EDID for output CRT1
[    14.881] (II) fglrx(0): Output LVDS connected
[    14.881] (II) fglrx(0): Output DFP1 disconnected
[    14.881] (II) fglrx(0): Output CRT1 disconnected
[    14.881] (II) fglrx(0): Using exact sizes for initial modes
[    14.881] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    14.881] (II) fglrx(0): Display dimensions: (310, 170) mm
[    14.881] (II) fglrx(0): DPI set to (111, 114)
[    14.881] (II) fglrx(0): Adapter AMD Radeon HD 6480G has 2 configurable heads and 1 displays connected.
[    14.881] (==) fglrx(0):  PseudoColor visuals disabled
[    14.881] (II) Loading sub module "ramdac"
[    14.881] (II) LoadModule: "ramdac"
[    14.881] (II) Module "ramdac" already built-in
[    14.881] (==) fglrx(0): NoDRI = NO
[    14.881] (==) fglrx(0): Capabilities: 0x00000000
[    14.881] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    14.881] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    14.881] (==) fglrx(0): UseFastTLS=0
[    14.881] (==) fglrx(0): BlockSignalsOnLock=1
[    14.881] (--) Depth 24 pixmap format is 32 bpp
[    14.991] (II) Loading extension ATIFGLRXDRI
[    14.991] (II) fglrx(0): doing swlDriScreenInit
[    14.991] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    14.991] ukiDynamicMajor: found major device number 251
[    14.991] ukiDynamicMajor: found major device number 251
[    14.991] ukiDynamicMajor: found major device number 251
[    14.991] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.991] ukiOpenDevice: node name is /dev/ati/card0
[    14.991] ukiOpenDevice: open result is 21, (OK)
[    14.991] ukiOpenByBusid: ukiOpenMinor returns 21
[    14.991] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    14.991] ukiOpenDevice: node name is /dev/ati/card1
[    14.991] ukiOpenDevice: open result is 21, (OK)
[    14.991] ukiOpenByBusid: ukiOpenMinor returns 21
[    14.991] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.991] (II) fglrx(0): [uki] DRM interface version 1.0
[    14.991] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    14.991] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    14.991] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb7548000
[    14.991] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    14.991] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    14.991] (II) fglrx(0): swlDriScreenInit done
[    14.991] (II) fglrx(0): Kernel Module Version Information:
[    14.991] (II) fglrx(0):     Name: fglrx
[    14.991] (II) fglrx(0):     Version: 8.88.7
[    14.991] (II) fglrx(0):     Date: Jul 28 2011
[    14.991] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    14.991] (II) fglrx(0): Kernel Module version matches driver.
[    14.991] (II) fglrx(0): Kernel Module Build Time Information:
[    14.991] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.0.0-13-generic
[    14.991] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    14.991] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    14.991] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    14.991] (II) fglrx(0): [uki] register handle = 0x00004000
[    15.022] (II) fglrx(0): Static shadow buffer initialized.
[    15.023] (II) fglrx(0): DRI initialization successfull
[    15.023] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x009c4000
[    15.024] (==) fglrx(0): Backing store disabled
[    15.024] (II) Loading extension FGLRXEXTENSION
[    15.024] (**) fglrx(0): DPMS enabled
[    15.025] (II) fglrx(0): Initialized in-driver Xinerama extension
[    15.025] (**) fglrx(0): Textured Video is enabled.
[    15.025] (II) LoadModule: "glesx"
[    15.025] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[    15.026] (II) Module glesx: vendor="X.Org Foundation"
[    15.026] 	compiled for 1.4.99.906, module version = 1.0.0
[    15.026] (II) Loading extension GLESX
[    15.026] (II) fglrx(0): GLESX enableFlags = 848
[    15.026] (II) fglrx(0): GLESX is enabled
[    15.026] (II) LoadModule: "amdxmm"
[    15.026] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[    15.027] (II) Module amdxmm: vendor="X.Org Foundation"
[    15.027] 	compiled for 1.4.99.906, module version = 2.0.0
[    15.027] (II) Loading extension AMDXVOPL
[    15.027] (II) Loading extension AMDXVBA
[    15.027] [-     XMM_GLX] [I ]glesxXvInit Configureable RGBOutputColorRange
[    15.029] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    15.032] (II) fglrx(0): Enable composite support successfully
[    15.032] (WW) fglrx(0): Option "AccelMethod" is not used
[    15.032] (WW) fglrx(0): Option "EnablePageFlip" is not used
[    15.032] (WW) fglrx(0): Option "TripleBuffer" is not used
[    15.032] (WW) fglrx(0): Option "ColorTiling" is not used
[    15.032] (WW) fglrx(0): Option "VendorName" is not used
[    15.032] (WW) fglrx(0): Option "ModelName" is not used
[    15.032] (II) fglrx(0): X context handle = 0x1
[    15.032] (II) fglrx(0): [DRI] installation complete
[    15.032] (==) fglrx(0): Silken mouse enabled
[    15.032] (==) fglrx(0): Using HW cursor of display infrastructure!
[    15.033] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    15.033] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    15.033] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    16.219] (--) RandR disabled
[    16.219] (II) Initializing built-in extension Generic Event Extension
[    16.219] (II) Initializing built-in extension SHAPE
[    16.219] (II) Initializing built-in extension MIT-SHM
[    16.219] (II) Initializing built-in extension XInputExtension
[    16.219] (II) Initializing built-in extension XTEST
[    16.219] (II) Initializing built-in extension BIG-REQUESTS
[    16.219] (II) Initializing built-in extension SYNC
[    16.219] (II) Initializing built-in extension XKEYBOARD
[    16.219] (II) Initializing built-in extension XC-MISC
[    16.219] (II) Initializing built-in extension SECURITY
[    16.219] (II) Initializing built-in extension XINERAMA
[    16.219] (II) Initializing built-in extension XFIXES
[    16.219] (II) Initializing built-in extension RENDER
[    16.219] (II) Initializing built-in extension RANDR
[    16.219] (II) Initializing built-in extension COMPOSITE
[    16.219] (II) Initializing built-in extension DAMAGE
[    16.219] (II) Initializing built-in extension GESTURE
[    16.242] ukiDynamicMajor: found major device number 251
[    16.242] ukiDynamicMajor: found major device number 251
[    16.242] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.242] ukiOpenDevice: node name is /dev/ati/card0
[    16.242] ukiOpenDevice: open result is 23, (OK)
[    16.242] ukiOpenByBusid: ukiOpenMinor returns 23
[    16.242] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    16.242] ukiOpenDevice: node name is /dev/ati/card1
[    16.242] ukiOpenDevice: open result is 23, (OK)
[    16.242] ukiOpenByBusid: ukiOpenMinor returns 23
[    16.242] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.374] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    16.374] (II) fglrx(0): Enable the clock gating!
[    16.374] (II) fglrx(0): Setting screen physical size to 361 x 203
[    16.390] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.405] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    16.405] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.405] (II) LoadModule: "evdev"
[    16.405] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.406] (II) Module evdev: vendor="X.Org Foundation"
[    16.406] 	compiled for 1.10.2, module version = 2.6.0
[    16.406] 	Module class: X.Org XInput Driver
[    16.406] 	ABI class: X.Org XInput driver, version 12.3
[    16.406] (II) Using input driver 'evdev' for 'Power Button'
[    16.406] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.406] (**) Power Button: always reports core events
[    16.406] (**) Power Button: Device: "/dev/input/event2"
[    16.406] (--) Power Button: Found keys
[    16.406] (II) Power Button: Configuring as keyboard
[    16.406] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    16.406] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.406] (**) Option "xkb_rules" "evdev"
[    16.406] (**) Option "xkb_model" "pc105"
[    16.406] (**) Option "xkb_layout" "us"
[    16.406] (**) Option "xkb_variant" "altgr-intl"
[    16.409] (II) XKB: reuse xkmfile /var/lib/xkb/server-E9EA10154E11AFEF2F1D0F18AF3DCD3D803A1FF6.xkm
[    16.411] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    16.411] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.411] (II) Using input driver 'evdev' for 'Video Bus'
[    16.411] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.411] (**) Video Bus: always reports core events
[    16.411] (**) Video Bus: Device: "/dev/input/event5"
[    16.411] (--) Video Bus: Found keys
[    16.411] (II) Video Bus: Configuring as keyboard
[    16.411] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input5/event5"
[    16.412] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    16.412] (**) Option "xkb_rules" "evdev"
[    16.412] (**) Option "xkb_model" "pc105"
[    16.412] (**) Option "xkb_layout" "us"
[    16.412] (**) Option "xkb_variant" "altgr-intl"
[    16.412] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    16.412] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.412] (II) Using input driver 'evdev' for 'Video Bus'
[    16.413] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.413] (**) Video Bus: always reports core events
[    16.413] (**) Video Bus: Device: "/dev/input/event4"
[    16.413] (--) Video Bus: Found keys
[    16.413] (II) Video Bus: Configuring as keyboard
[    16.413] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input4/event4"
[    16.413] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    16.413] (**) Option "xkb_rules" "evdev"
[    16.413] (**) Option "xkb_model" "pc105"
[    16.413] (**) Option "xkb_layout" "us"
[    16.413] (**) Option "xkb_variant" "altgr-intl"
[    16.416] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.416] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.416] (II) Using input driver 'evdev' for 'Power Button'
[    16.416] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.416] (**) Power Button: always reports core events
[    16.416] (**) Power Button: Device: "/dev/input/event1"
[    16.417] (--) Power Button: Found keys
[    16.417] (II) Power Button: Configuring as keyboard
[    16.417] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    16.417] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.417] (**) Option "xkb_rules" "evdev"
[    16.417] (**) Option "xkb_model" "pc105"
[    16.417] (**) Option "xkb_layout" "us"
[    16.417] (**) Option "xkb_variant" "altgr-intl"
[    16.417] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    16.417] (II) No input driver/identifier specified (ignoring)
[    16.418] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event7)
[    16.418] (II) No input driver/identifier specified (ignoring)
[    16.422] (II) config/udev: Adding input device Integrated Camera (/dev/input/event8)
[    16.422] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[    16.422] (II) Using input driver 'evdev' for 'Integrated Camera'
[    16.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.422] (**) Integrated Camera: always reports core events
[    16.422] (**) Integrated Camera: Device: "/dev/input/event8"
[    16.422] (--) Integrated Camera: Found keys
[    16.422] (II) Integrated Camera: Configuring as keyboard
[    16.422] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input8/event8"
[    16.422] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
[    16.422] (**) Option "xkb_rules" "evdev"
[    16.422] (**) Option "xkb_model" "pc105"
[    16.422] (**) Option "xkb_layout" "us"
[    16.422] (**) Option "xkb_variant" "altgr-intl"
[    16.426] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    16.426] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.426] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.426] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.426] (**) AT Translated Set 2 keyboard: always reports core events
[    16.426] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    16.426] (--) AT Translated Set 2 keyboard: Found keys
[    16.426] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    16.426] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    16.426] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    16.426] (**) Option "xkb_rules" "evdev"
[    16.426] (**) Option "xkb_model" "pc105"
[    16.426] (**) Option "xkb_layout" "us"
[    16.426] (**) Option "xkb_variant" "altgr-intl"
[    16.427] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    16.427] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.427] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.427] (II) LoadModule: "synaptics"
[    16.427] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.428] (II) Module synaptics: vendor="X.Org Foundation"
[    16.428] 	compiled for 1.10.4, module version = 1.4.1
[    16.428] 	Module class: X.Org XInput Driver
[    16.428] 	ABI class: X.Org XInput driver, version 12.3
[    16.428] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    16.428] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.428] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.428] (**) Option "Device" "/dev/input/event9"
[    16.428] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5752
[    16.428] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4912
[    16.428] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.428] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    16.428] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    16.432] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.432] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.440] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    16.440] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    16.440] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    16.440] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    16.440] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.036
[    16.440] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.440] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    16.440] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.440] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.441] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.441] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.441] (II) No input driver/identifier specified (ignoring)
[    16.444] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
[    16.444] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    16.444] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    16.444] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.444] (**) ThinkPad Extra Buttons: always reports core events
[    16.444] (**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
[    16.444] (--) ThinkPad Extra Buttons: Found keys
[    16.444] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    16.444] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input6/event6"
[    16.444] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    16.444] (**) Option "xkb_rules" "evdev"
[    16.444] (**) Option "xkb_model" "pc105"
[    16.444] (**) Option "xkb_layout" "us"
[    16.444] (**) Option "xkb_variant" "altgr-intl"
[    16.512] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    20.496] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    20.496] (II) fglrx(0): Printing DDC gathered Modelines:
[    20.496] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    21.449] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    21.449] (II) fglrx(0): Printing DDC gathered Modelines:
[    21.449] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    22.100] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    22.100] (II) No input driver/identifier specified (ignoring)
[    22.101] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event10)
[    22.101] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    22.101] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    22.101] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    22.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.101] (**) TPPS/2 IBM TrackPoint: always reports core events
[    22.101] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event10"
[    22.101] (--) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    22.101] (--) TPPS/2 IBM TrackPoint: Found relative axes
[    22.101] (--) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    22.101] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    22.101] (**) Option "Emulate3Buttons" "true"
[    22.101] (**) Option "EmulateWheel" "true"
[    22.101] (**) Option "EmulateWheelButton" "2"
[    22.101] (**) Option "YAxisMapping" "4 5"
[    22.101] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    22.101] (**) Option "XAxisMapping" "6 7"
[    22.101] (**) TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    22.101] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.101] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input10/event10"
[    22.101] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    22.101] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    22.101] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    22.101] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    22.102] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    22.102] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    23.020] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    26.374] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    26.374] (II) fglrx(0): Printing DDC gathered Modelines:
[    26.374] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    59.929] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    59.929] (II) fglrx(0): Printing DDC gathered Modelines:
[    59.929] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    60.642] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    60.642] (II) fglrx(0): Printing DDC gathered Modelines:
[    60.642] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    60.702] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    60.702] (II) fglrx(0): Printing DDC gathered Modelines:
[    60.702] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    62.333] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[    62.333] (II) fglrx(0): Printing DDC gathered Modelines:
[    62.333] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[    69.125] (II) XKB: reuse xkmfile /var/lib/xkb/server-5A9D9A1D19879612DA27D336BA29BED4101562E0.xkm
```

one of the many things i can't explain from that is
```
[    15.029] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    15.032] (II) fglrx(0): Enable composite support successfully
[    15.032] (WW) fglrx(0): Option "AccelMethod" is not used
[    15.032] (WW) fglrx(0): Option "EnablePageFlip" is not used
[    15.032] (WW) fglrx(0): Option "TripleBuffer" is not used
[    15.032] (WW) fglrx(0): Option "ColorTiling" is not used
[    15.032] (WW) fglrx(0): Option "VendorName" is not used
[    15.032] (WW) fglrx(0): Option "ModelName" is not used
[    15.032] (II) fglrx(0): X context handle = 0x1
[    15.032] (II) fglrx(0): [DRI] installation complete
[    15.032] (==) fglrx(0): Silken mouse enabled
[    15.032] (==) fglrx(0): Using HW cursor of display infrastructure!
[    15.033] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    15.033] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    15.033] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    16.219] (--) RandR disabled
```

what the "option XXX is not used" means? means it's not going to use the provided option? or that it was not provided in the config and it's missing it?

---

### Post by gcbzzzz on 2011-12-08
Here's the log for the SECOND X that run fast.

```
[  2261.262] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  2261.272] X Protocol Version 11, Revision 0
[  2261.273] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  2261.274] Current Operating System: Linux edge 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686
[  2261.276] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=0000fd0a-08e7-4fe5-bb57-902c8a28211c ro acpi_osi=Linux nosplash xforcevesa nomodeset
[  2261.279] Build Date: 19 October 2011  05:09:41AM
[  2261.280] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  2261.282] Current version of pixman: 0.22.2
[  2261.284] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  2261.287] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2261.293] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Dec  8 11:01:45 2011
[  2261.295] (==) Using config file: "/etc/X11/xorg.conf"
[  2261.297] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2261.299] (==) ServerLayout "aticonfig Layout"
[  2261.299] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[  2261.299] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[  2261.299] (**) |   |-->Device "aticonfig-Device[0]-0"
[  2261.299] (==) Automatically adding devices
[  2261.299] (==) Automatically enabling devices
[  2261.299] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2261.299] 	Entry deleted from font path.
[  2261.299] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2261.299] 	Entry deleted from font path.
[  2261.299] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2261.299] 	Entry deleted from font path.
[  2261.299] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2261.299] 	Entry deleted from font path.
[  2261.299] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2261.299] 	Entry deleted from font path.
[  2261.300] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  2261.300] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2261.300] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2261.300] (II) Loader magic: 0x823ada0
[  2261.300] (II) Module ABI versions:
[  2261.300] 	X.Org ANSI C Emulation: 0.4
[  2261.300] 	X.Org Video Driver: 10.0
[  2261.300] 	X.Org XInput driver : 12.3
[  2261.300] 	X.Org Server Extension : 5.0
[  2261.301] (--) PCI:*(0:0:1:0) 1002:9648:17aa:21eb rev 0, Mem @ 0xd0000000/268435456, 0xf0c00000/262144, I/O @ 0x00005000/256
[  2261.301] (--) PCI: (0:1:0:0) 1002:6760:17aa:21eb rev 0, Mem @ 0xe0000000/268435456, 0xf0b00000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[  2261.301] (II) Open ACPI successful (/var/run/acpid.socket)
[  2261.301] (II) "extmod" will be loaded by default.
[  2261.301] (II) "dbe" will be loaded by default.
[  2261.301] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  2261.301] (II) "record" will be loaded by default.
[  2261.301] (II) "dri" will be loaded by default.
[  2261.301] (II) "dri2" will be loaded by default.
[  2261.301] (II) LoadModule: "glx"
[  2261.301] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[  2261.302] (II) Module glx: vendor="FireGL - AMD Technologies Inc."
[  2261.302] 	compiled for 6.9.0, module version = 1.0.0
[  2261.302] (II) Loading extension GLX
[  2261.302] (II) LoadModule: "extmod"
[  2261.302] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2261.302] (II) Module extmod: vendor="X.Org Foundation"
[  2261.302] 	compiled for 1.10.4, module version = 1.0.0
[  2261.302] 	Module class: X.Org Server Extension
[  2261.302] 	ABI class: X.Org Server Extension, version 5.0
[  2261.302] (II) Loading extension MIT-SCREEN-SAVER
[  2261.302] (II) Loading extension XFree86-VidModeExtension
[  2261.302] (II) Loading extension XFree86-DGA
[  2261.302] (II) Loading extension DPMS
[  2261.302] (II) Loading extension XVideo
[  2261.302] (II) Loading extension XVideo-MotionCompensation
[  2261.302] (II) Loading extension X-Resource
[  2261.302] (II) LoadModule: "dbe"
[  2261.303] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2261.303] (II) Module dbe: vendor="X.Org Foundation"
[  2261.303] 	compiled for 1.10.4, module version = 1.0.0
[  2261.303] 	Module class: X.Org Server Extension
[  2261.303] 	ABI class: X.Org Server Extension, version 5.0
[  2261.303] (II) Loading extension DOUBLE-BUFFER
[  2261.303] (II) LoadModule: "record"
[  2261.303] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2261.303] (II) Module record: vendor="X.Org Foundation"
[  2261.303] 	compiled for 1.10.4, module version = 1.13.0
[  2261.303] 	Module class: X.Org Server Extension
[  2261.303] 	ABI class: X.Org Server Extension, version 5.0
[  2261.303] (II) Loading extension RECORD
[  2261.303] (II) LoadModule: "dri"
[  2261.303] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2261.304] (II) Module dri: vendor="X.Org Foundation"
[  2261.304] 	compiled for 1.10.4, module version = 1.0.0
[  2261.304] 	ABI class: X.Org Server Extension, version 5.0
[  2261.304] (II) Loading extension XFree86-DRI
[  2261.304] (II) LoadModule: "dri2"
[  2261.304] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2261.304] (II) Module dri2: vendor="X.Org Foundation"
[  2261.304] 	compiled for 1.10.4, module version = 1.2.0
[  2261.304] 	ABI class: X.Org Server Extension, version 5.0
[  2261.304] (II) Loading extension DRI2
[  2261.304] (II) LoadModule: "fglrx"
[  2261.304] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[  2261.324] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[  2261.324] 	compiled for 1.4.99.906, module version = 8.88.7
[  2261.324] 	Module class: X.Org Video Driver
[  2261.325] (II) Loading sub module "fglrxdrm"
[  2261.325] (II) LoadModule: "fglrxdrm"
[  2261.325] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[  2261.325] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[  2261.325] 	compiled for 1.4.99.906, module version = 8.88.7
[  2261.325] (II) ATI Proprietary Linux Driver Version Identifier:8.88.7
[  2261.325] (II) ATI Proprietary Linux Driver Release Identifier: 8.881                                
[  2261.325] (II) ATI Proprietary Linux Driver Build Date: Jul 28 2011 17:03:52
[  2261.325] (--) using VT number 8

[  2261.330] (WW) Falling back to old probe method for fglrx
[  2261.343] (II) Loading PCS database from /etc/ati/amdpcsdb
[  2261.344] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found
[  2261.344] (--) Chipset Supported AMD Graphics Processor (0x9648) found
[  2261.345] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[  2261.345] (**) ChipID override: 0x6760
[  2261.345] (**) Chipset Supported AMD Graphics Processor (0x6760) found
[  2261.347] ukiDynamicMajor: found major device number 251
[  2261.347] ukiDynamicMajor: found major device number 251
[  2261.347] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[  2261.347] ukiOpenDevice: node name is /dev/ati/card0
[  2261.347] ukiOpenDevice: open result is 10, (OK)
[  2261.347] ukiOpenByBusid: ukiOpenMinor returns 10
[  2261.347] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[  2261.348] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[  2261.348] (II) AMD Video driver is signed
[  2261.349] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[  2261.349] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[  2261.349] (II) fglrx(0): pEnt->device->identifier=0x8df73f0
[  2261.349] (II) pEnt->device->identifier=(nil)
[  2261.350] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[  2261.350] (II) Loading sub module "vgahw"
[  2261.350] (II) LoadModule: "vgahw"
[  2261.350] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[  2261.350] (II) Module vgahw: vendor="X.Org Foundation"
[  2261.350] 	compiled for 1.10.4, module version = 0.1.0
[  2261.350] 	ABI class: X.Org Video Driver, version 10.0
[  2261.350] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[  2261.350] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  2261.350] (==) fglrx(0): Default visual is TrueColor
[  2261.350] (**) fglrx(0): Option "DPMS" "true"
[  2261.351] (==) fglrx(0): RGB weight 888
[  2261.351] (II) fglrx(0): Using 8 bits per RGB 
[  2261.351] (==) fglrx(0): Buffer Tiling is ON
[  2261.351] (II) Loading sub module "fglrxdrm"
[  2261.351] (II) LoadModule: "fglrxdrm"
[  2261.351] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[  2261.351] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[  2261.351] 	compiled for 1.4.99.906, module version = 8.88.7
[  2261.353] ukiDynamicMajor: found major device number 251
[  2261.353] ukiDynamicMajor: found major device number 251
[  2261.353] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[  2261.353] ukiOpenDevice: node name is /dev/ati/card0
[  2261.354] ukiOpenDevice: open result is 14, (OK)
[  2261.354] ukiOpenByBusid: ukiOpenMinor returns 14
[  2261.354] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[  2261.354] ukiDynamicMajor: found major device number 251
[  2261.354] ukiDynamicMajor: found major device number 251
[  2261.354] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[  2261.354] ukiOpenDevice: node name is /dev/ati/card0
[  2261.354] ukiOpenDevice: open result is 15, (OK)
[  2261.354] ukiOpenByBusid: ukiOpenMinor returns 15
[  2261.354] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[  2261.354] ukiOpenDevice: node name is /dev/ati/card1
[  2261.354] ukiOpenDevice: open result is 15, (OK)
[  2261.354] ukiOpenByBusid: ukiOpenMinor returns 15
[  2261.354] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[  2261.354] (==) fglrx(0): NoAccel = NO
[  2261.354] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[  2261.354] (--) fglrx(0): Chipset: "AMD Radeon HD 6480G" (Chipset = 0x9648)
[  2261.354] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x21eb)
[  2261.354] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[  2261.354] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[  2261.354] (--) fglrx(0): MMIO registers at 0xf0c00000
[  2261.354] (--) fglrx(0): I/O port at 0x00005000
[  2261.354] (==) fglrx(0): ROM-BIOS at 0x000c0000
[  2261.354] (II) fglrx(0): ATIF platform detected
[  2261.355] (II) fglrx(0): Battery is used
[  2261.392] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[  2261.393] (II) Loading sub module "vbe"
[  2261.393] (II) LoadModule: "vbe"
[  2261.393] (II) Loading /usr/lib/xorg/modules/libvbe.so
[  2261.393] (II) Module vbe: vendor="X.Org Foundation"
[  2261.393] 	compiled for 1.10.4, module version = 1.1.0
[  2261.393] 	ABI class: X.Org Video Driver, version 10.0
[  2261.394] (II) fglrx(0): VESA BIOS detected
[  2261.394] (II) fglrx(0): VESA VBE Version 3.0
[  2261.394] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[  2261.394] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[  2261.394] (II) fglrx(0): VESA VBE OEM Software Rev: 12.43
[  2261.394] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[  2261.394] (II) fglrx(0): VESA VBE OEM Product: SUMO
[  2261.394] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[  2261.401] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[  2261.401] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
[  2261.401] (II) fglrx(0): PCIE card detected
[  2261.401] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[  2261.401] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[  2261.404] (II) fglrx(0): PowerXpress is enabled for AMD platform.
[  2261.404] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x21eb)
[  2261.404] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[  2261.404] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[  2261.404] (--) fglrx(0): MMIO registers at 0xf0b00000
[  2261.404] (--) fglrx(0): I/O port at 0x00004000
[  2261.404] (==) fglrx(0): ROM-BIOS at 0x000c0000
[  2261.905] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[  2261.905] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[  2261.905] (II) fglrx(0): PCIE card detected
[  2261.905] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[  2261.905] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[  2261.908] (II) fglrx(0): Using adapter: 0:1.0.
[  2261.908] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[  2261.908] (II) fglrx(0): Interrupt handler installed at IRQ 49.
[  2261.908] (II) fglrx(0): Using adapter: 1:0.0.
[  2261.908] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[  2261.908] (II) fglrx(0): Interrupt handler installed at IRQ 50.
[  2261.908] (II) fglrx(0): RandR 1.2 support is enabled!
[  2261.908] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[  2261.908] (==) fglrx(0): Center Mode is disabled 
[  2261.908] (II) Loading sub module "fb"
[  2261.908] (II) LoadModule: "fb"
[  2261.908] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2261.908] (II) Module fb: vendor="X.Org Foundation"
[  2261.908] 	compiled for 1.10.4, module version = 1.0.0
[  2261.908] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2261.908] (II) Loading sub module "ddc"
[  2261.908] (II) LoadModule: "ddc"
[  2261.908] (II) Module "ddc" already built-in
[  2262.033] (II) fglrx(0): Finished Initialize PPLIB!
[  2262.121] (EE) fglrx(0): PPLIB: PP_Initialize() failed.
[  2262.121] (II) fglrx(0): Finished Initialize PPLIB!
[  2262.121] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[  2262.121] (II) fglrx(0): Output DFP1 has no monitor section
[  2262.121] (II) fglrx(0): Output CRT1 has no monitor section
[  2262.121] (II) Loading sub module "ddc"
[  2262.121] (II) LoadModule: "ddc"
[  2262.121] (II) Module "ddc" already built-in
[  2262.121] (II) fglrx(0): Connected Display0: LVDS
[  2262.121] (II) fglrx(0): Display0 EDID data ---------------------------
[  2262.121] (II) fglrx(0): Manufacturer: SEC  Model: 304c  Serial#: 0
[  2262.121] (II) fglrx(0): Year: 2010  Week: 0
[  2262.121] (II) fglrx(0): EDID Version: 1.3
[  2262.121] (II) fglrx(0): Digital Display Input
[  2262.121] (II) fglrx(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[  2262.121] (II) fglrx(0): Gamma: 2.20
[  2262.121] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[  2262.121] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2262.121] (II) fglrx(0): First detailed timing is preferred mode
[  2262.121] (II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[  2262.121] (II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[  2262.121] (II) fglrx(0): Manufacturer's mask: 0
[  2262.121] (II) fglrx(0): Supported detailed timing:
[  2262.121] (II) fglrx(0): clock: 75.8 MHz   Image Size:  309 x 174 mm
[  2262.121] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1598 h_border: 0
[  2262.121] (II) fglrx(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
[  2262.121] (II) fglrx(0): Unknown vendor-specific block f
[  2262.121] (II) fglrx(0):  SAMSUNG
[  2262.121] (II) fglrx(0):  LTN140AT20401
[  2262.121] (II) fglrx(0): EDID (in hex):
[  2262.121] (II) fglrx(0): 	00ffffffffffff004ca34c3000000000
[  2262.121] (II) fglrx(0): 	00140103801f1178ea87f594574f8c27
[  2262.122] (II) fglrx(0): 	27505400000001010101010101010101
[  2262.122] (II) fglrx(0): 	010101010101971d56e8500016303020
[  2262.122] (II) fglrx(0): 	250035ae100000190000000f00000000
[  2262.122] (II) fglrx(0): 	000000000025d9066a00000000fe0053
[  2262.122] (II) fglrx(0): 	414d53554e470a204ca34154000000fe
[  2262.122] (II) fglrx(0): 	004c544e3134304154323034303100d0
[  2262.122] (II) fglrx(0): End of Display0 EDID data --------------------
[  2262.127] (II) fglrx(0): EDID for output LVDS
[  2262.127] (II) fglrx(0): Manufacturer: SEC  Model: 304c  Serial#: 0
[  2262.127] (II) fglrx(0): Year: 2010  Week: 0
[  2262.127] (II) fglrx(0): EDID Version: 1.3
[  2262.127] (II) fglrx(0): Digital Display Input
[  2262.127] (II) fglrx(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[  2262.127] (II) fglrx(0): Gamma: 2.20
[  2262.127] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[  2262.127] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2262.127] (II) fglrx(0): First detailed timing is preferred mode
[  2262.127] (II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[  2262.127] (II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[  2262.127] (II) fglrx(0): Manufacturer's mask: 0
[  2262.127] (II) fglrx(0): Supported detailed timing:
[  2262.127] (II) fglrx(0): clock: 75.8 MHz   Image Size:  309 x 174 mm
[  2262.127] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1598 h_border: 0
[  2262.127] (II) fglrx(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
[  2262.128] (II) fglrx(0): Unknown vendor-specific block f
[  2262.128] (II) fglrx(0):  SAMSUNG
[  2262.128] (II) fglrx(0):  LTN140AT20401
[  2262.128] (II) fglrx(0): EDID (in hex):
[  2262.128] (II) fglrx(0): 	00ffffffffffff004ca34c3000000000
[  2262.128] (II) fglrx(0): 	00140103801f1178ea87f594574f8c27
[  2262.128] (II) fglrx(0): 	27505400000001010101010101010101
[  2262.128] (II) fglrx(0): 	010101010101971d56e8500016303020
[  2262.128] (II) fglrx(0): 	250035ae100000190000000f00000000
[  2262.128] (II) fglrx(0): 	000000000025d9066a00000000fe0053
[  2262.128] (II) fglrx(0): 	414d53554e470a204ca34154000000fe
[  2262.128] (II) fglrx(0): 	004c544e3134304154323034303100d0
[  2262.128] (II) fglrx(0): EDID vendor "SEC", prod id 12364
[  2262.128] (II) fglrx(0): Printing DDC gathered Modelines:
[  2262.128] (II) fglrx(0): Modeline "1366x768"x0.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Printing probed modes for output LVDS
[  2262.128] (II) fglrx(0): Modeline "1366x768"x60.0   75.75  1366 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "1360x768"x60.0   75.75  1360 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "1280x768"x60.0   75.75  1280 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "1280x720"x60.0   75.75  1280 1414 1446 1598  720 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "1024x768"x60.0   75.75  1024 1414 1446 1598  768 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "1024x600"x60.0   75.75  1024 1414 1446 1598  600 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "800x600"x60.0   75.75  800 1414 1446 1598  600 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "800x480"x60.0   75.75  800 1414 1446 1598  480 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): Modeline "640x480"x60.0   75.75  640 1414 1446 1598  480 770 775 790 -hsync -vsync (47.4 kHz)
[  2262.128] (II) fglrx(0): EDID for output DFP1
[  2262.128] (II) fglrx(0): EDID for output CRT1
[  2262.128] (II) fglrx(0): Output LVDS connected
[  2262.128] (II) fglrx(0): Output DFP1 disconnected
[  2262.128] (II) fglrx(0): Output CRT1 disconnected
[  2262.128] (II) fglrx(0): Using exact sizes for initial modes
[  2262.128] (II) fglrx(0): Output LVDS using initial mode 1366x768
[  2262.128] (II) fglrx(0): Display dimensions: (310, 170) mm
[  2262.128] (II) fglrx(0): DPI set to (111, 114)
[  2262.128] (II) fglrx(0): Adapter AMD Radeon HD 6480G has 2 configurable heads and 1 displays connected.
[  2262.128] (==) fglrx(0):  PseudoColor visuals disabled
[  2262.128] (II) Loading sub module "ramdac"
[  2262.128] (II) LoadModule: "ramdac"
[  2262.128] (II) Module "ramdac" already built-in
[  2262.128] (==) fglrx(0): NoDRI = NO
[  2262.128] (==) fglrx(0): Capabilities: 0x00000000
[  2262.128] (==) fglrx(0): CapabilitiesEx: 0x00000000
[  2262.128] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[  2262.128] (==) fglrx(0): UseFastTLS=0
[  2262.128] (==) fglrx(0): BlockSignalsOnLock=1
[  2262.128] (--) Depth 24 pixmap format is 32 bpp
[  2262.128] (II) Loading extension ATIFGLRXDRI
[  2262.128] (II) fglrx(0): doing swlDriScreenInit
[  2262.128] (II) fglrx(0): swlDriScreenInit for fglrx driver
[  2262.129] ukiDynamicMajor: found major device number 251
[  2262.129] ukiDynamicMajor: found major device number 251
[  2262.129] ukiDynamicMajor: found major device number 251
[  2262.129] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[  2262.129] ukiOpenDevice: node name is /dev/ati/card0
[  2262.129] ukiOpenDevice: open result is 20, (OK)
[  2262.129] ukiOpenByBusid: ukiOpenMinor returns 20
[  2262.129] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[  2262.129] ukiOpenDevice: node name is /dev/ati/card1
[  2262.129] ukiOpenDevice: open result is 20, (OK)
[  2262.129] ukiOpenByBusid: ukiOpenMinor returns 20
[  2262.129] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[  2262.129] (II) fglrx(0): [uki] DRM interface version 1.0
[  2262.129] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[  2262.129] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x3fa8000
[  2262.129] (II) fglrx(0): [uki] mapped SAREA 0x3fa8000 to 0xb756a000
[  2262.129] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[  2262.129] (II) fglrx(0): [uki] added 1 reserved context for kernel
[  2262.129] (II) fglrx(0): swlDriScreenInit done
[  2262.129] (II) fglrx(0): Kernel Module Version Information:
[  2262.129] (II) fglrx(0):     Name: fglrx
[  2262.129] (II) fglrx(0):     Version: 8.88.7
[  2262.129] (II) fglrx(0):     Date: Jul 28 2011
[  2262.129] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[  2262.129] (II) fglrx(0): Kernel Module version matches driver.
[  2262.129] (II) fglrx(0): Kernel Module Build Time Information:
[  2262.129] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.0.0-13-generic
[  2262.129] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[  2262.129] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[  2262.129] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[  2262.129] (II) fglrx(0): [uki] register handle = 0x00004000
[  2262.137] (II) fglrx(0): Static shadow buffer initialized.
[  2262.138] (II) fglrx(0): DRI initialization successfull
[  2262.138] (II) fglrx(0): FBADPhys: 0xf071f7000 FBMappedSize: 0x009c4000
[  2262.139] (==) fglrx(0): Backing store disabled
[  2262.139] (II) Loading extension FGLRXEXTENSION
[  2262.139] (**) fglrx(0): DPMS enabled
[  2262.140] (II) fglrx(0): Initialized in-driver Xinerama extension
[  2262.140] (**) fglrx(0): Textured Video is enabled.
[  2262.140] (II) LoadModule: "glesx"
[  2262.140] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/glesx.so
[  2262.141] (II) Module glesx: vendor="X.Org Foundation"
[  2262.141] 	compiled for 1.4.99.906, module version = 1.0.0
[  2262.141] (II) Loading extension GLESX
[  2262.141] (II) fglrx(0): GLESX enableFlags = 848
[  2262.141] (II) fglrx(0): GLESX is enabled
[  2262.141] (II) LoadModule: "amdxmm"
[  2262.141] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/amdxmm.so
[  2262.142] (II) Module amdxmm: vendor="X.Org Foundation"
[  2262.142] 	compiled for 1.4.99.906, module version = 2.0.0
[  2262.142] (II) Loading extension AMDXVOPL
[  2262.142] (II) Loading extension AMDXVBA
[  2262.142] [-     XMM_GLX] [I ]glesxXvInit Configureable RGBOutputColorRange
[  2262.144] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[  2262.147] (II) fglrx(0): Enable composite support successfully
[  2262.147] (WW) fglrx(0): Option "AccelMethod" is not used
[  2262.147] (WW) fglrx(0): Option "EnablePageFlip" is not used
[  2262.147] (WW) fglrx(0): Option "TripleBuffer" is not used
[  2262.147] (WW) fglrx(0): Option "ColorTiling" is not used
[  2262.147] (WW) fglrx(0): Option "VendorName" is not used
[  2262.147] (WW) fglrx(0): Option "ModelName" is not used
[  2262.147] (II) fglrx(0): X context handle = 0x7
[  2262.147] (II) fglrx(0): [DRI] installation complete
[  2262.147] (==) fglrx(0): Silken mouse enabled
[  2262.147] (==) fglrx(0): Using HW cursor of display infrastructure!
[  2262.148] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[  2262.148] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[  2262.148] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[  2263.261] (--) RandR disabled
[  2263.261] (II) Initializing built-in extension Generic Event Extension
[  2263.261] (II) Initializing built-in extension SHAPE
[  2263.261] (II) Initializing built-in extension MIT-SHM
[  2263.261] (II) Initializing built-in extension XInputExtension
[  2263.261] (II) Initializing built-in extension XTEST
[  2263.261] (II) Initializing built-in extension BIG-REQUESTS
[  2263.261] (II) Initializing built-in extension SYNC
[  2263.261] (II) Initializing built-in extension XKEYBOARD
[  2263.261] (II) Initializing built-in extension XC-MISC
[  2263.261] (II) Initializing built-in extension SECURITY
[  2263.261] (II) Initializing built-in extension XINERAMA
[  2263.261] (II) Initializing built-in extension XFIXES
[  2263.261] (II) Initializing built-in extension RENDER
[  2263.261] (II) Initializing built-in extension RANDR
[  2263.261] (II) Initializing built-in extension COMPOSITE
[  2263.261] (II) Initializing built-in extension DAMAGE
[  2263.261] (II) Initializing built-in extension GESTURE
[  2263.284] ukiDynamicMajor: found major device number 251
[  2263.284] ukiDynamicMajor: found major device number 251
[  2263.284] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[  2263.284] ukiOpenDevice: node name is /dev/ati/card0
[  2263.284] ukiOpenDevice: open result is 22, (OK)
[  2263.285] ukiOpenByBusid: ukiOpenMinor returns 22
[  2263.285] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[  2263.285] ukiOpenDevice: node name is /dev/ati/card1
[  2263.285] ukiOpenDevice: open result is 22, (OK)
[  2263.285] ukiOpenByBusid: ukiOpenMinor returns 22
[  2263.285] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[  2263.412] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[  2263.412] (II) fglrx(0): Enable the clock gating!
[  2263.413] (II) fglrx(0): Setting screen physical size to 361 x 203
[  2263.423] (II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2263.433] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  2263.433] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2263.433] (II) LoadModule: "evdev"
[  2263.433] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.434] (II) Module evdev: vendor="X.Org Foundation"
[  2263.434] 	compiled for 1.10.2, module version = 2.6.0
[  2263.434] 	Module class: X.Org XInput Driver
[  2263.434] 	ABI class: X.Org XInput driver, version 12.3
[  2263.434] (II) Using input driver 'evdev' for 'Power Button'
[  2263.434] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.434] (**) Power Button: always reports core events
[  2263.434] (**) Power Button: Device: "/dev/input/event2"
[  2263.434] (--) Power Button: Found keys
[  2263.434] (II) Power Button: Configuring as keyboard
[  2263.434] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  2263.434] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2263.434] (**) Option "xkb_rules" "evdev"
[  2263.434] (**) Option "xkb_model" "pc105"
[  2263.434] (**) Option "xkb_layout" "us"
[  2263.434] (**) Option "xkb_variant" "altgr-intl"
[  2263.437] (II) XKB: generating xkmfile /tmp/server-E9EA10154E11AFEF2F1D0F18AF3DCD3D803A1FF6.xkm
[  2263.471] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[  2263.471] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  2263.471] (II) Using input driver 'evdev' for 'Video Bus'
[  2263.471] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.471] (**) Video Bus: always reports core events
[  2263.471] (**) Video Bus: Device: "/dev/input/event5"
[  2263.471] (--) Video Bus: Found keys
[  2263.471] (II) Video Bus: Configuring as keyboard
[  2263.471] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input5/event5"
[  2263.471] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  2263.471] (**) Option "xkb_rules" "evdev"
[  2263.471] (**) Option "xkb_model" "pc105"
[  2263.471] (**) Option "xkb_layout" "us"
[  2263.471] (**) Option "xkb_variant" "altgr-intl"
[  2263.472] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  2263.472] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  2263.472] (II) Using input driver 'evdev' for 'Video Bus'
[  2263.472] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.472] (**) Video Bus: always reports core events
[  2263.472] (**) Video Bus: Device: "/dev/input/event4"
[  2263.472] (--) Video Bus: Found keys
[  2263.472] (II) Video Bus: Configuring as keyboard
[  2263.472] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input4/event4"
[  2263.472] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  2263.472] (**) Option "xkb_rules" "evdev"
[  2263.472] (**) Option "xkb_model" "pc105"
[  2263.472] (**) Option "xkb_layout" "us"
[  2263.472] (**) Option "xkb_variant" "altgr-intl"
[  2263.476] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  2263.476] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2263.476] (II) Using input driver 'evdev' for 'Power Button'
[  2263.476] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.476] (**) Power Button: always reports core events
[  2263.476] (**) Power Button: Device: "/dev/input/event1"
[  2263.476] (--) Power Button: Found keys
[  2263.476] (II) Power Button: Configuring as keyboard
[  2263.476] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[  2263.476] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2263.476] (**) Option "xkb_rules" "evdev"
[  2263.476] (**) Option "xkb_model" "pc105"
[  2263.476] (**) Option "xkb_layout" "us"
[  2263.476] (**) Option "xkb_variant" "altgr-intl"
[  2263.477] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  2263.477] (II) No input driver/identifier specified (ignoring)
[  2263.477] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event6)
[  2263.477] (II) No input driver/identifier specified (ignoring)
[  2263.481] (II) config/udev: Adding input device Integrated Camera (/dev/input/event8)
[  2263.481] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[  2263.481] (II) Using input driver 'evdev' for 'Integrated Camera'
[  2263.481] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.481] (**) Integrated Camera: always reports core events
[  2263.481] (**) Integrated Camera: Device: "/dev/input/event8"
[  2263.481] (--) Integrated Camera: Found keys
[  2263.481] (II) Integrated Camera: Configuring as keyboard
[  2263.481] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input8/event8"
[  2263.481] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
[  2263.481] (**) Option "xkb_rules" "evdev"
[  2263.481] (**) Option "xkb_model" "pc105"
[  2263.481] (**) Option "xkb_layout" "us"
[  2263.481] (**) Option "xkb_variant" "altgr-intl"
[  2263.485] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  2263.485] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  2263.485] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  2263.485] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.485] (**) AT Translated Set 2 keyboard: always reports core events
[  2263.485] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  2263.485] (--) AT Translated Set 2 keyboard: Found keys
[  2263.485] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  2263.485] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  2263.485] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  2263.485] (**) Option "xkb_rules" "evdev"
[  2263.485] (**) Option "xkb_model" "pc105"
[  2263.485] (**) Option "xkb_layout" "us"
[  2263.485] (**) Option "xkb_variant" "altgr-intl"
[  2263.486] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[  2263.486] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  2263.486] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  2263.486] (II) LoadModule: "synaptics"
[  2263.486] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  2263.486] (II) Module synaptics: vendor="X.Org Foundation"
[  2263.486] 	compiled for 1.10.4, module version = 1.4.1
[  2263.486] 	Module class: X.Org XInput Driver
[  2263.486] 	ABI class: X.Org XInput driver, version 12.3
[  2263.486] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  2263.486] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  2263.486] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  2263.486] (**) Option "Device" "/dev/input/event9"
[  2263.512] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5752
[  2263.512] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4912
[  2263.512] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  2263.512] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  2263.512] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  2263.524] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  2263.524] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  2263.528] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[  2263.528] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  2263.528] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  2263.528] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  2263.528] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.036
[  2263.529] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  2263.529] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  2263.529] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  2263.529] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  2263.531] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  2263.532] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  2263.532] (II) No input driver/identifier specified (ignoring)
[  2263.533] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event10)
[  2263.533] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[  2263.533] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[  2263.533] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[  2263.533] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.533] (**) TPPS/2 IBM TrackPoint: always reports core events
[  2263.533] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event10"
[  2263.533] (--) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[  2263.533] (--) TPPS/2 IBM TrackPoint: Found relative axes
[  2263.533] (--) TPPS/2 IBM TrackPoint: Found x and y relative axes
[  2263.533] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[  2263.533] (**) Option "Emulate3Buttons" "true"
[  2263.533] (**) Option "EmulateWheel" "true"
[  2263.533] (**) Option "EmulateWheelButton" "2"
[  2263.533] (**) Option "YAxisMapping" "4 5"
[  2263.533] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[  2263.533] (**) Option "XAxisMapping" "6 7"
[  2263.533] (**) TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[  2263.533] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2263.533] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input10/event10"
[  2263.533] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[  2263.534] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[  2263.534] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[  2263.534] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[  2263.534] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[  2263.534] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[  2263.534] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[  2263.534] (II) No input driver/identifier specified (ignoring)
[  2263.540] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event7)
[  2263.540] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[  2263.540] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[  2263.540] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2263.540] (**) ThinkPad Extra Buttons: always reports core events
[  2263.540] (**) ThinkPad Extra Buttons: Device: "/dev/input/event7"
[  2263.540] (--) ThinkPad Extra Buttons: Found keys
[  2263.540] (II) ThinkPad Extra Buttons: Configuring as keyboard
[  2263.540] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input7/event7"
[  2263.540] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[  2263.540] (**) Option "xkb_rules" "evdev"
[  2263.540] (**) Option "xkb_model" "pc105"
[  2263.540] (**) Option "xkb_layout" "us"
[  2263.540] (**) Option "xkb_variant" "altgr-intl"
[  2263.578] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[  2272.230] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[  2278.980] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2278.980] (II) fglrx(0): Backup framebuffer data.
[  2278.980] (II) fglrx(0): Backup complete.
[  2278.980] (II) fglrx(0): Backup framebuffer data.
[  2279.550] (II) fglrx(0): Backup complete.
[  2283.095] (II) ThinkPad Extra Buttons: Close
[  2283.095] (II) UnloadModule: "evdev"
[  2283.095] (II) Unloading evdev
[  2283.095] (II) TPPS/2 IBM TrackPoint: Close
[  2283.095] (II) UnloadModule: "evdev"
[  2283.095] (II) Unloading evdev
[  2283.095] (II) UnloadModule: "synaptics"
[  2283.095] (II) Unloading synaptics
[  2283.095] (II) AT Translated Set 2 keyboard: Close
[  2283.095] (II) UnloadModule: "evdev"
[  2283.095] (II) Unloading evdev
[  2283.095] (II) Integrated Camera: Close
[  2283.095] (II) UnloadModule: "evdev"
[  2283.096] (II) Unloading evdev
[  2283.096] (II) Power Button: Close
[  2283.096] (II) UnloadModule: "evdev"
[  2283.096] (II) Unloading evdev
[  2283.096] (II) Video Bus: Close
[  2283.096] (II) UnloadModule: "evdev"
[  2283.096] (II) Unloading evdev
[  2283.096] (II) Video Bus: Close
[  2283.096] (II) UnloadModule: "evdev"
[  2283.096] (II) Unloading evdev
[  2283.096] (II) Power Button: Close
[  2283.096] (II) UnloadModule: "evdev"
[  2283.096] (II) Unloading evdev
[  2283.101] (II) fglrx(0): Shutdown CMMQS
[  2283.101] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[  2283.101] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x3fa8000 at 0xb756a000
[  2283.102] (II) fglrx(0): Interrupt handler Shutdown.
[  2283.102] (II) fglrx(0): Interrupt handler Shutdown.
[  2283.106]  ddxSigGiveUp: Closing log
```

---

### Post by gcbzzzz on 2011-12-08
entering BIOS
setup > display
discreet graphics = enabled
OS detection thingy = disable (was enabled previously)

this fixed it. gfl_gears now gives me 400+fps

it was a lenovo e425

---

### Post by kenpachiZaraki on 2012-11-14
Hey I know this post is almost one year old but did you ever resolve this issue with module "fglrx" not loading/functioning properly?!?

I ask as I too am seeing a problem with this linux display driver used for Radeon and FireGL family for video adapters.

I have a Radeon HD 6480G.

Any thoughts would be appreciated.

---

