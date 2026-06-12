---
title: "ATI Mobility Radeon HD 4650 does not work after Lucid upgrade"
date: 2010-05-11
forum: Hardware
---

### Post by alperyilmaz on 2010-05-11
I just did clean install of Lucid and I'm having ATI card display issues, although everything was fine in Karmic.
After the install, I installed Catalyst driver (version 10.4) from [http://support.amd.com](http://support.amd.com) website. And right now, compiz is not working and 2D rendering is terrible (tearing, etc).

I'd glad if you can help me with this problem.

I can confirm that radeon module is blacklisted.

Here's related information from system:
```

$ lspci -v | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]

$ glxinfo 
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

$ sudo modprobe -l | grep fglrx
no results

$ modprobe -v fglrx
FATAL: Module fglrx not found.

$ lsmod | grep fglrx
fglrx                2353422  0 

$ dmesg | grep fglrx
[22961.337404] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[22961.414664] [fglrx] Maximum main memory to use for locked dma buffers: 5784 MBytes.
[22961.415039] [fglrx]   vendor: 1002 device: 9480 count: 1
[22961.415512] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[22961.415721] [fglrx] Kernel PAT support is enabled
[22961.415741] [fglrx] module loaded - fglrx 8.72.5 [Apr  6 2010] with 1 minors
```

The lines containing fglrx from Xorg error log:
```

$ grep fglrx /var/log/Xorg.0.log
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(WW) Falling back to old probe method for fglrx
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x228b420
(II) fglrx(0): === [atiddxPreInit] === begin
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4650" (Chipset = 0x9480)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3624)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xda000000
(--) fglrx(0): I/O port at 0x00007000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(EE) fglrx(0): Hasn't establisted DRM connection
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 11.16
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M96
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): Hasn't establisted DRM connection
(WW) fglrx(0): Hasn't establisted DRM connection
(II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) fglrx(0): Connected Display0: LCD on internal LVDS [lvds]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LGD  Model: 1dd  Serial#: 0
(II) fglrx(0): Year: 2008  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.615 redY: 0.346   greenX: 0.314 greenY: 0.602
(II) fglrx(0): blueX: 0.151 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 97.8 MHz   Image Size:  382 x 215 mm
(II) fglrx(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1784 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
(II) fglrx(0):  
(II) fglrx(0):  LP173WD1-TLC1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0030e4dd0100000000
(II) fglrx(0): 	00120103802615780aa8c09d58509a26
(II) fglrx(0): 	1c505400000001010101010101010101
(II) fglrx(0): 	0101010101012f2640b860840c303030
(II) fglrx(0): 	23007ed7100000190000000000000000
(II) fglrx(0): 	00000000000000000000000000fe0000
(II) fglrx(0): 	00004c47446973706c61790a000000fe
(II) fglrx(0): 	004c503137335744312d544c43310063
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output LVDS using monitor section 0-LVDS
(**) fglrx(0): Option "PreferredMode" "1600x900"
(**) fglrx(0): Option "Position" "0 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(**) fglrx(0): Option "TargetRefresh" "60"
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output CRT1 using monitor section 0-CRT1
(**) fglrx(0): Option "PreferredMode" "1024x768"
(**) fglrx(0): Option "Position" "1600 0"
(**) fglrx(0): Option "Disable" "false"
(**) fglrx(0): Option "Rotate" "normal"
(**) fglrx(0): Option "TargetRefresh" "60"
(II) fglrx(0): Output LVDS connected
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Using user preference for initial modes
(II) fglrx(0): Output LVDS using initial mode 1600x900
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Mobility Radeon HD 4650 has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(**) fglrx(0): Capabilities: 0x00000800
(**) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(2624,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2624,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2624 x 7291
(==) fglrx(0): Backing store disabled
(==) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) fglrx(0): GLESX enableFlags = 78
(II) fglrx(0): Acceleration enabled
(EE) fglrx(0): XMM failed to open CMMQS connection.
(II) fglrx(0): XMM failed to initialize!
(II) fglrx(0): Enable composite support successfully
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
(II) fglrx(0): User Preference Output LVDS using refresh rate 60.0 Hz.
(II) fglrx(0): Setting screen physical size to 423 x 238
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
```

And xorg.conf contents are here:
(it was adjusted to have extended display in Karmic)
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1600x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1600 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1024x768"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2624 900
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Dr. Tyrell on 2010-06-07
I have the very same laptop.  Last time I went from radeon to fglrx I seem to remember having to remove other packages.  Sorry I don't remember if it was mesa or what.  After removing the now-forgotten libs and rebooting, I suddenly had full use of direct rendering, etc.  Hope this helps fwiw.

AHA, remove the FB packages!  And you might have to blacklist some FB stuff too.

---

### Post by benjamimgois on 2010-06-08
I'm having a similar problem with my ATI Mobility HD 4550. After installing fglrx with Jockey or the driver downloaded from ATI/AMD site the screen just goes black after the reboot. I check the X.org log and it seens that it has an invalid ATI BIOS. Do you have any idea how to fix it ?

/var/log/Xorg.1.log

[PHP](II) Loading extension DRI2
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
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9555) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x1a855e0
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
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4500 Series " (Chipset = 0x9555)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x1409)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xe8400000
(--) fglrx(0): I/O port at 0x00006000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Bad V_BIOS checksum
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdatper failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "fglrxdrm"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "fglrxdrm"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/PHP]

---

### Post by ericepsylon on 2010-07-28
Same problem here! Does someone have a solution?

---

### Post by ericepsylon on 2010-07-28
> **ericepsylon said:**
> Same problem here! Does someone have a solution?

Solved it myself. Using this tutorial: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by benjamimgois on 2010-07-28
> **ericepsylon said:**
> Same problem here! Does someone have a solution?

It seens to be a bug in the xorg-server. Mark this bug as affecting you here: 

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)

---

### Post by MarioMey on 2011-05-12
@Benjamimgois: I have a similar (or the same) problem. I have a HP Pavillion dv6-3160us with two ATI: 4200 and 5650. Ubuntu 11.04. I tried everything, even the last version of Catalyst (11.5). But, when I inititalize the xorg.conf, it detects only the 4200. If I boot on recovery mode, it detects both. I initialize the xorg.conf by aticonfig and I have a blank screen. This is the log, look at the end:

```
[    16.536] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    16.536] X Protocol Version 11, Revision 0
[    16.536] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    16.536] Current Operating System: Linux mario-HP-Pavilion-dv6-Notebook-PC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    16.536] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e93a8189-f808-45b6-8b61-b2ad5fceced5 ro quiet splash vt.handoff=7
[    16.536] Build Date: 19 April 2011  03:40:45PM
[    16.536] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    16.536] Current version of pixman: 0.20.2
[    16.536]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.536] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.536] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 12 11:16:32 2011
[    16.537] (==) Using config file: "/etc/X11/xorg.conf"
[    16.537] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.537] (==) ServerLayout "aticonfig Layout"
[    16.537] (**) |-->Screen "aticonfig-Screen[1]-0" (0)
[    16.537] (**) |   |-->Monitor "aticonfig-Monitor[1]-0"
[    16.537] (**) |   |-->Device "aticonfig-Device[1]-0"
[    16.537] (==) Automatically adding devices
[    16.537] (==) Automatically enabling devices
[    16.537] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.537]     Entry deleted from font path.
[    16.537] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.537]     Entry deleted from font path.
[    16.537] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.537]     Entry deleted from font path.
[    16.537] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.537]     Entry deleted from font path.
[    16.537] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.537]     Entry deleted from font path.
[    16.537] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    16.537] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.537] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.537] (II) Loader magic: 0x7e0280
[    16.537] (II) Module ABI versions:
[    16.537]     X.Org ANSI C Emulation: 0.4
[    16.537]     X.Org Video Driver: 10.0
[    16.537]     X.Org XInput driver : 12.3
[    16.537]     X.Org Server Extension : 5.0
[    16.538] (--) PCI:*(0:1:5:0) 1002:9712:103c:1440 rev 0, Mem @ 0xd0000000/268435456, 0xf0400000/65536, 0xf0300000/1048576, I/O @ 0x00004000/256
[    16.538] (--) PCI: (0:2:0:0) 1002:68c1:103c:1440 rev 0, Mem @ 0xe0000000/268435456, 0xf0200000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    16.538] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.538] (II) "extmod" will be loaded by default.
[    16.538] (II) "dbe" will be loaded by default.
[    16.538] (II) "glx" will be loaded by default.
[    16.538] (II) "record" will be loaded by default.
[    16.538] (II) "dri" will be loaded by default.
[    16.538] (II) "dri2" will be loaded by default.
[    16.538] (II) LoadModule: "extmod"
[    16.742] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.743] (II) Module extmod: vendor="X.Org Foundation"
[    16.743]     compiled for 1.10.1, module version = 1.0.0
[    16.743]     Module class: X.Org Server Extension
[    16.743]     ABI class: X.Org Server Extension, version 5.0
[    16.743] (II) Loading extension MIT-SCREEN-SAVER
[    16.743] (II) Loading extension XFree86-VidModeExtension
[    16.743] (II) Loading extension XFree86-DGA
[    16.743] (II) Loading extension DPMS
[    16.743] (II) Loading extension XVideo
[    16.743] (II) Loading extension XVideo-MotionCompensation
[    16.743] (II) Loading extension X-Resource
[    16.743] (II) LoadModule: "dbe"
[    16.743] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.743] (II) Module dbe: vendor="X.Org Foundation"
[    16.743]     compiled for 1.10.1, module version = 1.0.0
[    16.743]     Module class: X.Org Server Extension
[    16.743]     ABI class: X.Org Server Extension, version 5.0
[    16.743] (II) Loading extension DOUBLE-BUFFER
[    16.743] (II) LoadModule: "glx"
[    16.743] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    16.744] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    16.744]     compiled for 6.9.0, module version = 1.0.0
[    16.744] (II) Loading extension GLX
[    16.744] (II) LoadModule: "record"
[    16.744] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.744] (II) Module record: vendor="X.Org Foundation"
[    16.744]     compiled for 1.10.1, module version = 1.13.0
[    16.744]     Module class: X.Org Server Extension
[    16.744]     ABI class: X.Org Server Extension, version 5.0
[    16.744] (II) Loading extension RECORD
[    16.744] (II) LoadModule: "dri"
[    16.744] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.745] (II) Module dri: vendor="X.Org Foundation"
[    16.745]     compiled for 1.10.1, module version = 1.0.0
[    16.745]     ABI class: X.Org Server Extension, version 5.0
[    16.745] (II) Loading extension XFree86-DRI
[    16.745] (II) LoadModule: "dri2"
[    16.745] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.745] (II) Module dri2: vendor="X.Org Foundation"
[    16.745]     compiled for 1.10.1, module version = 1.2.0
[    16.745]     ABI class: X.Org Server Extension, version 5.0
[    16.745] (II) Loading extension DRI2
[    16.745] (II) LoadModule: "fglrx"
[    16.745] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.765] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    16.765]     compiled for 1.4.99.906, module version = 8.85.6
[    16.765]     Module class: X.Org Video Driver
[    16.766] (II) Loading sub module "fglrxdrm"
[    16.766] (II) LoadModule: "fglrxdrm"
[    16.766] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.766] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    16.766]     compiled for 1.4.99.906, module version = 8.85.6
[    16.766] (II) ATI Proprietary Linux Driver Version Identifier:8.85.6
[    16.766] (II) ATI Proprietary Linux Driver Release Identifier: 8.85                                 
[    16.766] (II) ATI Proprietary Linux Driver Build Date: Apr 19 2011 21:30:04
[    16.766] (++) using VT number 7

[    16.767] (WW) Falling back to old probe method for fglrx
[    16.773] (II) Loading PCS database from /etc/ati/amdpcsdb
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:0) found
[    16.774] (--) Chipset Supported AMD Graphics Processor (0x68C1) found
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    16.774] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    16.775] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    16.775] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    16.775] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    16.775] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    16.775] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    16.775] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    16.775] (**) ChipID override: 0x9712
[    16.775] (**) Chipset Supported AMD Graphics Processor (0x9712) found
[    16.775] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    16.775] (II) AMD Video driver is signed
[    16.775] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.775] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.775] (II) fglrx(0): pEnt->device->identifier=0x823380
[    16.775] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    16.776] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    16.776] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.776] (==) fglrx(0): Default visual is TrueColor
[    16.776] (**) fglrx(0): Option "DPMS" "true"
[    16.776] (==) fglrx(0): RGB weight 888
[    16.776] (II) fglrx(0): Using 8 bits per RGB 
[    16.776] (==) fglrx(0): Buffer Tiling is ON
[    16.776] (II) Loading sub module "fglrxdrm"
[    16.776] (II) LoadModule: "fglrxdrm"
[    16.776] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.776] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    16.776]     compiled for 1.4.99.906, module version = 8.85.6
[    16.778] ukiDynamicMajor: found major device number 250
[    16.778] ukiDynamicMajor: found major device number 250
[    16.778] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    16.778] ukiOpenDevice: node name is /dev/ati/card0
[    16.778] ukiOpenDevice: open result is 11, (OK)
[    16.778] ukiOpenByBusid: ukiOpenMinor returns 11
[    16.778] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    16.779] ukiOpenDevice: node name is /dev/ati/card1
[    16.779] ukiOpenDevice: open result is 11, (OK)
[    16.779] ukiOpenByBusid: ukiOpenMinor returns 11
[    16.779] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    16.779] (==) fglrx(0): NoAccel = NO
[    16.779] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    16.779] (--) fglrx(0): Chipset: "AMD Radeon HD 6500M/5600/5700 Series" (Chipset = 0x68c1)
[    16.779] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x1440)
[    16.779] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    16.779] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    16.779] (--) fglrx(0): MMIO registers at 0xf0200000
[    16.779] (--) fglrx(0): I/O port at 0x00003000
[    16.779] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    16.780] (II) fglrx(0): ATIF platform detected
[    16.781] (II) fglrx(0): AC Adapter is used
[    16.783] (II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
[    16.784] (EE) fglrx(0): Invalid video BIOS signature!
[    16.784] (EE) fglrx(0): GetBIOSParameter failed
[    16.784] (EE) fglrx(0): PreInitAdapter failed
[    16.784] (EE) fglrx(0): PreInit failed
[    16.784] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === end
[    16.820] (II) UnloadModule: "fglrx"
[    16.820] (II) Unloading fglrx
[    16.820] (II) UnloadModule: "fglrxdrm"
[    16.820] (II) Unloading fglrxdrm
[    16.820] (II) UnloadModule: "fglrxdrm"
[    16.820] (II) Unloading fglrxdrm
[    16.820] (EE) Screen(s) found, but none have a usable configuration.
[    16.820] 
Fatal server error:
[    16.820] no screens found
[    16.820] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    16.820] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    16.820] 
[    16.820]  ddxSigGiveUp: Closing log
```And the xorg.conf with the two cards:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
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

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```HP doesn't support Linux, they wash their hands. ATI only gives "generic" drivers... they didn't build this laptop. And now?

Do we have to wait for another version?

---

### Post by benjamimgois on 2011-05-12
> **MarioMey said:**
> @Benjamimgois: I have a similar (or the same) problem. I have a HP Pavillion dv6-3160us with two ATI: 4200 and 5650. Ubuntu 11.04. I tried everything, even the last version of Catalyst (11.5). But, when I inititalize the xorg.conf, it detects only the 4200. If I boot on recovery mode, it detects both. I initialize the xorg.conf by aticonfig and I have a blank screen. This is the log, look at the end:

HP doesn't support Linux, they wash their hands. ATI only gives "generic" drivers... they didn't build this laptop. And now?

Do we have to wait for another version?

MarioMey, after a long search on the web i could actually made it work on 11.04, here is what you need to do.

Edit [COLOR="RoyalBlue"]/etc/default/grub[/COLOR], and change the following line:

[COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]

To

[COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT=radeon.modeset=0[/COLOR]

then run update-grub.


It will turn-off your ATI card but at least you will be able to boot your PC and use the intel card in a normal way. Lets hope powerxpress on catalyst work for us in a near future.

---

### Post by MarioMey on 2011-05-16
Thanks Benjamimgois... but this computer has two ATIs. A 4250 and a 5650. The 4250 works, I can start Ubuntu and use it, but I can't turn off this card (the 4250) to use the 5650. That's what I want.

---

