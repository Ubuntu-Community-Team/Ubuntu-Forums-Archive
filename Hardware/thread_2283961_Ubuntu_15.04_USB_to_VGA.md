---
title: "Ubuntu 15.04 USB to VGA"
date: 2015-06-26
forum: Hardware
---

### Post by s7p4-justin on 2015-06-26
Hi I have been trying to get my USB to VGA working for sometime and have had no success.

I am running 64 bit Ubuntu 15.04 and trying to use the Eclipse SEE2 UV150 USB to VGA hardware with my computer.

When I plug it in use lsusb I get the following (the red line is the device):

```
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
[COLOR=#800000]Bus 002 Device 006: ID 0711:5100 Magic Control Technology Corp. Magic Control Technology Corp. (USB2VGA dongle)[/COLOR]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a006 Alcor Micro Corp. 
Bus 001 Device 009: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 008: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Running dmesg I get the following just after plugging it in:

```
[181480.679602] usb 2-1.2: new high-speed USB device number 7 using ehci-pci
[181480.773853] usb 2-1.2: New USB device found, idVendor=0711, idProduct=5100
[181480.773864] usb 2-1.2: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[181480.773870] usb 2-1.2: Product: USBVGA
[181480.773874] usb 2-1.2: Manufacturer: MCT CORP
```

I am not getting any response from my monitor that is plugged into the device. I have looked at some of the following threads:

[http://ubuntuforums.org/showthread.php?t=260863](http://ubuntuforums.org/showthread.php?t=260863)
[http://ubuntuforums.org/showthread.php?t=988298](http://ubuntuforums.org/showthread.php?t=988298)

but I have not been able to solve my problem from them. 

It seems I must use the sisusbvga driver but I believe it is already installed by default with the Linux kernel.

I'm not very tech-savy when it comes to hardware and would appreciate any help anyone could offer

---

### Post by dino99 on 2015-06-26
is the xserver-xorg-video-sisusb driver installed ?
it should be good to also know what the journalctl output is about that device, and also glance at 
xorg.0.log

---

### Post by s7p4-justin on 2015-06-26
> **dino99 said:**
> is the xserver-xorg-video-sisusb driver installed ?
it should be good to also know what the journalctl output is about that device, and also glance at 
xorg.0.log


Yes the [COLOR=#000000]xserver-xorg-video-sisusb driver is installed and up to date on my computer.

the output to journalctl is the following when attaching the USB to VGA device:

[/COLOR]```
Jun 26 17:46:20 Barbara kernel: [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:c2f8:daff:fea7:91a5 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Jun 26 17:46:20 Barbara kernel: [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:c2f8:daff:fea7:91a5 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Jun 26 17:46:27 Barbara kernel: usb 2-1.2: new high-speed USB device number 8 using ehci-pci
Jun 26 17:46:27 Barbara kernel: usb 2-1.2: New USB device found, idVendor=0711, idProduct=5100
Jun 26 17:46:27 Barbara kernel: usb 2-1.2: New USB device strings: Mfr=16, Product=32, SerialNumber=0
Jun 26 17:46:27 Barbara kernel: usb 2-1.2: Product: USBVGA
Jun 26 17:46:27 Barbara kernel: usb 2-1.2: Manufacturer: MCT CORP 
Jun 26 17:46:27 Barbara mtp-probe[26218]: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Jun 26 17:46:27 Barbara mtp-probe[26218]: bus: 2, device: 8 was not an MTP device
Jun 26 17:46:28 Barbara kernel: [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:c2f8:daff:fea7:91a5 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Jun 26 17:46:28 Barbara kernel: [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:c2f8:daff:fea7:91a5 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24 



```

my Xorg.0.log contained the following, I'm not sure what exactly you would like to view from this so I just copied the whole thing.

```
[    39.714] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    39.714] X Protocol Version 11, Revision 0
[    39.714] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    39.714] Current Operating System: Linux Barbara 3.19.0-21-generic #21-Ubuntu SMP Sun Jun 14 18:31:11 UTC 2015 x86_64
[    39.714] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-21-generic root=UUID=a105564f-b129-401d-a3b4-778bd02119f8 ro quiet splash acpi_backlight=vendor vt.handoff=7
[    39.715] Build Date: 19 March 2015  09:26:59AM
[    39.715] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[    39.715] Current version of pixman: 0.32.6
[    39.715]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    39.715] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    39.715] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 23 20:16:26 2015
[    39.822] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    39.965] (==) No Layout section.  Using the first Screen section.
[    39.965] (==) No screen section available. Using defaults.
[    39.965] (**) |-->Screen "Default Screen Section" (0)
[    39.965] (**) |   |-->Monitor "<default monitor>"
[    39.966] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    39.966] (==) Automatically adding devices
[    39.966] (==) Automatically enabling devices
[    39.966] (==) Automatically adding GPU devices
[    40.002] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    40.002]     Entry deleted from font path.
[    40.002] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    40.002]     Entry deleted from font path.
[    40.002] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    40.002]     Entry deleted from font path.
[    40.006] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    40.006]     Entry deleted from font path.
[    40.006] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    40.006]     Entry deleted from font path.
[    40.006] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    40.006] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    40.006] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    40.041] (II) Loader magic: 0x7f7023887d80
[    40.041] (II) Module ABI versions:
[    40.041]     X.Org ANSI C Emulation: 0.4
[    40.041]     X.Org Video Driver: 19.0
[    40.041]     X.Org XInput driver : 21.0
[    40.041]     X.Org Server Extension : 9.0
[    40.041] (II) xfree86: Adding drm device (/dev/dri/card0)
[    40.042] (--) PCI:*(0:0:2:0) 8086:0106:17aa:3975 rev 9, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00003000/64
[    40.076] (II) LoadModule: "glx"
[    40.362] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    41.313] (II) Module glx: vendor="X.Org Foundation"
[    41.313]     compiled for 1.17.1, module version = 1.0.0
[    41.313]     ABI class: X.Org Server Extension, version 9.0
[    41.313] (==) AIGLX enabled
[    41.313] (==) Matched intel as autoconfigured driver 0
[    41.313] (==) Matched intel as autoconfigured driver 1
[    41.313] (==) Matched modesetting as autoconfigured driver 2
[    41.313] (==) Matched fbdev as autoconfigured driver 3
[    41.313] (==) Matched vesa as autoconfigured driver 4
[    41.313] (==) Assigned the driver to the xf86ConfigLayout
[    41.313] (II) LoadModule: "intel"
[    41.313] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    41.461] (II) Module intel: vendor="X.Org Foundation"
[    41.461]     compiled for 1.17.1, module version = 2.99.917
[    41.461]     Module class: X.Org Video Driver
[    41.461]     ABI class: X.Org Video Driver, version 19.0
[    41.461] (II) LoadModule: "modesetting"
[    41.461] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    41.557] (II) Module modesetting: vendor="X.Org Foundation"
[    41.557]     compiled for 1.17.1, module version = 1.17.1
[    41.557]     Module class: X.Org Video Driver
[    41.557]     ABI class: X.Org Video Driver, version 19.0
[    41.557] (II) LoadModule: "fbdev"
[    41.557] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    41.613] (II) Module fbdev: vendor="X.Org Foundation"
[    41.613]     compiled for 1.17.1, module version = 0.4.4
[    41.613]     Module class: X.Org Video Driver
[    41.613]     ABI class: X.Org Video Driver, version 19.0
[    41.613] (II) LoadModule: "vesa"
[    41.613] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    41.654] (II) Module vesa: vendor="X.Org Foundation"
[    41.654]     compiled for 1.17.1, module version = 2.3.3
[    41.654]     Module class: X.Org Video Driver
[    41.654]     ABI class: X.Org Video Driver, version 19.0
[    41.654] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    41.654] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    41.654] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    41.654] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    41.654] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    41.654] (II) FBDEV: driver for framebuffer: fbdev
[    41.654] (II) VESA: driver for VESA chipsets: vesa
[    41.654] (++) using VT number 7


[    41.684] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[    41.684] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917-1~exp1ubuntu2.2 (Alessio Treglia <quadrispro@ubuntu.com>)
[    41.684] (II) intel(0): SNA compiled for use with valgrind
[    41.711] (WW) Falling back to old probe method for modesetting
[    41.711] (WW) Falling back to old probe method for fbdev
[    41.711] (II) Loading sub module "fbdevhw"
[    41.711] (II) LoadModule: "fbdevhw"
[    41.711] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    41.758] (II) Module fbdevhw: vendor="X.Org Foundation"
[    41.758]     compiled for 1.17.1, module version = 0.0.2
[    41.758]     ABI class: X.Org Video Driver, version 19.0
[    41.758] (WW) Falling back to old probe method for vesa
[    41.759] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 2000
[    41.759] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    41.759] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    41.759] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    41.759] (==) intel(0): RGB weight 888
[    41.759] (==) intel(0): Default visual is TrueColor
[    41.759] (II) intel(0): Output LVDS1 has no monitor section
[    41.759] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[    41.759] (II) intel(0): Enabled output LVDS1
[    41.759] (II) intel(0): Output VGA1 has no monitor section
[    41.759] (II) intel(0): Enabled output VGA1
[    41.759] (II) intel(0): Output HDMI1 has no monitor section
[    41.759] (II) intel(0): Enabled output HDMI1
[    41.759] (II) intel(0): Output DP1 has no monitor section
[    41.759] (II) intel(0): Enabled output DP1
[    41.759] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    41.760] (II) intel(0): Output VIRTUAL1 has no monitor section
[    41.760] (II) intel(0): Enabled output VIRTUAL1
[    41.760] (--) intel(0): Output VGA1 using initial mode 1280x1024 on pipe 0
[    41.760] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 1
[    41.760] (==) intel(0): TearFree disabled
[    41.760] (==) intel(0): DPI set to (96, 96)
[    41.760] (II) Loading sub module "dri2"
[    41.760] (II) LoadModule: "dri2"
[    41.760] (II) Module "dri2" already built-in
[    41.760] (II) Loading sub module "present"
[    41.760] (II) LoadModule: "present"
[    41.760] (II) Module "present" already built-in
[    41.760] (II) UnloadModule: "modesetting"
[    41.760] (II) Unloading modesetting
[    41.760] (II) UnloadModule: "fbdev"
[    41.760] (II) Unloading fbdev
[    41.760] (II) UnloadSubModule: "fbdevhw"
[    41.760] (II) Unloading fbdevhw
[    41.760] (II) UnloadModule: "vesa"
[    41.760] (II) Unloading vesa
[    41.760] (==) Depth 24 pixmap format is 32 bpp
[    41.938] (II) intel(0): SNA initialized with Sandybridge (gen6, gt1) backend
[    41.938] (==) intel(0): Backing store enabled
[    41.938] (==) intel(0): Silken mouse enabled
[    41.987] (II) intel(0): HW Cursor enabled
[    41.987] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    41.991] (==) intel(0): DPMS enabled
[    41.991] (==) intel(0): display hotplug detection enabled
[    41.991] (II) intel(0): [DRI2] Setup complete
[    41.991] (II) intel(0): [DRI2]   DRI driver: i965
[    41.991] (II) intel(0): [DRI2]   VDPAU driver: i965
[    41.991] (II) intel(0): direct rendering: DRI2 enabled
[    41.991] (II) intel(0): hardware support for Present enabled
[    41.991] (--) RandR disabled
[    42.015] (II) SELinux: Disabled on system
[    43.105] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    43.105] (II) AIGLX: enabled GLX_ARB_create_context
[    43.105] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    43.105] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    43.105] (II) AIGLX: enabled GLX_INTEL_swap_event
[    43.105] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    43.106] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    43.106] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    43.106] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    43.106] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    43.106] (II) AIGLX: Loaded and initialized i965
[    43.106] (II) GLX: Initialized DRI2 GL provider for screen 0
[    43.194] (II) intel(0): switch to mode 1280x1024@75.0 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    43.207] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 1, position (0, 0), rotation normal, reflection none
[    43.217] (II) intel(0): Setting screen physical size to 508 x 285
[    43.686] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    43.711] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    43.711] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.711] (II) LoadModule: "evdev"
[    43.711] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.997] (II) Module evdev: vendor="X.Org Foundation"
[    43.997]     compiled for 1.16.0, module version = 2.9.0
[    43.997]     Module class: X.Org XInput Driver
[    43.997]     ABI class: X.Org XInput driver, version 21.0
[    43.997] (II) Using input driver 'evdev' for 'Power Button'
[    43.997] (**) Power Button: always reports core events
[    43.997] (**) evdev: Power Button: Device: "/dev/input/event2"
[    43.997] (--) evdev: Power Button: Vendor 0 Product 0x1
[    43.997] (--) evdev: Power Button: Found keys
[    43.997] (II) evdev: Power Button: Configuring as keyboard
[    43.997] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    43.997] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    43.997] (**) Option "xkb_rules" "evdev"
[    43.997] (**) Option "xkb_model" "pc105"
[    43.997] (**) Option "xkb_layout" "us"
[    43.998] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    43.998] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    43.998] (II) Using input driver 'evdev' for 'Video Bus'
[    43.998] (**) Video Bus: always reports core events
[    43.998] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    43.998] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    43.998] (--) evdev: Video Bus: Found keys
[    43.998] (II) evdev: Video Bus: Configuring as keyboard
[    43.998] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input12/event11"
[    43.998] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    43.998] (**) Option "xkb_rules" "evdev"
[    43.998] (**) Option "xkb_model" "pc105"
[    43.998] (**) Option "xkb_layout" "us"
[    43.998] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    43.998] (II) No input driver specified, ignoring this device.
[    43.998] (II) This device may have been added with another device file.
[    43.999] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    43.999] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    43.999] (II) Using input driver 'evdev' for 'Sleep Button'
[    43.999] (**) Sleep Button: always reports core events
[    43.999] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    43.999] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    43.999] (--) evdev: Sleep Button: Found keys
[    43.999] (II) evdev: Sleep Button: Configuring as keyboard
[    43.999] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    43.999] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    43.999] (**) Option "xkb_rules" "evdev"
[    43.999] (**) Option "xkb_model" "pc105"
[    43.999] (**) Option "xkb_layout" "us"
[    44.000] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/event5)
[    44.000] (**) Plus More Enterprise LTD. USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    44.000] (II) Using input driver 'evdev' for 'Plus More Enterprise LTD. USB-compliant keyboard'
[    44.000] (**) Plus More Enterprise LTD. USB-compliant keyboard: always reports core events
[    44.000] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Device: "/dev/input/event5"
[    44.000] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Vendor 0x518 Product 0x1
[    44.000] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found keys
[    44.000] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Configuring as keyboard
[    44.000] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.0/0003:0518:0001.0001/input/input6/event5"
[    44.000] (II) XINPUT: Adding extended input device "Plus More Enterprise LTD. USB-compliant keyboard" (type: KEYBOARD, id 9)
[    44.000] (**) Option "xkb_rules" "evdev"
[    44.000] (**) Option "xkb_model" "pc105"
[    44.000] (**) Option "xkb_layout" "us"
[    44.000] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/event6)
[    44.000] (**) Plus More Enterprise LTD. USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[    44.000] (II) Using input driver 'evdev' for 'Plus More Enterprise LTD. USB-compliant keyboard'
[    44.000] (**) Plus More Enterprise LTD. USB-compliant keyboard: always reports core events
[    44.000] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Device: "/dev/input/event6"
[    44.001] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Vendor 0x518 Product 0x1
[    44.001] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found 1 mouse buttons
[    44.001] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found scroll wheel(s)
[    44.001] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found relative axes
[    44.001] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found x and y relative axes
[    44.001] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found absolute axes
[    44.001] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Forcing absolute x/y axes to exist.
[    44.001] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found keys
[    44.001] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Configuring as mouse
[    44.001] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Configuring as keyboard
[    44.001] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Adding scrollwheel support
[    44.001] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: YAxisMapping: buttons 4 and 5
[    44.001] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    44.001] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.1/0003:0518:0001.0002/input/input7/event6"
[    44.001] (II) XINPUT: Adding extended input device "Plus More Enterprise LTD. USB-compliant keyboard" (type: KEYBOARD, id 10)
[    44.001] (**) Option "xkb_rules" "evdev"
[    44.001] (**) Option "xkb_model" "pc105"
[    44.001] (**) Option "xkb_layout" "us"
[    44.001] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: initialized for relative axes.
[    44.001] (WW) evdev: Plus More Enterprise LTD. USB-compliant keyboard: ignoring absolute axes.
[    44.001] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) keeping acceleration scheme 1
[    44.001] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) acceleration profile 0
[    44.001] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) acceleration factor: 2.000
[    44.001] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) acceleration threshold: 4
[    44.001] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/mouse1)
[    44.001] (II) No input driver specified, ignoring this device.
[    44.001] (II) This device may have been added with another device file.
[    44.002] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/event7)
[    44.002] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Applying InputClass "evdev pointer catchall"
[    44.002] (II) Using input driver 'evdev' for 'Microsoft  Microsoft Basic Optical Mouse v2.0 '
[    44.002] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : always reports core events
[    44.002] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Device: "/dev/input/event7"
[    44.056] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Vendor 0x45e Product 0xcb
[    44.056] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found 3 mouse buttons
[    44.056] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found scroll wheel(s)
[    44.056] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found relative axes
[    44.056] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found x and y relative axes
[    44.056] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Configuring as mouse
[    44.056] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Adding scrollwheel support
[    44.056] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : YAxisMapping: buttons 4 and 5
[    44.056] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    44.056] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:045E:00CB.0003/input/input8/event7"
[    44.056] (II) XINPUT: Adding extended input device "Microsoft  Microsoft Basic Optical Mouse v2.0 " (type: MOUSE, id 11)
[    44.056] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : initialized for relative axes.
[    44.056] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) keeping acceleration scheme 1
[    44.056] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration profile 0
[    44.056] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration factor: 2.000
[    44.056] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration threshold: 4
[    44.056] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/mouse2)
[    44.056] (II) No input driver specified, ignoring this device.
[    44.056] (II) This device may have been added with another device file.
[    44.057] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event13)
[    44.057] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    44.057] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    44.057] (**) Lenovo EasyCamera: always reports core events
[    44.057] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event13"
[    44.057] (--) evdev: Lenovo EasyCamera: Vendor 0x58f Product 0xa006
[    44.057] (--) evdev: Lenovo EasyCamera: Found keys
[    44.057] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    44.057] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input14/event13"
[    44.057] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 12)
[    44.057] (**) Option "xkb_rules" "evdev"
[    44.057] (**) Option "xkb_model" "pc105"
[    44.057] (**) Option "xkb_layout" "us"
[    44.057] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    44.057] (II) No input driver specified, ignoring this device.
[    44.057] (II) This device may have been added with another device file.
[    44.058] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event10)
[    44.058] (II) No input driver specified, ignoring this device.
[    44.058] (II) This device may have been added with another device file.
[    44.058] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    44.058] (II) No input driver specified, ignoring this device.
[    44.058] (II) This device may have been added with another device file.
[    44.058] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    44.058] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    44.058] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    44.058] (**) AT Translated Set 2 keyboard: always reports core events
[    44.058] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    44.058] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    44.058] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    44.058] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    44.058] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    44.058] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    44.058] (**) Option "xkb_rules" "evdev"
[    44.058] (**) Option "xkb_model" "pc105"
[    44.058] (**) Option "xkb_layout" "us"
[    44.059] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    44.059] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    44.059] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    44.059] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    44.059] (II) LoadModule: "synaptics"
[    44.059] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    44.106] (II) Module synaptics: vendor="X.Org Foundation"
[    44.106]     compiled for 1.16.0, module version = 1.8.99
[    44.106]     Module class: X.Org XInput Driver
[    44.106]     ABI class: X.Org XInput driver, version 21.0
[    44.106] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    44.106] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    44.106] (**) Option "Device" "/dev/input/event4"
[    44.120] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    44.120] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5728 (res 46)
[    44.120] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4902 (res 83)
[    44.120] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    44.120] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    44.120] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    44.120] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    44.120] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    44.120] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    44.224] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    44.224] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    44.224] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    44.224] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    44.224] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    44.224] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    44.224] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    44.224] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    44.224] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    44.224] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    44.224] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    44.224] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    44.226] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event12)
[    44.226] (II) No input driver specified, ignoring this device.
[    44.226] (II) This device may have been added with another device file.
[    44.226] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    44.226] (II) No input driver specified, ignoring this device.
[    44.226] (II) This device may have been added with another device file.
[    44.552] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event14)
[    44.552] (II) No input driver specified, ignoring this device.
[    44.552] (II) This device may have been added with another device file.
[    76.326] (II) intel(0): resizing framebuffer to 3200x1080
[    76.345] (II) intel(0): switch to mode 1280x1024@75.0 on VGA1 using pipe 1, position (1920, 0), rotation normal, reflection none
[    76.400] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 13549.875] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 13552.534] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 13552.688] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 13566.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[ 16611.856] [mi] Increasing EQ size to 1024 to prevent dropped events.
[175677.370] (II) intel(0): resizing framebuffer to 3286x1080
[175678.186] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[175678.406] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 1, position (1366, 0), rotation normal, reflection none
[175719.302] (II) intel(0): resizing framebuffer to 1366x768
[176058.605] (II) config/udev: removing device Plus More Enterprise LTD. USB-compliant keyboard
[176058.608] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Close
[176059.597] (II) UnloadModule: "evdev"
[176059.634] (II) config/udev: removing device Plus More Enterprise LTD. USB-compliant keyboard
[176059.637] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Close
[176059.637] (II) UnloadModule: "evdev"
[176059.637] (II) config/udev: removing device Microsoft  Microsoft Basic Optical Mouse v2.0 
[176059.644] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Close
[176059.645] (II) UnloadModule: "evdev"
[176096.234] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/mouse2)
[176096.351] (II) No input driver specified, ignoring this device.
[176096.351] (II) This device may have been added with another device file.
[176096.359] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/mouse1)
[176096.359] (II) No input driver specified, ignoring this device.
[176096.359] (II) This device may have been added with another device file.
[176096.360] (II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse v2.0  (/dev/input/event7)
[176096.360] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : Applying InputClass "evdev pointer catchall"
[176096.360] (II) Using input driver 'evdev' for 'Microsoft  Microsoft Basic Optical Mouse v2.0 '
[176096.360] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : always reports core events
[176096.360] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Device: "/dev/input/event7"
[176096.416] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Vendor 0x45e Product 0xcb
[176096.416] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found 3 mouse buttons
[176096.416] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found scroll wheel(s)
[176096.416] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found relative axes
[176096.416] (--) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Found x and y relative axes
[176096.416] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Configuring as mouse
[176096.416] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : Adding scrollwheel support
[176096.416] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : YAxisMapping: buttons 4 and 5
[176096.416] (**) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[176096.416] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.3/1-1.3.3:1.0/0003:045E:00CB.0006/input/input18/event7"
[176096.416] (II) XINPUT: Adding extended input device "Microsoft  Microsoft Basic Optical Mouse v2.0 " (type: MOUSE, id 9)
[176096.416] (II) evdev: Microsoft  Microsoft Basic Optical Mouse v2.0 : initialized for relative axes.
[176096.417] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) keeping acceleration scheme 1
[176096.417] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration profile 0
[176096.417] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration factor: 2.000
[176096.417] (**) Microsoft  Microsoft Basic Optical Mouse v2.0 : (accel) acceleration threshold: 4
[176096.418] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/event6)
[176096.418] (**) Plus More Enterprise LTD. USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[176096.418] (II) Using input driver 'evdev' for 'Plus More Enterprise LTD. USB-compliant keyboard'
[176096.418] (**) Plus More Enterprise LTD. USB-compliant keyboard: always reports core events
[176096.418] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Device: "/dev/input/event6"
[176096.418] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Vendor 0x518 Product 0x1
[176096.418] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found 1 mouse buttons
[176096.418] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found scroll wheel(s)
[176096.418] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found relative axes
[176096.418] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found x and y relative axes
[176096.418] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found absolute axes
[176096.418] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Forcing absolute x/y axes to exist.
[176096.418] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found keys
[176096.418] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Configuring as mouse
[176096.418] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Configuring as keyboard
[176096.418] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Adding scrollwheel support
[176096.418] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: YAxisMapping: buttons 4 and 5
[176096.418] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[176096.418] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.1/0003:0518:0001.0005/input/input17/event6"
[176096.418] (II) XINPUT: Adding extended input device "Plus More Enterprise LTD. USB-compliant keyboard" (type: KEYBOARD, id 10)
[176096.418] (**) Option "xkb_rules" "evdev"
[176096.418] (**) Option "xkb_model" "pc105"
[176096.418] (**) Option "xkb_layout" "us"
[176096.419] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: initialized for relative axes.
[176096.419] (WW) evdev: Plus More Enterprise LTD. USB-compliant keyboard: ignoring absolute axes.
[176096.419] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) keeping acceleration scheme 1
[176096.419] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) acceleration profile 0
[176096.419] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) acceleration factor: 2.000
[176096.419] (**) Plus More Enterprise LTD. USB-compliant keyboard: (accel) acceleration threshold: 4
[176096.420] (II) config/udev: Adding input device Plus More Enterprise LTD. USB-compliant keyboard (/dev/input/event5)
[176096.420] (**) Plus More Enterprise LTD. USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[176096.420] (II) Using input driver 'evdev' for 'Plus More Enterprise LTD. USB-compliant keyboard'
[176096.420] (**) Plus More Enterprise LTD. USB-compliant keyboard: always reports core events
[176096.420] (**) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Device: "/dev/input/event5"
[176096.420] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Vendor 0x518 Product 0x1
[176096.420] (--) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Found keys
[176096.420] (II) evdev: Plus More Enterprise LTD. USB-compliant keyboard: Configuring as keyboard
[176096.420] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.2/1-1.3.2:1.0/0003:0518:0001.0004/input/input16/event5"
[176096.420] (II) XINPUT: Adding extended input device "Plus More Enterprise LTD. USB-compliant keyboard" (type: KEYBOARD, id 11)
[176096.420] (**) Option "xkb_rules" "evdev"
[176096.420] (**) Option "xkb_model" "pc105"
[176096.420] (**) Option "xkb_layout" "us"
[176097.352] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[176108.688] (II) intel(0): resizing framebuffer to 3286x1080
[176108.711] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 1, position (1366, 0), rotation normal, reflection none

```
I hope this gives you some more insight into my machine. Thank you for taking a look.

---

