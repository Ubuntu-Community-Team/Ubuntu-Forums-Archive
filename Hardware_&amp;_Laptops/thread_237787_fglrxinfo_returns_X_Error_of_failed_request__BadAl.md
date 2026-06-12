---
title: "fglrxinfo returns: X Error of failed request:  BadAlloc ..."
date: 2006-08-16
forum: Hardware &amp; Laptops
---

### Post by kolach on 2006-08-16
Hi everybody!

My system is Ubuntu Dapper 6.06 64bit edition with 2.6.17.4 kernel
My Laptop is Acer Aspire 5014WLMi with ATI Mobiliti Radeon X700

I' trying to install ati 8.27.10 driver following this HOWTO
[http://www.ubuntuforums.org/showthread.php?t=204910&highlight=1280x800]("http://www.ubuntuforums.org/showthread.php?t=204910&highlight=1280x800")

After I've completed it everything seems ok 
2D grathics works, and my screen resolution was automaticaly adjusted to 1280x800
**but 3d doesn't work!!!**

When I run

**fglrxinfo**

it returns

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  19
  Current serial number in output stream:  20
```

and

**dmesg | grep fglrx and /var/log/Xorg.0.log**

```
/var/log/Xorg.0.log:(II) LoadModule: "fglrx"
/var/log/Xorg.0.log:(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
/var/log/Xorg.0.log:(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
/var/log/Xorg.0.log:(II) fglrx(0): pEnt->device->identifier=0x6cfbf0
/var/log/Xorg.0.log:(II) fglrx(0): === [R200PreInit] === begin, [s]
/var/log/Xorg.0.log:(II) fglrx(0): PCI bus 1 card 0 func 0
/var/log/Xorg.0.log:(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
/var/log/Xorg.0.log:(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
/var/log/Xorg.0.log:(==) fglrx(0): Default visual is TrueColor
/var/log/Xorg.0.log:(**) fglrx(0): Option "OpenGLOverlay" "off"
/var/log/Xorg.0.log:(**) fglrx(0): Option "VideoOverlay" "on"
/var/log/Xorg.0.log:(**) fglrx(0): Option "DPMS" "true"
/var/log/Xorg.0.log:(==) fglrx(0): RGB weight 888
/var/log/Xorg.0.log:(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
/var/log/Xorg.0.log:(==) fglrx(0): Gamma Correction for I is 0x06419064
/var/log/Xorg.0.log:(==) fglrx(0): Gamma Correction for II is 0x06419064
/var/log/Xorg.0.log:(==) fglrx(0): Buffer Tiling is ON
/var/log/Xorg.0.log:(II) fglrx(0): Primary V_BIOS segment is: 0xc000
/var/log/Xorg.0.log:(--) fglrx(0): Chipset: "MOBILITY RADEON X700 (M26 5653)" (Chipset = 0x5653)
/var/log/Xorg.0.log:(--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0079)
/var/log/Xorg.0.log:(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
/var/log/Xorg.0.log:(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
/var/log/Xorg.0.log:(--) fglrx(0): MMIO registers at 0xc0100000
/var/log/Xorg.0.log:(==) fglrx(0): ROM-BIOS at 0x000c0000
/var/log/Xorg.0.log:(II) fglrx(0): VESA BIOS detected
/var/log/Xorg.0.log:(II) fglrx(0): VESA VBE Version 3.0
/var/log/Xorg.0.log:(II) fglrx(0): VESA VBE Total Mem: 16384 kB
/var/log/Xorg.0.log:(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
/var/log/Xorg.0.log:(II) fglrx(0): VESA VBE OEM Software Rev: 9.10
/var/log/Xorg.0.log:(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
/var/log/Xorg.0.log:(II) fglrx(0): VESA VBE OEM Product: M26-P
/var/log/Xorg.0.log:(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
/var/log/Xorg.0.log:(II) Loading sub module "fglrxdrm"
/var/log/Xorg.0.log:(II) LoadModule: "fglrxdrm"
/var/log/Xorg.0.log:(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
/var/log/Xorg.0.log:(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
/var/log/Xorg.0.log:(II) fglrx(0): ATI Video BIOS revision 9 or later detected
/var/log/Xorg.0.log:(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR1
/var/log/Xorg.0.log:(II) fglrx(0): PCIE card detected
/var/log/Xorg.0.log:(WW) fglrx(0): board is an unknown third party board, chipset is supported
/var/log/Xorg.0.log:(II) fglrx(0): Connected Display1: LCD on internal LVDS
/var/log/Xorg.0.log:(II) fglrx(0):  Display1: No EDID information from DDC.
/var/log/Xorg.0.log:(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
/var/log/Xorg.0.log:(II) fglrx(0): Display1 EDID data ---------------------------
/var/log/Xorg.0.log:(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
/var/log/Xorg.0.log:(II) fglrx(0): Year: 1990  Week: 0
/var/log/Xorg.0.log:(II) fglrx(0): EDID Version: 1.3
/var/log/Xorg.0.log:(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
/var/log/Xorg.0.log:(II) fglrx(0): Sync:Serration on. V.Sync Pulse req. if CompSync or SyncOnGreen
/var/log/Xorg.0.log:(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
/var/log/Xorg.0.log:(II) fglrx(0): Gamma: 1.00
/var/log/Xorg.0.log:(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
/var/log/Xorg.0.log:(II) fglrx(0): First detailed timing is preferred mode
/var/log/Xorg.0.log:(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
/var/log/Xorg.0.log:(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
/var/log/Xorg.0.log:(II) fglrx(0): Supported VESA Video Modes:
/var/log/Xorg.0.log:(II) fglrx(0): 640x480@60Hz
/var/log/Xorg.0.log:(II) fglrx(0): 800x600@60Hz
/var/log/Xorg.0.log:(II) fglrx(0): 1024x768@60Hz
/var/log/Xorg.0.log:(II) fglrx(0): Manufacturer's mask: 0
/var/log/Xorg.0.log:(II) fglrx(0): Supported Future Video Modes:
/var/log/Xorg.0.log:(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
/var/log/Xorg.0.log:(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
/var/log/Xorg.0.log:(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
/var/log/Xorg.0.log:(II) fglrx(0): Supported additional Video Mode:
/var/log/Xorg.0.log:(II) fglrx(0): clock: 68.9 MHz   Image Size:  0 x 0 mm
/var/log/Xorg.0.log:(II) fglrx(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1408 h_border: 0
/var/log/Xorg.0.log:(II) fglrx(0): v_active: 800  v_sync: 800  v_sync_end 800 v_blanking: 816 v_border: 0
/var/log/Xorg.0.log:(II) fglrx(0): End of Display1 EDID data --------------------
/var/log/Xorg.0.log:(WW) fglrx(0): Specified desktop setup not supported: 8
/var/log/Xorg.0.log:(II) fglrx(0): Primary Controller - LCD on internal LVDS
/var/log/Xorg.0.log:(II) fglrx(0): Internal Desktop Setting: 0x00000004
/var/log/Xorg.0.log:(II) fglrx(0): POWERplay version 3.  4 power states available:
/var/log/Xorg.0.log:(II) fglrx(0):   1. 358/331MHz @ 60Hz [enable load balancing]
/var/log/Xorg.0.log:(II) fglrx(0):   2. 105/120MHz @ 60Hz [low voltage, enable sleep]
/var/log/Xorg.0.log:(II) fglrx(0):   3. 209/182MHz @ 60Hz [low voltage, enable sleep]
/var/log/Xorg.0.log:(II) fglrx(0):   4. 267/331MHz @ 60Hz [enable sleep, thermal diode mode]
/var/log/Xorg.0.log:(==) fglrx(0): Qbs disabled
/var/log/Xorg.0.log:(==) fglrx(0): FAST_SWAP disabled
/var/log/Xorg.0.log:(==) fglrx(0):  PseudoColor visuals disabled
/var/log/Xorg.0.log:(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
/var/log/Xorg.0.log:(==) fglrx(0): Center Mode is disabled
/var/log/Xorg.0.log:(==) fglrx(0): TMDS coherent mode is enabled
/var/log/Xorg.0.log:(II) fglrx(0): Total of 9 modes found for primary display.
/var/log/Xorg.0.log:(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "1280x800"   68.90  1280 1301 1333 1408  800 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "1024x768"   68.90  1024 1045 1077 1408  768 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "800x600"   68.90  800 821 853 1408  600 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "640x480"   68.90  640 661 693 1408  480 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "640x400"   68.90  640 661 693 1408  400 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "512x384"   68.90  512 533 565 1408  384 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "400x300"   68.90  400 421 453 1408  300 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "320x240"   68.90  320 341 373 1408  240 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "320x200"   68.90  320 341 373 1408  200 804 808 816
/var/log/Xorg.0.log:(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "1280x800"   68.90  1280 1301 1333 1408  800 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "1024x768"   68.90  1024 1045 1077 1408  768 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "800x600"   68.90  800 821 853 1408  600 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "640x480"   68.90  640 661 693 1408  480 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "640x400"   68.90  640 661 693 1408  400 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "512x384"   68.90  512 533 565 1408  384 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "400x300"   68.90  400 421 453 1408  300 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "320x240"   68.90  320 341 373 1408  240 804 808 816
/var/log/Xorg.0.log:(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
/var/log/Xorg.0.log:(II) fglrx(0): Modeline "320x200"   68.90  320 341 373 1408  200 804 808 816
/var/log/Xorg.0.log:(--) fglrx(0): Display dimensions: (400, 300) mm
/var/log/Xorg.0.log:(--) fglrx(0): DPI set to (81, 67)
/var/log/Xorg.0.log:(==) fglrx(0): NoAccel = NO
/var/log/Xorg.0.log:(==) fglrx(0): HPV inactive
/var/log/Xorg.0.log:(==) fglrx(0): FSAA enabled: NO
/var/log/Xorg.0.log:(==) fglrx(0): FSAA Gamma enabled
/var/log/Xorg.0.log:(==) fglrx(0): FSAA Multisample Position is fix
/var/log/Xorg.0.log:(==) fglrx(0): NoDRI = NO
/var/log/Xorg.0.log:(II) Loading sub module "fglrxdrm"
/var/log/Xorg.0.log:(II) LoadModule: "fglrxdrm"
/var/log/Xorg.0.log:(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
/var/log/Xorg.0.log:(II) fglrx(0): Depth moves disabled by default
/var/log/Xorg.0.log:(==) fglrx(0): Capabilities: 0x00000000
/var/log/Xorg.0.log:(==) fglrx(0): CapabilitiesEx: 0x00000000
/var/log/Xorg.0.log:(==) fglrx(0): cpuFlags: 0x4000001f
/var/log/Xorg.0.log:(==) fglrx(0): cpuSpeedMHz: 0x00000898
/var/log/Xorg.0.log:(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
/var/log/Xorg.0.log:(**) fglrx(0): ATI GART size: 128 MB
/var/log/Xorg.0.log:(==) fglrx(0): UseFastTLS=0
/var/log/Xorg.0.log:(==) fglrx(0): BlockSignalsOnLock=1
/var/log/Xorg.0.log:(==) fglrx(0): EnablePrivateBackZ = NO
/var/log/Xorg.0.log:(II) fglrx(0): UMM Bus area:     0xc85e9000 (size=0x079f7000)
/var/log/Xorg.0.log:(II) fglrx(0): UMM area:     0xc85e9000 (size=0x079f7000)
/var/log/Xorg.0.log:(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
/var/log/Xorg.0.log:(II) fglrx(0): detected X.org 7.0.0.0
/var/log/Xorg.0.log:(II) fglrx(0): doing DRIScreenInit
/var/log/Xorg.0.log:(II) fglrx(0): [drm] DRM interface version 1.0
/var/log/Xorg.0.log:(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
/var/log/Xorg.0.log:(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
/var/log/Xorg.0.log:(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x2b19f78bc000
/var/log/Xorg.0.log:(II) fglrx(0): [drm] framebuffer handle = 0x3000
/var/log/Xorg.0.log:(II) fglrx(0): [drm] added 1 reserved context for kernel
/var/log/Xorg.0.log:(II) fglrx(0): DRIScreenInit done
/var/log/Xorg.0.log:(II) fglrx(0): Kernel Module Version Information:
/var/log/Xorg.0.log:(II) fglrx(0):     Name: fglrx
/var/log/Xorg.0.log:(II) fglrx(0):     Version: 8.27.10
/var/log/Xorg.0.log:(II) fglrx(0):     Date: Jul 27 2006
/var/log/Xorg.0.log:(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
/var/log/Xorg.0.log:(II) fglrx(0): Kernel Module version matches driver.
/var/log/Xorg.0.log:(II) fglrx(0): Kernel Module Build Time Information:
/var/log/Xorg.0.log:(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.17.4/var/log/Xorg.0.log:(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
/var/log/Xorg.0.log:(II) fglrx(0):     Build-Kernel __SMP__:            yes
/var/log/Xorg.0.log:(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
/var/log/Xorg.0.log:(II) fglrx(0): [drm] register handle = 0x00004000
/var/log/Xorg.0.log:(II) fglrx(0): [pcie] 131072 kB allocated with handle 0xdeadbeef
/var/log/Xorg.0.log:(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
/var/log/Xorg.0.log:(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
/var/log/Xorg.0.log:(II) fglrx(0): [drm] texture shared area handle = 0x00008000/var/log/Xorg.0.log:(II) fglrx(0): shared FSAAScale=1
/var/log/Xorg.0.log:(II) fglrx(0): DRI initialization successfull!
/var/log/Xorg.0.log:(II) fglrx(0): FBADPhys: 0xc8000000 FBMappedSize: 0x005e9000/var/log/Xorg.0.log:(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
/var/log/Xorg.0.log:(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
/var/log/Xorg.0.log:(==) fglrx(0): Backing store disabled
/var/log/Xorg.0.log:(==) fglrx(0): Silken mouse enabled
/var/log/Xorg.0.log:(**) fglrx(0): DPMS enabled
/var/log/Xorg.0.log:(WW) fglrx(0): Option "VendorName" is not used
/var/log/Xorg.0.log:(WW) fglrx(0): Option "ModelName" is not used
/var/log/Xorg.0.log:(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)/var/log/Xorg.0.log:(II) fglrx(0): Acceleration enabled
/var/log/Xorg.0.log:(II) fglrx(0): X context handle = 0x1
/var/log/Xorg.0.log:(II) fglrx(0): [DRI] installation complete
/var/log/Xorg.0.log:(II) fglrx(0): Direct rendering enabled
/var/log/Xorg.0.log:(==) fglrx(0): Using hardware cursor
/var/log/Xorg.0.log:(II) fglrx(0): Largest offscreen area available: 1280 x 410
/var/log/Xorg.0.log:(II) fglrx(0): Interrupt handler installed at IRQ 50.
/var/log/Xorg.0.log:(II) fglrx(0): Exposed events to the /proc interface


```

and I dont see any errors there.

Any ideas?

---

