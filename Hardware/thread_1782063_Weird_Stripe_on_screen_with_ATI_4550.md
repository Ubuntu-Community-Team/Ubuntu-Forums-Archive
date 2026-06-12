---
title: "Weird Stripe on screen with ATI 4550"
date: 2011-06-14
forum: Hardware
---

### Post by datvovan on 2011-06-14
My laptop :
CPU : i3 330M
ATI 4550 graphics
Ubuntu 11.04

When i installed driver through additional driver, it doesn't work so i installed catalyst 11.5, after reboot.
My screen like this :(

Please help me
[http://cC7.upanh.com/23.679.30741676.FnW0/screenshot.png](http://cC7.upanh.com/23.679.30741676.FnW0/screenshot.png)

---

### Post by datvovan on 2011-06-15
My Xorg.conf

> [    18.299] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    18.299] X Protocol Version 11, Revision 0
[    18.299] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    18.299] Current Operating System: Linux caomanhdat-HP-Pavilion-dv4-Notebook-PC 2.6.38-10-generic #44-Ubuntu SMP Thu Jun 2 21:32:22 UTC 2011 x86_64
[    18.299] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=0f197cd6-b04f-4531-8ff6-e15130c11f3d ro quiet splash vt.handoff=7
[    18.299] Build Date: 21 May 2011  11:48:41AM
[    18.299] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.299] Current version of pixman: 0.20.2
[    18.299]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    18.300] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.300] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 16 09:21:40 2011
[    18.324] (==) Using config file: "/etc/X11/xorg.conf"
[    18.324] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.480] (==) ServerLayout "aticonfig Layout"
[    18.480] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    18.480] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    18.486] (**) |   |-->Device "aticonfig-Device[0]-0"
[    18.486] (==) Automatically adding devices
[    18.486] (==) Automatically enabling devices
[    18.534] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    18.534] (**) ModulePath set to "/usr/lib64/xorg/modules,/usr/lib64/xorg/modules/extensions/fglrx"
[    18.534] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.534] (II) Loader magic: 0x7e0280
[    18.534] (II) Module ABI versions:
[    18.534]     X.Org ANSI C Emulation: 0.4
[    18.534]     X.Org Video Driver: 10.0
[    18.534]     X.Org XInput driver : 12.3
[    18.534]     X.Org Server Extension : 5.0
[    18.535] (--) PCI:*(0:0:2:0) 8086:0046:103c:1409 rev 2, Mem @ 0xe0000000/4194304, 0xd0000000/268435456, I/O @ 0x00007050/8
[    18.535] (--) PCI: (0:1:0:0) 1002:9555:103c:1409 rev 0, Mem @ 0xc0000000/268435456, 0xe8400000/65536, I/O @ 0x00006000/256, BIOS @ 0x????????/131072
[    18.535] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.535] (II) "extmod" will be loaded by default.
[    18.535] (II) "dbe" will be loaded by default.
[    18.535] (II) "glx" will be loaded by default.
[    18.535] (II) "record" will be loaded by default.
[    18.535] (II) "dri" will be loaded by default.
[    18.535] (II) "dri2" will be loaded by default.
[    18.535] (II) LoadModule: "extmod"
[    18.673] (II) Loading /usr/lib64/xorg/modules/extensions/libextmod.so
[    18.688] (II) Module extmod: vendor="X.Org Foundation"
[    18.688]     compiled for 1.10.1, module version = 1.0.0
[    18.688]     Module class: X.Org Server Extension
[    18.688]     ABI class: X.Org Server Extension, version 5.0
[    18.688] (II) Loading extension MIT-SCREEN-SAVER
[    18.688] (II) Loading extension XFree86-VidModeExtension
[    18.688] (II) Loading extension XFree86-DGA
[    18.688] (II) Loading extension DPMS
[    18.688] (II) Loading extension XVideo
[    18.688] (II) Loading extension XVideo-MotionCompensation
[    18.688] (II) Loading extension X-Resource
[    18.688] (II) LoadModule: "dbe"
[    18.707] (II) Loading /usr/lib64/xorg/modules/extensions/libdbe.so
[    18.724] (II) Module dbe: vendor="X.Org Foundation"
[    18.724]     compiled for 1.10.1, module version = 1.0.0
[    18.724]     Module class: X.Org Server Extension
[    18.724]     ABI class: X.Org Server Extension, version 5.0
[    18.724] (II) Loading extension DOUBLE-BUFFER
[    18.724] (II) LoadModule: "glx"
[    18.724] (II) Loading /usr/lib64/xorg/modules/extensions/libglx.so
[    18.767] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    18.768]     compiled for 6.9.0, module version = 1.0.0
[    18.768] (II) Loading extension GLX
[    18.768] (II) LoadModule: "record"
[    18.768] (II) Loading /usr/lib64/xorg/modules/extensions/librecord.so
[    18.769] (II) Module record: vendor="X.Org Foundation"
[    18.769]     compiled for 1.10.1, module version = 1.13.0
[    18.769]     Module class: X.Org Server Extension
[    18.769]     ABI class: X.Org Server Extension, version 5.0
[    18.769] (II) Loading extension RECORD
[    18.769] (II) LoadModule: "dri"
[    18.769] (II) Loading /usr/lib64/xorg/modules/extensions/libdri.so
[    18.815] (II) Module dri: vendor="X.Org Foundation"
[    18.815]     compiled for 1.10.1, module version = 1.0.0
[    18.815]     ABI class: X.Org Server Extension, version 5.0
[    18.815] (II) Loading extension XFree86-DRI
[    18.815] (II) LoadModule: "dri2"
[    18.816] (II) Loading /usr/lib64/xorg/modules/extensions/libdri2.so
[    18.816] (II) Module dri2: vendor="X.Org Foundation"
[    18.816]     compiled for 1.10.1, module version = 1.2.0
[    18.816]     ABI class: X.Org Server Extension, version 5.0
[    18.816] (II) Loading extension DRI2
[    18.816] (II) LoadModule: "fglrx"
[    18.816] (II) Loading /usr/lib64/xorg/modules/drivers/fglrx_drv.so
[    19.341] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    19.356]     compiled for 1.4.99.906, module version = 8.86.5
[    19.356]     Module class: X.Org Video Driver
[    19.357] (II) Loading sub module "fglrxdrm"
[    19.357] (II) LoadModule: "fglrxdrm"
[    19.357] (II) Loading /usr/lib64/xorg/modules/linux/libfglrxdrm.so
[    19.399] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    19.399]     compiled for 1.4.99.906, module version = 8.86.5
[    19.399] (II) ATI Proprietary Linux Driver Version Identifier:8.86.5
[    19.399] (II) ATI Proprietary Linux Driver Release Identifier: 8.861                                
[    19.399] (II) ATI Proprietary Linux Driver Build Date: May 24 2011 22:46:53
[    19.399] (++) using VT number 7

[    19.399] (WW) Falling back to old probe method for fglrx
[    19.470] (II) Loading PCS database from /etc/ati/amdpcsdb
[    19.505] (--) Chipset Supported AMD Graphics Processor (0x9555) found
[    19.506] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    19.506] (II) fglrx: intel VGA device detected, load intel driver.
[    19.506] (II) LoadModule: "intel"
[    19.506] (II) Loading /usr/lib64/xorg/modules/drivers/intel_drv.so
[    19.574] (II) Module intel: vendor="X.Org Foundation"
[    19.574]     compiled for 1.10.1, module version = 2.14.0
[    19.574]     Module class: X.Org Video Driver
[    19.574]     ABI class: X.Org Video Driver, version 10.0
[    19.723] ukiDynamicMajor: found major device number 249
[    19.723] ukiDynamicMajor: found major device number 249
[    19.723] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    19.723] ukiOpenDevice: node name is /dev/ati/card0
[    19.723] ukiOpenDevice: open result is 8, (OK)
[    19.723] ukiOpenByBusid: ukiOpenMinor returns 8
[    19.723] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    19.910] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    19.920] (II) AMD Video driver is signed
[    19.921] (II) Loading /usr/lib64/xorg/modules/drivers/fglrx_drv.so
[    19.921] (II) Loading /usr/lib64/xorg/modules/linux/libfglrxdrm.so
[    19.921] (II) fglrx(0): pEnt->device->identifier=0x14521e0
[    19.923] (II) Loading /usr/lib64/xorg/modules/drivers/intel_drv.so
[    19.923] (II) intel(1): pEnt->device->identifier=(nil)
[    19.923] (EE) Screen 1 deleted because of no matching config section.
[    19.923] (II) UnloadModule: "intel"
[    19.923] (II) Unloading intel
[    19.923] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    19.923] (II) fglrx(0): PowerXpress: Discrete GPU is selected.
[    20.119] drmOpenDevice: node name is /dev/dri/card0
[    20.119] drmOpenDevice: open result is 12, (OK)
[    20.119] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.119] drmOpenDevice: node name is /dev/dri/card0
[    20.119] drmOpenDevice: open result is 12, (OK)
[    20.119] drmOpenByBusid: drmOpenMinor returns 12
[    20.119] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.119] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    20.119] (==) fglrx(0): RGB weight 888
[    20.119] (==) fglrx(0): Default visual is TrueColor
[    20.119] (**) fglrx(0): Option "Tiling" "off"
[    20.119] (**) fglrx(0): Option "Shadow" "off"
[    20.119] (II) fglrx(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    20.119] (**) fglrx(0): ChipID override: 0x0046
[    20.119] (**) fglrx(0): ChipRev override: 2
[    20.119] (**) fglrx(0): Chipset: "Arrandale"
[    20.119] (**) fglrx(0): Relaxed fencing enabled
[    20.119] (**) fglrx(0): Tiling disabled
[    20.119] (**) fglrx(0): SwapBuffers wait enabled
[    20.119] (==) fglrx(0): video overlay key set to 0x101fe
[    20.119] (II) fglrx(0): Output LVDS1 using monitor section aticonfig-Monitor[0]-0
[    20.120] (II) fglrx(0): found backlight control interface /sys/class/backlight/acpi_video1
[    20.120] (II) fglrx(0): Output VGA1 has no monitor section
[    20.120] (II) fglrx(0): EDID for output LVDS1
[    20.120] (II) fglrx(0): Manufacturer: LGD  Model: 27e  Serial#: 0
[    20.120] (II) fglrx(0): Year: 2009  Week: 0
[    20.120] (II) fglrx(0): EDID Version: 1.3
[    20.120] (II) fglrx(0): Digital Display Input
[    20.120] (II) fglrx(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    20.120] (II) fglrx(0): Gamma: 2.20
[    20.120] (II) fglrx(0): No DPMS capabilities specified
[    20.120] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.120] (II) fglrx(0): First detailed timing is preferred mode
[    20.120] (II) fglrx(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    20.120] (II) fglrx(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    20.120] (II) fglrx(0): Manufacturer's mask: 0
[    20.120] (II) fglrx(0): Supported detailed timing:
[    20.120] (II) fglrx(0): clock: 69.3 MHz   Image Size:  304 x 190 mm
[    20.120] (II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1405 h_border: 0
[    20.120] (II) fglrx(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    20.120] (II) fglrx(0):  LG Display
[    20.120] (II) fglrx(0):  LP141WX3-TLN4
[    20.120] (II) fglrx(0): EDID (in hex):
[    20.120] (II) fglrx(0):     00ffffffffffff0030e47e0200000000
[    20.120] (II) fglrx(0):     00130103801e13780ab3859558538a28
[    20.120] (II) fglrx(0):     25505400000001010101010101010101
[    20.120] (II) fglrx(0):     010101010101121b007d502016303020
[    20.120] (II) fglrx(0):     360030be100000180000000000000000
[    20.120] (II) fglrx(0):     00000000000000000000000000fe004c
[    20.120] (II) fglrx(0):     4720446973706c61790a2020000000fe
[    20.120] (II) fglrx(0):     004c503134315758332d544c4e3400f7
[    20.120] (II) fglrx(0): EDID vendor "LGD", prod id 638
[    20.120] (II) fglrx(0): Printing DDC gathered Modelines:
[    20.120] (II) fglrx(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    20.120] (II) fglrx(0): Not using default mode "320x240" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "512x384" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "640x480" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "640x512" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "800x600" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "896x672" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "928x696" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "960x720" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "576x432" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "700x525" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "720x450" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "800x512" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "960x540" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "960x600" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Not using default mode "1024x768" (doublescan mode not supported)
[    20.120] (II) fglrx(0): Printing probed modes for output LVDS1
[    20.120] (II) fglrx(0): Modeline "1280x800"x60.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    20.120] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.120] (II) fglrx(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.120] (II) fglrx(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    20.120] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.120] (II) fglrx(0): EDID for output VGA1
[    20.120] (II) fglrx(0): Output LVDS1 connected
[    20.120] (II) fglrx(0): Output VGA1 disconnected
[    20.120] (II) fglrx(0): Using exact sizes for initial modes
[    20.120] (II) fglrx(0): Output LVDS1 using initial mode 1280x800
[    20.120] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.120] (II) fglrx(0): Kernel page flipping support detected, enabling
[    20.120] (**) fglrx(0): Display dimensions: (300, 190) mm
[    20.120] (**) fglrx(0): DPI set to (108, 106)
[    20.120] (II) Loading sub module "fb"
[    20.120] (II) LoadModule: "fb"
[    20.121] (II) Loading /usr/lib64/xorg/modules/libfb.so
[    20.152] (II) Module fb: vendor="X.Org Foundation"
[    20.169]     compiled for 1.10.1, module version = 1.0.0
[    20.169]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.169] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    20.169] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    20.169] (==) fglrx(0): Default visual is TrueColor
[    20.169] (**) fglrx(0): Option "DPMS" "true"
[    20.169] (==) fglrx(0): RGB weight 888
[    20.169] (II) fglrx(0): Using 8 bits per RGB 
[    20.169] (==) fglrx(0): Buffer Tiling is ON
[    20.169] (II) Loading sub module "fglrxdrm"
[    20.169] (II) LoadModule: "fglrxdrm"
[    20.169] (II) Loading /usr/lib64/xorg/modules/linux/libfglrxdrm.so
[    20.169] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    20.169]     compiled for 1.4.99.906, module version = 8.86.5
[    20.171] ukiDynamicMajor: found major device number 249
[    20.171] ukiDynamicMajor: found major device number 249
[    20.171] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    20.171] ukiOpenDevice: node name is /dev/ati/card0
[    20.171] ukiOpenDevice: open result is 13, (OK)
[    20.171] ukiOpenByBusid: ukiOpenMinor returns 13
[    20.171] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    20.171] (==) fglrx(0): NoAccel = NO
[    20.172] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    20.172] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4500 Series " (Chipset = 0x9555)
[    20.172] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x1409)
[    20.172] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    20.172] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    20.172] (--) fglrx(0): MMIO registers at 0xe8400000
[    20.172] (--) fglrx(0): I/O port at 0x00006000
[    20.172] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    20.830] (II) fglrx(0): AC Adapter is used
[    24.578] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    24.578] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
[    24.578] (II) fglrx(0): PCIE card detected
[    24.578] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    24.578] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    24.603] (II) fglrx(0): Using adapter: 1:0.0.
[    24.627] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    24.677] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[    24.678] (II) fglrx(0): RandR 1.2 support is enabled!
[    24.678] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    24.678] (==) fglrx(0): Center Mode is disabled 
[    24.678] (II) Loading sub module "fb"
[    24.678] (II) LoadModule: "fb"
[    24.678] (II) Loading /usr/lib64/xorg/modules/libfb.so
[    24.678] (II) Module fb: vendor="X.Org Foundation"
[    24.678]     compiled for 1.10.1, module version = 1.0.0
[    24.678]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.678] (II) Loading sub module "ddc"
[    24.678] (II) LoadModule: "ddc"
[    24.678] (II) Module "ddc" already built-in
[    24.913] (II) fglrx(0): Finished Initialize PPLIB!
[    24.927] (II) fglrx(0): Adapter ATI Mobility Radeon HD 4500 Series  has 2 configurable heads and 1 displays connected.
[    24.927] (==) fglrx(0):  PseudoColor visuals disabled
[    24.927] (II) Loading sub module "ramdac"
[    24.927] (II) LoadModule: "ramdac"
[    24.927] (II) Module "ramdac" already built-in
[    24.927] (==) fglrx(0): NoDRI = NO
[    24.927] (==) fglrx(0): Capabilities: 0x00000000
[    24.927] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    24.927] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    24.927] (==) fglrx(0): UseFastTLS=0
[    24.927] (==) fglrx(0): BlockSignalsOnLock=1
[    24.927] (--) Depth 24 pixmap format is 32 bpp
[    24.927] (II) LoadModule: "glesx"
[    24.927] (II) Loading /usr/lib64/xorg/modules/glesx.so
[    25.120] (II) Module glesx: vendor="X.Org Foundation"
[    25.120]     compiled for 1.4.99.906, module version = 1.0.0
[    25.120] (II) Loading extension GLESX
[    25.134] (==) fglrx(0): VideoRam: 262144 KB
[    25.134] (II) fglrx(0): [DRI2] Setup complete
[    25.134] (II) fglrx(0): [DRI2]   DRI driver: i965
[    25.134] (II) fglrx(0): Allocated new frame buffer 1280x800 stride 5120, untiled
[    25.146] (II) UXA(0): Driver registered support for the following operations:
[    25.147] (II)         solid
[    25.147] (II)         copy
[    25.147] (II)         composite (RENDER acceleration)
[    25.147] (II)         put_image
[    25.147] (II)         get_image
[    25.147] (==) fglrx(0): Backing store disabled
[    25.147] (==) fglrx(0): Silken mouse enabled
[    25.147] (II) fglrx(0): Initializing HW Cursor
[    25.220] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.242] (**) fglrx(0): DPMS enabled
[    25.242] (==) fglrx(0): Intel XvMC decoder enabled
[    25.242] (II) fglrx(0): Set up textured video
[    25.242] (II) fglrx(0): [XvMC] xvmc_vld driver initialized.
[    25.242] (II) fglrx(0): direct rendering: DRI2 Enabled
[    25.242] (WW) fglrx(0): Option "VendorName" is not used
[    25.242] (WW) fglrx(0): Option "ModelName" is not used
[    25.242] (WW) fglrx(0): Option "Shadow" is not used
[    25.242] (WW) fglrx(0): Option "Tiling" is not used
[    25.242] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[    25.242] (==) fglrx(0): hotplug detection: "enabled"
[    25.243] (II) Loading extension ATIFGLRXDRI
[    25.243] (II) fglrx(0): doing swlDriScreenInit
[    25.243] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    25.243] ukiDynamicMajor: found major device number 249
[    25.243] ukiDynamicMajor: found major device number 249
[    25.243] ukiDynamicMajor: found major device number 249
[    25.243] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    25.243] ukiOpenDevice: node name is /dev/ati/card0
[    25.243] ukiOpenDevice: open result is 15, (OK)
[    25.243] ukiOpenByBusid: ukiOpenMinor returns 15
[    25.243] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    25.243] (II) fglrx(0): [uki] DRM interface version 1.0
[    25.243] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    25.244] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    25.244] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7ff4369e0000
[    25.244] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    25.244] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    25.244] (II) fglrx(0): swlDriScreenInit done
[    25.244] (II) fglrx(0): Kernel Module Version Information:
[    25.244] (II) fglrx(0):     Name: fglrx
[    25.244] (II) fglrx(0):     Version: 8.86.5
[    25.244] (II) fglrx(0):     Date: May 24 2011
[    25.244] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    25.244] (II) fglrx(0): Kernel Module version matches driver.
[    25.244] (II) fglrx(0): Kernel Module Build Time Information:
[    25.244] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-10-generic
[    25.244] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    25.244] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    25.244] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    25.244] (II) fglrx(0): [uki] register handle = 0x00004000
[    25.271] (II) fglrx(0): DRI initialization successfull
[    25.271] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x003e8000
[    25.271] (II) fglrx(0): Intel display surface mc addr for AMD: 69d48000
[    25.272] (==) fglrx(0): Backing store disabled
[    25.272] (II) Loading extension FGLRXEXTENSION
[    25.272] (**) fglrx(0): DPMS enabled
[    25.273] (II) fglrx(0): Initialized in-driver Xinerama extension
[    25.273] (**) fglrx(0): Textured Video is enabled.
[    25.273] (II) fglrx(0): GLESX enableFlags = 784
[    25.273] (II) fglrx(0): GLESX is enabled
[    25.273] (II) LoadModule: "amdxmm"
[    25.273] (II) Loading /usr/lib64/xorg/modules/amdxmm.so
[    25.289] (II) Module amdxmm: vendor="X.Org Foundation"
[    25.289]     compiled for 1.4.99.906, module version = 2.0.0
[    25.290] (II) Loading extension AMDXVOPL
[    25.290] (II) Loading extension AMDXVBA
[    25.290] XvScreenInit: screen devPrivates ptr non-NULL before init
[    25.309] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    25.311] (II) fglrx(0): Enable composite support successfully
[    25.320] (WW) fglrx(0): Option "VendorName" is not used
[    25.320] (WW) fglrx(0): Option "ModelName" is not used
[    25.320] (WW) fglrx(0): Option "Shadow" is not used
[    25.320] (WW) fglrx(0): Option "Tiling" is not used
[    25.320] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[    25.320] (II) fglrx(0): X context handle = 0x1
[    25.320] (II) fglrx(0): [DRI] installation complete
[    25.354] (--) RandR disabled
[    25.354] (II) Initializing built-in extension Generic Event Extension
[    25.354] (II) Initializing built-in extension SHAPE
[    25.354] (II) Initializing built-in extension MIT-SHM
[    25.354] (II) Initializing built-in extension XInputExtension
[    25.354] (II) Initializing built-in extension XTEST
[    25.354] (II) Initializing built-in extension BIG-REQUESTS
[    25.354] (II) Initializing built-in extension SYNC
[    25.354] (II) Initializing built-in extension XKEYBOARD
[    25.354] (II) Initializing built-in extension XC-MISC
[    25.354] (II) Initializing built-in extension SECURITY
[    25.354] (II) Initializing built-in extension XINERAMA
[    25.354] (II) Initializing built-in extension XFIXES
[    25.354] (II) Initializing built-in extension RENDER
[    25.354] (II) Initializing built-in extension RANDR
[    25.354] (II) Initializing built-in extension COMPOSITE
[    25.354] (II) Initializing built-in extension DAMAGE
[    25.354] (II) Initializing built-in extension GESTURE
[    25.356] ukiDynamicMajor: found major device number 249
[    25.356] ukiDynamicMajor: found major device number 249
[    25.356] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    25.356] ukiOpenDevice: node name is /dev/ati/card0
[    25.356] ukiOpenDevice: open result is 16, (OK)
[    25.356] ukiOpenByBusid: ukiOpenMinor returns 16
[    25.356] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    26.321] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    26.414] (II) fglrx(0): Enable the clock gating!
[    26.414] (II) fglrx(0): Setting screen physical size to 338 x 211
[    26.558] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.579] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    26.580] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.580] (II) LoadModule: "evdev"
[    26.580] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.678] (II) Module evdev: vendor="X.Org Foundation"
[    26.678]     compiled for 1.10.0.902, module version = 2.6.0
[    26.678]     Module class: X.Org XInput Driver
[    26.678]     ABI class: X.Org XInput driver, version 12.3
[    26.678] (II) Using input driver 'evdev' for 'Power Button'
[    26.678] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.678] (**) Power Button: always reports core events
[    26.678] (**) Power Button: Device: "/dev/input/event3"
[    26.680] (--) Power Button: Found keys
[    26.680] (II) Power Button: Configuring as keyboard
[    26.680] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    26.680] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.680] (**) Option "xkb_rules" "evdev"
[    26.680] (**) Option "xkb_model" "pc105"
[    26.680] (**) Option "xkb_layout" "us"
[    26.820] (II) config/udev: Adding input device Video Bus (/dev/input/event14)
[    26.821] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.821] (II) Using input driver 'evdev' for 'Video Bus'
[    26.821] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.821] (**) Video Bus: always reports core events
[    26.821] (**) Video Bus: Device: "/dev/input/event14"
[    26.821] (--) Video Bus: Found keys
[    26.821] (II) Video Bus: Configuring as keyboard
[    26.821] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input14/event14"
[    26.821] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.821] (**) Option "xkb_rules" "evdev"
[    26.821] (**) Option "xkb_model" "pc105"
[    26.821] (**) Option "xkb_layout" "us"
[    26.821] (II) config/udev: Adding input device Video Bus (/dev/input/event15)
[    26.821] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.821] (II) Using input driver 'evdev' for 'Video Bus'
[    26.821] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.821] (**) Video Bus: always reports core events
[    26.821] (**) Video Bus: Device: "/dev/input/event15"
[    26.830] (--) Video Bus: Found keys
[    26.830] (II) Video Bus: Configuring as keyboard
[    26.830] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input15/event15"
[    26.830] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.830] (**) Option "xkb_rules" "evdev"
[    26.830] (**) Option "xkb_model" "pc105"
[    26.830] (**) Option "xkb_layout" "us"
[    26.834] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.834] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.834] (II) Using input driver 'evdev' for 'Power Button'
[    26.834] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.834] (**) Power Button: always reports core events
[    26.834] (**) Power Button: Device: "/dev/input/event0"
[    26.834] (--) Power Button: Found keys
[    26.834] (II) Power Button: Configuring as keyboard
[    26.834] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    26.834] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.834] (**) Option "xkb_rules" "evdev"
[    26.834] (**) Option "xkb_model" "pc105"
[    26.834] (**) Option "xkb_layout" "us"
[    26.835] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    26.835] (II) No input driver/identifier specified (ignoring)
[    26.835] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.835] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.835] (II) Using input driver 'evdev' for 'Sleep Button'
[    26.835] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.835] (**) Sleep Button: always reports core events
[    26.835] (**) Sleep Button: Device: "/dev/input/event2"
[    26.835] (--) Sleep Button: Found keys
[    26.835] (II) Sleep Button: Configuring as keyboard
[    26.835] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    26.835] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    26.835] (**) Option "xkb_rules" "evdev"
[    26.835] (**) Option "xkb_model" "pc105"
[    26.835] (**) Option "xkb_layout" "us"
[    26.839] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
[    26.839] (II) No input driver/identifier specified (ignoring)
[    26.839] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event13)
[    26.839] (II) No input driver/identifier specified (ignoring)
[    26.840] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event5)
[    26.841] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    26.841] (**) USB Optical Mouse: Applying InputClass "Avago Technologies mouse quirks (LP: #746639)"
[    26.841] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    26.841] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.841] (**) USB Optical Mouse: always reports core events
[    26.841] (**) USB Optical Mouse: Device: "/dev/input/event5"
[    26.841] (--) USB Optical Mouse: Found 3 mouse buttons
[    26.841] (--) USB Optical Mouse: Found scroll wheel(s)
[    26.841] (--) USB Optical Mouse: Found relative axes
[    26.841] (--) USB Optical Mouse: Found x and y relative axes
[    26.841] (II) USB Optical Mouse: Configuring as mouse
[    26.841] (II) USB Optical Mouse: Adding scrollwheel support
[    26.841] (**) Option "Emulate3Buttons" "True"
[    26.841] (**) Option "Emulate3Timeout" "50"
[    26.841] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    26.841] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.841] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input5/event5"
[    26.841] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    26.841] (II) USB Optical Mouse: initialized for relative axes.
[    26.841] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    26.841] (**) USB Optical Mouse: (accel) acceleration profile 0
[    26.841] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    26.841] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    26.841] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    26.841] (II) No input driver/identifier specified (ignoring)
[    26.842] (II) config/udev: Adding input device USB Camera Device (/dev/input/event8)
[    26.842] (**) USB Camera Device: Applying InputClass "evdev keyboard catchall"
[    26.842] (II) Using input driver 'evdev' for 'USB Camera Device'
[    26.842] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.842] (**) USB Camera Device: always reports core events
[    26.842] (**) USB Camera Device: Device: "/dev/input/event8"
[    26.842] (--) USB Camera Device: Found keys
[    26.842] (II) USB Camera Device: Configuring as keyboard
[    26.842] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input8/event8"
[    26.842] (II) XINPUT: Adding extended input device "USB Camera Device" (type: KEYBOARD)
[    26.842] (**) Option "xkb_rules" "evdev"
[    26.842] (**) Option "xkb_model" "pc105"
[    26.842] (**) Option "xkb_layout" "us"
[    26.846] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    26.846] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.846] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.846] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.846] (**) AT Translated Set 2 keyboard: always reports core events
[    26.846] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    26.850] (--) AT Translated Set 2 keyboard: Found keys
[    26.850] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.850] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    26.850] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.850] (**) Option "xkb_rules" "evdev"
[    26.850] (**) Option "xkb_model" "pc105"
[    26.850] (**) Option "xkb_layout" "us"
[    26.850] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event10)
[    26.850] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    26.850] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    26.850] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.850] (**) PS/2 Mouse: always reports core events
[    26.850] (**) PS/2 Mouse: Device: "/dev/input/event10"
[    26.850] (--) PS/2 Mouse: Found 3 mouse buttons
[    26.850] (--) PS/2 Mouse: Found relative axes
[    26.850] (--) PS/2 Mouse: Found x and y relative axes
[    26.850] (II) PS/2 Mouse: Configuring as mouse
[    26.850] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    26.850] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.851] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    26.851] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    26.851] (II) PS/2 Mouse: initialized for relative axes.
[    26.851] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    26.851] (**) PS/2 Mouse: (accel) acceleration profile 0
[    26.851] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    26.851] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    26.851] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    26.851] (II) No input driver/identifier specified (ignoring)
[    26.851] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event11)
[    26.851] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    26.851] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    26.851] (II) LoadModule: "synaptics"
[    26.851] (II) Loading /usr/lib64/xorg/modules/input/synaptics_drv.so
[    26.897] (II) Module synaptics: vendor="X.Org Foundation"
[    26.897]     compiled for 1.10.1, module version = 1.3.99
[    26.897]     Module class: X.Org XInput Driver
[    26.897]     ABI class: X.Org XInput driver, version 12.3
[    26.897] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    26.897] (II) Loading /usr/lib64/xorg/modules/input/synaptics_drv.so
[    26.897] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    26.897] (**) Option "Device" "/dev/input/event11"
[    26.910] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    26.910] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    26.910] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    26.910] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    26.910] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    26.910] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    26.910] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    26.910] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    26.910] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    26.911] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    26.911] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    26.911] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    26.911] (II) No input driver/identifier specified (ignoring)
[    26.911] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event7)
[    26.911] (II) No input driver/identifier specified (ignoring)
[    26.911] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    26.911] (II) No input driver/identifier specified (ignoring)
[    26.916] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    26.916] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    26.916] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    26.916] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.916] (**) HP WMI hotkeys: always reports core events
[    26.916] (**) HP WMI hotkeys: Device: "/dev/input/event6"
[    26.920] (--) HP WMI hotkeys: Found keys
[    26.920] (II) HP WMI hotkeys: Configuring as keyboard
[    26.920] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    26.920] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    26.920] (**) Option "xkb_rules" "evdev"
[    26.920] (**) Option "xkb_model" "pc105"
[    26.920] (**) Option "xkb_layout" "us"
[    26.922] (II) config/udev: Adding input device ENE eHome Infrared Remote Receiver (/dev/input/event9)
[    26.922] (**) ENE eHome Infrared Remote Receiver: Applying InputClass "evdev keyboard catchall"
[    26.922] (II) Using input driver 'evdev' for 'ENE eHome Infrared Remote Receiver'
[    26.922] (II) Loading /usr/lib64/xorg/modules/input/evdev_drv.so
[    26.922] (**) ENE eHome Infrared Remote Receiver: always reports core events
[    26.922] (**) ENE eHome Infrared Remote Receiver: Device: "/dev/input/event9"
[    26.922] (--) ENE eHome Infrared Remote Receiver: Found keys
[    26.922] (II) ENE eHome Infrared Remote Receiver: Configuring as keyboard
[    26.922] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input9/event9"
[    26.922] (II) XINPUT: Adding extended input device "ENE eHome Infrared Remote Receiver" (type: KEYBOARD)
[    26.922] (**) Option "xkb_rules" "evdev"
[    26.922] (**) Option "xkb_model" "pc105"
[    26.922] (**) Option "xkb_layout" "us"
[    26.938] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    29.458] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    30.008] (II) fglrx(0): EDID vendor "LGD", prod id 638
[    30.008] (II) fglrx(0): Printing DDC gathered Modelines:
[    30.008] (II) fglrx(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    30.011] (II) fglrx(0): EDID vendor "LGD", prod id 638
[    30.011] (II) fglrx(0): Printing DDC gathered Modelines:
[    30.011] (II) fglrx(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    30.013] (II) fglrx(0): EDID vendor "LGD", prod id 638
[    30.013] (II) fglrx(0): Printing DDC gathered Modelines:
[    30.013] (II) fglrx(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    32.084] (II) fglrx(0): EDID vendor "LGD", prod id 638
[    32.084] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.084] (II) fglrx(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)
[    38.236] (II) fglrx(0): EDID vendor "LGD", prod id 638
[    38.237] (II) fglrx(0): Printing DDC gathered Modelines:
[    38.237] (II) fglrx(0): Modeline "1280x800"x0.0   69.30  1280 1328 1360 1405  800 803 809 822 -hsync -vsync (49.3 kHz)

---

### Post by mozy_55 on 2011-06-17
I also came to me this problem
 I am a novice Can you let me know step by step
 And Look at this page I did not understand
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

my laptop is hp pavilion dv4 2100 
[PHP]CPU
    Intel Core i3 330M  @ 2.13GHz    44 °C
    Arrandale 32nm Technology
RAM
    4.0GB Dual-Channel DDR3 @ 532MHz (7-7-7-20)
Motherboard
    Hewlett-Packard 1409 (CPU)
Graphics
    Generic PnP Monitor (1280x800@60Hz)
    ATI Mobility Radeon HD 4550 (HP)    54 °C
Hard Drives
    313GB Seagate ST9320423AS (SATA)    39 °C
Optical Drives
    hp DVDRAM GT30L
Audio
    IDT High Definition Audio CODEC[/PHP]and
[PHP]Graphics
        Monitor
            Name    Generic PnP Monitor on ATI Mobility Radeon HD 4550
            Current Resolution    1280x800 pixels
            Work Resolution    1280x760 pixels
            State    enabled, primary, output devices support
            Monitor Width    1280
            Monitor Height    800
            Monitor BPP    32 bits per pixel
            Monitor Frequency    60 Hz
            Device    \\.\DISPLAY5\Monitor0
        ATI Mobility Radeon HD 4550
            GPU    M92
            Device ID    1002-9555
            Subvendor    HP (103C)
            Technology    55 nm
            Die Size    190 nm&#1030;
            Transistors    666 M
            Release Date    2009
            DirectX Support    10.1
            DirectX Shader Model    4.1
            OpenGL Support    2.1
            Bios Core Clock    123.36
            Bios Mem Clock    123.36
            Temperature    54 °C
            Core Voltage    0.950 V
            BIOS Version    BR34961.001
            ROPs    4
            Shaders    80 unified
            Pixel Fillrate    1.2 GPixels/s
            Texture Fillrate    1.2 GTexels/s
[/PHP]I use ubuntu 11.4 
I am waiting for your help

---

### Post by smurfgod on 2011-06-17
Looks like artifacts due to either heat, wear or a bad driver. I have seen vertical lines with my HD 4200 after waking from a closed lid, but not that. 

Have yall both done the whole, 3rd party driver thing?? Proprietary drivers?? I had to activate mine for my 4200. Activate and then restart.

---

### Post by mozy_55 on 2011-06-17
Look at this pages 
[http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but i can not understand because I'm Newbie

---

### Post by datvovan on 2011-06-24
I give up, i unistall driver and work without driver :(

---

