---
title: "nvidia-glx-config doesn't work; Xlib-error"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by richardwartenburger on 2005-05-17
Hello,

I have quite a special problem with the driver-installation for my graphics device (Nvidia GForce4 MX 440 AGP). I spent many hours with searching for a solution but didn't find any.
I managed to install the driver as described in the HowTo (sudo apt-get install nvidia-glx , sudo apt-get install nvidia-settings), but the last step didn't work: "sudo nvidia-glx-config enable" was only answered with "sudo: nvidia-glx-config: command not found"
Is the only task of nvidia-glx-config to configure my xorg.conf? If yes, you don't need to read further.

How ever, I edited xorg.conf, uncommented "load glx" and changed the driver to "nvidia" (see below).

If I now try to execute glxgears I get the following error (I am working on a remote computer via VNC):

Xlib:  extension "GLX" missing on display ":2.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.

An error also occurs if I try to execute glxinfo or any other application that seems to use 3D-acceleration.
It seems that the driver isn't installed correctly or something is missing, but I can find the folders which were created during the installation process before.
I am sure that my system uses the following xorg.conf:

Section "Module"
# This loads the DBE extension module.
    Load        "dbe"  	# Double buffer extension
# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
# This loads the font modules
    Load        "type1"
#    Load        "speedo"
    Load        "freetype"
#    Load        "xtt"
# This loads the GLX module
    Load       "glx"
# This loads the DRI module
    Load       "dri"
#    Load       "GLcore"
EndSection

Section "Files"
	RgbPath	"/usr/X11R6/lib/X11/rgb"
#	...
	ModulePath "/usr/X11R6/lib/modules"
EndSection

Section "ServerFlags"
#	(all commented)
EndSection

#	...

Section "Monitor"
    Identifier  "Belinea"

    HorizSync   31.5 - 37.9
#    HorizSync	30-64         # multisync
#    HorizSync	31.5, 35.2    # multiple fixed sync frequencies
#    HorizSync	15-25, 30-50  # multiple ranges of sync frequencies
    VertRefresh 50-90

EndSection

# Standard VGA Device:
Section "Device"
    Identifier	"Standard VGA"
    VendorName	"Unknown"
    BoardName	"Unknown"
#    Chipset	"generic"

    Driver     "vga"
#   (ALSO wrote "nvidia" here, but had - of cause - no effect)
#    BusID      "PCI:0:10:0"
#    VideoRam	256
#    Clocks	25.2 28.3
EndSection
# Device configured by xorgconfig:
Section "Device"
    Identifier  "Nvidia Corporation"
    Driver      "nvidia"
    #VideoRam    32768
    # Insert Clocks lines here if appropriate
EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "Nvidia Corporation"
    Monitor     "Belinea"
    DefaultDepth 24
    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
EndSection
Section "ServerLayout"
    Screen "Screen 1"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

# Section "DRI"
#    Mode 0666
# EndSection

If you need any more information I will provide it to you at once.
I am very thankful for any little answer!

---

### Post by alastair on 2005-05-17
The log file would be useful :

/var/log/Xorg.0.log

---

### Post by richardwartenburger on 2005-05-18
hi, please find the Xorg.0.log below. thank you very much for your help!
best, richard


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux netzer 2.6.10-5-686-smp #1 SMP Tue Mar 15 15:49:06 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686-smp (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Tue Mar 15 15:49:06 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 17 17:01:09 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Simple Layout"
(**) |-->Screen "Screen 1" (0)
(**) |   |-->Monitor "Belinea"
(**) |   |-->Device "Nvidia Corporation"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(--) using VT number 8

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,254c card 0000,0000 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2543 card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2482 card 8086,2480 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 42 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2480 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,248b card 8086,2480 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2483 card 8086,2480 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0181 card 0000,0000 rev a4 class 03,00,00 hdr 00
(II) PCI: 01:03:0: chip 8086,1229 card 8086,1040 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:1c:0: chip 8086,1461 card 8086,1461 rev 04 class 08,00,20 hdr 00
(II) PCI: 02:1d:0: chip 8086,1460 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 02:1e:0: chip 8086,1461 card 8086,1461 rev 04 class 08,00,20 hdr 00
(II) PCI: 02:1f:0: chip 8086,1460 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 04:01:0: chip 8086,1010 card 8086,1011 rev 01 class 02,00,00 hdr 80
(II) PCI: 04:01:1: chip 8086,1010 card 8086,1011 rev 01 class 02,00,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfeafffff (0x300000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfc300000 - 0xfc5fffff (0x300000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc700000 - 0xfe7fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf4200000 - 0xfc2fffff (0x8100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (2:29:0), (2,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfc400000 - 0xfc4fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (2:31:0), (2,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfc300000 - 0xfc3fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 164, Mem @ 0xfd000000/24, 0xf8000000/26, BIOS @ 0xfe7e0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B]
	[1] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[3] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[4] -1	0	0xfe7a0000 - 0xfe7bffff (0x20000) MX[B]
	[5] -1	0	0xfe7df000 - 0xfe7dffff (0x1000) MX[B]
	[6] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[7] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[8] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[13] -1	0	0x00000540 - 0x0000055f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B]
	[1] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[3] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[4] -1	0	0xfe7a0000 - 0xfe7bffff (0x20000) MX[B]
	[5] -1	0	0xfe7df000 - 0xfe7dffff (0x1000) MX[B]
	[6] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[7] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[8] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[13] -1	0	0x00000540 - 0x0000055f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B]
	[6] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B]
	[7] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[8] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[9] -1	0	0xfe7a0000 - 0xfe7bffff (0x20000) MX[B]
	[10] -1	0	0xfe7df000 - 0xfe7dffff (0x1000) MX[B]
	[11] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[12] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[20] -1	0	0x00000540 - 0x0000055f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7174
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7174
	Module class: XFree86 Video Driver
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7174  Tue Mar 22 06:48:37 PST 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B]
	[6] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B]
	[7] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[8] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[9] -1	0	0xfe7a0000 - 0xfe7bffff (0x20000) MX[B]
	[10] -1	0	0xfe7df000 - 0xfe7dffff (0x1000) MX[B]
	[11] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[12] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[20] -1	0	0x00000540 - 0x0000055f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B]
	[6] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B]
	[7] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[8] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[9] -1	0	0xfe7a0000 - 0xfe7bffff (0x20000) MX[B]
	[10] -1	0	0xfe7df000 - 0xfe7dffff (0x1000) MX[B]
	[11] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[12] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[13] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[23] -1	0	0x00000540 - 0x0000055f (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xF8000000
(--) NVIDIA(0): MMIO registers at 0xFD000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce4 MX 440 with AGP8X
(--) NVIDIA(0): VideoBIOS: 04.18.20.38.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 350 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(0): Belinea: Using hsync range of 31.50-37.90 kHz
(II) NVIDIA(0): Belinea: Using vrefresh range of 50.00-90.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "832x624" (hsync out of range)
(II) NVIDIA(0): Not using default mode "416x312" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x800" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x400" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(0): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using mode "1280x1024" (no mode of this name)
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B]
	[8] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B]
	[9] -1	0	0xfeaff000 - 0xfeafffff (0x1000) MX[B]
	[10] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[11] -1	0	0xfe7a0000 - 0xfe7bffff (0x20000) MX[B]
	[12] -1	0	0xfe7df000 - 0xfe7dffff (0x1000) MX[B]
	[13] -1	0	0x80000000 - 0x800003ff (0x400) MX[B]
	[14] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d83f (0x40) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c83f (0x40) IX[B]
	[25] -1	0	0x00000540 - 0x0000055f (0x20) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "Protocol" "Auto"
(**) Mouse1: Device: "/dev/input/mouse0"
(**) Mouse1: Protocol: "Auto"
(**) Option "CorePointer"
(**) Mouse1: Core Pointer
(**) Option "Device" "/dev/input/mouse0"
(==) Mouse1: Emulate3Buttons, Emulate3Timeout: 50
(==) Mouse1: Buttons: 3
(**) Option "CoreKeyboard"
(**) Keyboard1: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard1: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Keyboard1: XkbModel: "pc101"
(**) Option "XkbLayout" "us"
(**) Keyboard1: XkbLayout: "us"
(**) Option "XkbVariant" "ger"
(**) Keyboard1: XkbVariant: "ger"
(**) Option "CustomKeycodes" "off"
(**) Keyboard1: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse1" (type: MOUSE)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(--) Mouse1: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse1: ps2EnableDataReporting: succeeded
AUDIT: Tue May 17 17:01:24 2005: 7020 X: client 5 rejected from local host

---

### Post by alastair on 2005-05-18
I was going to say that .... the log looks OK to me. I cannot see any real problem - even with GLX. It seems to be loaded OK. Then I saw you mention :

"If I now try to execute glxgears I get the following error (I am working on a remote computer via VNC) : Xlib: extension "GLX" missing on display ":2.0"."

There's the problem. Try "glxinfo" on the local display i.e. the one on the system with the NVidia. VNC has it's own display - minus GLX it appears.

---

### Post by richardwartenburger on 2005-05-19
Thanks for your reply.

VNC really was the reason for the problems - executing glxgears on the local display showed the gears in a popup-window.

Do you know any alternative remote desktop application that supports OpenGL?

---

### Post by Mega_slayer on 2007-02-18
Hey guys, I was going to start a new thread but I seem to have the same problem. I am not using VNC and the problem persists. I was wondering if you guys had any suggestions?

Here is the output of commands:

glxgears

```
ulysse@ubuntu:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

glxinfo

```
ulysse@ubuntu:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```

---

### Post by Mega_slayer on 2007-02-18
Here is my log output:

log file

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 18 12:56:34 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA / SGS Thomson (Joint Venture) Riva128"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0c:0: chip 1274,1371 card 4ca1,0001 rev 06 class 04,01,00 hdr 00
(II) PCI: 00:0e:0: chip 8086,1229 card 8086,0001 rev 08 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 12d2,0018 card 10b0,0000 rev 22 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0088 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) NVidia / SGS Thomson (Joint Venture) Riva128 rev 34, Mem @ 0xe8000000/24, 0xea000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xec000000 - 0xec0fffff (0x100000) MX[B]
	[1] -1	0	0xec100000 - 0xec100fff (0x1000) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[4] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[6] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xec000000 - 0xec0fffff (0x100000) MX[B]
	[1] -1	0	0xec100000 - 0xec100fff (0x1000) MX[B]
	[2] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[3] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[4] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[6] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[8] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xec000000 - 0xec0fffff (0x100000) MX[B]
	[5] -1	0	0xec100000 - 0xec100fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7174
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 GT, GeForce 6800 GT,
	GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000, GeForce 6800 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800,
	GeForce Go 6800 Ultra, Quadro FX Go1400, Quadro FX 3450/4000 SDI,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, GeForce 6600 LE,
	GeForce 6600 VE, GeForce Go 6600, GeForce 6610 XL,
	GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, GeForce Go 6600,
	GeForce Go 6600 GT, Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 7800 GTX, GeForce 7800 GTX, GeForce 7800 GT, GeForce 7800 GS,
	GeForce 7800 SLI, GeForce Go 7800, GeForce Go 7800 GTX,
	Quadro FX 4500, GeForce 7300 LE, GeForce Go 7200, GeForce Go 7300,
	GeForce Go 7400, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	Quadro FX 350, GeForce 7300 GS, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, Quadro FX 550M, GeForce Go 7900 GS,
	GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M, GeForce 6150,
	GeForce 6150 LE, GeForce 6100, GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 01:00:0
(--) Chipset RIVA 128 found
(II) Loading sub module "riva128"
(II) LoadModule: "riva128"
(II) Loading /usr/lib/xorg/modules/drivers/riva128.so
(II) Module riva: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xec000000 - 0xec0fffff (0x100000) MX[B]
	[5] -1	0	0xec100000 - 0xec100fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xec000000 - 0xec0fffff (0x100000) MX[B]
	[5] -1	0	0xec100000 - 0xec100fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[9] 0	0	0xe90a0000 - 0xe90affff (0x10000) MS[B]
	[10] 0	0	0xe90b0000 - 0xe90b7fff (0x8000) MS[B]
	[11] 0	0	0xe90b8000 - 0xe90bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[17] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[18] 0	0	0xe90003b0 - 0xe90003bb (0xc) IS[B]
	[19] 0	0	0xe90003c0 - 0xe90003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) RIVA128(0): Initializing int10
(II) RIVA128(0): Primary V_BIOS segment is: 0xc000
(**) RIVA128(0): Depth 24, (--) framebuffer bpp 32
(==) RIVA128(0): RGB weight 888
(==) RIVA128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) RIVA128(0): Using HW cursor
(--) RIVA128(0): Linear framebuffer at 0xEA000000
(--) RIVA128(0): MMIO registers at 0xE8000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) RIVA128(0): I2C bus "DDC" initialized.
(II) RIVA128(0): Probing for EDID...
(II) RIVA128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RIVA128(0): I2C device "DDC:ddc2" removed.
(II) RIVA128(0):   ... found one
(II) RIVA128(0): Manufacturer: HSL  Model: 6a7  Serial#: 0
(II) RIVA128(0): Year: 1999  Week: 6
(II) RIVA128(0): EDID Version: 1.1
(II) RIVA128(0): Analog Display Input,  Input Voltage Level: 0.714/0.286 V
(II) RIVA128(0): Sync:  Separate  CompositeSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) RIVA128(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RIVA128(0): Gamma: 2.25
(II) RIVA128(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RIVA128(0): redX: 0.624 redY: 0.340   greenX: 0.281 greenY: 0.594
(II) RIVA128(0): blueX: 0.150 blueY: 0.063   whiteX: 0.283 whiteY: 0.298
(II) RIVA128(0): Supported VESA Video Modes:
(II) RIVA128(0): 720x400@70Hz
(II) RIVA128(0): 720x400@88Hz
(II) RIVA128(0): 640x480@60Hz
(II) RIVA128(0): 640x480@67Hz
(II) RIVA128(0): 640x480@72Hz
(II) RIVA128(0): 640x480@75Hz
(II) RIVA128(0): 800x600@56Hz
(II) RIVA128(0): 800x600@60Hz
(II) RIVA128(0): 800x600@72Hz
(II) RIVA128(0): 800x600@75Hz
(II) RIVA128(0): 832x624@75Hz
(II) RIVA128(0): 1024x768@87Hz (interlaced)
(II) RIVA128(0): 1024x768@60Hz
(II) RIVA128(0): 1024x768@70Hz
(II) RIVA128(0): 1024x768@75Hz
(II) RIVA128(0): Manufacturer's mask: 0
(II) RIVA128(0): Supported Future Video Modes:
(II) RIVA128(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RIVA128(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RIVA128(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RIVA128(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RIVA128(0): Supported additional Video Mode:
(II) RIVA128(0): clock: 56.2 MHz   Image Size:  306 x 230 mm
(II) RIVA128(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) RIVA128(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) RIVA128(0): Supported additional Video Mode:
(II) RIVA128(0): clock: 94.5 MHz   Image Size:  306 x 230 mm
(II) RIVA128(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RIVA128(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RIVA128(0): Supported additional Video Mode:
(II) RIVA128(0): clock: 108.0 MHz   Image Size:  306 x 230 mm
(II) RIVA128(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RIVA128(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RIVA128(0): Ranges: V min: 47  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(--) RIVA128(0): VideoRAM: 8192 kBytes
(==) RIVA128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RIVA128(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) RIVA128(0): Generic Monitor: Using vrefresh range of 50.00-150.00 Hz
(II) RIVA128(0): Clock range:  12.00 to 256.00 MHz
(WW) (1280x960,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1280x960" (hsync out of range)
(II) RIVA128(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,Generic Monitor) mode clock 135MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1280x1024" (hsync out of range)
(II) RIVA128(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,Generic Monitor) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1280x1024" (hsync out of range)
(II) RIVA128(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1600x1200" (hsync out of range)
(II) RIVA128(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1600x1200" (hsync out of range)
(II) RIVA128(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1600x1200" (hsync out of range)
(II) RIVA128(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1600x1200" (hsync out of range)
(II) RIVA128(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,Generic Monitor) mode clock 114.75MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "800x600" (hsync out of range)
(II) RIVA128(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) RIVA128(0): Not using default mode "896x672" (hsync out of range)
(II) RIVA128(0): Not using default mode "1792x1344" (insufficient memory for mode)
(WW) (896x672,Generic Monitor) mode clock 130.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "896x672" (hsync out of range)
(II) RIVA128(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) RIVA128(0): Not using default mode "928x696" (hsync out of range)
(II) RIVA128(0): Not using default mode "1856x1392" (insufficient memory for mode)
(WW) (928x696,Generic Monitor) mode clock 144MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "928x696" (hsync out of range)
(II) RIVA128(0): Not using default mode "1920x1440" (insufficient memory for mode)
(WW) (960x720,Generic Monitor) mode clock 117MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "960x720" (hsync out of range)
(II) RIVA128(0): Not using default mode "1920x1440" (insufficient memory for mode)
(WW) (960x720,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "960x720" (hsync out of range)
(WW) (1152x864,Generic Monitor) mode clock 121.5MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1152x864" (hsync out of range)
(II) RIVA128(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 122MHz exceeds DDC maximum 110MHz
(WW) (1400x1050,Generic Monitor) mode clock 151MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1400x1050" (hsync out of range)
(II) RIVA128(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 155.8MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1400x1050" (hsync out of range)
(II) RIVA128(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1400x1050" (hsync out of range)
(II) RIVA128(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,Generic Monitor) mode clock 147.14MHz exceeds DDC maximum 110MHz
(WW) (1680x1050,Generic Monitor) mode clock 146.25MHz exceeds DDC maximum 110MHz
(WW) (1680x1050,Generic Monitor) mode clock 214.51MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1680x1050" (hsync out of range)
(II) RIVA128(0): Not using default mode "840x525" (hsync out of range)
(II) RIVA128(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) RIVA128(0): Not using default mode "960x600" (hsync out of range)
(II) RIVA128(0): Not using default mode "1920x1200" (insufficient memory for mode)
(WW) (960x600,Generic Monitor) mode clock 115MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "960x600" (hsync out of range)
(II) RIVA128(0): Not using default mode "1920x1440" (insufficient memory for mode)
(WW) (960x720,Generic Monitor) mode clock 170.675MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "960x720" (hsync out of range)
(II) RIVA128(0): Not using default mode "2048x1536" (insufficient memory for mode)
(WW) (1024x768,Generic Monitor) mode clock 133.475MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1024x768" (hsync out of range)
(II) RIVA128(0): Not using default mode "2048x1536" (insufficient memory for mode)
(WW) (1024x768,Generic Monitor) mode clock 170.24MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1024x768" (hsync out of range)
(II) RIVA128(0): Not using default mode "2048x1536" (insufficient memory for mode)
(WW) (1024x768,Generic Monitor) mode clock 194.02MHz exceeds DDC maximum 110MHz
(II) RIVA128(0): Not using default mode "1024x768" (hsync out of range)
(II) RIVA128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1440x900" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1280x960" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1280x800" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1280x768" (width too large for virtual size)
(II) RIVA128(0): Not using default mode "1152x768" (width too large for virtual size)
(--) RIVA128(0): Virtual size is 1024x768 (pitch 1024)
(**) RIVA128(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) RIVA128(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) RIVA128(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) RIVA128(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) RIVA128(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) RIVA128(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) RIVA128(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) RIVA128(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) RIVA128(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RIVA128(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) RIVA128(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RIVA128(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RIVA128(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) RIVA128(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) RIVA128(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RIVA128(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) RIVA128(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RIVA128(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RIVA128(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RIVA128(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RIVA128(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RIVA128(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RIVA128(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RIVA128(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RIVA128(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) RIVA128(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) RIVA128(0):  Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) RIVA128(0): Modeline "840x525"   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync
(**) RIVA128(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) RIVA128(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) RIVA128(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) RIVA128(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RIVA128(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RIVA128(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RIVA128(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) RIVA128(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RIVA128(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RIVA128(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) RIVA128(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) RIVA128(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) RIVA128(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RIVA128(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) RIVA128(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) RIVA128(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) RIVA128(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) RIVA128(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) RIVA128(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) RIVA128(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) RIVA128(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) RIVA128(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) RIVA128(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) RIVA128(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) RIVA128(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) RIVA128(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) RIVA128(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) RIVA128(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) RIVA128(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) RIVA128(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RIVA128(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) RIVA128(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) RIVA128(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RIVA128(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RIVA128(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RIVA128(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) RIVA128(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) RIVA128(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) RIVA128(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) RIVA128(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) RIVA128(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) RIVA128(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) RIVA128(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) RIVA128(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) RIVA128(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) RIVA128(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) RIVA128(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) RIVA128(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) RIVA128(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) RIVA128(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) RIVA128(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(++) RIVA128(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xea000000 - 0xeaffffff (0x1000000) MX[B]
	[1] 0	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xec000000 - 0xec0fffff (0x100000) MX[B]
	[7] -1	0	0xec100000 - 0xec100fff (0x1000) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xea000000 - 0xeaffffff (0x1000000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B](B)
	[11] 0	0	0xe90a0000 - 0xe90affff (0x10000) MS[B](OprD)
	[12] 0	0	0xe90b0000 - 0xe90b7fff (0x8000) MS[B](OprD)
	[13] 0	0	0xe90b8000 - 0xe90bffff (0x8000) MS[B](OprD)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e43f (0x40) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] 0	0	0xe90003b0 - 0xe90003bb (0xc) IS[B](OprU)
	[21] 0	0	0xe90003c0 - 0xe90003df (0x20) IS[B](OprU)
(II) RIVA128(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		10 256x256 slots
(==) RIVA128(0): Backing store disabled
(==) RIVA128(0): Silken mouse enabled
(**) Option "dpms"
(**) RIVA128(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"

```

(I removed some of the end of the log file to fit it in the post, it was the information concerning keyboard, mouse ect..)

Any help would be greatly appreciated,

- Scott

---

### Post by Mega_slayer on 2007-02-18
And finally my xorg.conf file:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"NVIDIA / SGS Thomson (Joint Venture) Riva128"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA / SGS Thomson (Joint Venture) Riva128"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

```

---

### Post by Napster69 on 2007-02-18
use envy ?

---

### Post by Mega_slayer on 2007-02-20
> **Napster69 said:**
> use envy ?

Thanks alot Napster69, I searched what envy was and it seems that it will do the trick. I will let you know how it goes.

---

### Post by Mega_slayer on 2007-02-21
Envy works great, it got my direct rendering working, however the reason I am doing this is to get Google Earth working and unfortunately it hangs when I open the program. Some people said that version 8.28.8 doesn`t work with Google Earth...

So I guess that my problem has changed now. I am trying to get another version, possibly 8.30.8 of fglrx installed. But I`m trying to figure out what packages I need to install... I started a new thread for this here:

[HTML]http://www.ubuntuforums.org/showthread.php?p=2189199#post2189199[/HTML]

---

