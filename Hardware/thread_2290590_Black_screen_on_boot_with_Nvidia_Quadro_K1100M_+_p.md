---
title: "Black screen on boot with Nvidia Quadro K1100M + proprietary driver + Cuda"
date: 2015-08-13
forum: Hardware
---

### Post by giacof on 2015-08-13
Hi, I'm using current nvidia drivers (nvidia-346.59) on Kubuntu 15.04, with Cuda 7.0 also installed (yet from nvidia dev repository).
The system works fine if I use the intel card, but when I use prime-select to switch from intel to nvidia, then after logoff I get a black screen and the system hangs.
I can't but switch to a virtual console by pressing [Ctrl+Alt+Fn] and then revert to the intel card and restart the sddm service. 
Even reboot doesn't help, as I get yet another black screen.

```
$ apt-cache policy nvidia-346 nvidia-prime
nvidia-346:
  Installed: 346.59-0ubuntu1
  Candidate: 346.59-0ubuntu1
  Version table:
 *** 346.59-0ubuntu1 0
        500 http://it.archive.ubuntu.com/ubuntu/ vivid/restricted amd64 Packages
        100 /var/lib/dpkg/status
     346.46-0ubuntu1 0
        500 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1410/x86_64/  Packages
nvidia-prime:
  Installed: 0.8.1
  Candidate: 0.8.1
  Version table:
 *** 0.8.1 0
        500 http://it.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status

```

```
$ lspci -v
[...]

01:00.0 VGA compatible controller: NVIDIA Corporation GK107GLM [Quadro K1100M] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 15cc
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at e0000000 (64-bit, prefetchable) [size=32M]
        I/O ports at e000 [size=128]
        Expansion ROM at f4000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
```

```
*** /etc/X11/xorg.conf
*** ls: -rw-r--r-- 1 root root 593 2015-07-26 18:17:26.987864801 +0200 /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```

```
dmesg extract:
[   28.210156] nvidia: module license 'NVIDIA' taints kernel.
[   28.210159] Disabling lock debugging due to kernel taint
[   28.212155] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   28.215216] nvidia 0000:01:00.0: enabling device (0004 -> 0007)
[   28.215283] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   28.215597] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
[   28.215602] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.59  Tue Mar 31 14:10:31 PDT 2015

```

```
*** /var/log/Xorg.0.log
*** ls: -rw-r--r-- 1 root root 31416 2015-07-26 22:55:47.010829709 +0200 /var/log/Xorg.0.log
[    46.601] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    46.601] X Protocol Version 11, Revision 0
[    46.601] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    46.601] Current Operating System: Linux Home1 3.19.0-24-generic #25-Ubuntu SMP Wed Jul 22 18:24:45 UTC 2015 x86_64
[    46.601] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-24-generic.efi.signed root=/dev/mapper/vg-test--root ro acpi_backlight=vendor dell_laptop.backlight=0 pci=nocrs pci=realloc quiet splash vt.
handoff=7
[    46.601] Build Date: 19 March 2015  09:26:59AM
[    46.601] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[    46.601] Current version of pixman: 0.32.6
[    46.601]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    46.601] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    46.601] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 26 22:52:21 2015
[    46.628] (==) Using config file: "/etc/X11/xorg.conf"
[    46.628] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    46.634] (==) ServerLayout "layout"
[    46.634] (**) |-->Screen "nvidia" (0)
[    46.634] (**) |   |-->Monitor "<default monitor>"
[    46.634] (**) |   |-->Device "nvidia"
[    46.634] (==) No monitor specified for screen "nvidia".
        Using a default monitor configuration.
[    46.634] (**) |-->Inactive Device "intel"
[    46.634] (==) Automatically adding devices
[    46.634] (==) Automatically enabling devices
[    46.634] (==) Automatically adding GPU devices
[    46.634] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    46.634]    Entry deleted from font path.
[    46.634] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    46.634]    Entry deleted from font path.
[    46.634] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    46.634]    Entry deleted from font path.
[    46.634] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    46.634]    Entry deleted from font path.
[    46.634] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    46.634]    Entry deleted from font path.
[    46.634] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    46.634] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    46.634] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    46.634] (II) Loader magic: 0x7f1d60b4bd80
[    46.634] (II) Module ABI versions:
[    46.634]    X.Org ANSI C Emulation: 0.4
[    46.634]    X.Org Video Driver: 19.0
[    46.634]    X.Org XInput driver : 21.0
[    46.634]    X.Org Server Extension : 9.0
[    46.634] (II) xfree86: Adding drm device (/dev/dri/card1)
[    46.634] (II) xfree86: Adding drm device (/dev/dri/card0)
[    46.635] (--) PCI:*(0:0:2:0) 8086:0416:1028:05cc rev 6, Mem @ 0xf5400000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    46.635] (--) PCI: (0:1:0:0) 10de:0ff6:1028:15cc rev 161, Mem @ 0xf3000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    46.635] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    46.635] (II) "glx" will be loaded by default.
[    46.635] (WW) "xmir" is not to be loaded by default. Skipping.
[    46.635] (II) LoadModule: "glx"
[    46.650] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    47.368] (II) Module glx: vendor="NVIDIA Corporation"
[    47.368]    compiled for 4.0.2, module version = 1.0.0
[    47.368]    Module class: X.Org Server Extension
[    47.374] (II) NVIDIA GLX Module  346.59  Tue Mar 31 13:38:58 PDT 2015
[    47.386] (II) LoadModule: "nvidia"
[    47.386] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    47.450] (II) Module nvidia: vendor="NVIDIA Corporation"
[    47.450]    compiled for 4.0.2, module version = 1.0.0
[    47.450]    Module class: X.Org Video Driver
[    47.460] (II) LoadModule: "intel"
[    47.460] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    47.469] (II) Module intel: vendor="X.Org Foundation"
[    47.469]    compiled for 1.17.1, module version = 2.99.917
[    47.469]    Module class: X.Org Video Driver
[    47.469]    ABI class: X.Org Video Driver, version 19.0
[    47.469] (II) NVIDIA dlloader X Driver  346.59  Tue Mar 31 13:17:41 PDT 2015
[    47.469] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    47.470] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    47.471] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    47.471] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    47.471] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    47.471] (++) using VT number 7

[    47.479] (II) Loading sub module "fb"
[    47.479] (II) LoadModule: "fb"
[    47.479] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.489] (II) Module fb: vendor="X.Org Foundation"
[    47.489]    compiled for 1.17.1, module version = 1.0.0
[    47.489]    ABI class: X.Org ANSI C Emulation, version 0.4
[    47.489] (II) Loading sub module "wfb"
[    47.489] (II) LoadModule: "wfb"
[    47.489] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    47.495] (II) Module wfb: vendor="X.Org Foundation"
[    47.496]    compiled for 1.17.1, module version = 1.0.0
[    47.496]    ABI class: X.Org ANSI C Emulation, version 0.4
[    47.496] (II) Loading sub module "ramdac"
[    47.496] (II) LoadModule: "ramdac"
[    47.496] (II) Module "ramdac" already built-in
[    47.497] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    47.497] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917-1~exp1ubuntu2.2 (Alessio Treglia <quadrispro@ubuntu.com>)
[    47.497] (II) intel(G0): SNA compiled for use with valgrind
[    47.497] (II) intel(G1): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    47.497] (II) intel(G1): SNA compiled: xserver-xorg-video-intel 2:2.99.917-1~exp1ubuntu2.2 (Alessio Treglia <quadrispro@ubuntu.com>)
[    47.497] (II) intel(G1): SNA compiled for use with valgrind
[    47.497] (II) NVIDIA(0): Creating default Display subsection in Screen section
        "nvidia" for depth/fbbpp 24/32
[    47.497] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    47.497] (==) NVIDIA(0): RGB weight 888
[    47.497] (==) NVIDIA(0): Default visual is TrueColor
[    47.497] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    47.498] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    47.498] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    47.498] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    47.498] (**) NVIDIA(0): Enabling 2D acceleration
[    48.232] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    48.233] (II) NVIDIA(0): NVIDIA GPU Quadro K1100M (GK107GL) at PCI:1:0:0 (GPU-0)
[    48.233] (--) NVIDIA(0): Memory: 2097152 kBytes
[    48.233] (--) NVIDIA(0): VideoBIOS: 80.07.ab.00.07
[    48.233] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    48.241] (--) NVIDIA(0): Valid display device(s) on Quadro K1100M at PCI:1:0:0
[    48.241] (--) NVIDIA(0):     DFP-0
[    48.241] (--) NVIDIA(0):     DFP-1
[    48.241] (--) NVIDIA(0):     DFP-2
[    48.241] (--) NVIDIA(0):     DFP-3
[    48.241] (--) NVIDIA(0):     DFP-4
[    48.241] (--) NVIDIA(0):     DFP-5
[    48.241] (--) NVIDIA(0): DFP-0: Internal TMDS
[    48.241] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[    48.241] (--) NVIDIA(0): DFP-1: Internal TMDS
[    48.241] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    48.241] (--) NVIDIA(0): DFP-2: Internal TMDS
[    48.241] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    48.241] (--) NVIDIA(0): DFP-3: Internal DisplayPort
[    48.241] (--) NVIDIA(GPU-0): DFP-3: 960.0 MHz maximum pixel clock
[    48.241] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    48.241] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    48.241] (--) NVIDIA(0): DFP-5: Internal DisplayPort
[    48.241] (--) NVIDIA(GPU-0): DFP-5: 960.0 MHz maximum pixel clock
[    48.241] (==) NVIDIA(0): 
[    48.241] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    48.241] (==) NVIDIA(0):     will be used as the requested mode.
[    48.241] (==) NVIDIA(0): 
[    48.241] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[    48.241] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[    48.241] (II) NVIDIA(0): Validated MetaModes:
[    48.241] (II) NVIDIA(0):     "NULL"
[    48.241] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    48.244] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    48.244] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    48.244] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    48.244] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    48.244] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    48.244] (==) intel(G0): RGB weight 888
[    48.244] (==) intel(G0): Default visual is TrueColor
[    48.244] (**) intel(G0): Option "AccelMethod" "SNA"
[    48.244] (II) intel(G0): Output eDP1 has no monitor section
[    48.245] (--) intel(G0): Found backlight control interface dell_backlight (type 'platform') for output eDP1
[    48.245] (II) intel(G0): Enabled output eDP1
[    48.245] (II) intel(G0): Output VGA1 has no monitor section
[    48.245] (II) intel(G0): Enabled output VGA1
[    48.245] (II) intel(G0): Output DP1 has no monitor section
[    48.245] (II) intel(G0): Enabled output DP1
[    48.245] (II) intel(G0): Output HDMI1 has no monitor section
[    48.245] (II) intel(G0): Enabled output HDMI1
[    48.245] (--) intel(G0): Using a maximum size of 256x256 for hardware cursors
[    48.245] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    48.245] (II) intel(G0): Enabled output VIRTUAL1
[    48.247] (==) intel(G0): TearFree disabled
[    48.247] (==) intel(G0): DPI set to (96, 96)
[    48.247] (II) Loading sub module "dri2"
[    48.247] (II) LoadModule: "dri2"
[    48.247] (II) Module "dri2" already built-in
[    48.247] (II) Loading sub module "present"
[    48.247] (II) LoadModule: "present"
[    48.247] (II) Module "present" already built-in
[    50.490] (EE) intel(G1): [drm] failed to set drm interface version: Permission denied [13].
[    50.490] (II) intel(G1): [drm] Contents of '/sys/kernel/debug/dri/0/clients':
[    50.490] (II) intel(G1): [drm]              command   pid dev master a   uid      magic
[    50.490] (II) intel(G1): [drm]                 Xorg  1119   0   y    y     0          0
[    50.490] (II) intel(G1): [drm]                 Xorg  1119   0   n    y     0          0
[    50.490] (EE) intel(G1): Failed to claim DRM device.
[    50.490] (II) UnloadModule: "intel"
[    50.490] (--) Depth 24 pixmap format is 32 bpp
[    50.490] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[    50.490] (==) intel(G0): Backing store enabled
[    50.490] (==) intel(G0): Silken mouse enabled
[    50.490] (II) intel(G0): HW Cursor enabled
[    50.490] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    50.490] (==) intel(G0): DPMS enabled
[    50.490] (==) intel(G0): display hotplug detection enabled
[    50.490] (II) intel(G0): [DRI2] Setup complete
[    50.490] (II) intel(G0): [DRI2]   DRI driver: i965
[    50.490] (II) intel(G0): [DRI2]   VDPAU driver: i965
[    50.490] (II) intel(G0): direct rendering: DRI2 enabled
[    50.490] (II) intel(G0): hardware support for Present enabled
[    50.490] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[    50.490] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[    50.490] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    50.490] (II) NVIDIA:     access.
[    50.501] (II) NVIDIA(0): Setting mode "NULL"
[    50.548] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    50.556] (==) NVIDIA(0): Disabling shared memory pixmaps
[    50.556] (==) NVIDIA(0): Backing store enabled
[    50.556] (==) NVIDIA(0): Silken mouse enabled
[    50.557] (==) NVIDIA(0): DPMS enabled
[    50.563] (II) Loading sub module "dri2"
[    50.563] (II) LoadModule: "dri2"
[    50.563] (II) Module "dri2" already built-in
[    50.563] (II) NVIDIA(0): [DRI2] Setup complete
[    50.563] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    50.563] (--) RandR disabled
[    50.567] (II) SELinux: Disabled on system
[    50.567] (II) Initializing extension GLX
[    50.567] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    52.755] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    52.755] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    52.755] (II) LoadModule: "evdev"
[    52.755] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.779] (II) Module evdev: vendor="X.Org Foundation"
[    52.779]    compiled for 1.16.0, module version = 2.9.0
[    52.779]    Module class: X.Org XInput Driver
[    52.779]    ABI class: X.Org XInput driver, version 21.0
[    52.779] (II) Using input driver 'evdev' for 'Power Button'
[    52.779] (**) Power Button: always reports core events
[    52.779] (**) evdev: Power Button: Device: "/dev/input/event3"
[    52.779] (--) evdev: Power Button: Vendor 0 Product 0x1
[    52.779] (--) evdev: Power Button: Found keys
[    52.779] (II) evdev: Power Button: Configuring as keyboard
[    52.779] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    52.779] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    52.779] (**) Option "xkb_rules" "evdev"
[    52.779] (**) Option "xkb_model" "pc105"
[    52.779] (**) Option "xkb_layout" "it"
[    52.781] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    52.781] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    52.781] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    52.781] (II) Using input driver 'evdev' for 'Video Bus'
[    52.781] (**) Video Bus: always reports core events
[    52.781] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    52.781] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    52.781] (--) evdev: Video Bus: Found keys
[    52.781] (II) evdev: Video Bus: Configuring as keyboard
[    52.781] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    52.781] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    52.781] (**) Option "xkb_rules" "evdev"
[    52.781] (**) Option "xkb_model" "pc105"
[    52.781] (**) Option "xkb_layout" "it"
[    52.781] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    52.781] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    52.781] (II) Using input driver 'evdev' for 'Video Bus'
[    52.781] (**) Video Bus: always reports core events
[    52.781] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    52.781] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    52.781] (--) evdev: Video Bus: Found keys
[    52.781] (II) evdev: Video Bus: Configuring as keyboard
[    52.781] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:50/LNXVIDEO:00/input/input7/event5"
[    52.781] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    52.781] (**) Option "xkb_rules" "evdev"
[    52.781] (**) Option "xkb_model" "pc105"
[    52.781] (**) Option "xkb_layout" "it"
[    52.782] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    52.782] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    52.782] (II) Using input driver 'evdev' for 'Power Button'
[    52.782] (**) Power Button: always reports core events
[    52.782] (**) evdev: Power Button: Device: "/dev/input/event1"
[    52.782] (--) evdev: Power Button: Vendor 0 Product 0x1
[    52.782] (--) evdev: Power Button: Found keys
[    52.782] (II) evdev: Power Button: Configuring as keyboard
[    52.782] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    52.782] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    52.782] (**) Option "xkb_rules" "evdev"
[    52.782] (**) Option "xkb_model" "pc105"
[    52.782] (**) Option "xkb_layout" "it"
[    52.782] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    52.782] (II) No input driver specified, ignoring this device.
[    52.782] (II) This device may have been added with another device file.
[    52.782] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    52.782] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    52.782] (II) Using input driver 'evdev' for 'Sleep Button'
[    52.782] (**) Sleep Button: always reports core events
[    52.782] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    52.782] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    52.782] (--) evdev: Sleep Button: Found keys
[    52.782] (II) evdev: Sleep Button: Configuring as keyboard
[    52.782] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    52.782] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    52.782] (**) Option "xkb_rules" "evdev"
[    52.782] (**) Option "xkb_model" "pc105"
[    52.782] (**) Option "xkb_layout" "it"
[    52.782] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event16)
[    52.782] (II) No input driver specified, ignoring this device.
[    52.782] (II) This device may have been added with another device file.
[    52.783] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event17)
[    52.783] (II) No input driver specified, ignoring this device.
[    52.783] (II) This device may have been added with another device file.
[    52.783] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event18)
[    52.783] (II) No input driver specified, ignoring this device.
[    52.783] (II) This device may have been added with another device file.
[    52.783] (II) config/udev: Adding input device Logitech M325 (/dev/input/event9)
[    52.783] (**) Logitech M325: Applying InputClass "evdev pointer catchall"
[    52.783] (II) Using input driver 'evdev' for 'Logitech M325'
[    52.783] (**) Logitech M325: always reports core events
[    52.783] (**) evdev: Logitech M325: Device: "/dev/input/event9"
[    52.783] (--) evdev: Logitech M325: Vendor 0x46d Product 0x400a
[    52.783] (--) evdev: Logitech M325: Found 20 mouse buttons
[    52.783] (--) evdev: Logitech M325: Found scroll wheel(s)
[    52.783] (--) evdev: Logitech M325: Found relative axes
[    52.783] (--) evdev: Logitech M325: Found x and y relative axes
[    52.783] (II) evdev: Logitech M325: Configuring as mouse
[    52.783] (II) evdev: Logitech M325: Adding scrollwheel support
[    52.783] (**) evdev: Logitech M325: YAxisMapping: buttons 4 and 5
[    52.783] (**) evdev: Logitech M325: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    52.783] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.2/0003:046D:C52B.0003/0003:046D:400A.0004/input/input10/event9"
[    52.783] (II) XINPUT: Adding extended input device "Logitech M325" (type: MOUSE, id 11)
[    52.783] (II) evdev: Logitech M325: initialized for relative axes.
[    52.783] (**) Logitech M325: (accel) keeping acceleration scheme 1
[    52.783] (**) Logitech M325: (accel) acceleration profile 0
[    52.783] (**) Logitech M325: (accel) acceleration factor: 2.000
[    52.783] (**) Logitech M325: (accel) acceleration threshold: 4
[    52.783] (II) config/udev: Adding input device Logitech M325 (/dev/input/mouse2)
[    52.783] (II) No input driver specified, ignoring this device.
[    52.783] (II) This device may have been added with another device file.
[    52.783] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event10)
[    52.783] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    52.783] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    52.783] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    52.783] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event10"
[    52.783] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xc45 Product 0x649d
[    52.783] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    52.783] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    52.783] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.5/3-1.5:1.0/input/input11/event10"
[    52.783] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 12)
[    52.783] (**) Option "xkb_rules" "evdev"
[    52.783] (**) Option "xkb_model" "pc105"
[    52.783] (**) Option "xkb_layout" "it"
[    52.783] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event12)
[    52.783] (II) No input driver specified, ignoring this device.
[    52.783] (II) This device may have been added with another device file.
[    52.784] (II) config/udev: Adding input device HDA Intel PCH Dock Mic (/dev/input/event13)
[    52.784] (II) No input driver specified, ignoring this device.
[    52.784] (II) This device may have been added with another device file.
[    52.784] (II) config/udev: Adding input device HDA Intel PCH Dock Line Out (/dev/input/event14)
[    52.784] (II) No input driver specified, ignoring this device.
[    52.784] (II) This device may have been added with another device file.
[    52.784] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event15)
[    52.784] (II) No input driver specified, ignoring this device.
[    52.784] (II) This device may have been added with another device file.
[    52.784] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    52.784] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    52.784] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    52.784] (**) AT Translated Set 2 keyboard: always reports core events
[    52.784] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    52.784] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    52.784] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    52.784] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    52.784] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    52.784] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    52.784] (**) Option "xkb_rules" "evdev"
[    52.784] (**) Option "xkb_model" "pc105"
[    52.784] (**) Option "xkb_layout" "it"
[    52.784] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event8)
[    52.784] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    52.784] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    52.784] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "Default clickpad buttons"
[    52.784] (II) LoadModule: "synaptics"
[    52.784] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    52.784] (II) Module synaptics: vendor="X.Org Foundation"
[    52.784]    compiled for 1.16.0, module version = 1.8.99
[    52.784]    Module class: X.Org XInput Driver
[    52.784]    ABI class: X.Org XInput driver, version 21.0
[    52.784] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    52.784] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    52.784] (**) Option "Device" "/dev/input/event8"
[    52.804] (II) synaptics: AlpsPS/2 ALPS GlidePoint: ignoring touch events for semi-multitouch device
[    52.804] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 2000 (res 25)
[    52.804] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 1400 (res 32)
[    52.804] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    52.804] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    52.804] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle double triple
[    52.804] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    52.804] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    52.804] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    52.804] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    52.820] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event8"
[    52.820] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 14)
[    52.820] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    52.820] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MaxSpeed is now 1.75
[    52.820] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) AccelFactor is now 0.082
[    52.820] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    52.820] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    52.820] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    52.820] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    52.820] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    52.820] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    52.820] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    52.820] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event7)
[    52.820] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    52.820] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    52.820] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    52.820] (**) DualPoint Stick: always reports core events
[    52.820] (**) evdev: DualPoint Stick: Device: "/dev/input/event7"
[    52.820] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    52.820] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    52.820] (--) evdev: DualPoint Stick: Found relative axes
[    52.820] (--) evdev: DualPoint Stick: Found x and y relative axes
[    52.820] (II) evdev: DualPoint Stick: Configuring as mouse
[    52.820] (**) Option "Emulate3Buttons" "true"
[    52.820] (**) Option "EmulateWheel" "true"
[    52.820] (**) Option "EmulateWheelButton" "2"
[    52.820] (**) Option "YAxisMapping" "4 5"
[    52.820] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    52.820] (**) Option "XAxisMapping" "6 7"
[    52.820] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    52.820] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    52.820] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event7"
[    52.820] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 15)
[    52.821] (II) evdev: DualPoint Stick: initialized for relative axes.
[    52.821] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    52.821] (**) DualPoint Stick: (accel) acceleration profile 0
[    52.821] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    52.821] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    52.821] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse0)
[    52.821] (II) No input driver specified, ignoring this device.
[    52.821] (II) This device may have been added with another device file.
[    52.821] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event11)
[    52.821] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    52.821] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    52.821] (**) Dell WMI hotkeys: always reports core events
[    52.821] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event11"
[    52.821] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    52.822] (--) evdev: Dell WMI hotkeys: Found keys
[    52.822] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    52.822] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event11"
[    52.822] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 16)
[    52.822] (**) Option "xkb_rules" "evdev"
[    52.822] (**) Option "xkb_model" "pc105"
[    52.822] (**) Option "xkb_layout" "it"
[    53.293] (II) intel(G0): EDID vendor "AUO", prod id 8685
[    53.293] (II) intel(G0): Printing DDC gathered Modelines:
[    53.293] (II) intel(G0): Modeline "1920x1080"x0.0  140.00  1920 1968 2068 2082  1080 1090 1100 1120 +hsync -vsync (67.2 kHz eP)
[    53.293] (II) intel(G0): Modeline "1920x1080"x0.0  140.00  1920 1968 2068 2520  1080 1090 1100 1388 +hsync -vsync (55.6 kHz e)
[    53.294] reporting 8 11 17 141
[    53.344] have a master to look out for
[    53.344] adjust shatters 0 1920
[    53.347] need to create shared pixmap 1(II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    53.602] reporting 8 11 17 141
[    53.607] reporting 8 11 17 141
[    53.608] have a master to look out for
[    53.610] need to create shared pixmap 1reporting 8 11 17 141
[    54.706] reporting 8 11 17 141
[    54.753] have a master to look out for
[    54.753] adjust shatters 0 1920
[    54.755] need to create shared pixmap 1(II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    80.353] (II) NVIDIA(0): Setting mode "NULL"
[    80.382] (II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    80.412] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    90.944] (II) NVIDIA(0): Setting mode "NULL"
[    90.969] (II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    90.989] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[   252.354] (II) NVIDIA(0): Setting mode "NULL"
[   252.411] (II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[   252.439] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found

```

---

### Post by J_Me on 2015-08-13
Hey, I have a couple of questions. What's 'nvidia dev repository' is that from Nvidia's official website. Have you had the nividia card running yet with cuda 7.0 and did you compile cuda 7.0 yourself, if you did you may need to recompile it after every kernel/ubuntu update.  But Nvidia's proprietary driver in ubuntu's repository already gives you access to your cuda cores so no need for extra software or compiling.

---

### Post by giacof on 2015-08-13
> **J_Me said:**
> Hey, I have a couple of questions. What's 'nvidia dev repository' is that from Nvidia's official website. Have you had the nividia card running yet with cuda 7.0 and did you compile cuda 7.0 yourself, if you did you may need to recompile it after every kernel/ubuntu update.  But Nvidia's proprietary driver in ubuntu's repository already gives you access to your cuda cores so no need for extra software or compiling.

yes, it's from Nvidia's official website. To be more precise, it's for Ubuntu 14.10 as there is no repository for 15.04. I never tried to compile cuda driver myself, anyway I used the extra repository because Ubuntu's official one contains an outdated Cuda version (namely 6.5)

---

### Post by J_Me on 2015-08-14
```
dmesg extract:
[   28.210156] nvidia: module license 'NVIDIA' taints kernel.
[   28.210159] Disabling lock debugging due to kernel taint
[   28.212155] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
```It seems the kernel is looking for some unique number/thing for nvidia's closed source proprietary driver which it isn't getting, this maybe because you added the cuda 7.0 module, I could be wrong as I'm no expert. Hopefully someone with better knowledge can help.

Good luck with your project

---

