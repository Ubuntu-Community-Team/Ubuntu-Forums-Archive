---
title: "ATI Catalyst frglx not redrawing OpenGL windows anymore"
date: 2013-02-14
forum: Hardware
---

### Post by wattyka on 2013-02-14
Hi,

I'm actually using Kubuntu 12.10, but I doubt the problem is KDE related, so i'll try my luck here.

Heres what I've done:

1.) installed Kubuntu 12.10 AMD64 on a Core I7 + HD5750 machine
2.) installed ATI prorietary Catalyst 13.1 (using provided shell script)
=>now Desktop & OpenGL apps (glxgears/Steam/TF2 ) worked perfectly fine and fast

3.) installed all pending updates with Muon updater (which included an update to kernel 3.5.0-24-generic)
 =>after reboot, the system locked up at X server startup (also not possible to switch consoles etc.); it even locked up with the previous kernel selection in grub 

4.) booted into recovery mode, uninstalled Catalyst 13.1 with uninstall shell script in /usr/share/ati, removed x.org conf, rebooted
5.) X starts up using default driver; installed Catalyst 13.2 beta  (using privided shell script), removed x.org conf, rebooted
=> Desktop runs perfectly fine, however: all OpenGL windows (glxgears/Steam/TF2) wont refresh/redraw anymore; they only refresh/redraw when I move them or move another window over them; glxgears spits our reasonable fps values and nothing unusual when started with LIBGL_DEBUG=verbose

Now I've tried a whole bunch of other things like uninstalling/puring the Catalyst drivers cleanly and installing both 13.1 and 13.2 again using generated .deb packages. Nothing seems to work except the default driver combination always, which however has very poor OpenGL performance.

I cannot find any specific information on that problem. Maybe someone here would have an idea where to look next ?

Thanks alot,
Watz

x.org log:
```

[    13.117] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    13.117] X Protocol Version 11, Revision 0
[    13.117] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    13.117] Current Operating System: Linux exterminator 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 01:50:30 UTC 2013 x86_64
[    13.117] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-24-generic root=UUID=753583a8-dcd7-42f9-b75e-70738892c92e ro quiet splash vt.handoff=7
[    13.117] Build Date: 27 November 2012  07:44:35AM
[    13.117] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    13.117] Current version of pixman: 0.26.0
[    13.117]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    13.117] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.117] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 14 23:16:35 2013
[    13.149] (==) Using config file: "/etc/X11/xorg.conf"
[    13.149] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.276] (==) ServerLayout "aticonfig Layout"
[    13.276] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    13.276] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    13.276] (**) |   |-->Device "aticonfig-Device[0]-0"
[    13.276] (==) Automatically adding devices
[    13.276] (==) Automatically enabling devices
[    13.276] (==) Automatically adding GPU devices
[    13.326] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.326]     Entry deleted from font path.
[    13.326] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.326]     Entry deleted from font path.
[    13.326] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.326]     Entry deleted from font path.
[    13.326] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.326]     Entry deleted from font path.
[    13.326] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.326]     Entry deleted from font path.
[    13.326] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    13.326]     Entry deleted from font path.
[    13.326] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    13.326] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.326] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.326] (II) Loader magic: 0x7f2edde19c40
[    13.326] (II) Module ABI versions:
[    13.326]     X.Org ANSI C Emulation: 0.4
[    13.326]     X.Org Video Driver: 13.0
[    13.326]     X.Org XInput driver : 18.0
[    13.326]     X.Org Server Extension : 7.0
[    13.327] (--) PCI:*(0:1:0:0) 1002:68be:1787:2287 rev 0, Mem @ 0xe0000000/268435456, 0xf7e20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    13.327] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.347] Initializing built-in extension Generic Event Extension
[    13.347] Initializing built-in extension SHAPE
[    13.347] Initializing built-in extension MIT-SHM
[    13.347] Initializing built-in extension XInputExtension
[    13.347] Initializing built-in extension XTEST
[    13.347] Initializing built-in extension BIG-REQUESTS
[    13.347] Initializing built-in extension SYNC
[    13.347] Initializing built-in extension XKEYBOARD
[    13.347] Initializing built-in extension XC-MISC
[    13.347] Initializing built-in extension SECURITY
[    13.347] Initializing built-in extension XINERAMA
[    13.347] Initializing built-in extension XFIXES
[    13.347] Initializing built-in extension RENDER
[    13.347] Initializing built-in extension RANDR
[    13.347] Initializing built-in extension COMPOSITE
[    13.347] Initializing built-in extension DAMAGE
[    13.347] Initializing built-in extension MIT-SCREEN-SAVER
[    13.347] Initializing built-in extension DOUBLE-BUFFER
[    13.347] Initializing built-in extension RECORD
[    13.347] Initializing built-in extension DPMS
[    13.347] Initializing built-in extension X-Resource
[    13.347] Initializing built-in extension XVideo
[    13.347] Initializing built-in extension XVideo-MotionCompensation
[    13.347] Initializing built-in extension XFree86-VidModeExtension
[    13.347] Initializing built-in extension XFree86-DGA
[    13.347] Initializing built-in extension XFree86-DRI
[    13.347] Initializing built-in extension DRI2
[    13.347] (II) "glx" will be loaded by default.
[    13.347] (II) LoadModule: "glx"
[    13.683] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    13.775] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    13.775]     compiled for 6.9.0, module version = 1.0.0
[    13.775] Loading extension GLX
[    13.775] (II) LoadModule: "fglrx"
[    13.775] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    14.406] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    14.406]     compiled for 1.4.99.906, module version = 9.1.11
[    14.406]     Module class: X.Org Video Driver
[    14.406] (II) Loading sub module "fglrxdrm"
[    14.406] (II) LoadModule: "fglrxdrm"
[    14.406] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    14.455] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    14.455]     compiled for 1.4.99.906, module version = 9.1.11
[    14.455] (II) AMD Proprietary Linux Driver Version Identifier:9.01.11
[    14.455] (II) AMD Proprietary Linux Driver Release Identifier: 9.012                                
[    14.455] (II) AMD Proprietary Linux Driver Build Date: Dec 19 2012 14:41:10
[    14.455] (++) using VT number 7

[    14.455] (WW) Falling back to old probe method for fglrx
[    14.518] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    14.519] ukiDynamicMajor: found major device number 250
[    14.519] ukiDynamicMajor: found major device number 250
[    14.519] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.519] ukiOpenDevice: node name is /dev/ati/card0
[    14.520] ukiOpenDevice: open result is 10, (OK)
[    14.745] ukiOpenByBusid: ukiOpenMinor returns 10
[    14.745] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.769] (--) Chipset Supported AMD Graphics Processor (0x68BE) found
[    14.784] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    14.784] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    14.801] (II) AMD Video driver is signed
[    14.801] (II) fglrx(0): pEnt->device->identifier=0x7f2edf354100
[    14.801] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[    14.801] (II) Loading sub module "vgahw"
[    14.801] (II) LoadModule: "vgahw"
[    14.855] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    14.869] (II) Module vgahw: vendor="X.Org Foundation"
[    14.869]     compiled for 1.13.0, module version = 0.1.0
[    14.869]     ABI class: X.Org Video Driver, version 13.0
[    14.869] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    14.869] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.869] (==) fglrx(0): Default visual is TrueColor
[    14.869] (**) fglrx(0): Option "DPMS" "true"
[    14.869] (==) fglrx(0): RGB weight 888
[    14.869] (II) fglrx(0): Using 8 bits per RGB 
[    14.869] (==) fglrx(0): Buffer Tiling is ON
[    14.869] (II) Loading sub module "fglrxdrm"
[    14.869] (II) LoadModule: "fglrxdrm"
[    14.869] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    14.869] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    14.869]     compiled for 1.4.99.906, module version = 9.1.11
[    14.870] ukiDynamicMajor: found major device number 250
[    14.870] ukiDynamicMajor: found major device number 250
[    14.870] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.870] ukiOpenDevice: node name is /dev/ati/card0
[    14.870] ukiOpenDevice: open result is 13, (OK)
[    14.870] ukiOpenByBusid: ukiOpenMinor returns 13
[    14.870] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.870] (**) fglrx(0): NoAccel = NO
[    14.870] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    14.870] (--) fglrx(0): Chipset: "ATI Radeon HD 5700 Series " (Chipset = 0x68be)
[    14.870] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x2287)
[    14.870] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    14.870] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    14.870] (--) fglrx(0): MMIO registers at 0xf7e20000
[    14.870] (--) fglrx(0): I/O port at 0x0000e000
[    14.870] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    14.888] (II) fglrx(0): AC Adapter is used
[    14.890] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    14.891] (II) Loading sub module "vbe"
[    14.891] (II) LoadModule: "vbe"
[    14.891] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.920] (II) Module vbe: vendor="X.Org Foundation"
[    14.920]     compiled for 1.13.0, module version = 1.1.0
[    14.920]     ABI class: X.Org Video Driver, version 13.0
[    14.920] (II) fglrx(0): VESA BIOS detected
[    14.920] (II) fglrx(0): VESA VBE Version 3.0
[    14.920] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    14.920] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    14.920] (II) fglrx(0): VESA VBE OEM Software Rev: 12.14
[    14.920] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    14.920] (II) fglrx(0): VESA VBE OEM Product: JUNIPER
[    14.920] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    14.920] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    14.920] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    14.920] (II) fglrx(0): PCIE card detected
[    14.920] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    14.920] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    14.920] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    14.920] (II) fglrx(0): RandR 1.2 support is enabled!
[    14.920] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    14.920] (==) fglrx(0): Center Mode is disabled 
[    14.920] (II) Loading sub module "fb"
[    14.920] (II) LoadModule: "fb"
[    14.921] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.939] (II) Module fb: vendor="X.Org Foundation"
[    14.939]     compiled for 1.13.0, module version = 1.0.0
[    14.939]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.939] (II) Loading sub module "ddc"
[    14.939] (II) LoadModule: "ddc"
[    14.939] (II) Module "ddc" already built-in
[    15.119] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    15.119] (II) fglrx(0): Output DFP2 has no monitor section
[    15.119] (II) fglrx(0): Output DFP3 has no monitor section
[    15.119] (II) fglrx(0): Output DFP4 has no monitor section
[    15.119] (II) fglrx(0): Output CRT1 has no monitor section
[    15.119] (II) fglrx(0): Output CRT2 has no monitor section
[    15.119] (II) Loading sub module "ddc"
[    15.119] (II) LoadModule: "ddc"
[    15.119] (II) Module "ddc" already built-in
[    15.119] (II) fglrx(0): Connected Display0: DFP3
[    15.119] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    15.119] (II) fglrx(0): Connected Display1: CRT1
[    15.119] (II) fglrx(0):  Display1: Failed to get EDID information. 
[    15.120] (II) fglrx(0): EDID for output DFP1
[    15.120] (II) fglrx(0): EDID for output DFP2
[    15.120] (II) fglrx(0): EDID for output DFP3
[    15.120] (II) fglrx(0): Manufacturer: SAM  Model: 589  Serial#: 1263088180
[    15.120] (II) fglrx(0): Year: 2009  Week: 31
[    15.120] (II) fglrx(0): EDID Version: 1.3
[    15.120] (II) fglrx(0): Digital Display Input
[    15.120] (II) fglrx(0): Max Image Size [cm]: horiz.: 52  vert.: 29
[    15.120] (II) fglrx(0): Gamma: 2.20
[    15.120] (II) fglrx(0): DPMS capabilities: Off
[    15.120] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.120] (II) fglrx(0): First detailed timing is preferred mode
[    15.120] (II) fglrx(0): redX: 0.649 redY: 0.338   greenX: 0.289 greenY: 0.609
[    15.120] (II) fglrx(0): blueX: 0.146 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    15.120] (II) fglrx(0): Supported established timings:
[    15.120] (II) fglrx(0): 640x480@60Hz
[    15.120] (II) fglrx(0): 800x600@56Hz
[    15.120] (II) fglrx(0): 800x600@60Hz
[    15.120] (II) fglrx(0): 1024x768@60Hz
[    15.120] (II) fglrx(0): Manufacturer's mask: 0
[    15.120] (II) fglrx(0): Supported standard timings:
[    15.120] (II) fglrx(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.120] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.120] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.120] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.120] (II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    15.120] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.120] (II) fglrx(0): Supported detailed timing:
[    15.120] (II) fglrx(0): clock: 148.5 MHz   Image Size:  521 x 293 mm
[    15.120] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.120] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.120] (II) fglrx(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[    15.120] (II) fglrx(0): Monitor name: SyncMaster
[    15.120] (II) fglrx(0): Serial No: H9XS707106
[    15.120] (II) fglrx(0): Supported detailed timing:
[    15.120] (II) fglrx(0): clock: 148.5 MHz   Image Size:  521 x 293 mm
[    15.120] (II) fglrx(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    15.120] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.120] (II) fglrx(0): Supported detailed timing:
[    15.120] (II) fglrx(0): clock: 74.2 MHz   Image Size:  521 x 293 mm
[    15.120] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    15.120] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    15.120] (II) fglrx(0): Supported detailed timing:
[    15.120] (II) fglrx(0): clock: 74.2 MHz   Image Size:  521 x 293 mm
[    15.120] (II) fglrx(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    15.120] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    15.120] (II) fglrx(0): Supported detailed timing:
[    15.120] (II) fglrx(0): clock: 27.0 MHz   Image Size:  521 x 293 mm
[    15.120] (II) fglrx(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    15.120] (II) fglrx(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    15.120] (II) fglrx(0): Supported detailed timing:
[    15.120] (II) fglrx(0): clock: 27.0 MHz   Image Size:  521 x 293 mm
[    15.120] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    15.120] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    15.120] (II) fglrx(0): Number of EDID sections to follow: 1
[    15.120] (II) fglrx(0): EDID (in hex):
[    15.120] (II) fglrx(0):     00ffffffffffff004c2d89053432494b
[    15.120] (II) fglrx(0):     1f13010380341d782a6041a6564a9c25
[    15.120] (II) fglrx(0):     1250542308008100814081809500a940
[    15.120] (II) fglrx(0):     b30001010101023a801871382d40582c
[    15.120] (II) fglrx(0):     450009252100001e000000fd00383c1e
[    15.120] (II) fglrx(0):     5111000a202020202020000000fc0053
[    15.120] (II) fglrx(0):     796e634d61737465720a2020000000ff
[    15.120] (II) fglrx(0):     00483958533730373130360a20200186
[    15.120] (II) fglrx(0): Printing probed modes for output DFP3
[    15.120] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    15.120] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    15.120] (II) fglrx(0): Modeline "1776x1000"x50.0  148.50  1776 2304 2348 2640  1000 1004 1009 1125 +hsync +vsync (56.2 kHz ez)
[    15.120] (II) fglrx(0): Modeline "1680x1050"x50.0  148.50  1680 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    15.120] (II) fglrx(0): Modeline "1400x1050"x60.0  162.00  1400 1664 1856 2160  1050 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    15.120] (II) fglrx(0): Modeline "1400x1050"x50.0  148.50  1400 2448 2492 2640  1050 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1600x900"x60.0  162.00  1600 1664 1856 2160  900 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    15.120] (II) fglrx(0): Modeline "1600x900"x50.0  148.50  1600 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1360x1024"x60.0  162.00  1360 1664 1856 2160  1024 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    15.120] (II) fglrx(0): Modeline "1360x1024"x50.0  148.50  1360 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1280x1024"x50.0  148.50  1280 2448 2492 2640  1024 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    15.120] (II) fglrx(0): Modeline "1440x900"x50.0  148.50  1440 2448 2492 2640  900 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    15.120] (II) fglrx(0): Modeline "1280x960"x50.0  148.50  1280 2448 2492 2640  960 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    15.120] (II) fglrx(0): Modeline "1280x800"x50.0  148.50  1280 2448 2492 2640  800 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.120] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    15.120] (II) fglrx(0): Modeline "1280x768"x50.0  148.50  1280 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    15.121] (II) fglrx(0): Modeline "1024x768"x50.0  148.50  1024 2448 2492 2640  768 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.121] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    15.121] (II) fglrx(0): Modeline "1152x648"x50.0   74.25  1152 1592 1632 1980  648 653 658 750 +hsync +vsync (37.5 kHz ez)
[    15.121] (II) fglrx(0): Modeline "800x600"x50.0  148.50  800 2448 2492 2640  600 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.121] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    15.121] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    15.121] (II) fglrx(0): Modeline "720x576"x60.0  148.50  720 2008 2052 2200  576 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    15.121] (II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    15.121] (II) fglrx(0): Modeline "720x480"x50.0  148.50  720 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.121] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    15.121] (II) fglrx(0): Modeline "640x480"x50.0  148.50  640 2448 2492 2640  480 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    15.121] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    15.121] (II) fglrx(0): EDID for output DFP4
[    15.121] (II) fglrx(0): EDID for output CRT1
[    15.121] (II) fglrx(0): Manufacturer: BNQ  Model: 7d01  Serial#: 21573
[    15.121] (II) fglrx(0): Year: 2010  Week: 12
[    15.121] (II) fglrx(0): EDID Version: 1.3
[    15.121] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    15.121] (II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
[    15.121] (II) fglrx(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    15.121] (II) fglrx(0): Gamma: 2.20
[    15.121] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    15.121] (II) fglrx(0): Default color space is primary color space
[    15.121] (II) fglrx(0): First detailed timing is preferred mode
[    15.121] (II) fglrx(0): redX: 0.638 redY: 0.348   greenX: 0.334 greenY: 0.608
[    15.121] (II) fglrx(0): blueX: 0.150 blueY: 0.057   whiteX: 0.312 whiteY: 0.329
[    15.121] (II) fglrx(0): Supported established timings:
[    15.121] (II) fglrx(0): 720x400@70Hz
[    15.121] (II) fglrx(0): 640x480@60Hz
[    15.121] (II) fglrx(0): 640x480@75Hz
[    15.121] (II) fglrx(0): 800x600@60Hz
[    15.121] (II) fglrx(0): 800x600@75Hz
[    15.121] (II) fglrx(0): 832x624@75Hz
[    15.121] (II) fglrx(0): 1024x768@60Hz
[    15.121] (II) fglrx(0): 1024x768@75Hz
[    15.121] (II) fglrx(0): 1280x1024@75Hz
[    15.121] (II) fglrx(0): 1152x864@75Hz
[    15.121] (II) fglrx(0): Manufacturer's mask: 0
[    15.121] (II) fglrx(0): Supported standard timings:
[    15.121] (II) fglrx(0): #0: hsize: 1024  vsize 576  refresh: 60  vid: 49249
[    15.121] (II) fglrx(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.121] (II) fglrx(0): #2: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    15.121] (II) fglrx(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.121] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.121] (II) fglrx(0): #5: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    15.121] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.121] (II) fglrx(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    15.121] (II) fglrx(0): Supported detailed timing:
[    15.121] (II) fglrx(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    15.121] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.121] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.121] (II) fglrx(0): Serial No: 83A06738SL0
[    15.121] (II) fglrx(0): Ranges: V min: 50 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 175 MHz
[    15.121] (II) fglrx(0): Monitor name: BenQ V2400Eco
[    15.121] (II) fglrx(0): EDID (in hex):
[    15.121] (II) fglrx(0):     00ffffffffffff0009d1017d45540000
[    15.121] (II) fglrx(0):     0c1401030e351e782e4ba1a359559b26
[    15.121] (II) fglrx(0):     0e5054a56b8061c0810081c081408180
[    15.121] (II) fglrx(0):     a9c0b300d1c0023a801871382d40582c
[    15.121] (II) fglrx(0):     4500132b2100001e000000ff00383341
[    15.121] (II) fglrx(0):     3036373338534c300a20000000fd0032
[    15.121] (II) fglrx(0):     4c185311000a202020202020000000fc
[    15.121] (II) fglrx(0):     0042656e5120563234303045636f0006
[    15.121] (II) fglrx(0): Printing probed modes for output CRT1
[    15.121] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    15.121] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    15.121] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    15.121] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[    15.121] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    15.121] (II) fglrx(0): Modeline "1440x900"x60.0  108.00  1440 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz e)
[    15.121] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    15.121] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    15.121] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    15.121] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    15.121] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    15.121] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    15.121] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    15.121] (II) fglrx(0): EDID for output CRT2
[    15.121] (II) fglrx(0): Output DFP1 disconnected
[    15.121] (II) fglrx(0): Output DFP2 disconnected
[    15.121] (II) fglrx(0): Output DFP3 connected
[    15.121] (II) fglrx(0): Output DFP4 disconnected
[    15.121] (II) fglrx(0): Output CRT1 connected
[    15.121] (II) fglrx(0): Output CRT2 disconnected
[    15.121] (II) fglrx(0): Using exact sizes for initial modes
[    15.121] (II) fglrx(0): Output DFP3 using initial mode 1920x1080
[    15.121] (II) fglrx(0): Output CRT1 using initial mode 1920x1080
[    15.121] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.121] (II) fglrx(0): DPI set to (96, 96)
[    15.121] (II) fglrx(0): Eyefinity capable adapter detected.
[    15.121] (II) fglrx(0): Adapter ATI Radeon HD 5700 Series  has 5 configurable heads and 2 displays connected.
[    15.121] (==) fglrx(0):  PseudoColor visuals disabled
[    15.121] (II) Loading sub module "ramdac"
[    15.121] (II) LoadModule: "ramdac"
[    15.121] (II) Module "ramdac" already built-in
[    15.121] (==) fglrx(0): NoDRI = NO
[    15.121] (==) fglrx(0): Capabilities: 0x00000000
[    15.121] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    15.121] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    15.121] (==) fglrx(0): UseFastTLS=0
[    15.121] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    15.121] (--) Depth 24 pixmap format is 32 bpp
[    15.125] Loading extension ATIFGLRXDRI
[    15.125] (II) fglrx(0): doing swlDriScreenInit
[    15.125] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    15.125] ukiDynamicMajor: found major device number 250
[    15.125] ukiDynamicMajor: found major device number 250
[    15.125] ukiDynamicMajor: found major device number 250
[    15.125] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.125] ukiOpenDevice: node name is /dev/ati/card0
[    15.125] ukiOpenDevice: open result is 14, (OK)
[    15.125] ukiOpenByBusid: ukiOpenMinor returns 14
[    15.125] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.125] (II) fglrx(0): [uki] DRM interface version 1.0
[    15.125] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    15.125] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    15.125] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f2edd9f2000
[    15.125] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    15.125] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    15.125] (II) fglrx(0): swlDriScreenInit done
[    15.125] (II) fglrx(0): Kernel Module Version Information:
[    15.125] (II) fglrx(0):     Name: fglrx
[    15.125] (II) fglrx(0):     Version: 9.1.11
[    15.125] (II) fglrx(0):     Date: Dec 19 2012
[    15.125] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    15.125] (II) fglrx(0): Kernel Module version matches driver.
[    15.125] (II) fglrx(0): Kernel Module Build Time Information:
[    15.125] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.5.0-24-generic
[    15.125] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    15.125] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    15.125] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    15.125] (II) fglrx(0): [uki] register handle = 0x00004000
[    15.127] (II) fglrx(0): DRI initialization successfull
[    15.138] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    15.144] (==) fglrx(0): Backing store disabled
[    15.144] Loading extension FGLRXEXTENSION
[    15.144] (**) fglrx(0): DPMS enabled
[    15.144] (II) fglrx(0): Initialized in-driver Xinerama extension
[    15.144] (**) fglrx(0): Textured Video is enabled.
[    15.144] (II) LoadModule: "glesx"
[    15.144] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    15.220] (II) Module glesx: vendor="X.Org Foundation"
[    15.220]     compiled for 1.4.99.906, module version = 1.0.0
[    15.220] Loading extension GLESX
[    15.220] (II) fglrx(0): GLESX enableFlags = 592
[    15.222] (II) fglrx(0): GLESX is enabled
[    15.222] (II) LoadModule: "amdxmm"
[    15.222] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    15.233] (II) Module amdxmm: vendor="X.Org Foundation"
[    15.233]     compiled for 1.4.99.906, module version = 2.0.0
[    15.252] Loading extension AMDXVOPL
[    15.252] Loading extension AMDXVBA
[    15.264] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    15.265] (II) fglrx(0): Enable composite support successfully
[    15.265] (WW) fglrx(0): Option "VendorName" is not used
[    15.265] (WW) fglrx(0): Option "ModelName" is not used
[    15.265] (II) fglrx(0): X context handle = 0x1
[    15.265] (II) fglrx(0): [DRI] installation complete
[    15.265] (==) fglrx(0): Silken mouse enabled
[    15.265] (==) fglrx(0): Using HW cursor of display infrastructure!
[    15.265] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.342] (--) RandR disabled
[    15.345] ukiDynamicMajor: found major device number 250
[    15.345] ukiDynamicMajor: found major device number 250
[    15.345] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.345] ukiOpenDevice: node name is /dev/ati/card0
[    15.345] ukiOpenDevice: open result is 15, (OK)
[    15.345] ukiOpenByBusid: ukiOpenMinor returns 15
[    15.345] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.696] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    16.761] (II) fglrx(0): Setting screen physical size to 508 x 285
[    16.862] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.871] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.871] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.871] (II) LoadModule: "evdev"
[    16.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.893] (II) Module evdev: vendor="X.Org Foundation"
[    16.893]     compiled for 1.13.0, module version = 2.7.3
[    16.893]     Module class: X.Org XInput Driver
[    16.893]     ABI class: X.Org XInput driver, version 18.0
[    16.893] (II) Using input driver 'evdev' for 'Power Button'
[    16.893] (**) Power Button: always reports core events
[    16.893] (**) evdev: Power Button: Device: "/dev/input/event1"
[    16.894] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.894] (--) evdev: Power Button: Found keys
[    16.894] (II) evdev: Power Button: Configuring as keyboard
[    16.894] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.894] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.894] (**) Option "xkb_rules" "evdev"
[    16.894] (**) Option "xkb_model" "pc105"
[    16.894] (**) Option "xkb_layout" "de"
[    16.894] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    16.895] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.895] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.895] (II) Using input driver 'evdev' for 'Power Button'
[    16.895] (**) Power Button: always reports core events
[    16.895] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.895] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.895] (--) evdev: Power Button: Found keys
[    16.895] (II) evdev: Power Button: Configuring as keyboard
[    16.895] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    16.895] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    16.895] (**) Option "xkb_rules" "evdev"
[    16.895] (**) Option "xkb_model" "pc105"
[    16.895] (**) Option "xkb_layout" "de"
[    16.895] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[    16.895] (II) No input driver specified, ignoring this device.
[    16.895] (II) This device may have been added with another device file.
[    16.895] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event5)
[    16.895] (II) No input driver specified, ignoring this device.
[    16.895] (II) This device may have been added with another device file.
[    16.896] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[    16.896] (II) No input driver specified, ignoring this device.
[    16.896] (II) This device may have been added with another device file.
[    16.896] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    16.896] (II) No input driver specified, ignoring this device.
[    16.896] (II) This device may have been added with another device file.
[    16.896] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event8)
[    16.896] (II) No input driver specified, ignoring this device.
[    16.896] (II) This device may have been added with another device file.
[    16.896] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event9)
[    16.896] (II) No input driver specified, ignoring this device.
[    16.896] (II) This device may have been added with another device file.
[    16.896] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:2007 (/dev/input/event2)
[    16.896] (**) Logitech Unifying Device. Wireless PID:2007: Applying InputClass "evdev keyboard catchall"
[    16.896] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:2007'
[    16.896] (**) Logitech Unifying Device. Wireless PID:2007: always reports core events
[    16.896] (**) evdev: Logitech Unifying Device. Wireless PID:2007: Device: "/dev/input/event2"
[    16.896] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Vendor 0x46d Product 0xc52b
[    16.896] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found 1 mouse buttons
[    16.896] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found scroll wheel(s)
[    16.896] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found relative axes
[    16.896] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Forcing relative x/y axes to exist.
[    16.896] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found absolute axes
[    16.896] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Forcing absolute x/y axes to exist.
[    16.896] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found keys
[    16.896] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Configuring as mouse
[    16.896] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Configuring as keyboard
[    16.896] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Adding scrollwheel support
[    16.896] (**) evdev: Logitech Unifying Device. Wireless PID:2007: YAxisMapping: buttons 4 and 5
[    16.896] (**) evdev: Logitech Unifying Device. Wireless PID:2007: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.896] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2/0003:046D:C52B.0003/input/input2/event2"
[    16.896] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:2007" (type: KEYBOARD, id 8)
[    16.896] (**) Option "xkb_rules" "evdev"
[    16.896] (**) Option "xkb_model" "pc105"
[    16.896] (**) Option "xkb_layout" "de"
[    16.896] (II) evdev: Logitech Unifying Device. Wireless PID:2007: initialized for relative axes.
[    16.896] (WW) evdev: Logitech Unifying Device. Wireless PID:2007: ignoring absolute axes.
[    16.896] (**) Logitech Unifying Device. Wireless PID:2007: (accel) keeping acceleration scheme 1
[    16.896] (**) Logitech Unifying Device. Wireless PID:2007: (accel) acceleration profile 0
[    16.896] (**) Logitech Unifying Device. Wireless PID:2007: (accel) acceleration factor: 2.000
[    16.896] (**) Logitech Unifying Device. Wireless PID:2007: (accel) acceleration threshold: 4
[    16.897] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1025 (/dev/input/event3)
[    16.897] (**) Logitech Unifying Device. Wireless PID:1025: Applying InputClass "evdev pointer catchall"
[    16.897] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:1025'
[    16.897] (**) Logitech Unifying Device. Wireless PID:1025: always reports core events
[    16.897] (**) evdev: Logitech Unifying Device. Wireless PID:1025: Device: "/dev/input/event3"
[    16.897] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Vendor 0x46d Product 0xc52b
[    16.897] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found 20 mouse buttons
[    16.897] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found scroll wheel(s)
[    16.897] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found relative axes
[    16.897] (--) evdev: Logitech Unifying Device. Wireless PID:1025: Found x and y relative axes
[    16.897] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Configuring as mouse
[    16.897] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Adding scrollwheel support
[    16.897] (**) evdev: Logitech Unifying Device. Wireless PID:1025: YAxisMapping: buttons 4 and 5
[    16.897] (**) evdev: Logitech Unifying Device. Wireless PID:1025: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.897] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2/0003:046D:C52B.0003/input/input3/event3"
[    16.897] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:1025" (type: MOUSE, id 9)
[    16.897] (II) evdev: Logitech Unifying Device. Wireless PID:1025: initialized for relative axes.
[    16.897] (**) Logitech Unifying Device. Wireless PID:1025: (accel) keeping acceleration scheme 1
[    16.897] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration profile 0
[    16.897] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration factor: 2.000
[    16.897] (**) Logitech Unifying Device. Wireless PID:1025: (accel) acceleration threshold: 4
[    16.897] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:1025 (/dev/input/mouse0)
[    16.897] (II) No input driver specified, ignoring this device.
[    16.897] (II) This device may have been added with another device file.
[    16.897] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
[    16.897] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    16.897] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    16.897] (**) Eee PC WMI hotkeys: always reports core events
[    16.897] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event4"
[    16.897] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    16.897] (--) evdev: Eee PC WMI hotkeys: Found keys
[    16.897] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    16.897] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input4/event4"
[    16.897] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[    16.897] (**) Option "xkb_rules" "evdev"
[    16.897] (**) Option "xkb_model" "pc105"
[    16.897] (**) Option "xkb_layout" "de"
[    16.921] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    33.022] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    33.022] (II) fglrx(0): Using EDID range info for horizontal sync
[    33.022] (II) fglrx(0): Using EDID range info for vertical refresh
[    33.022] (II) fglrx(0): Printing DDC gathered Modelines:
[    33.022] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    33.022] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    33.022] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    33.022] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    33.022] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    33.022] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    33.022] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    33.022] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    33.022] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    33.022] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    33.022] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    33.022] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    33.022] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    33.022] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    33.022] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    33.022] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    33.022] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    33.022] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    33.022] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    33.035] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    33.035] (II) fglrx(0): Using hsync ranges from config file
[    33.035] (II) fglrx(0): Using vrefresh ranges from config file
[    33.035] (II) fglrx(0): Printing DDC gathered Modelines:
[    33.035] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    33.035] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    33.035] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    33.035] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    33.035] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    33.035] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    33.035] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    33.035] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    33.035] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    33.035] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    33.035] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    33.035] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    33.035] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    33.035] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    33.035] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    33.035] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    33.035] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    33.035] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    33.035] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    33.048] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    33.048] (II) fglrx(0): Using hsync ranges from config file
[    33.048] (II) fglrx(0): Using vrefresh ranges from config file
[    33.048] (II) fglrx(0): Printing DDC gathered Modelines:
[    33.048] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    33.048] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    33.048] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    33.048] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    33.048] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    33.048] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    33.048] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    33.048] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    33.048] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    33.048] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    33.048] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    33.048] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    33.048] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    33.048] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    33.048] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    33.048] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    33.048] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    33.048] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    33.048] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    34.978] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    34.978] (II) fglrx(0): Using hsync ranges from config file
[    34.978] (II) fglrx(0): Using vrefresh ranges from config file
[    34.978] (II) fglrx(0): Printing DDC gathered Modelines:
[    34.978] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    34.978] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    34.978] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    34.978] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    34.978] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    34.978] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    34.978] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    34.978] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    34.978] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    34.978] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    34.978] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    34.978] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    34.978] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    34.978] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    34.978] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    34.978] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    34.978] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    34.978] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    34.978] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    35.635] (II) XKB: reuse xkmfile /var/lib/xkb/server-A854226913527907A36C4D2DAF9AFA87EAB7AF64.xkm
[    37.376] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    37.376] (II) fglrx(0): Using hsync ranges from config file
[    37.376] (II) fglrx(0): Using vrefresh ranges from config file
[    37.376] (II) fglrx(0): Printing DDC gathered Modelines:
[    37.376] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    37.376] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.376] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.377] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.377] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.377] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    37.377] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    37.377] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.377] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    37.377] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.377] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    37.377] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    37.377] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    37.377] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    37.377] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    37.377] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    37.377] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    37.377] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    37.377] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    46.589] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    46.589] (II) fglrx(0): Using hsync ranges from config file
[    46.589] (II) fglrx(0): Using vrefresh ranges from config file
[    46.589] (II) fglrx(0): Printing DDC gathered Modelines:
[    46.589] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    46.589] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    46.589] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    46.589] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    46.589] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    46.589] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    46.589] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    46.589] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    46.589] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    46.589] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    46.589] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    46.589] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    46.589] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    46.589] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    46.589] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    46.589] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    46.589] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    46.589] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    46.589] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    48.696] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    48.696] (II) fglrx(0): Using hsync ranges from config file
[    48.696] (II) fglrx(0): Using vrefresh ranges from config file
[    48.696] (II) fglrx(0): Printing DDC gathered Modelines:
[    48.696] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    48.696] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    48.696] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    48.696] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    48.696] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    48.696] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    48.696] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    48.696] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    48.696] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    48.696] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    48.696] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    48.696] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    48.696] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    48.696] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    48.696] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    48.696] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    48.696] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    48.696] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    48.696] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    49.536] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    49.536] (II) fglrx(0): Using hsync ranges from config file
[    49.536] (II) fglrx(0): Using vrefresh ranges from config file
[    49.536] (II) fglrx(0): Printing DDC gathered Modelines:
[    49.536] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.536] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.536] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    49.536] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.536] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.536] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    49.536] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    49.536] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.536] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    49.536] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    49.536] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.536] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    49.536] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    49.536] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    49.536] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    49.536] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.536] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    49.536] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    49.536] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    64.532] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[    64.532] (II) fglrx(0): Using hsync ranges from config file
[    64.532] (II) fglrx(0): Using vrefresh ranges from config file
[    64.532] (II) fglrx(0): Printing DDC gathered Modelines:
[    64.532] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    64.532] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    64.532] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    64.532] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    64.532] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    64.532] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    64.532] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    64.532] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    64.532] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    64.532] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    64.532] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    64.532] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[    64.532] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    64.532] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    64.532] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    64.532] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    64.532] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    64.532] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    64.532] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   202.708] (II) fglrx(0): EDID vendor "BNQ", prod id 32001
[   202.708] (II) fglrx(0): Using hsync ranges from config file
[   202.708] (II) fglrx(0): Using vrefresh ranges from config file
[   202.709] (II) fglrx(0): Printing DDC gathered Modelines:
[   202.709] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   202.709] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   202.709] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   202.709] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   202.709] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   202.709] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   202.709] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   202.709] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   202.709] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   202.709] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   202.709] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   202.709] (II) fglrx(0): Modeline "1024x576"x60.0   46.99  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz e)
[   202.709] (II) fglrx(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[   202.709] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   202.709] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   202.709] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   202.709] (II) fglrx(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   202.709] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   202.709] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)

```glxinfo
```

name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_fbconfig_float, GLX_AMD_gpu_association
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series 
OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012
OpenGL shading language version string: 4.20
OpenGL extensions:
    GL_AMDX_debug_output, GL_AMDX_vertex_shader_tessellator, 
    GL_AMD_conservative_depth, GL_AMD_debug_output, 
    GL_AMD_depth_clamp_separate, GL_AMD_draw_buffers_blend, 
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_AMD_performance_monitor, GL_AMD_pinned_memory, 
    GL_AMD_query_buffer_object, GL_AMD_sample_positions, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trace, GL_AMD_texture_cube_map_array, 
    GL_AMD_texture_texture4, GL_AMD_transform_feedback3_lines_triangles, 
    GL_AMD_vertex_shader_layer, GL_AMD_vertex_shader_tessellator, 
    GL_AMD_vertex_shader_viewport_index, GL_ARB_ES2_compatibility, 
    GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_program_binary, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_objects, 
    GL_ARB_shader_precision, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_bptc, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_snorm, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, GL_EXT_texture_array, 
    GL_EXT_texture_buffer_object, GL_EXT_texture_compression_bptc, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent, 
    GL_EXT_texture_snorm, GL_EXT_texture_storage, GL_EXT_texture_swizzle, 
    GL_EXT_timer_query, GL_EXT_transform_feedback, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_explicit_multisample, GL_NV_float_buffer, GL_NV_half_float, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_SUN_multi_draw_arrays, GL_WIN_swap_hint

81 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0ce 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon

91 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0ce 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon
0x0ce 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 Ncon
0x0ce 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0ce 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0ce 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 Ncon
0x0ce  0 tc  0 128  0    y .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0ce  0 tc  0 128  0    . .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0ce  0 tc  0  64  0    y .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0ce  0 tc  0  64  0    . .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0ce  0 tc  0  32  0    y .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ce  0 tc  0  32  0    . .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None

```

---

### Post by Yellow Pasque on 2013-02-14
Have you tried turning off vsync in the catalyst control center?

---

### Post by wattyka on 2013-02-15
> **Temüjin said:**
> Have you tried turning off vsync in the catalyst control center?

Good idea. I tried that (even with reboot), but that doesn't help either.

---

### Post by pepemsk on 2013-03-05
Did you try this ?
Go to System Settings -> Desktop Effects -> tab Advanced
In Compositing type, choose OpenGL.

This helped me like a charm. My configuration is Linux Mint 14 KDE 64-bit, using AMD Catalyst driver (right now it's 13.2.beta7, but I guess this would work also with 13.1).

---

