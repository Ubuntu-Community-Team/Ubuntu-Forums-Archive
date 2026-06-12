---
title: "Nvidia GeForce GTX 650"
date: 2013-06-26
forum: Hardware
---

### Post by djpemberton on 2013-06-26
My system acts very "laggy," even when doing minimal tasks. So, I decided to check for different drivers. I opened up Jockey and saw that an NVIDIA driver was selected (green dot), but "No proprietary drivers are in use on this system" was written at the top, and "this driver is activated but not currently in use" at the bottom. I tried to change NVIDIA drivers from Jockey, restarted, but no change in this. As per another thread, 

lspci | grep nVidia

returns nothing, and


sudo lshw -C display

returns

*-display               
       description: VGA compatible controller
       product: GK107 [GeForce GTX 650]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

Is there a problem? and what is the solution?

Kubuntu 13.04

Hardware:
Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz1600.00MHz
8GB RAM
NVIDIA GeForce GTX 650

---

### Post by djpemberton on 2013-06-26
Also my fps in glxgears is around 59. Is that normal?

---

### Post by djpemberton on 2013-06-26
Not good. I was going to try my hand at installing it from the command line, so I uninstalled the driver and rebooted. Now it will only boot to a terminal, and I didn't think about only having wireless wpa Internet that I cannot connect to physically!!

---

### Post by djpemberton on 2013-06-26
Don't mean to bump this -- really. Just giving a status update. I'm back up and running with only the original problem still remaining. I guess it is just a bug? What could be making my mouse lag so much? I've tweaked the mouse settings here and there, to no avail.

---

### Post by Yellow Pasque on 2013-06-26
Post your /var/log/Xorg.0.log

> **djpemberton said:**
> Also my fps in glxgears is around 59. Is that normal?
Yes, it's synced to monitor refresh (60Hz). glxgears is not a benchmark...

---

### Post by djpemberton on 2013-06-27
Yes. I understand that now. Any advice for the driver issue?
thanks.

---

### Post by Yellow Pasque on 2013-06-27
> **djpemberton said:**
> Any advice for the driver issue?
...
> Post your /var/log/Xorg.0.log

---

### Post by djpemberton on 2013-06-28
```
[    30.251] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    30.251] X Protocol Version 11, Revision 0
[    30.251] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    30.251] Current Operating System: Linux derrick-Lenovo-Kubuntu 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64
[    30.251] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=09e27e6f-9c51-4384-ad88-873295012a02 ro quiet splash
[    30.251] Build Date: 17 April 2013  10:43:13PM
[    30.251] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    30.251] Current version of pixman: 0.28.2
[    30.251]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    30.251] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.251] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 28 08:44:51 2013
[    30.252] (==) Using config file: "/etc/X11/xorg.conf"
[    30.252] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.252] (==) ServerLayout "Layout0"
[    30.252] (**) |-->Screen "Screen0" (0)
[    30.252] (**) |   |-->Monitor "Monitor0"
[    30.252] (**) |   |-->Device "Device0"
[    30.252] (**) |-->Input Device "Keyboard0"
[    30.252] (**) |-->Input Device "Mouse0"
[    30.252] (**) Option "Xinerama" "0"
[    30.252] (==) Automatically adding devices
[    30.252] (==) Automatically enabling devices
[    30.252] (==) Automatically adding GPU devices
[    30.252] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.252]     Entry deleted from font path.
[    30.252] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.252]     Entry deleted from font path.
[    30.252] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.252]     Entry deleted from font path.
[    30.252] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.252]     Entry deleted from font path.
[    30.252] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.252]     Entry deleted from font path.
[    30.252] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    30.252]     Entry deleted from font path.
[    30.252] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    30.252] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.252] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    30.252] (WW) Disabling Keyboard0
[    30.252] (WW) Disabling Mouse0
[    30.252] (II) Loader magic: 0x7f0bf5678d20
[    30.252] (II) Module ABI versions:
[    30.252]     X.Org ANSI C Emulation: 0.4
[    30.252]     X.Org Video Driver: 13.1
[    30.252]     X.Org XInput driver : 18.0
[    30.252]     X.Org Server Extension : 7.0
[    30.253] (--) PCI:*(0:1:0:0) 10de:0fc6:1043:843e rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    30.253] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.253] Initializing built-in extension Generic Event Extension
[    30.253] Initializing built-in extension SHAPE
[    30.253] Initializing built-in extension MIT-SHM
[    30.253] Initializing built-in extension XInputExtension
[    30.253] Initializing built-in extension XTEST
[    30.253] Initializing built-in extension BIG-REQUESTS
[    30.253] Initializing built-in extension SYNC
[    30.253] Initializing built-in extension XKEYBOARD
[    30.253] Initializing built-in extension XC-MISC
[    30.253] Initializing built-in extension SECURITY
[    30.253] Initializing built-in extension XINERAMA
[    30.253] Initializing built-in extension XFIXES
[    30.253] Initializing built-in extension RENDER
[    30.253] Initializing built-in extension RANDR
[    30.253] Initializing built-in extension COMPOSITE
[    30.253] Initializing built-in extension DAMAGE
[    30.253] Initializing built-in extension MIT-SCREEN-SAVER
[    30.253] Initializing built-in extension DOUBLE-BUFFER
[    30.253] Initializing built-in extension RECORD
[    30.253] Initializing built-in extension DPMS
[    30.253] Initializing built-in extension X-Resource
[    30.253] Initializing built-in extension XVideo
[    30.253] Initializing built-in extension XVideo-MotionCompensation
[    30.253] Initializing built-in extension SELinux
[    30.253] Initializing built-in extension XFree86-VidModeExtension
[    30.253] Initializing built-in extension XFree86-DGA
[    30.253] Initializing built-in extension XFree86-DRI
[    30.253] Initializing built-in extension DRI2
[    30.253] (II) LoadModule: "glx"
[    30.253] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.463] (II) Module glx: vendor="NVIDIA Corporation"
[    30.463]     compiled for 4.0.2, module version = 1.0.0
[    30.463]     Module class: X.Org Server Extension
[    30.463] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    30.463] Loading extension GLX
[    30.463] (II) LoadModule: "nvidia"
[    30.463] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.464] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.464]     compiled for 4.0.2, module version = 1.0.0
[    30.464]     Module class: X.Org Video Driver
[    30.464] (II) NVIDIA dlloader X Driver  304.88  Wed Mar 27 14:28:14 PDT 2013
[    30.464] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.464] (++) using VT number 7

[    30.469] (II) Loading sub module "fb"
[    30.469] (II) LoadModule: "fb"
[    30.543] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.543] (II) Module fb: vendor="X.Org Foundation"
[    30.543]     compiled for 1.13.3, module version = 1.0.0
[    30.543]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.543] (II) Loading sub module "wfb"
[    30.543] (II) LoadModule: "wfb"
[    30.543] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.543] (II) Module wfb: vendor="X.Org Foundation"
[    30.543]     compiled for 1.13.3, module version = 1.0.0
[    30.543]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.543] (II) Loading sub module "ramdac"
[    30.544] (II) LoadModule: "ramdac"
[    30.544] (II) Module "ramdac" already built-in
[    30.544] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    30.544] (==) NVIDIA(0): RGB weight 888
[    30.544] (==) NVIDIA(0): Default visual is TrueColor
[    30.544] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.544] (**) NVIDIA(0): Option "Stereo" "0"
[    30.544] (**) NVIDIA(0): Option "nvidiaXineramaInfoOrder" "DFP-1"
[    30.544] (**) NVIDIA(0): Stereo disabled by request
[    30.544] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +1920+0, DFP: nvidia-auto-select +0+0"
[    30.544] (**) NVIDIA(0): Enabling 2D acceleration
[    31.094] (II) NVIDIA(GPU-0): Display (AOC 2262w (CRT-0)) does not support NVIDIA 3D Vision
[    31.094] (II) NVIDIA(GPU-0):     stereo.
[    31.104] (II) NVIDIA(GPU-0): Display (AOC 2262w (DFP-1)) does not support NVIDIA 3D Vision
[    31.104] (II) NVIDIA(GPU-0):     stereo.
[    31.104] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 650 (GK107) at PCI:1:0:0 (GPU-0)
[    31.104] (--) NVIDIA(0): Memory: 2097152 kBytes
[    31.104] (--) NVIDIA(0): VideoBIOS: 80.07.35.00.1d
[    31.104] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.104] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.107] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 650 at PCI:1:0:0
[    31.107] (--) NVIDIA(0):     AOC 2262w (CRT-0) (connected)
[    31.107] (--) NVIDIA(0):     DFP-0
[    31.107] (--) NVIDIA(0):     AOC 2262w (DFP-1) (connected)
[    31.107] (--) NVIDIA(0): AOC 2262w (CRT-0): 400.0 MHz maximum pixel clock
[    31.107] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.107] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.107] (--) NVIDIA(0): AOC 2262w (DFP-1): 165.0 MHz maximum pixel clock
[    31.107] (--) NVIDIA(0): AOC 2262w (DFP-1): Internal Single Link TMDS
[    31.107] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.107] (**) NVIDIA(0):     device AOC 2262w (CRT-0) (Using EDID frequencies has been
[    31.107] (**) NVIDIA(0):     enabled on all display devices.)
[    31.108] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.108] (**) NVIDIA(0):     device AOC 2262w (DFP-1) (Using EDID frequencies has been
[    31.108] (**) NVIDIA(0):     enabled on all display devices.)
[    31.109] (WW) NVIDIA(GPU-0): The EDID for AOC 2262w (DFP-1) contradicts itself: mode
[    31.109] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    31.109] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-83.000 kHz) would exclude
[    31.109] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    31.109] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    31.110] (II) NVIDIA(0): Validated MetaModes:
[    31.110] (II) NVIDIA(0):    
[    31.110] (II) NVIDIA(0):     "CRT:nvidia-auto-select+1920+0,DFP:nvidia-auto-select+0+0"
[    31.110] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1080
[    31.133] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[    31.133] (--) NVIDIA(0):     option
[    31.133] (--) Depth 24 pixmap format is 32 bpp
[    31.133] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    31.133] (II) NVIDIA:     access.
[    31.138] (II) NVIDIA(0): Setting mode "CRT:nvidia-auto-select+1920+0,DFP:nvidia-auto-select+0+0"
[    31.243] Loading extension NV-GLX
[    31.296] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.296] (==) NVIDIA(0): Backing store disabled
[    31.296] (==) NVIDIA(0): Silken mouse enabled
[    31.296] (**) NVIDIA(0): DPMS enabled
[    31.296] Loading extension NV-CONTROL
[    31.297] Loading extension XINERAMA
[    31.297] (II) Loading sub module "dri2"
[    31.297] (II) LoadModule: "dri2"
[    31.297] (II) Module "dri2" already built-in
[    31.297] (II) NVIDIA(0): [DRI2] Setup complete
[    31.297] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.297] (--) RandR disabled
[    31.299] (II) SELinux: Disabled on system
[    31.300] (II) Initializing extension GLX
[    31.310] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.311] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.311] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.311] (II) LoadModule: "evdev"
[    31.317] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.328] (II) Module evdev: vendor="X.Org Foundation"
[    31.328]     compiled for 1.13.3, module version = 2.7.3
[    31.328]     Module class: X.Org XInput Driver
[    31.328]     ABI class: X.Org XInput driver, version 18.0
[    31.328] (II) Using input driver 'evdev' for 'Power Button'
[    31.328] (**) Power Button: always reports core events
[    31.328] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.328] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.328] (--) evdev: Power Button: Found keys
[    31.328] (II) evdev: Power Button: Configuring as keyboard
[    31.328] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.328] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.328] (**) Option "xkb_rules" "evdev"
[    31.328] (**) Option "xkb_model" "pc105"
[    31.328] (**) Option "xkb_layout" "us"
[    31.328] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.328] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.328] (II) Using input driver 'evdev' for 'Power Button'
[    31.328] (**) Power Button: always reports core events
[    31.328] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.328] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.328] (--) evdev: Power Button: Found keys
[    31.328] (II) evdev: Power Button: Configuring as keyboard
[    31.328] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    31.328] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.328] (**) Option "xkb_rules" "evdev"
[    31.328] (**) Option "xkb_model" "pc105"
[    31.328] (**) Option "xkb_layout" "us"
[    31.329] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event13)
[    31.329] (II) No input driver specified, ignoring this device.
[    31.329] (II) This device may have been added with another device file.
[    31.329] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[    31.329] (II) No input driver specified, ignoring this device.
[    31.329] (II) This device may have been added with another device file.
[    31.329] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event15)
[    31.329] (II) No input driver specified, ignoring this device.
[    31.329] (II) This device may have been added with another device file.
[    31.329] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v7.0 (/dev/input/event2)
[    31.329] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: Applying InputClass "evdev keyboard catchall"
[    31.329] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v7.0'
[    31.329] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: always reports core events
[    31.329] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Device: "/dev/input/event2"
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Vendor 0x45e Product 0x745
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found keys
[    31.329] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Configuring as keyboard
[    31.329] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2/event2"
[    31.329] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v7.0" (type: KEYBOARD, id 8)
[    31.329] (**) Option "xkb_rules" "evdev"
[    31.329] (**) Option "xkb_model" "pc105"
[    31.329] (**) Option "xkb_layout" "us"
[    31.329] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v7.0 (/dev/input/event3)
[    31.329] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: Applying InputClass "evdev pointer catchall"
[    31.329] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: Applying InputClass "evdev keyboard catchall"
[    31.329] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v7.0'
[    31.329] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: always reports core events
[    31.329] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Device: "/dev/input/event3"
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Vendor 0x45e Product 0x745
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found 9 mouse buttons
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found scroll wheel(s)
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found relative axes
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found x and y relative axes
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found absolute axes
[    31.329] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Forcing absolute x/y axes to exist.
[    31.329] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found keys
[    31.329] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Configuring as mouse
[    31.329] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Configuring as keyboard
[    31.329] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Adding scrollwheel support
[    31.329] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: YAxisMapping: buttons 4 and 5
[    31.329] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.329] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input3/event3"
[    31.329] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v7.0" (type: KEYBOARD, id 9)
[    31.329] (**) Option "xkb_rules" "evdev"
[    31.329] (**) Option "xkb_model" "pc105"
[    31.329] (**) Option "xkb_layout" "us"
[    31.329] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: initialized for relative axes.
[    31.329] (WW) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: ignoring absolute axes.
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) keeping acceleration scheme 1
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) acceleration profile 0
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) acceleration factor: 2.000
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) acceleration threshold: 4
[    31.330] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v7.0 (/dev/input/mouse0)
[    31.330] (II) No input driver specified, ignoring this device.
[    31.330] (II) This device may have been added with another device file.
[    31.330] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v7.0 (/dev/input/event4)
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: Applying InputClass "evdev keyboard catchall"
[    31.330] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v7.0'
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: always reports core events
[    31.330] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Device: "/dev/input/event4"
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Vendor 0x45e Product 0x745
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found 1 mouse buttons
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found scroll wheel(s)
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found relative axes
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found absolute axes
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found absolute multitouch axes
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found x and y absolute axes
[    31.330] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Found keys
[    31.330] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Forcing relative x/y axes to exist.
[    31.330] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Configuring as mouse
[    31.330] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Configuring as keyboard
[    31.330] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: Adding scrollwheel support
[    31.330] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: YAxisMapping: buttons 4 and 5
[    31.330] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.330] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.2/input/input4/event4"
[    31.330] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v7.0" (type: KEYBOARD, id 10)
[    31.330] (**) Option "xkb_rules" "evdev"
[    31.330] (**) Option "xkb_model" "pc105"
[    31.330] (**) Option "xkb_layout" "us"
[    31.330] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: initialized for relative axes.
[    31.330] (WW) evdev: Microsoft Microsoft® 2.4GHz Transceiver v7.0: ignoring absolute axes.
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) keeping acceleration scheme 1
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) acceleration profile 0
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) acceleration factor: 2.000
[    31.330] (**) Microsoft Microsoft® 2.4GHz Transceiver v7.0: (accel) acceleration threshold: 4
[    31.330] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v7.0 (/dev/input/js0)
[    31.330] (II) No input driver specified, ignoring this device.
[    31.330] (II) This device may have been added with another device file.
[    31.330] (II) config/udev: Adding input device HD Webcam C615 (/dev/input/event5)
[    31.330] (**) HD Webcam C615: Applying InputClass "evdev keyboard catchall"
[    31.330] (II) Using input driver 'evdev' for 'HD Webcam C615'
[    31.330] (**) HD Webcam C615: always reports core events
[    31.330] (**) evdev: HD Webcam C615: Device: "/dev/input/event5"
[    31.330] (--) evdev: HD Webcam C615: Vendor 0x46d Product 0x82c
[    31.330] (--) evdev: HD Webcam C615: Found keys
[    31.330] (II) evdev: HD Webcam C615: Configuring as keyboard
[    31.330] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/input/input5/event5"
[    31.330] (II) XINPUT: Adding extended input device "HD Webcam C615" (type: KEYBOARD, id 11)
[    31.330] (**) Option "xkb_rules" "evdev"
[    31.330] (**) Option "xkb_model" "pc105"
[    31.330] (**) Option "xkb_layout" "us"
[    31.331] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event10)
[    31.331] (II) No input driver specified, ignoring this device.
[    31.331] (II) This device may have been added with another device file.
[    31.331] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event11)
[    31.331] (II) No input driver specified, ignoring this device.
[    31.331] (II) This device may have been added with another device file.
[    31.331] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event12)
[    31.331] (II) No input driver specified, ignoring this device.
[    31.331] (II) This device may have been added with another device file.
[    31.331] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[    31.331] (II) No input driver specified, ignoring this device.
[    31.331] (II) This device may have been added with another device file.
[    31.331] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[    31.331] (II) No input driver specified, ignoring this device.
[    31.331] (II) This device may have been added with another device file.
[    31.331] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[    31.331] (II) No input driver specified, ignoring this device.
[    31.331] (II) This device may have been added with another device file.
[    31.331] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[    31.331] (II) No input driver specified, ignoring this device.
[    31.331] (II) This device may have been added with another device file.
[    46.698] (II) NVIDIA(GPU-0): Display (AOC 2262w (CRT-0)) does not support NVIDIA 3D Vision
[    46.698] (II) NVIDIA(GPU-0):     stereo.
[    46.698] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.698] (**) NVIDIA(0):     device AOC 2262w (CRT-0) (Using EDID frequencies has been
[    46.698] (**) NVIDIA(0):     enabled on all display devices.)
[    46.708] (II) NVIDIA(GPU-0): Display (AOC 2262w (DFP-1)) does not support NVIDIA 3D Vision
[    46.708] (II) NVIDIA(GPU-0):     stereo.
[    46.708] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.708] (**) NVIDIA(0):     device AOC 2262w (DFP-1) (Using EDID frequencies has been
[    46.708] (**) NVIDIA(0):     enabled on all display devices.)
[    46.709] (WW) NVIDIA(GPU-0): The EDID for AOC 2262w (DFP-1) contradicts itself: mode
[    46.709] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    46.709] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-83.000 kHz) would exclude
[    46.709] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    46.709] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    46.748] (II) NVIDIA(GPU-0): Display (AOC 2262w (CRT-0)) does not support NVIDIA 3D Vision
[    46.748] (II) NVIDIA(GPU-0):     stereo.
[    46.748] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.748] (**) NVIDIA(0):     device AOC 2262w (CRT-0) (Using EDID frequencies has been
[    46.748] (**) NVIDIA(0):     enabled on all display devices.)
[    46.759] (II) NVIDIA(GPU-0): Display (AOC 2262w (DFP-1)) does not support NVIDIA 3D Vision
[    46.759] (II) NVIDIA(GPU-0):     stereo.
[    46.759] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.759] (**) NVIDIA(0):     device AOC 2262w (DFP-1) (Using EDID frequencies has been
[    46.759] (**) NVIDIA(0):     enabled on all display devices.)
[    46.759] (WW) NVIDIA(GPU-0): The EDID for AOC 2262w (DFP-1) contradicts itself: mode
[    46.759] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    46.759] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-83.000 kHz) would exclude
[    46.759] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    46.759] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[    46.928] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    46.940] (II) XKB: reuse xkmfile /var/lib/xkb/server-F07ECF8A7578B0AD11EB22124C91B69AEC5C0640.xkm
[    47.270] (II) NVIDIA(GPU-0): Display (AOC 2262w (CRT-0)) does not support NVIDIA 3D Vision
[    47.270] (II) NVIDIA(GPU-0):     stereo.
[    47.270] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    47.270] (**) NVIDIA(0):     device AOC 2262w (CRT-0) (Using EDID frequencies has been
[    47.270] (**) NVIDIA(0):     enabled on all display devices.)
[    47.285] (II) NVIDIA(GPU-0): Display (AOC 2262w (DFP-1)) does not support NVIDIA 3D Vision
[    47.285] (II) NVIDIA(GPU-0):     stereo.
[    47.285] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    47.285] (**) NVIDIA(0):     device AOC 2262w (DFP-1) (Using EDID frequencies has been
[    47.285] (**) NVIDIA(0):     enabled on all display devices.)
[    47.286] (WW) NVIDIA(GPU-0): The EDID for AOC 2262w (DFP-1) contradicts itself: mode
[    47.286] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[    47.286] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-83.000 kHz) would exclude
[    47.286] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[    47.286] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[  1944.025] (II) XKB: reuse xkmfile /var/lib/xkb/server-E184E0E9F2CAE941E9AD964632128A5B0C5E7771.xkm
[  2666.925] (II) XKB: reuse xkmfile /var/lib/xkb/server-E184E0E9F2CAE941E9AD964632128A5B0C5E7771.xkm
[  4726.598] (II) XKB: reuse xkmfile /var/lib/xkb/server-E184E0E9F2CAE941E9AD964632128A5B0C5E7771.xkm
```

---

### Post by Yellow Pasque on 2013-06-28
The log looks fine and the nvidia driver is in use. I'm not sure why Jockey says it's not.
As for the cursor issue, I would look at the Kwin/Desktop Effects settings. Are you using XRender or OpenGL?

The other possibility is using the latest driver: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by djpemberton on 2013-06-29
I'm using OpenGL, because I believe it was required for Google Earth, which I use almost daily. I may try the latest drivers, though I have a feeling they won't fix the Jockey issue. As long as those that I have are engaged and working relatively well, I don't know that it would be wise to try anything different. ??

---

### Post by djpemberton on 2013-07-01
I am noticing that the lag is happening in association with some programs more than others. Firefox 22.0 seems to slow the system down more than most other software I commonly use. This happens even when it doesn't appear to be loading anything or doing any significant work. The mouse pointer lags most when it is over the FF window. However, some lag happens also with LibreOffice 4.0.2.2. I use these programs more than any others. It could be that it would happen with nearly any software open. These are just my most used apps, so I notice it more.

It seems like my system should be able to handle these better. Is there something I could do to make this better? I don't have a large amount of effects toggled on.

I am not a hardware guru (obviously). What would be most likely at fault with these issues. My Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz1600.00MHz, low RAM (8GB), my NVIDIA GeForce GTX 650 card, or software?

UPDATE: OK, my whole system is definitely laggy with almost any program at all  open -- even Dolphin! When I try to actually do anything with several  programs open, I either can't, or it is extraordinarily slow. Why would  this be?

---

### Post by dannyboy79 on 2013-07-01
you have a very compotent computer as far as hardware goes so it's got to be something with your configuration. What nvidia driver are you using? Also, any reason you're still using 11.04?

I am running 12.04 on a core2duo 1.8Ghz with only 2GB of DDRII ram and my machine doesn't suffer any lag. I am using Xubuntu because I don't like Unity but your hardware should be able to handle Unity just fine. Are you using Compiz or any other compositing software?

---

### Post by djpemberton on 2013-07-01
LOL. Sorry, I am using Kubuntu 13.04. I just have not maintained my ubuntuforums profile well! I am using whatever effects software is already built into Kubuntu 13.04. I haven't added anything in that regard. It is not Compiz.

---

### Post by dannyboy79 on 2013-07-01
it appears you're running Nvidia driver 304.88, have you tried out 319.32?

---

### Post by djpemberton on 2013-07-01
I may have to.

---

### Post by djpemberton on 2013-07-01
OK. I have installed 319.32. I'll let you know how it goes. Everything booted up fine, so that's a start!

---

### Post by djpemberton on 2013-07-02
No improvement with the updated driver. Everything is functioning, or not, exactly as it was before. I have had the System Monitor open while I work. I almost always have several programs open at once (usually Firefox, a LibreOffice program, and Scribus or something else). However, the lag can happen even if I only have one open. Back to the System Monitor: during times of extreme lag, I am not noticing any peculiar spike in CPU% or Memory usage (consider my limited knowledge though). No program is usually getting above 4% of CPU usage (whatever I am active on will usually hover around 1-2%, though FF can spike to 10% when opening a page, etc.). Swap is never being used. Memory usage stays close to 1.7GB out of 8GB. I am not sure what I should expect with any of these figures. It does seem excessive that there are 241 processes listed. It doesn't look like most of them are active. What should I expect with any of these? Is anything looking out of the ordinary to anybody? Could it just be a KDE issue?

---

### Post by djpemberton on 2013-07-03
Update: Perhaps in ignorance about how these things work, I installed another desktop environment -- Cinnamon. I tried that for a few minutes, as well as Unity (which was already installed). I noticed the same lagging in both of them! This is so frustrating. It is extraordinarily distracting and time consuming. I'm not sure what the next steps would be. A totally different distro? Something else?

---

### Post by djpemberton on 2013-07-04
Problem solved?! It appears to have been my bluetooth mouse and keyboard--or Kubuntu's handling of the bluetooth. I have a new bluetooth keyboard and mouse (got it when I got the computer). The batteries are fresh in them. However, I began to realize that the lagginess was really only experienced in relation to the mouse pointer and typing. Programs were opening and closing fine, as was the operating system. So, I purchased a cheap usb mouse and keyboard set, plugged it in, and ceased to experience problems! Is there any way I can easily test to see if the problem is the OS's handling of bluetooth or my bluetooth devices themselves? Once I do that, I can perhaps mark this as solved.

---

### Post by djpemberton on 2013-07-05
Problem definitely solved. I move the bluetooth adapter to the front of my computer. Since then, no more lagging! Feel kinda dumb, but it is solved! Good enough trade-off for me!

---

