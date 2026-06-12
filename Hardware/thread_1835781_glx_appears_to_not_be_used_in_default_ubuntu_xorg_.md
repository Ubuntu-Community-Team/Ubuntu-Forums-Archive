---
title: "glx appears to not be used in default ubuntu xorg config"
date: 2011-08-29
forum: Hardware
---

### Post by dpengel3 on 2011-08-29
I have a new Samsung NP-QX411 laptop and installed Ubuntu 11.04 on it. The desktop seemed to be working slowly, so I did 'glxinfo' and got this:

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

However, the glx module appears to be loading according to the log files. 'grep glx /var/log/Xorg.0.log' gives me this:

[  5226.653] (II) LoadModule: "glx"
[  5226.653] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  5226.692] (II) Module glx: vendor="NVIDIA Corporation"

Here's the output of 'lspci -v':

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: e0000000-e0ffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000c1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at e1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e1705000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at e170a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at e1700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: e1600000-e16fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000e1400000-00000000e14fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: e1500000-e15fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at e1709000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at e1708000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: medium devsel, IRQ 10
    Memory at e1704000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

01:00.0 3D controller: nVidia Corporation Device 1050 (rev a1)
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at c0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at e1600000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at 2000 [size=256]
    Memory at e1404000 (64-bit, prefetchable) [size=4K]
    Memory at e1400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Samsung Electronics Co Ltd Device c0a0
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e1500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd


```and here's the complete /var/log/Xorg.0.log:

```
[  5226.646] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  5226.646] X Protocol Version 11, Revision 0
[  5226.646] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  5226.646] Current Operating System: Linux dan-QX311-QX411-QX412-QX511 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686
[  5226.646] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-11-generic-pae root=UUID=c9473add-7ae2-4698-8e24-d12e3b3204a3 ro quiet splash acpi_osi=Linux vt.handoff=7
[  5226.646] Build Date: 11 August 2011  03:47:56PM
[  5226.646] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[  5226.646] Current version of pixman: 0.20.2
[  5226.646]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  5226.646] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  5226.646] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 29 22:52:42 2011
[  5226.647] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  5226.647] (==) No Layout section.  Using the first Screen section.
[  5226.647] (==) No screen section available. Using defaults.
[  5226.647] (**) |-->Screen "Default Screen Section" (0)
[  5226.647] (**) |   |-->Monitor "<default monitor>"
[  5226.648] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  5226.648] (==) Automatically adding devices
[  5226.648] (==) Automatically enabling devices
[  5226.648] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  5226.648]     Entry deleted from font path.
[  5226.648] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  5226.648]     Entry deleted from font path.
[  5226.648] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  5226.648]     Entry deleted from font path.
[  5226.648] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  5226.648]     Entry deleted from font path.
[  5226.648] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  5226.648]     Entry deleted from font path.
[  5226.648] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[  5226.648] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  5226.648] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  5226.649] (II) Loader magic: 0x81ffde0
[  5226.649] (II) Module ABI versions:
[  5226.649]     X.Org ANSI C Emulation: 0.4
[  5226.649]     X.Org Video Driver: 10.0
[  5226.649]     X.Org XInput driver : 12.3
[  5226.649]     X.Org Server Extension : 5.0
[  5226.650] (--) PCI:*(0:0:2:0) 8086:0116:144d:c0a0 rev 9, Mem @ 0xe1000000/4194304, 0xd0000000/268435456, I/O @ 0x00004000/64
[  5226.650] (--) PCI: (0:1:0:0) 10de:1050:144d:c0a0 rev 161, Mem @ 0xe0000000/16777216, 0xb0000000/268435456, 0xc0000000/33554432, I/O @ 0x00003000/128
[  5226.651] (II) Open ACPI successful (/var/run/acpid.socket)
[  5226.651] (II) LoadModule: "extmod"
[  5226.651] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  5226.652] (II) Module extmod: vendor="X.Org Foundation"
[  5226.652]     compiled for 1.10.1, module version = 1.0.0
[  5226.652]     Module class: X.Org Server Extension
[  5226.652]     ABI class: X.Org Server Extension, version 5.0
[  5226.652] (II) Loading extension MIT-SCREEN-SAVER
[  5226.652] (II) Loading extension XFree86-VidModeExtension
[  5226.652] (II) Loading extension XFree86-DGA
[  5226.652] (II) Loading extension DPMS
[  5226.652] (II) Loading extension XVideo
[  5226.652] (II) Loading extension XVideo-MotionCompensation
[  5226.652] (II) Loading extension X-Resource
[  5226.652] (II) LoadModule: "dbe"
[  5226.652] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  5226.653] (II) Module dbe: vendor="X.Org Foundation"
[  5226.653]     compiled for 1.10.1, module version = 1.0.0
[  5226.653]     Module class: X.Org Server Extension
[  5226.653]     ABI class: X.Org Server Extension, version 5.0
[  5226.653] (II) Loading extension DOUBLE-BUFFER
[  5226.653] (II) LoadModule: "glx"
[  5226.653] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  5226.692] (II) Module glx: vendor="NVIDIA Corporation"
[  5226.692]     compiled for 4.0.2, module version = 1.0.0
[  5226.692]     Module class: X.Org Server Extension
[  5226.692] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[  5226.692] (II) Loading extension GLX
[  5226.692] (II) LoadModule: "record"
[  5226.692] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  5226.692] (II) Module record: vendor="X.Org Foundation"
[  5226.692]     compiled for 1.10.1, module version = 1.13.0
[  5226.692]     Module class: X.Org Server Extension
[  5226.692]     ABI class: X.Org Server Extension, version 5.0
[  5226.692] (II) Loading extension RECORD
[  5226.692] (II) LoadModule: "dri"
[  5226.693] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  5226.693] (II) Module dri: vendor="X.Org Foundation"
[  5226.693]     compiled for 1.10.1, module version = 1.0.0
[  5226.693]     ABI class: X.Org Server Extension, version 5.0
[  5226.693] (II) Loading extension XFree86-DRI
[  5226.693] (II) LoadModule: "dri2"
[  5226.694] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  5226.694] (II) Module dri2: vendor="X.Org Foundation"
[  5226.694]     compiled for 1.10.1, module version = 1.2.0
[  5226.694]     ABI class: X.Org Server Extension, version 5.0
[  5226.694] (II) Loading extension DRI2
[  5226.694] (==) Matched intel as autoconfigured driver 0
[  5226.694] (==) Matched vesa as autoconfigured driver 1
[  5226.694] (==) Matched fbdev as autoconfigured driver 2
[  5226.694] (==) Assigned the driver to the xf86ConfigLayout
[  5226.694] (II) LoadModule: "intel"
[  5226.695] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  5226.695] (II) Module intel: vendor="X.Org Foundation"
[  5226.695]     compiled for 1.10.1, module version = 2.14.0
[  5226.695]     Module class: X.Org Video Driver
[  5226.695]     ABI class: X.Org Video Driver, version 10.0
[  5226.695] (II) LoadModule: "vesa"
[  5226.696] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  5226.696] (II) Module vesa: vendor="X.Org Foundation"
[  5226.696]     compiled for 1.10.0, module version = 2.3.0
[  5226.696]     Module class: X.Org Video Driver
[  5226.696]     ABI class: X.Org Video Driver, version 10.0
[  5226.696] (II) LoadModule: "fbdev"
[  5226.697] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  5226.697] (II) Module fbdev: vendor="X.Org Foundation"
[  5226.697]     compiled for 1.10.0, module version = 0.4.2
[  5226.697]     ABI class: X.Org Video Driver, version 10.0
[  5226.697] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[  5226.698] (II) VESA: driver for VESA chipsets: vesa
[  5226.698] (II) FBDEV: driver for framebuffer: fbdev
[  5226.698] (--) using VT number 8

[  5226.713] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  5226.713] (WW) Falling back to old probe method for vesa
[  5226.713] (WW) Falling back to old probe method for fbdev
[  5226.713] (II) Loading sub module "fbdevhw"
[  5226.713] (II) LoadModule: "fbdevhw"
[  5226.714] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  5226.714] (II) Module fbdevhw: vendor="X.Org Foundation"
[  5226.714]     compiled for 1.10.1, module version = 0.0.2
[  5226.714]     ABI class: X.Org Video Driver, version 10.0
[  5226.714] drmOpenDevice: node name is /dev/dri/card0
[  5226.714] drmOpenDevice: open result is 9, (OK)
[  5226.714] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  5226.714] drmOpenDevice: node name is /dev/dri/card0
[  5226.715] drmOpenDevice: open result is 9, (OK)
[  5226.715] drmOpenByBusid: drmOpenMinor returns 9
[  5226.715] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  5226.715] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[  5226.715] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  5226.715] (==) intel(0): RGB weight 888
[  5226.715] (==) intel(0): Default visual is TrueColor
[  5226.715] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
[  5226.715] (--) intel(0): Chipset: "Sandybridge"
[  5226.715] (**) intel(0): Relaxed fencing enabled
[  5226.715] (**) intel(0): Tiling enabled
[  5226.715] (**) intel(0): SwapBuffers wait disabled
[  5226.715] (==) intel(0): video overlay key set to 0x101fe
[  5226.715] (II) intel(0): Output LVDS1 has no monitor section
[  5226.716] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[  5226.716] (II) intel(0): Output VGA1 has no monitor section
[  5226.721] (II) intel(0): Output HDMI1 has no monitor section
[  5226.722] (II) intel(0): Output DP1 has no monitor section
[  5226.722] (II) intel(0): EDID for output LVDS1
[  5226.722] (II) intel(0): Manufacturer: SEC  Model: 3449  Serial#: 0
[  5226.722] (II) intel(0): Year: 2011  Week: 0
[  5226.722] (II) intel(0): EDID Version: 1.3
[  5226.722] (II) intel(0): Digital Display Input
[  5226.722] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[  5226.722] (II) intel(0): Gamma: 2.20
[  5226.722] (II) intel(0): No DPMS capabilities specified
[  5226.722] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  5226.722] (II) intel(0): First detailed timing is preferred mode
[  5226.722] (II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.330 greenY: 0.540
[  5226.722] (II) intel(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[  5226.722] (II) intel(0): Manufacturer's mask: 0
[  5226.722] (II) intel(0): Supported detailed timing:
[  5226.722] (II) intel(0): clock: 70.7 MHz   Image Size:  309 x 174 mm
[  5226.722] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[  5226.722] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 792 v_border: 0
[  5226.722] (II) intel(0): Unknown vendor-specific block f
[  5226.722] (II) intel(0):  SAMSUNG
[  5226.722] (II) intel(0):  LTN140AT21801
[  5226.723] (II) intel(0): EDID (in hex):
[  5226.723] (II) intel(0):     00ffffffffffff004ca3493400000000
[  5226.723] (II) intel(0):     00150103801f11780a09e59757548a27
[  5226.723] (II) intel(0):     22505400000001010101010101010101
[  5226.723] (II) intel(0):     0101010101019e1b5678500018303020
[  5226.723] (II) intel(0):     250035ae100000190000000f00000000
[  5226.723] (II) intel(0):     00000000001eb4027400000000fe0053
[  5226.723] (II) intel(0):     414d53554e470a2020202020000000fe
[  5226.723] (II) intel(0):     004c544e3134304154323138303100c9
[  5226.723] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5226.723] (II) intel(0): Printing DDC gathered Modelines:
[  5226.723] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5226.723] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  5226.723] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  5226.724] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  5226.724] (II) intel(0): Printing probed modes for output LVDS1
[  5226.724] (II) intel(0): Modeline "1366x768"x60.1   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5226.724] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[  5226.724] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[  5226.724] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  5226.724] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  5226.724] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  5226.724] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  5226.724] (II) intel(0): EDID for output VGA1
[  5226.729] (II) intel(0): EDID for output HDMI1
[  5226.730] (II) intel(0): EDID for output DP1
[  5226.730] (II) intel(0): Output LVDS1 connected
[  5226.730] (II) intel(0): Output VGA1 disconnected
[  5226.730] (II) intel(0): Output HDMI1 disconnected
[  5226.730] (II) intel(0): Output DP1 disconnected
[  5226.730] (II) intel(0): Using exact sizes for initial modes
[  5226.730] (II) intel(0): Output LVDS1 using initial mode 1366x768
[  5226.730] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  5226.730] (II) intel(0): Kernel page flipping support detected, enabling
[  5226.730] (**) intel(0): Display dimensions: (310, 170) mm
[  5226.730] (**) intel(0): DPI set to (111, 114)
[  5226.730] (II) Loading sub module "fb"
[  5226.730] (II) LoadModule: "fb"
[  5226.731] (II) Loading /usr/lib/xorg/modules/libfb.so
[  5226.731] (II) Module fb: vendor="X.Org Foundation"
[  5226.731]     compiled for 1.10.1, module version = 1.0.0
[  5226.731]     ABI class: X.Org ANSI C Emulation, version 0.4
[  5226.731] (II) UnloadModule: "vesa"
[  5226.731] (II) Unloading vesa
[  5226.731] (II) UnloadModule: "fbdev"
[  5226.731] (II) Unloading fbdev
[  5226.731] (II) UnloadModule: "fbdevhw"
[  5226.731] (II) Unloading fbdevhw
[  5226.731] (==) Depth 24 pixmap format is 32 bpp
[  5226.731] (==) intel(0): VideoRam: 262144 KB
[  5226.731] (II) intel(0): [DRI2] Setup complete
[  5226.732] (II) intel(0): [DRI2]   DRI driver: i965
[  5226.732] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  5226.734] (II) UXA(0): Driver registered support for the following operations:
[  5226.734] (II)         solid
[  5226.734] (II)         copy
[  5226.734] (II)         composite (RENDER acceleration)
[  5226.734] (II)         put_image
[  5226.734] (II)         get_image
[  5226.734] (==) intel(0): Backing store disabled
[  5226.734] (==) intel(0): Silken mouse enabled
[  5226.735] (II) intel(0): Initializing HW Cursor
[  5226.804] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  5226.805] (==) intel(0): DPMS enabled
[  5226.805] (==) intel(0): Intel XvMC decoder enabled
[  5226.805] (II) intel(0): Set up textured video
[  5226.805] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[  5226.805] (II) intel(0): direct rendering: DRI2 Enabled
[  5226.805] (==) intel(0): hotplug detection: "enabled"
[  5226.805] (--) RandR disabled
[  5226.805] (II) Initializing built-in extension Generic Event Extension
[  5226.805] (II) Initializing built-in extension SHAPE
[  5226.805] (II) Initializing built-in extension MIT-SHM
[  5226.806] (II) Initializing built-in extension XInputExtension
[  5226.806] (II) Initializing built-in extension XTEST
[  5226.806] (II) Initializing built-in extension BIG-REQUESTS
[  5226.806] (II) Initializing built-in extension SYNC
[  5226.806] (II) Initializing built-in extension XKEYBOARD
[  5226.806] (II) Initializing built-in extension XC-MISC
[  5226.806] (II) Initializing built-in extension SECURITY
[  5226.806] (II) Initializing built-in extension XINERAMA
[  5226.806] (II) Initializing built-in extension XFIXES
[  5226.806] (II) Initializing built-in extension RENDER
[  5226.806] (II) Initializing built-in extension RANDR
[  5226.806] (II) Initializing built-in extension COMPOSITE
[  5226.806] (II) Initializing built-in extension DAMAGE
[  5226.806] (II) Initializing built-in extension GESTURE
[  5226.813] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[  5226.828] (II) intel(0): Setting screen physical size to 361 x 203
[  5226.851] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  5226.873] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[  5226.873] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  5226.873] (II) LoadModule: "evdev"
[  5226.873] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.874] (II) Module evdev: vendor="X.Org Foundation"
[  5226.874]     compiled for 1.10.0.902, module version = 2.6.0
[  5226.874]     Module class: X.Org XInput Driver
[  5226.874]     ABI class: X.Org XInput driver, version 12.3
[  5226.874] (II) Using input driver 'evdev' for 'Power Button'
[  5226.874] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.874] (**) Power Button: always reports core events
[  5226.874] (**) Power Button: Device: "/dev/input/event3"
[  5226.874] (--) Power Button: Found keys
[  5226.875] (II) Power Button: Configuring as keyboard
[  5226.875] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[  5226.875] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  5226.875] (**) Option "xkb_rules" "evdev"
[  5226.875] (**) Option "xkb_model" "pc105"
[  5226.875] (**) Option "xkb_layout" "us"
[  5226.878] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[  5226.878] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  5226.878] (II) Using input driver 'evdev' for 'Video Bus'
[  5226.878] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.878] (**) Video Bus: always reports core events
[  5226.878] (**) Video Bus: Device: "/dev/input/event6"
[  5226.880] (--) Video Bus: Found keys
[  5226.880] (II) Video Bus: Configuring as keyboard
[  5226.880] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6/event6"
[  5226.880] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  5226.880] (**) Option "xkb_rules" "evdev"
[  5226.880] (**) Option "xkb_model" "pc105"
[  5226.880] (**) Option "xkb_layout" "us"
[  5226.892] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[  5226.892] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  5226.892] (II) Using input driver 'evdev' for 'Video Bus'
[  5226.892] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.892] (**) Video Bus: always reports core events
[  5226.892] (**) Video Bus: Device: "/dev/input/event5"
[  5226.892] (--) Video Bus: Found keys
[  5226.893] (II) Video Bus: Configuring as keyboard
[  5226.893] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/LNXVIDEO:00/input/input5/event5"
[  5226.893] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  5226.893] (**) Option "xkb_rules" "evdev"
[  5226.893] (**) Option "xkb_model" "pc105"
[  5226.893] (**) Option "xkb_layout" "us"
[  5226.894] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  5226.894] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  5226.895] (II) Using input driver 'evdev' for 'Power Button'
[  5226.895] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.895] (**) Power Button: always reports core events
[  5226.895] (**) Power Button: Device: "/dev/input/event1"
[  5226.895] (--) Power Button: Found keys
[  5226.895] (II) Power Button: Configuring as keyboard
[  5226.895] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[  5226.895] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  5226.895] (**) Option "xkb_rules" "evdev"
[  5226.895] (**) Option "xkb_model" "pc105"
[  5226.895] (**) Option "xkb_layout" "us"
[  5226.896] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  5226.896] (II) No input driver/identifier specified (ignoring)
[  5226.897] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  5226.897] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  5226.897] (II) Using input driver 'evdev' for 'Sleep Button'
[  5226.897] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.897] (**) Sleep Button: always reports core events
[  5226.897] (**) Sleep Button: Device: "/dev/input/event2"
[  5226.897] (--) Sleep Button: Found keys
[  5226.897] (II) Sleep Button: Configuring as keyboard
[  5226.897] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[  5226.897] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  5226.898] (**) Option "xkb_rules" "evdev"
[  5226.898] (**) Option "xkb_model" "pc105"
[  5226.898] (**) Option "xkb_layout" "us"
[  5226.904] (II) config/udev: Adding input device WebCam SCB-1100N (/dev/input/event8)
[  5226.904] (**) WebCam SCB-1100N: Applying InputClass "evdev keyboard catchall"
[  5226.905] (II) Using input driver 'evdev' for 'WebCam SCB-1100N'
[  5226.905] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.905] (**) WebCam SCB-1100N: always reports core events
[  5226.905] (**) WebCam SCB-1100N: Device: "/dev/input/event8"
[  5226.905] (--) WebCam SCB-1100N: Found keys
[  5226.905] (II) WebCam SCB-1100N: Configuring as keyboard
[  5226.905] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input8/event8"
[  5226.905] (II) XINPUT: Adding extended input device "WebCam SCB-1100N" (type: KEYBOARD)
[  5226.905] (**) Option "xkb_rules" "evdev"
[  5226.905] (**) Option "xkb_model" "pc105"
[  5226.905] (**) Option "xkb_layout" "us"
[  5226.907] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[  5226.907] (II) No input driver/identifier specified (ignoring)
[  5226.908] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[  5226.908] (II) No input driver/identifier specified (ignoring)
[  5226.911] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event7)
[  5226.911] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[  5226.911] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[  5226.912] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.912] (**) USB Optical Mouse: always reports core events
[  5226.912] (**) USB Optical Mouse: Device: "/dev/input/event7"
[  5226.912] (--) USB Optical Mouse: Found 3 mouse buttons
[  5226.912] (--) USB Optical Mouse: Found scroll wheel(s)
[  5226.912] (--) USB Optical Mouse: Found relative axes
[  5226.912] (--) USB Optical Mouse: Found x and y relative axes
[  5226.912] (II) USB Optical Mouse: Configuring as mouse
[  5226.912] (II) USB Optical Mouse: Adding scrollwheel support
[  5226.912] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[  5226.912] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  5226.912] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/usb3/3-3/3-3:1.0/input/input7/event7"
[  5226.912] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[  5226.912] (II) USB Optical Mouse: initialized for relative axes.
[  5226.913] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[  5226.913] (**) USB Optical Mouse: (accel) acceleration profile 0
[  5226.913] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[  5226.913] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[  5226.913] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[  5226.913] (II) No input driver/identifier specified (ignoring)
[  5226.923] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[  5226.923] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  5226.923] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  5226.923] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5226.923] (**) AT Translated Set 2 keyboard: always reports core events
[  5226.923] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[  5226.924] (--) AT Translated Set 2 keyboard: Found keys
[  5226.924] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  5226.924] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[  5226.924] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  5226.924] (**) Option "xkb_rules" "evdev"
[  5226.924] (**) Option "xkb_model" "pc105"
[  5226.924] (**) Option "xkb_layout" "us"
[  5226.925] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[  5226.925] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  5226.925] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  5226.925] (II) LoadModule: "synaptics"
[  5226.926] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  5226.926] (II) Module synaptics: vendor="X.Org Foundation"
[  5226.926]     compiled for 1.10.1, module version = 1.3.99
[  5226.926]     Module class: X.Org XInput Driver
[  5226.926]     ABI class: X.Org XInput driver, version 12.3
[  5226.926] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  5226.926] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  5226.926] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  5226.926] (**) Option "Device" "/dev/input/event11"
[  5226.926] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[  5226.926] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[  5226.927] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  5226.927] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  5226.927] (--) SynPS/2 Synaptics TouchPad: buttons: left double triple
[  5226.927] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  5226.927] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  5226.927] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[  5226.927] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  5226.927] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  5226.927] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  5226.927] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[  5226.928] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  5226.928] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  5226.928] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  5226.928] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  5226.928] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  5226.928] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  5226.929] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  5226.929] (II) No input driver/identifier specified (ignoring)
[  5227.365] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5227.365] (II) intel(0): Printing DDC gathered Modelines:
[  5227.365] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5227.374] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5227.374] (II) intel(0): Printing DDC gathered Modelines:
[  5227.374] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5227.384] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5227.384] (II) intel(0): Printing DDC gathered Modelines:
[  5227.384] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5227.393] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5227.393] (II) intel(0): Printing DDC gathered Modelines:
[  5227.393] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5233.956] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5233.957] (II) intel(0): Printing DDC gathered Modelines:
[  5233.957] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5233.966] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5233.967] (II) intel(0): Printing DDC gathered Modelines:
[  5233.967] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5233.975] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5233.975] (II) intel(0): Printing DDC gathered Modelines:
[  5233.975] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5238.607] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5238.608] (II) intel(0): Printing DDC gathered Modelines:
[  5238.608] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)
[  5239.526] (II) intel(0): EDID vendor "SEC", prod id 13385
[  5239.526] (II) intel(0): Printing DDC gathered Modelines:
[  5239.526] (II) intel(0): Modeline "1366x768"x0.0   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz)

```Does anyone know how I might get the glx stuff to actually run, maybe making the desktop a bit faster? What other information is needed?

Thanks in advance.

---

### Post by .... on 2011-08-30
That's a poor choice for running Linux. You have hybrid Intel/Nvidia graphics (a.k.a. Optimus). It's not officially supported by nvidia : [http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/)[]("http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/")

---

### Post by marty331 on 2011-10-04
> **.... said:**
> That's a poor choice for running Linux. You have hybrid Intel/Nvidia graphics (a.k.a. Optimus). It's not officially supported by nvidia : [http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/)[]("http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/")

What would be a better choice or solution?  I have nearly the exact same setup.

Thanks!

---

