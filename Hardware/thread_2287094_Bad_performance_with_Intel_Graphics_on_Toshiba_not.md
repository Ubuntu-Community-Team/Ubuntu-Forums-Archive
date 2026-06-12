---
title: "Bad performance with Intel Graphics on Toshiba notebook in Ubuntu 14.10 and 15.04"
date: 2015-07-16
forum: Hardware
---

### Post by wolfgang4 on 2015-07-16
I am desperately lost with my bad graphics performance in Ubuntu. I was so happy with it until I decided to upgrade from 14.04 to 14.10 about 6 months ago. Since then overall performance is horrible. I strongly suspect graphics related problems but can't find any cure. Tried many suggestions in online forums but nothing seems to work. Did not get any acceptable performance in 14.10 or now 15.04.

It's crazy. Because sometimes directly after boot everything seems to be running as snappy as ever before. But after about half a minute everything crawls to a third of the expected speed. Working mostly in Browser, LibreOffice, Inkscape, Gimp. 90% Chrome I would guess. Even typing is not real-time. And I do not know how to fix this. Especially bad is video editing. Not even the preview of raw clips in a small window runs smoothly (e.g. in openshot or flowblade).

I am using Debian based distributions since about 15 years now (Sidux, Kubuntu, Ubuntu in the last few years) but sadly have not a very deep understanding of how I could pinpoint (or even better fix) the problem. Some things I tried so far:

[LIST]
[*]Intel open source installer from 01.org does not yet support 15.04 as it would not add anything to standard libraries/drivers in 15.04 (if I understand correctly from the forums).
[*]Also tried to add ppa:oibaf/graphics-drivers with no performance change.
[*]Also *Option "AccelMethod" "sna"* in xorg.conf did nothing.
[/LIST]

I am happy to provide any information that could help fix my problem.

Hardware is a Toshiba Notebook Z930. More information about my system:

uname -r
```
3.19.0-22-generic
```

System Settings > Details
```
Memory 7,7 GiB
Processor Intel® Core™ i7-3667U CPU @ 2.00GHz × 4 
```

lspci -knn | grep -A2 VGA
```

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:0004]
    Kernel driver in use: i915

```

---

### Post by kerry_s on 2015-07-16
intel driver uses sna by default, you probably want to try uxa, which is the old method.

also there is no xorg.conf anymore, the proper way to do it is to create a /usr/share/X11/xorg.conf.d/20-intel.conf file.

so for example:
pkexec mousepad /usr/share/X11/xorg.conf.d/20-intel.conf

copy paste:
```

Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"	"uxa"
   Option      "TearFree"	"true"
EndSection

```

i use xubuntu 15.04, so replace mousepad with your editor.

i find intel vid just does not play good with compiz, the less fancy crap, the better.

---

### Post by wolfgang4 on 2015-07-17
Jus tested it and sadly did not work. Tried removing compiz but then unity is gone too. Will try in the evening with more time if replacing unity makes a difference.

Also tried multiple settings in xdiagnose with no effect.

Edit: also this did not help [http://ubuntuforums.org/archive/index.php/t-2282942.html](http://ubuntuforums.org/archive/index.php/t-2282942.html)

Edit2: also tried most suggestions of that thread: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1386721](https://bugs.launchpad.net/ubuntu-gnome/+bug/1386721) Admittedtly some months ago. But back then nothing improved.

---

### Post by Yellow Pasque on 2015-07-17
Give the /var/log/Xorg.0.log (use code tags like you did above)

---

### Post by wolfgang4 on 2015-07-18
[COLOR=#000000]/var/log/Xorg.0.log r[/COLOR]ight after boot:

```
[     4.616] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[     4.616] X Protocol Version 11, Revision 0
[     4.616] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[     4.616] Current Operating System: Linux LM-woha 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:15:15 UTC 2015 x86_64
[     4.616] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-22-generic root=UUID=a0c92925-671d-427e-87a3-c3e11b575f00 ro vesafb.invalid=1 splash quiet acpi_backlight=vendor
[     4.616] Build Date: 19 March 2015  09:26:59AM
[     4.616] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[     4.616] Current version of pixman: 0.32.6
[     4.616]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     4.616] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.616] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 18 16:50:06 2015
[     4.619] (==) Using config directory: "/etc/X11/xorg.conf.d"
[     4.619] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.621] (==) No Layout section.  Using the first Screen section.
[     4.621] (==) No screen section available. Using defaults.
[     4.621] (**) |-->Screen "Default Screen Section" (0)
[     4.621] (**) |   |-->Monitor "<default monitor>"
[     4.621] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[     4.621] (**) |   |-->Device "card0"
[     4.621] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     4.622] (==) Automatically adding devices
[     4.622] (==) Automatically enabling devices
[     4.622] (==) Automatically adding GPU devices
[     4.622] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.622]     Entry deleted from font path.
[     4.622] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.622]     Entry deleted from font path.
[     4.622] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.622]     Entry deleted from font path.
[     4.622] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.622]     Entry deleted from font path.
[     4.622] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.622]     Entry deleted from font path.
[     4.622] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.622] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.622] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.622] (II) Loader magic: 0x7fd9b0d86d80
[     4.623] (II) Module ABI versions:
[     4.623]     X.Org ANSI C Emulation: 0.4
[     4.623]     X.Org Video Driver: 19.0
[     4.623]     X.Org XInput driver : 21.0
[     4.623]     X.Org Server Extension : 9.0
[     4.623] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.624] (--) PCI:*(0:0:2:0) 8086:0166:1179:0004 rev 9, Mem @ 0xe0000000/4194304, 0xd0000000/268435456, I/O @ 0x00002000/64
[     4.625] (II) LoadModule: "glx"
[     4.625] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     4.632] (II) Module glx: vendor="X.Org Foundation"
[     4.632]     compiled for 1.17.1, module version = 1.0.0
[     4.632]     ABI class: X.Org Server Extension, version 9.0
[     4.632] (==) AIGLX enabled
[     4.632] (II) LoadModule: "intel"
[     4.632] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.633] (II) Module intel: vendor="X.Org Foundation"
[     4.633]     compiled for 1.17.1, module version = 2.99.917
[     4.633]     Module class: X.Org Video Driver
[     4.633]     ABI class: X.Org Video Driver, version 19.0
[     4.633] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     4.633] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     4.633] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     4.633] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     4.633] (++) using VT number 7


[     4.633] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[     4.633] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git1507101930.2c5063~gd~v (Oibaf <fmrummey@gmail.com>)
[     4.633] (II) intel(0): SNA compiled for use with valgrind
[     4.634] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[     4.634] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx; using a maximum of 2 threads
[     4.634] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     4.634] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     4.634] (==) intel(0): RGB weight 888
[     4.634] (==) intel(0): Default visual is TrueColor
[     4.634] (**) intel(0): Option "Backlight" "intel_backlight"
[     4.634] (**) intel(0): Option "TearFree" "true"
[     4.634] (II) intel(0): Output LVDS1 has no monitor section
[     4.634] (**) intel(0): Found backlight control interface intel_backlight (type 'raw') for output LVDS1
[     4.634] (II) intel(0): Enabled output LVDS1
[     4.634] (II) intel(0): Output VGA1 has no monitor section
[     4.634] (II) intel(0): Enabled output VGA1
[     4.634] (II) intel(0): Output HDMI1 has no monitor section
[     4.634] (II) intel(0): Enabled output HDMI1
[     4.634] (II) intel(0): Output DP1 has no monitor section
[     4.634] (II) intel(0): Enabled output DP1
[     4.634] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     4.634] (II) intel(0): Output VIRTUAL1 has no monitor section
[     4.634] (II) intel(0): Enabled output VIRTUAL1
[     4.634] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[     4.634] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 1
[     4.634] (**) intel(0): TearFree enabled
[     4.634] (==) intel(0): DPI set to (96, 96)
[     4.634] (II) Loading sub module "dri2"
[     4.634] (II) LoadModule: "dri2"
[     4.634] (II) Module "dri2" already built-in
[     4.634] (II) Loading sub module "present"
[     4.634] (II) LoadModule: "present"
[     4.634] (II) Module "present" already built-in
[     4.635] (==) Depth 24 pixmap format is 32 bpp
[     4.637] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[     4.637] (==) intel(0): Backing store enabled
[     4.637] (==) intel(0): Silken mouse enabled
[     4.637] (II) intel(0): HW Cursor enabled
[     4.637] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.638] (==) intel(0): DPMS enabled
[     4.638] (==) intel(0): Display hotplug detection enabled
[     4.638] (II) intel(0): [DRI2] Setup complete
[     4.638] (II) intel(0): [DRI2]   DRI driver: i965
[     4.638] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[     4.638] (II) intel(0): direct rendering: DRI2 enabled
[     4.638] (II) intel(0): hardware support for Present enabled
[     4.638] (--) RandR disabled
[     4.642] (II) SELinux: Disabled on system
[     4.671] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     4.671] (II) AIGLX: enabled GLX_ARB_create_context
[     4.671] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     4.671] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     4.671] (II) AIGLX: enabled GLX_INTEL_swap_event
[     4.671] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     4.671] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     4.671] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     4.671] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     4.671] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     4.671] (II) AIGLX: Loaded and initialized i965
[     4.671] (II) GLX: Initialized DRI2 GL provider for screen 0
[     4.673] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[     4.673] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 1, position (0, 0), rotation normal, reflection none
[     4.673] (II) intel(0): Setting screen physical size to 508 x 285
[     4.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.683] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     4.683] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.683] (II) LoadModule: "evdev"
[     4.683] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.684] (II) Module evdev: vendor="X.Org Foundation"
[     4.684]     compiled for 1.16.0, module version = 2.9.0
[     4.684]     Module class: X.Org XInput Driver
[     4.684]     ABI class: X.Org XInput driver, version 21.0
[     4.684] (II) Using input driver 'evdev' for 'Power Button'
[     4.684] (**) Power Button: always reports core events
[     4.684] (**) evdev: Power Button: Device: "/dev/input/event2"
[     4.684] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.684] (--) evdev: Power Button: Found keys
[     4.684] (II) evdev: Power Button: Configuring as keyboard
[     4.684] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     4.684] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.684] (**) Option "xkb_rules" "evdev"
[     4.684] (**) Option "xkb_model" "pc105"
[     4.684] (**) Option "xkb_layout" "de"
[     4.686] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[     4.687] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[     4.687] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     4.687] (II) Using input driver 'evdev' for 'Video Bus'
[     4.687] (**) Video Bus: always reports core events
[     4.687] (**) evdev: Video Bus: Device: "/dev/input/event4"
[     4.687] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     4.687] (--) evdev: Video Bus: Found keys
[     4.687] (II) evdev: Video Bus: Configuring as keyboard
[     4.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7/event4"
[     4.687] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     4.687] (**) Option "xkb_rules" "evdev"
[     4.687] (**) Option "xkb_model" "pc105"
[     4.687] (**) Option "xkb_layout" "de"
[     4.687] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     4.687] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.687] (II) Using input driver 'evdev' for 'Power Button'
[     4.688] (**) Power Button: always reports core events
[     4.688] (**) evdev: Power Button: Device: "/dev/input/event0"
[     4.688] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.688] (--) evdev: Power Button: Found keys
[     4.688] (II) evdev: Power Button: Configuring as keyboard
[     4.688] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     4.688] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     4.688] (**) Option "xkb_rules" "evdev"
[     4.688] (**) Option "xkb_model" "pc105"
[     4.688] (**) Option "xkb_layout" "de"
[     4.688] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[     4.688] (II) No input driver specified, ignoring this device.
[     4.688] (II) This device may have been added with another device file.
[     4.688] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event5)
[     4.688] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[     4.688] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[     4.688] (**) Logitech USB Laser Mouse: always reports core events
[     4.688] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event5"
[     4.744] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc069
[     4.744] (--) evdev: Logitech USB Laser Mouse: Found 12 mouse buttons
[     4.744] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[     4.744] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[     4.744] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[     4.744] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[     4.744] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[     4.744] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[     4.744] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.744] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:046D:C069.0001/input/input8/event5"
[     4.744] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 9)
[     4.744] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[     4.746] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[     4.746] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[     4.746] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[     4.746] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[     4.746] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse0)
[     4.746] (II) No input driver specified, ignoring this device.
[     4.746] (II) This device may have been added with another device file.
[     4.746] (II) config/udev: Adding input device LITEON Technology USB Multimedia Keyboard (/dev/input/event6)
[     4.746] (**) LITEON Technology USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[     4.746] (II) Using input driver 'evdev' for 'LITEON Technology USB Multimedia Keyboard'
[     4.746] (**) LITEON Technology USB Multimedia Keyboard: always reports core events
[     4.746] (**) evdev: LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event6"
[     4.746] (--) evdev: LITEON Technology USB Multimedia Keyboard: Vendor 0x46d Product 0xc312
[     4.746] (--) evdev: LITEON Technology USB Multimedia Keyboard: Found keys
[     4.746] (II) evdev: LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
[     4.746] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:046D:C312.0002/input/input9/event6"
[     4.746] (II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD, id 10)
[     4.746] (**) Option "xkb_rules" "evdev"
[     4.746] (**) Option "xkb_model" "pc105"
[     4.746] (**) Option "xkb_layout" "de"
[     4.747] (II) config/udev: Adding input device TOSHIBA Web Camera - HD (/dev/input/event12)
[     4.747] (**) TOSHIBA Web Camera - HD: Applying InputClass "evdev keyboard catchall"
[     4.747] (II) Using input driver 'evdev' for 'TOSHIBA Web Camera - HD'
[     4.747] (**) TOSHIBA Web Camera - HD: always reports core events
[     4.747] (**) evdev: TOSHIBA Web Camera - HD: Device: "/dev/input/event12"
[     4.752] (--) evdev: TOSHIBA Web Camera - HD: Vendor 0x1bcf Product 0x288e
[     4.752] (--) evdev: TOSHIBA Web Camera - HD: Found keys
[     4.752] (II) evdev: TOSHIBA Web Camera - HD: Configuring as keyboard
[     4.752] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/input/input14/event12"
[     4.752] (II) XINPUT: Adding extended input device "TOSHIBA Web Camera - HD" (type: KEYBOARD, id 11)
[     4.752] (**) Option "xkb_rules" "evdev"
[     4.752] (**) Option "xkb_model" "pc105"
[     4.752] (**) Option "xkb_layout" "de"
[     4.752] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[     4.752] (II) No input driver specified, ignoring this device.
[     4.752] (II) This device may have been added with another device file.
[     4.753] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[     4.753] (II) No input driver specified, ignoring this device.
[     4.753] (II) This device may have been added with another device file.
[     4.753] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[     4.753] (II) No input driver specified, ignoring this device.
[     4.753] (II) This device may have been added with another device file.
[     4.753] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     4.753] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     4.753] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     4.753] (**) AT Translated Set 2 keyboard: always reports core events
[     4.753] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     4.753] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     4.753] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     4.753] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     4.753] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     4.753] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[     4.753] (**) Option "xkb_rules" "evdev"
[     4.753] (**) Option "xkb_model" "pc105"
[     4.753] (**) Option "xkb_layout" "de"
[     4.753] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[     4.754] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     4.754] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     4.754] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     4.754] (II) LoadModule: "synaptics"
[     4.754] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     4.754] (II) Module synaptics: vendor="X.Org Foundation"
[     4.754]     compiled for 1.16.0, module version = 1.8.99
[     4.754]     Module class: X.Org XInput Driver
[     4.754]     ABI class: X.Org XInput driver, version 21.0
[     4.754] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     4.754] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.754] (**) Option "Device" "/dev/input/event7"
[     4.804] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[     4.804] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1142 - 5792 (res 59)
[     4.804] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 924 - 4930 (res 88)
[     4.804] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     4.804] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     4.804] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     4.804] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     4.804] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.804] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.892] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[     4.892] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[     4.892] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     4.892] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     4.892] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.033
[     4.892] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     4.892] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     4.892] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     4.892] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     4.892] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.892] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[     4.892] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     4.893] (II) config/udev: Adding input device Toshiba input device (/dev/input/event8)
[     4.893] (**) Toshiba input device: Applying InputClass "evdev keyboard catchall"
[     4.893] (II) Using input driver 'evdev' for 'Toshiba input device'
[     4.893] (**) Toshiba input device: always reports core events
[     4.893] (**) evdev: Toshiba input device: Device: "/dev/input/event8"
[     4.893] (--) evdev: Toshiba input device: Vendor 0 Product 0
[     4.893] (--) evdev: Toshiba input device: Found keys
[     4.893] (II) evdev: Toshiba input device: Configuring as keyboard
[     4.893] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event8"
[     4.893] (II) XINPUT: Adding extended input device "Toshiba input device" (type: KEYBOARD, id 14)
[     4.893] (**) Option "xkb_rules" "evdev"
[     4.893] (**) Option "xkb_model" "pc105"
[     4.893] (**) Option "xkb_layout" "de"
[     6.115] (II) intel(0): resizing framebuffer to 3286x1080
[     6.137] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 1, position (1366, 0), rotation normal, reflection none
[    20.298] (II) XKB: reuse xkmfile /var/lib/xkb/server-D6DBE0E55D1FA64FF4CA7ADEF8BE42D3044F0938.xkm
[    20.608] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 1, position (0, 0), rotation normal, reflection none
[    20.620] (II) intel(0): switch to mode 1366x768@60.2 on LVDS1 using pipe 0, position (1920, 0), rotation normal, reflection none
[    20.698] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-2C7E1B575DED7715735E948A34AC093C42EF546B.xkm
[    21.338] (II) XKB: reuse xkmfile /var/lib/xkb/server-2C7E1B575DED7715735E948A34AC093C42EF546B.xkm
[    22.143] (II) XKB: reuse xkmfile /var/lib/xkb/server-077304FDF78C75D1863AF81542623E8F115C8EFE.xkm

```

---

### Post by Yellow Pasque on 2015-07-18
The X log looks okay. It sounds like a memory leak.
How about:
```
free -m
```

---

### Post by wolfgang4 on 2015-07-19
free -m (half a minute after  boot)
```
             total       used       free     shared    buffers     cached
Mem:          7862       4438       3423        491        102       2897
-/+ buffers/cache:       1438       6423
Swap:            0          0          0

```

free -m (not one minute later)
```
             total       used       free     shared    buffers     cached
Mem:          7862       4755       3106        501        105       3071
-/+ buffers/cache:       1578       6283
Swap:            0          0          0

```


free -m (some more minutes later)
```
             total       used       free     shared    buffers     cached
Mem:          7862       5221       2640        638        108       3495
-/+ buffers/cache:       1617       6244
Swap:            0          0          0

```

As far as I can see it does not go below much after several more minutes using Chrome.
From that I would confirm that memory is leaking but there are always 2 to 3 GiB free... is it still a problem?

I always used htop to see memory usage. The attached screenshot was taken around the same time. It always gave me the impression that there is nothing wrong.

---

### Post by Yellow Pasque on 2015-07-20
^No, it looks okay. You don't have a swap partition, but you have plenty of free RAM (about 6GB from that output).
This isn't an Optimus system with an Nvidia GPU, is it? Give full output of lspci:
```
sudo update-pciids
lspci
```

---

### Post by wolfgang4 on 2015-07-21
Thank you so much for sticking with me. I appreciate it a lot!


lspci
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
01:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
```

lspci -knn | grep -A2 VGA
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)    Subsystem: Toshiba America Info Systems Device [1179:0004]
    Kernel driver in use: i915
```

---

### Post by Yellow Pasque on 2015-07-23
> Thank you so much for sticking with me. I appreciate it a lot
Unfortunately, I'm running out of ideas. Let's make sure the CPU isn't being throttled unnecessarily:
```
cat /proc/cpuinfo
```

---

### Post by kerry_s on 2015-07-23
ubuntu-mate, xubuntu or lubuntu will run like a champ on intel.

unity & gnome3 have a habit of chocking on intel.

your chock point is the weak intel graphics, i have the same graphics.

---

### Post by wolfgang4 on 2015-07-23
cat /proc/cpuinfo
```
processor    : 0vendor_id    : GenuineIntel
cpu family    : 6
model        : 58
model name    : Intel(R) Core(TM) i7-3667U CPU @ 2.00GHz
stepping    : 9
microcode    : 0x1b
cpu MHz        : 1499.902
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt
bugs        :
bogomips    : 4988.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 58
model name    : Intel(R) Core(TM) i7-3667U CPU @ 2.00GHz
stepping    : 9
microcode    : 0x1b
cpu MHz        : 1499.902
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt
bugs        :
bogomips    : 4988.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 58
model name    : Intel(R) Core(TM) i7-3667U CPU @ 2.00GHz
stepping    : 9
microcode    : 0x1b
cpu MHz        : 1499.902
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt
bugs        :
bogomips    : 4988.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 58
model name    : Intel(R) Core(TM) i7-3667U CPU @ 2.00GHz
stepping    : 9
microcode    : 0x1b
cpu MHz        : 1500.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt
bugs        :
bogomips    : 4988.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```

---

### Post by sgian on 2015-07-24
Since the graphics were fine with 14.04 LTS, I would suggest going back to it.  That is what I did, I wasn't happy with 15.04 either.  The LTS is supposed to be more stable anyway and will be supported for years, unlike 14.10 and 15.04 which are only supported something like 9 months after release, IIRC.

---

### Post by wolfgang4 on 2015-08-07
Quick update: tried a completely new 15.04 install yesterday. Sadly even on a fresh installation performance is painful. Still feeling like in a slow motion movie :)

Not familiar with ubuntu-mate, xubuntu or lubuntu yet. My next option most likely will be to try a fresh 14.04 install. Who needs weekends anyways...

---

### Post by kerry_s on 2015-08-07
> **wolfgang4 said:**
> Quick update: tried a completely new 15.04 install yesterday. Sadly even on a fresh installation performance is painful. Still feeling like in a slow motion movie :)

Not familiar with ubuntu-mate, xubuntu or lubuntu yet. My next option most likely will be to try a fresh 14.04 install. Who needs weekends anyways...

well good timing, they just came out with the updated iso's. just saw it over there on distrowatch.
[http://distrowatch.com/](http://distrowatch.com/)

all the iso's in one place so you can pick which ever version you want to try.

---

### Post by wolfgang4 on 2015-08-17
Just switched to Ubuntu-Mate. Sadly only minor improvements.

There are two main areas that are bothering everyday workflow: video playback is absolutely broken. Can't really play any online video with higher quality than 480p. But that would be still fine as 480p is OK-ish to watch. Really terrible is that no video editing is possible (e.g. openshot, flowblade). Realtime video playback does not work at all... video and audio stuttering.

Second is browser performance. I am mostly using google chrome and working with google apps (spreadsheet, presentations, docs) is a nightmare. Even browsing through drive is absolutely slow.

Maybe a hardware problem... but what hardware problem slows down everything but does not crash the system?

---

### Post by monkeybrain20122 on 2015-08-17
Probably updating graphic driver helps. If you are on 15.04 (or 14.04.0 or 14.04.1, not later point releases) 
```

sudo apt-get install ppa-purge
sudo add-apt-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt-get upgrade
```

Then reboot.

If the new driver works even worse, purge the ppa with
```
sudo ppa-purge ppa:oibaf/graphics-drivers
```
then reboot of course.

---

### Post by kerry_s on 2015-08-17
> **wolfgang4 said:**
> Just switched to Ubuntu-Mate. Sadly only minor improvements.

There are two main areas that are bothering everyday workflow: video playback is absolutely broken. Can't really play any online video with higher quality than 480p. But that would be still fine as 480p is OK-ish to watch. Really terrible is that no video editing is possible (e.g. openshot, flowblade). Realtime video playback does not work at all... video and audio stuttering.

Second is browser performance. I am mostly using google chrome and working with google apps (spreadsheet, presentations, docs) is a nightmare. Even browsing through drive is absolutely slow.

Maybe a hardware problem... but what hardware problem slows down everything but does not crash the system?

try the ubuntu 14lts again, since the 14.04.3 release the intel driver seems to work better. i'm running a full ubuntu unity install & it's not running like crap, still a little slow to load for me cause i only have 2gb ram, but for you should be better.

---

### Post by wolfgang4 on 2015-08-18
Thank you for your suggestions.

I am happy to announce that I found (and fixed) the problem yesterday!

It was really strange that no suggestions would improve anything. Which led me to the conclusion that the problem had to be deeper under the surface than Ubuntu itself. As it turns out it was not hardware itself but problematic bios settings. I still cannot pinpoint which setting exactly as I changed several settings at once. Maybe a mix of several factors.

I turned all power management towards performance. Maybe especially one setting (which was somehow linked/dependent on battery performance) could have been it, as my battery is quite old/broken and only lasts ~35 minutes. Maybe the setting plus the bad battery stats caused some strange internal commands which slowed down performance drastically. I honestly never expected bios settings concerning performance vs. power efficiency to have such deep impact. Also I am not sure how I could miss that connection when I previously changed the setting. Sadly it was too long ago... was working in slow-motion for more than 6 months.

Thank you all very much for your time and patience!
I apologize deeply for my incompetence on that matter.

As for the future: Currently enjoying a really responsive Ubuntu Mate... thinking about switching back to plain Ubuntu in the coming days.

---

### Post by wolfgang4 on 2015-08-21
And Ubuntu it is again... since two days... running perfectly! In a constant state of awe now :)

---

