---
title: "What is the really problem with fglrx-drivers on Intrepid?"
date: 2009-03-12
forum: Hardware
---

### Post by Vantskruv on 2009-03-12
Sorry for creating a new thread about this, but I've searched and haven't found any answers.

I wasted 3 lifehours yesterday trying to get the new 9.2 drivers to work on my Ubuntu Intrepid with the X1950XTX card.

Temporily I'll give up and need to ask you some questions. Is it something I've done wrong? Or doesn't the new ATI work on Intrepid or the X1950XTX card?

What is my problem then! A black screen appears after the starting process. The computer tries three times to get the screen work, after that the computer locks up with a weird black screen with some red stripes on it (different appearing after every restart).

How did I make the installation? I've followed this guide, [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide), using method 2 described. I've been avoiding installing the drivers with the ATI:s graphical interface, because I'm afraid not to be able to go revert, it feels more safe to install via the package manager. I've uninstalled the Xserver-xorg-video-radeon and the fglrx-modaliases packages, I've added "fglrx" to DISABLED_MODULES in the linux-restricted-modules-common file, I've added a # before the the row with fgrlx in the blacklist-local file.

The only way to get rid of the black-screen after startup is to uninstall the xorg-driver-fglrx in failsafe mode, changing fglrx to vesa in the xorg.conf doesn't help.

I haven't found any errors in the Xorg.0.log file, only warnings (I've deleted some lines in the file that did not seem so important, because of the forum charactar limit):

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux johannes-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
*borttaget*
(II) Module ABI versions:
   X.Org ANSI C Emulation: 0.4
   X.Org Video Driver: 4.1
   X.Org XInput driver : 2.1
   X.Org Server Extension : 1.1
   X.Org Font Renderer : 0.6

(--) PCI:*(0@1:0:0) ATI Technologies Inc R580 [Radeon X1900] rev 0, Mem @ 0xd0000000/0, 0xc7fe0000/0, I/O @ 0x0000d000/0, BIOS @ 0x????????/131072
(--) PCI: (0@1:0:1) ATI Technologies Inc unknown chipset (0x7260) rev 0, Mem @ 0xc7ff0000/0


(WW) Falling back to old probe method for fglrx
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(II) AMD ASIC control file status: R2 S1 B324 N324 T323
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7240) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
   compiled for 1.5.2, module version = 0.1.0
   ABI class: X.Org Video Driver, version 4.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "UseFastTLS" "1"
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"

*borttaget*

(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [pcie] 524288 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(0): UseFastTLS=1
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Interrupt handler installed at IRQ 18.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x26000
(II) fglrx(0): [drm] mapped SAREA 0x26000 to 0xb7a30000
(II) fglrx(0): [drm] framebuffer handle = 0x27000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.58.2
(II) fglrx(0):     Date: Feb  4 2009
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.27-11-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00028000
(II) fglrx(0): Adjust primary surface width to 0x500 for rotation!
(II) fglrx(0): Adjust desktop virtualY to 0x500! for rotation
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1280) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2000
(NI) fglrx(0): ASIC Family ID/Name:60/R520 

(NI) fglrx(0): ASIC Rev ID/Name:28/Not RV6xx family Device 

(NI) fglrx(0): ASIC Device ID/Name:0X7240/Not RV6xx family Device 

(NI) fglrx(0): CPLIB is initialized.

(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"

(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
   compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
   Screen to screen bit blits
   Solid filled rectangles
   Solid Horizontal and Vertical Lines
   Driver provided ScreenToScreenBitBlt replacement
   Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"

(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
   compiled for 1.4.99.906, module version = 1.0.0
   ABI class: X.Org Server Extension, version 1.1
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(==) fglrx(0): Using software cursor
(II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) fglrx(0): atiddxDisplayScreenLoadPalette: numColors: 256
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23 //osv till 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Setting screen physical size to 376 x 301
(II) fglrx(0): Shutdown CMMQS
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x26000 at 0xb7a30000
```

---

### Post by Vantskruv on 2009-03-12
My xorg.conf file:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection
```

---

