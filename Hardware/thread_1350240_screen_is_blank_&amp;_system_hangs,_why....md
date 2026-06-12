---
title: "screen is blank &amp; system hangs, why?..."
date: 2009-12-09
forum: Hardware
---

### Post by kohei on 2009-12-09
What's happening in my laptop? Perhaps, paranormal activities...

Sometimes ubuntu hangs after splash screen and before login screen shows, and
logs don't seem to suggest any errors. My laptop model is acer extensa 5630ez,
with intel gm45 express chipset, and i installed ubuntu 8.10 with a customized 
kernel (2.6.27.10). Can anyone helps me?

/var/log/messages (last lines)
-----------------
Linux agpgart interface v0.103
ACPI: Power Button (FF) [PWRF]
input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
ACPI: Lid Switch [LID0]
input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
agpgart-intel 0000:00:00.0: detected 65532K stolen memory
ACPI: Sleep Button (CM) [SLPB]
ACPI: WMI: Mapper loaded
agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
ACPI: AC Adapter [ADP1] (on-line)
input: PC Speaker as /devices/platform/pcspkr/input/input4
acpi device:03: registered as cooling_device2
input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
ath9k: 0.1
ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
ACPI: Battery Slot [BAT0] (battery absent)
acer-wmi: Acer Laptop ACPI-WMI Extras
phy0: Atheros 9280: mem=0xf8cc0000, irq=17
Yenta: CardBus bridge found at 0000:0d:06.0 [1025:013c]
Yenta O2: res at 0x94/0xD4: 00/ea
Yenta O2: enabling read prefetch/write burst
Synaptics Touchpad, model: 1, fw: 6.3, id: 0x12a0b1, caps: 0xa04711/0xa04000
HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input6
hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
Yenta: ISA IRQ mask 0x0cb8, PCI irq 22
Socket status: 30000006
Yenta: Raising subordinate bus# of parent bus (#0d) from #0e to #11
pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
cs: IO port probe 0x3000-0x3fff: clean.
pcmcia: parent PCI bridge Memory window: 0xf4700000 - 0xf47fffff
pcmcia: parent PCI bridge Memory window: 0xc0000000 - 0xc3ffffff
cs: IO port probe 0x100-0x3af: clean.
cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x820-0x8ff: clean.
cs: IO port probe 0xc00-0xcf7: clean.
cs: IO port probe 0xa00-0xaff: clean.
Adding 5855652k swap on /dev/sda7.  Priority:-1 extents:1 across:5855652k
EXT3 FS on sda6, internal journal
ip_tables: (C) 2000-2006 Netfilter Core Team
[drm] Initialized drm 1.1.0 20060810
pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[drm] Initialized i915 1.6.0 20060119 on minor 0


/var/log/X.org.0.log (last lines)
---------------------

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf4000000/0, 0xd0000000/0, I/O @ 0x00001800/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf4400000/0
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.4.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile Intel® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Mobile Intel® GM45 Express Chipset
(--) intel(0): Chipset: "Mobile Intel® GM45 Express Chipset"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xF4000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
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
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.4.0
    ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000206 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000206 to 0x00000206
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0x80008200 to 0x5500a700
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) intel(0): Kernel reported 731904 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 2927612 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xf4000000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] mapped front buffer at 0xd0100000, handle = 0xd0100000
(II) intel(0): [drm] mapped back buffer at 0xd1a00000, handle = 0xd1a00000
(II) intel(0): [drm] mapped depth buffer at 0xd2040000, handle = 0xd2040000
(II) intel(0): [drm] mapped classic textures at 0xd4000000, handle = 0xd4000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Disable render standby.
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x03fff000 (pgoffset 16383)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x04000000 (pgoffset 16384)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00083fff: compressed frame buffer (400 kB, 0x00000000bc020000 physical
)
(II) intel(0): 0x00084000-0x0008dfff: HW cursors (40 kB)
(II) intel(0): 0x0008e000-0x00095fff: logical 3D context (32 kB)
(II) intel(0): 0x00096000-0x000a7fff: exa G965 state buffer (72 kB)
(II) intel(0): 0x000a8000-0x000a8fff: power context (4 kB)
(II) intel(0): 0x00100000-0x0073ffff: front buffer (6400 kB) X tiled
(II) intel(0): 0x00740000-0x019fffff: exa offscreen (19200 kB)
(II) intel(0): 0x01a00000-0x0203ffff: back buffer (6400 kB) X tiled
(II) intel(0): 0x02040000-0x0267ffff: depth buffer (6400 kB) Y tiled
(II) intel(0): 0x03fff000:            end of stolen memory
(II) intel(0): 0x03fff000-0x03ffffff: HW status (4 kB)
(II) intel(0): 0x04000000-0x05ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 100 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.

---

