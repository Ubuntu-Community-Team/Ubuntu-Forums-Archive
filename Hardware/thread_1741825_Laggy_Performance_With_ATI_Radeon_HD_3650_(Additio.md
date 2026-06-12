---
title: "Laggy Performance With ATI Radeon HD 3650 (Additional Drivers Installed)"
date: 2011-04-28
forum: Hardware
---

### Post by Shahe on 2011-04-28
I Need Advice About This Problem, Because I Cannot Even Try To Play My Games With Such A Laggy Performacne. Thanks.

---

### Post by brunis on 2011-04-28
No ati card have ever worked well with Linux, i suggest you buy nVidia.

I have a dual core 3.9Ghz Machine with a "Cypress" Radeon HD 5850 .. and i get **** out of it.. it can't view movies, it can't do desktop effects, it can't do anything. Vesa mode runs better than ATI's hardware acceleration. It's been like this forever!

Good luck!

---

### Post by Shahe on 2011-04-28
> **brunis said:**
> No ati card have ever worked well with Linux, i suggest you buy nVidia.

I have a dual core 3.9Ghz Machine with a "Cypress" Radeon HD 5850 .. and i get **** out of it.. it can't view movies, it can't do desktop effects, it can't do anything. Vesa mode runs better than ATI's hardware acceleration. It's been like this forever!

Good luck!
thanks for the info, im going to change the pc soon, ill get Nvidia for sure!

---

### Post by Yellow Pasque on 2011-04-28
> **brunis said:**
> No ati card have ever worked well with Linux, i suggest you buy nVidia.

I have a dual core 3.9Ghz Machine with a "Cypress" Radeon HD 5850 .. and i get **** out of it.. it can't view movies, it can't do desktop effects, it can't do anything. Vesa mode runs better than ATI's hardware acceleration. It's been like this forever!

Good luck!
"It doesn't work for me, so it must not work for anyone else."

---

### Post by Shahe on 2011-04-28
> **Temüjin said:**
> "It doesn't work for me, so it must not work for anyone else."
you have a better solution? :D

---

### Post by Yellow Pasque on 2011-04-28
Post your /var/log/Xorg.0.log

---

### Post by Yellow Pasque on 2011-04-28
> **Shahe said:**
> you have a better solution? :D
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by Shahe on 2011-04-28
> **Temüjin said:**
> Post your /var/log/Xorg.0.log
1 more thing, i downloaded the driver of my videocard from AMD.com and now dont even have unity.

```
[    14.175] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.175] X Protocol Version 11, Revision 0
[    14.175] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    14.175] Current Operating System: Linux Ubuntu 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    14.175] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=fa26fbff-9a84-464b-97e1-f165d9ed3210 ro quiet splash vt.handoff=7
[    14.175] Build Date: 19 April 2011  03:33:17PM
[    14.176] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    14.176] Current version of pixman: 0.20.2
[    14.176]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.176] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.176] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 28 23:23:15 2011
[    14.176] (==) Using config file: "/etc/X11/xorg.conf"
[    14.176] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.176] (==) ServerLayout "aticonfig Layout"
[    14.176] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    14.176] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    14.176] (**) |   |-->Device "aticonfig-Device[0]-0"
[    14.176] (==) Automatically adding devices
[    14.176] (==) Automatically enabling devices
[    14.176] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.176]     Entry deleted from font path.
[    14.176] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.176]     Entry deleted from font path.
[    14.177] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.177]     Entry deleted from font path.
[    14.177] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.177]     Entry deleted from font path.
[    14.177] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.177]     Entry deleted from font path.
[    14.177] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.177] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.177] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.177] (II) Loader magic: 0x81ffde0
[    14.177] (II) Module ABI versions:
[    14.177]     X.Org ANSI C Emulation: 0.4
[    14.177]     X.Org Video Driver: 10.0
[    14.177]     X.Org XInput driver : 12.3
[    14.177]     X.Org Server Extension : 5.0
[    14.178] (--) PCI:*(0:3:0:0) 1002:9598:1043:01da rev 0, Mem @ 0xd0000000/268435456, 0xfeae0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    14.178] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.178] (II) "extmod" will be loaded by default.
[    14.178] (II) "dbe" will be loaded by default.
[    14.178] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    14.178] (II) "record" will be loaded by default.
[    14.178] (II) "dri" will be loaded by default.
[    14.178] (II) "dri2" will be loaded by default.
[    14.178] (II) LoadModule: "glx"
[    14.178] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    14.178] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    14.178]     compiled for 6.9.0, module version = 1.0.0
[    14.178] (II) Loading extension GLX
[    14.178] (II) LoadModule: "extmod"
[    14.210] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.210] (II) Module extmod: vendor="X.Org Foundation"
[    14.210]     compiled for 1.10.1, module version = 1.0.0
[    14.210]     Module class: X.Org Server Extension
[    14.210]     ABI class: X.Org Server Extension, version 5.0
[    14.210] (II) Loading extension MIT-SCREEN-SAVER
[    14.210] (II) Loading extension XFree86-VidModeExtension
[    14.210] (II) Loading extension XFree86-DGA
[    14.210] (II) Loading extension DPMS
[    14.210] (II) Loading extension XVideo
[    14.210] (II) Loading extension XVideo-MotionCompensation
[    14.210] (II) Loading extension X-Resource
[    14.210] (II) LoadModule: "dbe"
[    14.210] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.211] (II) Module dbe: vendor="X.Org Foundation"
[    14.211]     compiled for 1.10.1, module version = 1.0.0
[    14.211]     Module class: X.Org Server Extension
[    14.211]     ABI class: X.Org Server Extension, version 5.0
[    14.211] (II) Loading extension DOUBLE-BUFFER
[    14.211] (II) LoadModule: "record"
[    14.211] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.211] (II) Module record: vendor="X.Org Foundation"
[    14.211]     compiled for 1.10.1, module version = 1.13.0
[    14.211]     Module class: X.Org Server Extension
[    14.211]     ABI class: X.Org Server Extension, version 5.0
[    14.211] (II) Loading extension RECORD
[    14.211] (II) LoadModule: "dri"
[    14.211] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.211] (II) Module dri: vendor="X.Org Foundation"
[    14.211]     compiled for 1.10.1, module version = 1.0.0
[    14.211]     ABI class: X.Org Server Extension, version 5.0
[    14.211] (II) Loading extension XFree86-DRI
[    14.211] (II) LoadModule: "dri2"
[    14.212] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.212] (II) Module dri2: vendor="X.Org Foundation"
[    14.212]     compiled for 1.10.1, module version = 1.2.0
[    14.212]     ABI class: X.Org Server Extension, version 5.0
[    14.212] (II) Loading extension DRI2
[    14.212] (II) LoadModule: "fglrx"
[    14.212] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    14.228] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    14.228]     compiled for 1.4.99.906, module version = 8.84.60
[    14.228]     Module class: X.Org Video Driver
[    14.228] (II) Loading sub module "fglrxdrm"
[    14.228] (II) LoadModule: "fglrxdrm"
[    14.228] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    14.229] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    14.229]     compiled for 1.4.99.906, module version = 8.84.60
[    14.229] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    14.229] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    14.229] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    14.229] (++) using VT number 7

[    14.229] (WW) Falling back to old probe method for fglrx
[    14.305] (II) Loading PCS database from /etc/ati/amdpcsdb
[    14.341] (--) Chipset Supported AMD Graphics Processor (0x9598) found
[    14.341] (WW) fglrx: No matching Device section for instance (BusID PCI:0@3:0:1) found
[    14.342] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    14.342] (II) AMD Video driver is signed
[    14.342] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    14.342] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    14.342] (II) fglrx(0): pEnt->device->identifier=0x8965670
[    14.342] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    14.342] (II) Loading sub module "vgahw"
[    14.342] (II) LoadModule: "vgahw"
[    14.343] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    14.343] (II) Module vgahw: vendor="X.Org Foundation"
[    14.343]     compiled for 1.10.1, module version = 0.1.0
[    14.343]     ABI class: X.Org Video Driver, version 10.0
[    14.343] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    14.343] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.343] (==) fglrx(0): Default visual is TrueColor
[    14.343] (**) fglrx(0): Option "DPMS" "true"
[    14.343] (==) fglrx(0): RGB weight 888
[    14.343] (II) fglrx(0): Using 8 bits per RGB 
[    14.343] (==) fglrx(0): Buffer Tiling is ON
[    14.343] (II) Loading sub module "fglrxdrm"
[    14.343] (II) LoadModule: "fglrxdrm"
[    14.344] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    14.344] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    14.344]     compiled for 1.4.99.906, module version = 8.84.60
[    14.345] ukiDynamicMajor: found major device number 249
[    14.345] ukiDynamicMajor: found major device number 249
[    14.345] ukiOpenByBusid: Searching for BusID PCI:3:0:0
[    14.345] ukiOpenDevice: node name is /dev/ati/card0
[    14.345] ukiOpenDevice: open result is 11, (OK)
[    14.345] ukiOpenByBusid: ukiOpenMinor returns 11
[    14.346] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    14.346] (==) fglrx(0): NoAccel = NO
[    14.346] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    14.346] (--) fglrx(0): Chipset: "ATI Radeon HD 3600 Series      " (Chipset = 0x9598)
[    14.346] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x01da)
[    14.346] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    14.346] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    14.346] (--) fglrx(0): MMIO registers at 0xfeae0000
[    14.346] (--) fglrx(0): I/O port at 0x0000d000
[    14.346] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    14.346] (II) fglrx(0): AC Adapter is used
[    14.351] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    14.352] (II) Loading sub module "vbe"
[    14.352] (II) LoadModule: "vbe"
[    14.352] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.352] (II) Module vbe: vendor="X.Org Foundation"
[    14.352]     compiled for 1.10.1, module version = 1.1.0
[    14.352]     ABI class: X.Org Video Driver, version 10.0
[    14.352] (II) fglrx(0): VESA BIOS detected
[    14.352] (II) fglrx(0): VESA VBE Version 3.0
[    14.352] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    14.352] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    14.352] (II) fglrx(0): VESA VBE OEM Software Rev: 10.78
[    14.352] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    14.352] (II) fglrx(0): VESA VBE OEM Product: RV635
[    14.352] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    14.386] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    14.386] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
[    14.386] (II) fglrx(0): PCIE card detected
[    14.386] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    14.386] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    14.390] (II) fglrx(0): Using adapter: 3:0.0.
[    14.419] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x20000000)
[    14.960] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[    14.960] (II) fglrx(0): RandR 1.2 support is enabled!
[    14.960] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    14.960] (==) fglrx(0): Center Mode is disabled 
[    14.960] (II) Loading sub module "fb"
[    14.960] (II) LoadModule: "fb"
[    14.960] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.961] (II) Module fb: vendor="X.Org Foundation"
[    14.961]     compiled for 1.10.1, module version = 1.0.0
[    14.961]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.961] (II) Loading sub module "ddc"
[    14.961] (II) LoadModule: "ddc"
[    14.961] (II) Module "ddc" already built-in
[    15.927] (II) fglrx(0): Finished Initialize PPLIB!
[    15.930] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    15.930] (II) fglrx(0): Output DFP2 has no monitor section
[    15.930] (II) fglrx(0): Output CRT1 has no monitor section
[    15.930] (II) fglrx(0): Output CRT2 has no monitor section
[    15.930] (II) fglrx(0): Output TV has no monitor section
[    15.931] (II) fglrx(0): Output CV has no monitor section
[    15.931] (II) Loading sub module "ddc"
[    15.931] (II) LoadModule: "ddc"
[    15.931] (II) Module "ddc" already built-in
[    15.931] (II) fglrx(0): Connected Display0: DFP2
[    15.931] (II) fglrx(0): Display0 EDID data ---------------------------
[    15.931] (II) fglrx(0): Manufacturer: SAM  Model: 21e  Serial#: 1212232240
[    15.931] (II) fglrx(0): Year: 2007  Week: 29
[    15.931] (II) fglrx(0): EDID Version: 1.3
[    15.931] (II) fglrx(0): Digital Display Input
[    15.931] (II) fglrx(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[    15.931] (II) fglrx(0): Gamma: 2.20
[    15.931] (II) fglrx(0): DPMS capabilities: Off
[    15.931] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.931] (II) fglrx(0): First detailed timing is preferred mode
[    15.931] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    15.931] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    15.931] (II) fglrx(0): Supported established timings:
[    15.931] (II) fglrx(0): 720x400@70Hz
[    15.931] (II) fglrx(0): 640x480@60Hz
[    15.931] (II) fglrx(0): 640x480@67Hz
[    15.931] (II) fglrx(0): 640x480@72Hz
[    15.931] (II) fglrx(0): 640x480@75Hz
[    15.931] (II) fglrx(0): 800x600@56Hz
[    15.931] (II) fglrx(0): 800x600@60Hz
[    15.931] (II) fglrx(0): 800x600@72Hz
[    15.931] (II) fglrx(0): 800x600@75Hz
[    15.931] (II) fglrx(0): 832x624@75Hz
[    15.931] (II) fglrx(0): 1024x768@60Hz
[    15.931] (II) fglrx(0): 1024x768@70Hz
[    15.931] (II) fglrx(0): 1024x768@75Hz
[    15.931] (II) fglrx(0): 1280x1024@75Hz
[    15.931] (II) fglrx(0): 1152x864@75Hz
[    15.931] (II) fglrx(0): Manufacturer's mask: 0
[    15.931] (II) fglrx(0): Supported standard timings:
[    15.931] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.931] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.931] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.931] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.931] (II) fglrx(0): Supported detailed timing:
[    15.931] (II) fglrx(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
[    15.931] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    15.931] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    15.931] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 165 MHz
[    15.931] (II) fglrx(0): Monitor name: SyncMaster
[    15.931] (II) fglrx(0): Serial No: HVJP701093
[    15.931] (II) fglrx(0): EDID (in hex):
[    15.931] (II) fglrx(0):     00ffffffffffff004c2d1e0230324148
[    15.931] (II) fglrx(0):     1d110103802b1b782aee95a3544c9926
[    15.931] (II) fglrx(0):     0f5054bfef80b30081808140714f0101
[    15.931] (II) fglrx(0):     01010101010121399030621a274068b0
[    15.931] (II) fglrx(0):     3600b10f1100001c000000fd00384b1e
[    15.931] (II) fglrx(0):     5110000a202020202020000000fc0053
[    15.931] (II) fglrx(0):     796e634d61737465720a2020000000ff
[    15.931] (II) fglrx(0):     0048564a503730313039330a20200040
[    15.931] (II) fglrx(0): End of Display0 EDID data --------------------
[    16.154] (II) fglrx(0): EDID for output DFP1
[    16.154] (II) fglrx(0): EDID for output DFP2
[    16.154] (II) fglrx(0): Manufacturer: SAM  Model: 21e  Serial#: 1212232240
[    16.154] (II) fglrx(0): Year: 2007  Week: 29
[    16.154] (II) fglrx(0): EDID Version: 1.3
[    16.154] (II) fglrx(0): Digital Display Input
[    16.154] (II) fglrx(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[    16.154] (II) fglrx(0): Gamma: 2.20
[    16.154] (II) fglrx(0): DPMS capabilities: Off
[    16.154] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.154] (II) fglrx(0): First detailed timing is preferred mode
[    16.154] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    16.154] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    16.154] (II) fglrx(0): Supported established timings:
[    16.154] (II) fglrx(0): 720x400@70Hz
[    16.154] (II) fglrx(0): 640x480@60Hz
[    16.154] (II) fglrx(0): 640x480@67Hz
[    16.154] (II) fglrx(0): 640x480@72Hz
[    16.154] (II) fglrx(0): 640x480@75Hz
[    16.154] (II) fglrx(0): 800x600@56Hz
[    16.154] (II) fglrx(0): 800x600@60Hz
[    16.154] (II) fglrx(0): 800x600@72Hz
[    16.154] (II) fglrx(0): 800x600@75Hz
[    16.154] (II) fglrx(0): 832x624@75Hz
[    16.154] (II) fglrx(0): 1024x768@60Hz
[    16.154] (II) fglrx(0): 1024x768@70Hz
[    16.154] (II) fglrx(0): 1024x768@75Hz
[    16.154] (II) fglrx(0): 1280x1024@75Hz
[    16.154] (II) fglrx(0): 1152x864@75Hz
[    16.154] (II) fglrx(0): Manufacturer's mask: 0
[    16.154] (II) fglrx(0): Supported standard timings:
[    16.154] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    16.154] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    16.154] (II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    16.154] (II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    16.154] (II) fglrx(0): Supported detailed timing:
[    16.154] (II) fglrx(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
[    16.154] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    16.155] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    16.155] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 165 MHz
[    16.155] (II) fglrx(0): Monitor name: SyncMaster
[    16.155] (II) fglrx(0): Serial No: HVJP701093
[    16.155] (II) fglrx(0): EDID (in hex):
[    16.155] (II) fglrx(0):     00000000782830293a20454449442028
[    16.155] (II) fglrx(0):     696e20686578293a0a0020204d6f6465
[    16.155] (II) fglrx(0):     6c3a2025410000000000000078283029
[    16.155] (II) fglrx(0):     3a2046697273742064657461696c6564
[    16.155] (II) fglrx(0):     2074696d696e67206973207072656665
[    16.155] (II) fglrx(0):     72726564206d6f64650a000a00fc0053
[    16.155] (II) fglrx(0):     796e634d390000000000000078283029
[    16.155] (II) fglrx(0):     3a20537570706f727465642064657461
[    16.155] (II) fglrx(0): Printing probed modes for output DFP2
[    16.155] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    16.155] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    16.155] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    16.155] (II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync -vsync (40.3 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    16.155] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    16.155] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    16.155] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    16.155] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    16.155] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    16.155] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    16.155] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    16.155] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    16.155] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    16.155] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    16.155] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    16.155] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    16.155] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    16.155] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    16.155] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    16.155] (II) fglrx(0): EDID for output CRT1
[    16.155] (II) fglrx(0): EDID for output CRT2
[    16.155] (II) fglrx(0): EDID for output TV
[    16.155] (II) fglrx(0): EDID for output CV
[    16.155] (II) fglrx(0): Output DFP1 disconnected
[    16.155] (II) fglrx(0): Output DFP2 connected
[    16.155] (II) fglrx(0): Output CRT1 disconnected
[    16.155] (II) fglrx(0): Output CRT2 disconnected
[    16.155] (II) fglrx(0): Output TV disconnected
[    16.155] (II) fglrx(0): Output CV disconnected
[    16.155] (II) fglrx(0): Using exact sizes for initial modes
[    16.155] (II) fglrx(0): Output DFP2 using initial mode 1680x1050
[    16.155] (II) fglrx(0): DPI set to (96, 96)
[    16.155] (II) fglrx(0): Adapter ATI Radeon HD 3600 Series       has 2 configurable heads and 1 displays connected.
[    16.155] (==) fglrx(0):  PseudoColor visuals disabled
[    16.155] (II) Loading sub module "ramdac"
[    16.155] (II) LoadModule: "ramdac"
[    16.155] (II) Module "ramdac" already built-in
[    16.156] (==) fglrx(0): NoDRI = NO
[    16.156] (==) fglrx(0): Capabilities: 0x00000000
[    16.156] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    16.156] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    16.156] (==) fglrx(0): UseFastTLS=0
[    16.156] (==) fglrx(0): BlockSignalsOnLock=1
[    16.156] (--) Depth 24 pixmap format is 32 bpp
[    16.157] (II) Loading extension ATIFGLRXDRI
[    16.157] (II) fglrx(0): doing swlDriScreenInit
[    16.157] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    16.157] ukiDynamicMajor: found major device number 249
[    16.158] ukiDynamicMajor: found major device number 249
[    16.158] ukiDynamicMajor: found major device number 249
[    16.158] ukiOpenByBusid: Searching for BusID PCI:3:0:0
[    16.158] ukiOpenDevice: node name is /dev/ati/card0
[    16.158] ukiOpenDevice: open result is 16, (OK)
[    16.158] ukiOpenByBusid: ukiOpenMinor returns 16
[    16.158] ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
[    16.158] (II) fglrx(0): [uki] DRM interface version 1.0
[    16.158] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:3:0:0"
[    16.158] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    16.158] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb786e000
[    16.158] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    16.158] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    16.158] (II) fglrx(0): swlDriScreenInit done
[    16.158] (II) fglrx(0): Kernel Module Version Information:
[    16.158] (II) fglrx(0):     Name: fglrx
[    16.158] (II) fglrx(0):     Version: 8.84.5
[    16.158] (II) fglrx(0):     Date: Apr  5 2011
[    16.158] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    16.158] (WW) fglrx(0): Kernel Module version does *not* match driver.
[    16.158] (EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
[    16.158] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[    16.158] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0xb786e000
[    16.158] (WW) fglrx(0): ***********************************************************
[    16.158] (WW) fglrx(0): * DRI initialization failed                               *
[    16.158] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    16.158] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    16.158] (WW) fglrx(0): ***********************************************************
[    16.158] (II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
[    16.185] (II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
[    16.185] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1680) (front color buffer - assumption)
[    16.185] (II) fglrx(0): Largest offscreen area available: 1728 x 6511
[    16.185] (==) fglrx(0): Backing store disabled
[    16.185] (II) Loading extension FGLRXEXTENSION
[    16.185] (**) fglrx(0): DPMS enabled
[    16.185] (II) fglrx(0): Initialized in-driver Xinerama extension
[    16.185] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    16.185] (II) LoadModule: "glesx"
[    16.186] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    16.187] (II) Module glesx: vendor="X.Org Foundation"
[    16.187]     compiled for 1.4.99.906, module version = 1.0.0
[    16.187] (II) Loading extension GLESX
[    16.187] (II) fglrx(0): GLESX enableFlags = 512
[    16.187] (II) LoadModule: "amdxmm"
[    16.187] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    16.187] (II) Module amdxmm: vendor="X.Org Foundation"
[    16.187]     compiled for 1.4.99.906, module version = 2.0.0
[    16.187] (EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
[    16.187] (EE) fglrx(0): XMM failed to initialize
[    16.187] (WW) fglrx(0): No XV video playback available
[    16.187] (II) fglrx(0): Enable composite support successfully
[    16.187] (WW) fglrx(0): Option "VendorName" is not used
[    16.187] (WW) fglrx(0): Option "ModelName" is not used
[    16.187] (==) fglrx(0): Silken mouse enabled
[    16.187] (==) fglrx(0): Using HW cursor of display infrastructure!
[    16.188] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    16.188] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    16.188] (II) fglrx(0): Cannot set TV horizontal size.
[    16.188] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    16.188] (II) fglrx(0): Cannot set TV horizontal position.
[    16.188] (II) fglrx(0): Cannot set TV vertical position.
[    16.823] (--) RandR disabled
[    16.823] (II) Initializing built-in extension Generic Event Extension
[    16.823] (II) Initializing built-in extension SHAPE
[    16.823] (II) Initializing built-in extension MIT-SHM
[    16.823] (II) Initializing built-in extension XInputExtension
[    16.823] (II) Initializing built-in extension XTEST
[    16.823] (II) Initializing built-in extension BIG-REQUESTS
[    16.823] (II) Initializing built-in extension SYNC
[    16.823] (II) Initializing built-in extension XKEYBOARD
[    16.823] (II) Initializing built-in extension XC-MISC
[    16.823] (II) Initializing built-in extension SECURITY
[    16.823] (II) Initializing built-in extension XINERAMA
[    16.823] (II) Initializing built-in extension XFIXES
[    16.823] (II) Initializing built-in extension RENDER
[    16.823] (II) Initializing built-in extension RANDR
[    16.823] (II) Initializing built-in extension COMPOSITE
[    16.823] (II) Initializing built-in extension DAMAGE
[    16.823] (II) Initializing built-in extension GESTURE
[    16.827] [glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
[    16.833] (II) AIGLX: Screen 0 is not DRI capable
[    16.834] (II) fglrx(0): Setting screen physical size to 444 x 277
[    16.956] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.965] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.965] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.965] (II) LoadModule: "evdev"
[    16.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.966] (II) Module evdev: vendor="X.Org Foundation"
[    16.966]     compiled for 1.10.0.902, module version = 2.6.0
[    16.966]     Module class: X.Org XInput Driver
[    16.966]     ABI class: X.Org XInput driver, version 12.3
[    16.966] (II) Using input driver 'evdev' for 'Power Button'
[    16.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.966] (**) Power Button: always reports core events
[    16.966] (**) Power Button: Device: "/dev/input/event1"
[    16.984] (--) Power Button: Found keys
[    16.984] (II) Power Button: Configuring as keyboard
[    16.984] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.984] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.984] (**) Option "xkb_rules" "evdev"
[    16.984] (**) Option "xkb_model" "pc105"
[    16.984] (**) Option "xkb_layout" "us"
[    16.986] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.986] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.986] (II) Using input driver 'evdev' for 'Power Button'
[    16.986] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.986] (**) Power Button: always reports core events
[    16.986] (**) Power Button: Device: "/dev/input/event0"
[    17.008] (--) Power Button: Found keys
[    17.008] (II) Power Button: Configuring as keyboard
[    17.008] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    17.008] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.008] (**) Option "xkb_rules" "evdev"
[    17.008] (**) Option "xkb_model" "pc105"
[    17.008] (**) Option "xkb_layout" "us"
[    17.009] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event3)
[    17.009] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[    17.009] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[    17.009] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.009] (**) Genius Optical Mouse: always reports core events
[    17.009] (**) Genius Optical Mouse: Device: "/dev/input/event3"
[    17.024] (--) Genius Optical Mouse: Found 3 mouse buttons
[    17.024] (--) Genius Optical Mouse: Found scroll wheel(s)
[    17.024] (--) Genius Optical Mouse: Found relative axes
[    17.024] (--) Genius Optical Mouse: Found x and y relative axes
[    17.024] (II) Genius Optical Mouse: Configuring as mouse
[    17.024] (II) Genius Optical Mouse: Adding scrollwheel support
[    17.024] (**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[    17.024] (**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.024] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3/event3"
[    17.024] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
[    17.024] (II) Genius Optical Mouse: initialized for relative axes.
[    17.024] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[    17.024] (**) Genius Optical Mouse: (accel) acceleration profile 0
[    17.024] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[    17.024] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[    17.024] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[    17.024] (II) No input driver/identifier specified (ignoring)
[    17.025] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event4)
[    17.025] (II) No input driver/identifier specified (ignoring)
[    17.032] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    17.032] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    17.032] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    17.032] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.032] (**) AT Translated Set 2 keyboard: always reports core events
[    17.032] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    17.060] (--) AT Translated Set 2 keyboard: Found keys
[    17.060] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    17.060] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    17.060] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    17.060] (**) Option "xkb_rules" "evdev"
[    17.060] (**) Option "xkb_model" "pc105"
[    17.060] (**) Option "xkb_layout" "us"
[    17.505] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    25.481] (II) fglrx(0): EDID vendor "SAM", prod id 542
[    25.481] (II) fglrx(0): Using EDID range info for horizontal sync
[    25.481] (II) fglrx(0): Using EDID range info for vertical refresh
[    25.481] (II) fglrx(0): Printing DDC gathered Modelines:
[    25.481] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.481] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.481] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.481] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.481] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.481] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.481] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.481] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.481] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.481] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.481] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.481] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.481] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.481] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.481] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.481] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.481] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    25.481] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.482] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    25.636] (WW) fglrx(0): Cannot get updated TV attributes.
[    25.664] (II) fglrx(0): EDID vendor "SAM", prod id 542
[    25.664] (II) fglrx(0): Using hsync ranges from config file
[    25.664] (II) fglrx(0): Using vrefresh ranges from config file
[    25.664] (II) fglrx(0): Printing DDC gathered Modelines:
[    25.664] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.664] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.664] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.664] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.665] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.665] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.665] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.665] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.665] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.665] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.665] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.665] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.665] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.665] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.665] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.665] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.665] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    25.665] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.665] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    25.819] (WW) fglrx(0): Cannot get updated TV attributes.
[    25.847] (II) fglrx(0): EDID vendor "SAM", prod id 542
[    25.847] (II) fglrx(0): Using hsync ranges from config file
[    25.847] (II) fglrx(0): Using vrefresh ranges from config file
[    25.847] (II) fglrx(0): Printing DDC gathered Modelines:
[    25.847] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.847] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.847] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.847] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.847] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.847] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.847] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.847] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.847] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.847] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.847] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.847] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.847] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.847] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.847] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.847] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.847] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    25.847] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.847] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    26.001] (WW) fglrx(0): Cannot get updated TV attributes.
[    26.030] (II) fglrx(0): EDID vendor "SAM", prod id 542
[    26.030] (II) fglrx(0): Using hsync ranges from config file
[    26.030] (II) fglrx(0): Using vrefresh ranges from config file
[    26.030] (II) fglrx(0): Printing DDC gathered Modelines:
[    26.030] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    26.030] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.030] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.030] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    26.030] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    26.030] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    26.030] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.030] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    26.030] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    26.030] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    26.030] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    26.030] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.030] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    26.030] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    26.030] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    26.030] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    26.030] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    26.030] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    26.030] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    26.184] (WW) fglrx(0): Cannot get updated TV attributes.
[    31.419] (II) fglrx(0): EDID vendor "SAM", prod id 542
[    31.419] (II) fglrx(0): Using hsync ranges from config file
[    31.419] (II) fglrx(0): Using vrefresh ranges from config file
[    31.419] (II) fglrx(0): Printing DDC gathered Modelines:
[    31.419] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    31.419] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    31.419] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    31.420] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    31.420] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    31.420] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    31.420] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    31.420] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    31.420] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    31.420] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    31.420] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    31.420] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    31.420] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    31.420] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    31.420] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    31.420] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    31.420] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    31.420] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    31.420] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    31.574] (WW) fglrx(0): Cannot get updated TV attributes.
```

---

### Post by Fightback on 2011-04-28
> **brunis said:**
> No ati card have ever worked well with Linux, i suggest you buy nVidia.

I have a dual core 3.9Ghz Machine with a "Cypress" Radeon HD 5850 .. and i get **** out of it.. it can't view movies, it can't do desktop effects, it can't do anything. Vesa mode runs better than ATI's hardware acceleration. It's been like this forever!

Good luck!

Err. On my desktop I have a Radeon HD 4870 and it works just fine. I get as good a performance as I get with MS Windows.

---

### Post by Shahe on 2011-04-28
> **Temüjin said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)
got my videocard installed, though i still dont like the performance, ill go back to windows until i get a Nvidia card

---

### Post by Yellow Pasque on 2011-04-28
> **Shahe said:**
> got my videocard installed, though i still dont like the performance, ill go back to windows until i get a Nvidia card
good luck with that...

---

