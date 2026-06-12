---
title: "Intel graphics card and OpenGL GLX?"
date: 2009-10-26
forum: Hardware
---

### Post by rebeltaz on 2009-10-26
I am trying to run FlightGear which apparently requires OpenGL. Whenever I try to run it, I get this error message:

Xlib:  extension "GLX" missing on display ":0.0".
freeglut (fgfs): OpenGL GLX extension not supported by display ':0.0'

I have run lshw and this is what it reports for the graphics card on my eMachines E520 laptop:

        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

I have read a lot about installing OpenGL for NVidia cards, but I have also seen warnings not to install NVidia drivers if you have an Intel card. So can someone tell me how to install OpenGL? BTW- here is a copy of my xorg.conf file:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option 		"MigrationHeuristic"	"greedy"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


thanks....

---

### Post by Yellow Pasque on 2009-10-26
Graphics drivers and OpenGL should work "out-of-the-box" for your GPU (Intel GMA 4500MHD). If they don't check:
```
LIBGL_DEBUG=verbose glxinfo
cat /var/log/Xorg.0.log
```

---

### Post by rebeltaz on 2009-10-26
> **Temüjin said:**
> Graphics drivers and OpenGL should work "out-of-the-box" for your GPU (Intel GMA 4500MHD). If they don't check:
```
LIBGL_DEBUG=verbose glxinfo
cat /var/log/Xorg.0.log
```

I have no idea what all of this means:

LIBGL_DEBUG=verbose glxinfo
```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

cat /var/log/Xorg.0.log
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux eMachines 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 26 01:03:45 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00005110/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Mobile Intel® GM45 Express Chipset
(--) intel(0): Chipset: "Mobile Intel® GM45 Express Chipset"
(--) intel(0): Linear framebuffer at 0x80000000
(--) intel(0): IO registers at addr 0x90000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 65472 kB
(II) intel(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 65532 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000206 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000206 to 0x00000206
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0x5002c100 to 0x6a004000
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 474624 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1898492 kB available
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(**) intel(0): Option "MigrationHeuristic" "greedy"
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00083fff: compressed frame buffer (400 kB, 0x000000007c020000 physical
)
(II) intel(0): 0x00084000-0x0008dfff: HW cursors (40 kB)
(II) intel(0): 0x0008e000-0x00095fff: logical 3D context (32 kB)
(II) intel(0): 0x00096000-0x000a7fff: exa G965 state buffer (72 kB)
(II) intel(0): 0x000a8000-0x000a8fff: power context (4 kB)
(II) intel(0): 0x00100000-0x0073ffff: front buffer (6400 kB) X tiled
(II) intel(0): 0x00740000-0x019fffff: exa offscreen (19200 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: Failed
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event11"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event10"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event6"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): EDID vendor "SEC", prod id 14661
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 14661

```

---

### Post by Yellow Pasque on 2009-10-26
```
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension

```
It means you tried to install the nvidia driver, and it overwrote the open-source version of libglx.so with the proprietary nvidia version, so you need to reinstall the open-source mesa stack.

Try this: 
```
sudo nvidia-settings --uninstall
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
Reboot.

---

### Post by rebeltaz on 2009-10-26
> **Temüjin said:**
> ```
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension

```
It means you tried to install the nvidia driver, and it overwrote the open-source version of libglx.so with the proprietary nvidia version, so you need to reinstall the open-source mesa stack.

Try this: 
```
sudo nvidia-settings --uninstall
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
Reboot.


yeah... I forgot about that, when Ubuntu first upgraded to 9.04, I was having video problems so I did try the Nvidia drivers. So, I did what you suggested, but on the first line, to uninstall nvidia, it reports command (nvidia-settings) not found. So I went ahead and did the other two commands. Rebooted and tried the FlightGear again with the same results. I looked at the Xorg.0.log again and found this: 

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

These lines are still there:

```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX

```

---

### Post by rebeltaz on 2009-10-26
I need to add that I now have the same problems that I had back when I first tried to install the Nvidia drivers after the Ubuntu 9.04 upgrade. First I noticed it with Cheese Webcam. If I click any item on the menu bar, as soon as the menu drops down over the image, the image colors go solarized and the X-Server restarts. Same thing happened when I was watching videos. I paused it and then pulled up Nautilus on top of it. As soon as I did that, the video solarized and X-Server restarted. 

I replaced the xorg.conf file with the original that I was using before running the reconfigure program, but I still have the same effect....

So now, I am back to square one... or maybe zero....

---

### Post by Yellow Pasque on 2009-10-26
That's strange, the file in question (libglx.so) should have been overwritten with the xorg version. Try it again:
> (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
Get rid of that file, or overwrite it with the open-source one:
```
sudo rm /usr/lib/xorg/modules/extensions//libglx.so
sudo apt-get --reinstall install xserver-xorg-core
```

---

### Post by rebeltaz on 2009-10-27
> **Temüjin said:**
> That's strange, the file in question (libglx.so) should have been overwritten with the xorg version. Try it again:

Get rid of that file, or overwrite it with the open-source one:
```
sudo rm /usr/lib/xorg/modules/extensions//libglx.so
sudo apt-get --reinstall install xserver-xorg-core
```

I tried that and rebooted, with the same results, but when I looked at the Xorg.0.log, I found this:

```
(II) LoadModule: "glx"
(WW) Warning, couldn't open module glx
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (module does not exist, 0)
```

so I tried to reinstall everything:

```
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
``` 

After I rebooted and looked at Xorg.0.log again, that same warning is there.

---

### Post by Yellow Pasque on 2009-10-27
Are you trolling?

---

### Post by rebeltaz on 2009-10-27
> **Temüjin said:**
> Are you trolling?

I beg your pardon... am I doing what?

---

### Post by rebeltaz on 2010-02-19
I know this is old, but since I never got a complete solution to this problem, I thought I'd post the solution I found, in case any one else needs it:

```

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```
 and then reboot ...

The second and third lines are not my own, they were posted originally by Temüjin. Hopefully, this will be of some use to someone. It worked for me...

---

### Post by teresaejunior on 2010-04-17
> **rebeltaz said:**
> I know this is old, but since I never got a complete solution to this problem, I thought I'd post the solution I found, in case any one else needs it:

```

sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

``` and then reboot ...

The second and third lines are not my own, they were posted originally by Temüjin. Hopefully, this will be of some use to someone. It worked for me...

It solved mine indeed:lolflag:

---

### Post by phlegm on 2010-04-19
Thank you thank you. This got my compiz working after upgrading to 10.04

---

### Post by rebeltaz on 2010-04-19
Always glad to be of service! :guitar:

---

### Post by asvravi on 2010-05-01
Thanks a lot, this should help me too as this seems to the exact problem I am having. I ran the above commands, but yet to reboot. Meanwhile I found the GL.conf is being linked to the nvidia file by the alternatives tool. I  ran the following to fix that -
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

---

### Post by mrstimpy on 2010-07-16
THANK YOU GUYS!!!

All your solutions together and first deleting the xorg.conf* files from /etc/X11 got my issues solved with XBMC!

---

### Post by conorsulli on 2010-07-18
> **teresaejunior said:**
> It solved mine indeed:lolflag:

Mine too! thank you Sir :)

---

### Post by vedavrata on 2011-04-26
> **Temüjin said:**
>  ... you tried to install the nvidia driver, and it overwrote the open-source version of libglx.so with the proprietary nvidia version, so you need to reinstall the open-source mesa stack.
Try this: 
```
sudo nvidia-settings --uninstall
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```Reboot.

Thank you, friend!
Your solution helped me in such problem: 

# glxinfo
# glxgears
# google-earth
-- all of them gave "**Xlib:  extension GLX missing on display :0.0**" error report...

# lspci
00:02.0 **VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller** (rev 03)

After, by yoyr advice, 
# **sudo nvidia-settings --uninstall**
# **sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core**
# **sudo dpkg-reconfigure xserver-xorg**
and **reboot**
the problem has gone! 
Thank you! :-)

---

### Post by iammeagain on 2011-05-02
Big help, the purge solved my problem. Now I have Nvidia completely off and can enjoy the great battery life and still play my minecraft. :D

---

### Post by jdahling on 2011-10-27
Awesome, this along with a posting from Eugene Crosser here:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/859188](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/859188)

Fixed my openGL issues as well as helped me reinstall libgl1-mesa-glx and libgl1-mesa-dri which wouldn't reinstall for me.

Laptop: Toshiba P505-S8980

Hooray and THANK YOU!\\:D/

---

### Post by mokert8 on 2011-11-05
I'm having the same problem :/ except when I try to use the code mentioned above, after it asks for confirmation to remove said 5 files, even if I say "y", it says aborted... any Ideas ? :/
```
The following packages were automatically installed and are no longer required:
  ttf-umefont unrar icoutils localechooser-data ttf-mscorefonts-installer cabextract libmpg123-0 winbind ttf-droid
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-173* nvidia-common* nvidia-current* nvidia-settings* ubuntu-desktop*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 120 MB disk space will be freed.
Do you want to continue [Y/n]?y
Abort.
kyle@kyle-MS-6566E:~/UrbanTerror$
``` I'm about to try it form the home directory, but I'm not sure if that will work. :/

---

