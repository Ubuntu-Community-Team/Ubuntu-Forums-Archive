---
title: "dri and xv stopped working"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by mekanix on 2007-03-08
Hi

DRI and (to some extend) xv stopped working today. I've got a new PC with an Intel 945G chipset and have been playing around with it for the last week or so.

I *had* DRI working, had xv working following the instructions here: [http://ubuntuforums.org/showthread.php?t=326864](http://ubuntuforums.org/showthread.php?t=326864)

I just can't figure out what I have done to break the system.

Help!

Here are some log-snippets:

$ dmesg |grep drm
> [17179596.888000] [drm] Initialized drm 1.0.1 20051102
[17179596.892000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179596.912000] [drm:drm_unlock] *ERROR* Process 4349 using kernel context 0
[17179709.064000] [drm:drm_unlock] *ERROR* Process 5172 using kernel context 0

$ dmesg |grep agp
> [17179585.232000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.240000] agpgart: Detected an Intel 945G Chipset.
[17179585.244000] agpgart: Detected 7932K stolen memory.
[17179585.256000] agpgart: AGP aperture is 256M @ 0xd0000000

$ less /var/log/Xorg.0.log |grep drm
> (II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf9d2a000
(II) I810(0): [drm] mapped SAREA 0xf9d2a000 to 0xb7aba000
(II) I810(0): [drm] framebuffer handle = 0xd0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): [drm] Registers = 0xe5000000
(II) I810(0): [drm] ring buffer = 0xd0000000
(II) I810(0): [drm] init sarea width,height = 1680 x 1050 (pitch 1696)
(II) I810(0): [drm] Mapping front buffer
(EE) I810(0): [drm] drmAddMap(front_handle) failed. Disabling DRI
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xf9d2a000 at 0xb7aba000
(EE) I810(0): [drm] drmAddMap(screen mappings) failed. Disabling DRI

$ less /var/log/Xorg.0.log |grep 810
> (II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(**) I810(0): Depth 16, (--) framebuffer bpp 16
(==) I810(0): RGB weight 565
(==) I810(0): Default visual is TrueColor
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)Lakeport-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)Lakeport-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 945G
(--) I810(0): Chipset: "945G"
(--) I810(0): Linear framebuffer at 0xD0000000
(--) I810(0): IO registers at addr 0xE5000000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 238848 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 955388 kB available
(WW) I810(0): VideoRAM reduced to 253952 kByte (page aligned - was 256000)
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)Lakeport-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)Lakeport-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(**) I810(0): VideoRAM: 253952 kByte
(==) I810(0): video overlay key set to 0x83e
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1215
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0):   DFP (digital flat panel)
(II) I810(0): No display size information available for pipe A.
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 253784 kByte
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: PHL  Model: 832  Serial#: 23525
(II) I810(0): Year: 2006  Week: 4
(II) I810(0): EDID Version: 1.3
(II) I810(0): Digital Display Input
(II) I810(0): DFP 1.x compatible TMDS
(II) I810(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: Off; RGB/Color Display
(II) I810(0): Default color space is primary color space
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.640 redY: 0.346   greenX: 0.292 greenY: 0.619
(II) I810(0): blueX: 0.145 blueY: 0.073   whiteX: 0.313 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@56Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): 1152x870@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1152  vsize 864  refresh: 70  vid: 19057
(II) I810(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) I810(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.0 MHz   Image Size:  433 x 271 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) I810(0): Serial No:  VN  023525
(II) I810(0): Monitor name: Philips 200W
(II) I810(0): Ranges: V min: 56  V max: 85 Hz, H min: 30  H max: 93 kHz, PixClock max 170 MHz
(--) I810(0): A non-CRT device is attached to pipe A.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0):   HorizSync 30-93
(II) I810(0):   VertRefresh 56-85
(WW) I810(0): config file hsync range 28-51kHz not within DDC hsync range 30-93kHz
(WW) I810(0): config file vrefresh range 43-60Hz not within DDC vrefresh range 56-85Hz
(II) I810(0): Generic Monitor: Using hsync range of 30.00-93.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 56.00-85.00 Hz
(II) I810(0): Correcting stride (1680 -> 3392)
(WW) I810(0): Allocation with DRI tiling enabled would exceed the
(--) I810(0): Virtual size is 1680x1050 (pitch 1696)
(**) I810(0): *Built-in mode "1680x1050"
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(**) I810(0):  Built-in mode "1280x1024"
(--) I810(0): Display dimensions: (430, 270) mm
(--) I810(0): DPI set to (99, 98)
(==) I810(0): VBE Restore workaround: enabled.
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)Lakeport-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)Lakeport-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 384 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 6840 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xffff000 (0x202d6000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xfffb000 (0x21314000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xfffa000 (0x201ed000).
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xffea000
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf9d2a000
(II) I810(0): [drm] mapped SAREA 0xf9d2a000 to 0xb7aba000
(II) I810(0): [drm] framebuffer handle = 0xd0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
(II) I810(0): Allocated 32 kB for the logical context at 0xffe2000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 870 pages failed
(II) I810(0): Allocated 3480 kB for the back buffer at 0xfc7c000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 870 pages failed
(II) I810(0): Allocated 3480 kB for the depth buffer at 0xf916000.
(II) I810(0): Allocated 239616 kB for textures at 0x6ce000
(WW) I810(0): xf86AllocateGARTMemory: allocation of 59663 pages failed
(II) I810(0): 0x81fe508: Memory at offset 0x00020000, size 6840 kBytes
(II) I810(0): 0x81fd880: Memory at offset 0x0ffff000, size 4 kBytes
(II) I810(0): 0x81fee40: Memory at offset 0x0fffb000, size 16 kBytes
(II) I810(0): 0x81fd7bc: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81fe548: Memory at offset 0x0ffea000, size 64 kBytes
(II) I810(0): 0x81fee68: Memory at offset 0x0fffa000, size 4 kBytes
(II) I810(0): 0x81fe6e0: Memory at offset 0x0ffe2000, size 32 kBytes
(II) I810(0): 0x81fe700: Memory at offset 0x0fc7c000, size 3480 kBytes
(II) I810(0): 0x81fe720: Memory at offset 0x0f916000, size 3480 kBytes
(II) I810(0): 0x81fe740: Memory at offset 0x006ce000, size 239616 kBytes
(II) I810(0): I830SetupMemoryTiling: Not tileable 0xd40
(II) I810(0): [drm] Registers = 0xe5000000
(II) I810(0): [drm] ring buffer = 0xd0000000
(II) I810(0): [drm] init sarea width,height = 1680 x 1050 (pitch 1696)
(II) I810(0): [drm] Mapping front buffer
(EE) I810(0): [drm] drmAddMap(front_handle) failed. Disabling DRI
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xf9d2a000 at 0xb7aba000
(EE) I810(0): [drm] drmAddMap(screen mappings) failed. Disabling DRI
(==) I810(0): Write-combining range (0xd0000000,0x10000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(--) I810(0): A non-CRT device is attached to pipe A.
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Display plane B is disabled and connected to Pipe B.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): Display plane B is now disabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 105 Mpixel/s
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): Set up textured video
(II) I810(0): direct rendering: Failed
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(II) I810(0): Rotating to 0 degrees


xorg.conf:
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	256000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		#Modes		"1680x1050" "1440x1050" "1440x900" "1366x768" "1280x1024" "1280x800" "1024x768" "800x600" "640x480" "320x240"
		#Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
		#Modes		"1680x1050" "1024x768" "800x600" "640x480"
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

