---
title: "Dark screen at starting. Help!"
date: 2009-06-03
forum: Hardware
---

### Post by duddy67 on 2009-06-03
Hi all,

I've installed XUbuntu 8.10  on my laptop (Emachines E520) and it works fine except that 
sometimes I have a dark screen problem at starting. Everything is loaded as usually but when the log screen is about to be displayed 
I get a dark screen and no way to do anything. All keys combinations are useless and the only solution is to reboot.
So the last time it happened I retrieved the syslog (log_fail) and tried to compare it with the syslog of the next session (log_next).
Here's what I found:


in log_fail this line is missing:
> 
May 26 13:09:25 duddy-laptop kernel: [    2.077347] tty ttyr6: hash matches
libata librarie is not loaded at the same moment:

log_fail:
> 
May 26 13:04:52 duddy-laptop kernel: [    3.243440] libata version 3.00 loaded.
May 26 13:04:52 duddy-laptop kernel: [    3.252335] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May 26 13:04:52 duddy-laptop kernel: [    3.252345] uhci_hcd 0000:00:1a.1: setting latency timer to 64
May 26 13:04:52 duddy-laptop kernel: [    3.252349] uhci_hcd 0000:00:1a.1: UHCI Host Controller
May 26 13:04:52 duddy-laptop kernel: [    3.252373] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
May 26 13:04:52 duddy-laptop kernel: [    3.252425] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000050a0
May 26 13:04:52 duddy-laptop kernel: [    3.252517] usb usb2: configuration #1 chosen from 1 choice
May 26 13:04:52 duddy-laptop kernel: [    3.252543] hub 2-0:1.0: USB hub found
May 26 13:04:52 duddy-laptop kernel: [    3.252550] hub 2-0:1.0: 2 ports detected
log_next:
> 
May 26 13:09:25 duddy-laptop kernel: [    3.244289] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May 26 13:09:25 duddy-laptop kernel: [    3.244300] uhci_hcd 0000:00:1a.1: setting latency timer to 64 
May 26 13:09:25 duddy-laptop kernel: [    3.244304] uhci_hcd 0000:00:1a.1: UHCI Host Controller
May 26 13:09:25 duddy-laptop kernel: [    3.244330] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
May 26 13:09:25 duddy-laptop kernel: [    3.244373] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000050a0
May 26 13:09:25 duddy-laptop kernel: [    3.244471] usb usb2: configuration #1 chosen from 1 choice
May 26 13:09:25 duddy-laptop kernel: [    3.244496] hub 2-0:1.0: USB hub found 
May 26 13:09:25 duddy-laptop kernel: [    3.244503] hub 2-0:1.0: 2 ports detected
May 26 13:09:25 duddy-laptop kernel: [    3.252570] libata version 3.00 loaded.
At this place datas are not quiet the same:

log_fail:
> 
May 26 13:04:52 duddy-laptop kernel: [    7.192771] kjournald starting.  Commit interval 5 seconds
May 26 13:04:52 duddy-laptop kernel: [    7.192784] EXT3-fs: mounted filesystem with ordered data mode.
May 26 13:04:52 duddy-laptop kernel: [   12.758693] udevd version 124 started
May 26 13:04:52 duddy-laptop kernel: [   13.274336] Linux agpgart interface v0.103
May 26 13:04:52 duddy-laptop kernel: [   13.310847] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
May 26 13:04:52 duddy-laptop kernel: [   13.311073] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
May 26 13:04:52 duddy-laptop kernel: [   13.324913] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
log_next:
> 
May 26 13:09:25 duddy-laptop kernel: [    7.128901] EXT3-fs: INFO: recovery required on readonly filesystem.
May 26 13:09:25 duddy-laptop kernel: [    7.128905] EXT3-fs: write access will be enabled during recovery.
May 26 13:09:25 duddy-laptop kernel: [    7.178566] kjournald starting.  Commit interval 5 seconds
May 26 13:09:25 duddy-laptop kernel: [    7.178582] EXT3-fs: sda3: orphan cleanup on readonly fs
May 26 13:09:25 duddy-laptop kernel: [    7.178587] ext3_orphan_cleanup: deleting unreferenced inode 507912
May 26 13:09:25 duddy-laptop kernel: [    7.178619] ext3_orphan_cleanup: deleting unreferenced inode 507911
May 26 13:09:25 duddy-laptop kernel: [    7.178624] ext3_orphan_cleanup: deleting unreferenced inode 507910
May 26 13:09:25 duddy-laptop kernel: [    7.178629] ext3_orphan_cleanup: deleting unreferenced inode 507909
May 26 13:09:25 duddy-laptop kernel: [    7.178634] ext3_orphan_cleanup: deleting unreferenced inode 507908
May 26 13:09:25 duddy-laptop kernel: [    7.178638] EXT3-fs: sda3: 5 orphan inodes deleted
May 26 13:09:25 duddy-laptop kernel: [    7.178640] EXT3-fs: recovery complete.
May 26 13:09:25 duddy-laptop kernel: [    7.181303] EXT3-fs: mounted filesystem with ordered data mode.
May 26 13:09:25 duddy-laptop kernel: [   12.932347] udevd version 124 started
May 26 13:09:25 duddy-laptop kernel: [   13.393951] Linux agpgart interface v0.103
May 26 13:09:25 duddy-laptop kernel: [   13.445673] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
May 26 13:09:25 duddy-laptop kernel: [   13.445899] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
May 26 13:09:25 duddy-laptop kernel: [   13.486953] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
May 26 13:09:25 duddy-laptop kernel: [   13.618676] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 26 13:09:25 duddy-laptop kernel: [   13.637075] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Can someone say if there's any clues relevant to that dark screen problem ?


Thanks for advance.

---

### Post by kerry_s on 2009-06-03
for the screen we need to see the xorg log.

---

### Post by duddy67 on 2009-06-03
Ok, here is the Xorg.0.log file:
> 
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux duddy-laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 25 20:51:35 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0x90000000/0, 0x80000000/0, I/O @ 0x00005140/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0x93500000/0
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
(--) intel(0): Linear framebuffer at 0x80000000
(--) intel(0): IO registers at addr 0x90000000
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
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video1
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
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0x0001d400 to 0xca000200
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
(II) intel(0): Kernel reported 474624 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1898492 kB available
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
(II) intel(0): [drm] Registers = 0x90000000
(II) intel(0): [drm] ring buffer = 0x80000000
(II) intel(0): [drm] mapped front buffer at 0x80100000, handle = 0x80100000
(II) intel(0): [drm] mapped back buffer at 0x81a00000, handle = 0x81a00000
(II) intel(0): [drm] mapped depth buffer at 0x82040000, handle = 0x82040000
(II) intel(0): [drm] mapped classic textures at 0x84000000, handle = 0x84000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
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
(II) intel(0): 0x00020000-0x00083fff: compressed frame buffer (400 kB, 0x000000007c020000 physical
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
(II) intel(0): using SSC reference clock of 96 MHz
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
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: Enabled
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
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 2.0.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
Do you see something wrong in it ?

---

### Post by kerry_s on 2009-06-03
lets see your /etc/X11/xorg.conf

---

### Post by duddy67 on 2009-06-03
Here it is:
> 
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
 
Section "Device"
         Identifier      "Configured Video Device"
EndSection
 
Section "Monitor"
         Identifier      "Configured Monitor"
EndSection
 
Section "Screen"
         Identifier      "Default Screen"
         Monitor         "Configured Monitor"
         Device          "Configured Video Device"
EndSection


---

### Post by kerry_s on 2009-06-03
press **alt+f2**
type> **gksudo mousepad /etc/X11/xorg.conf**

```
Section "Device"
           Identifier "Configured Video Device"
           **Option "FramebufferCompression" "off"**
EndSection

```

i also see a dri bug on your driver, but disabling that would mean losing 3d, so try that first, if it don't work then change it to:

```
        **Option "NoDRI"**
```

---

### Post by duddy67 on 2009-06-03
Thanks for your response. :D
For now, I'm gonna try the first solution you brought.
> 
i also see a dri bug on your driver, but disabling that would mean losing 3d
It doesn't matter, I don't use 3d on my laptop, so if the first solution doesn't 
work I'll try the second one.

The thing is that problem happens in a random way, everything could be ok during a month then suddenly I get a dark screen.

So I'll let you know if that problem comes again.


Thanks.

---

### Post by kerry_s on 2009-06-03
> **duddy67 said:**
> Thanks for your response. :D
For now, I'm gonna try the first solution you brought.
It doesn't matter, I don't use 3d on my laptop, so if the first solution doesn't 
work I'll try the second one.

The thing is that problem happens in a random way, everything could be ok during a month then suddenly I get a dark screen.

So I'll let you know if that problem comes again.


Thanks.

yeah, googling shows theres been a bit of problems with the intel driver as of late, there are work arounds, but i'm sure if you you just hang in there they'll get fixed. good luck

---

### Post by duddy67 on 2009-06-07
Dark screen problem has come again :(

So I added the Option "NoDRI" line in the /etc/X11/xorg.conf
I hope it will fixe that pb for good.
I'll let you know if it doesn't.

---

### Post by duddy67 on 2009-06-15
That problem just happened again this morning. :( :( :( 
So both of the options typed in the  /etc/X11/xorg.conf don't work.
I really don't know what to do (except changing my laptop).
May be an improvement in the next xserver-xorg-video-intel package will fix 
that problem but it's not sure.

Any idea ?

---

