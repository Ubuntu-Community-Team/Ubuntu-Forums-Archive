---
title: "Aiptek 6000U tablet on 9.10"
date: 2010-08-08
forum: Hardware
---

### Post by knurledflanges on 2010-08-08
Hello,
I have an old Aiptek T-6000U tablet I'm trying to make work on Ubuntu 9.10. Long story short, I've tried everything on the Aiptek [community documentation page]("https://help.ubuntu.com/community/AiptekTablet#Ubuntu%208.10%20-%20Ubuntu%209.10") and the Aiptek driver seems to not work - various erratic behavior including never recognizing pressure and not letting me "hover" the pen after it's touched down once. The Aiptek community documentation page says that some Aiptek models, including 6000U (I'm not sure what the "T" counts for on mine) need the Wacom driver instead. However, it's not "just working" for me and I have no idea how to set it up. I have xserver-xorg-input-wacom and wacom-tools installed. Any help is much appreciated, thanks!

---

### Post by knurledflanges on 2010-08-08
Is this as simple as editing custom_wacom.fdi with the location and/or name of the aiptek tablet to trick it?

---

### Post by knurledflanges on 2010-08-09
Also, because it's old and been sitting for a while, I just tested the tablet on a Windows machine, and it's working perfectly. Any help would be realllly appreciated; I've got a project I need to do some graphics for, but money is tight and I can't justify buying a new tablet.

---

### Post by knurledflanges on 2010-08-09
Can anyone help me with this? I would try upgrading to 10.04 but there's a bunch of stuff on my current install that took work to set up, and I really don't want to do it all over again if there's an easier way.

---

### Post by Favux on 2010-08-10
Hi knurledflanges,

First we need to identify if Aiptek is actually the OEM of your tablet.  There's a bunch of ways to do this including looking at the output of:
```
xinput --list
```
or
```
lsusb
```
or
```
grep -i name /proc/bus/input/devices
```

---

### Post by knurledflanges on 2010-08-10
Hi Favux, thanks for replying.

lsusb gives me "Aiptek International, Inc. APT-6000U Tablet".

grep -i name /proc/bus/input/devices gives me

```
N: Name="Power Button"
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Microsoft Microsoft Optical Mouse with Tilt Wheel"
N: Name="Aiptek"
```xinput --list gives me

```

"Aiptek"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 7
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 2999
        Resolution is 10000
    Axis 1 :
        Min_value is 0
        Max_value is 2249
        Resolution is 10000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 10000
    Axis 3 :
        Min_value is 0
        Max_value is 511
        Resolution is 10000
    Axis 4 :
        Min_value is -128
        Max_value is 127
        Resolution is 10000
    Axis 5 :
        Min_value is -128
        Max_value is 127
        Resolution is 10000
    Axis 6 :
        Min_value is 0
        Max_value is 0
        Resolution is 10000


```cat /sys/bus/usb/devices/*/product (a command I found some other place, trust me I have no idea how to figure out this stuff on my own) gives "APT-6000U".

This is with the aiptek package installed and /usr/share/hal/fdi/policy/10-linuxaiptek.fdi in place.

---

### Post by Favux on 2010-08-10
OK, no doubt, it is an Aiptek.

With Synaptic Package Manager tell it to reinstall the aiptek package.  Then post your aiptek .fdi and you Xorg.0.log in /var/logs.

---

### Post by knurledflanges on 2010-08-10
Here's the 10-linuxaiptek.fdi file I created by copying from the guide:

```
<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="info.product" contains="Aiptek">
<merge key="input.x11_driver" type="string">aiptek</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
<merge key="input.x11_options.USB" type="string">On</merge>
<merge key="input.x11_options.Type" type="string">stylus</merge>
<merge key="input.x11_options.Mode" type="string">absolute</merge>
<merge key="input.x11_options.zMin" type="string">0</merge>
<merge key="input.x11_options.zMax" type="string">511</merge>
<merge key="input.x11_options.KeepShape" type="string">On</merge>
</match>
</device>
</deviceinfo>

```Here's the log file
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux huntingmoa 2.6.31-22-generic #61-Ubuntu SMP Wed Jul 28 01:57:06 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=UUID=a48b33be-47d9-40e2-b07f-e4e908b31c34 ro quiet splash
Build Date: 06 May 2010  09:30:46PM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 10 14:34:11 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
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

(--) PCI:*(0:1:0:0) 10de:0221:1458:343c nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     ACI ASUS VH242H (DFP-0)
(--) NVIDIA(0): ACI ASUS VH242H (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): ACI ASUS VH242H (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
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
(II) Initializing extension GLX
(II) config/hal: Adding input device Aiptek
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Option "SendCoreEvents" "true "
(**) Aiptek: always reports core events
(**) Aiptek: Device: "/dev/input/event6"
(II) Aiptek: Found 3 mouse buttons
(II) Aiptek: Found x and y relative axes
(II) Aiptek: Found scroll wheel(s)
(II) Aiptek: Found x and y absolute axes
(II) Aiptek: Found absolute touchpad
(II) Aiptek: Found keys
(II) Aiptek: Configuring as touchpad
(II) Aiptek: Configuring as keyboard
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(WW) Aiptek: touchpads and touchscreens ignore relative axes.
(**) Aiptek: (accel) keeping acceleration scheme 1
(**) Aiptek: (accel) filter chain progression: 2.00
(**) Aiptek: (accel) filter stage 0: 20.00 ms
(**) Aiptek: (accel) set acceleration profile 0
(II) Aiptek: initialized for absolute axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event5"
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) set acceleration profile 0
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
(II) config/hal: removing device Aiptek
(II) Aiptek: Close
(II) UnloadModule: "evdev"

```

---

### Post by Favux on 2010-08-10
OK, Aiptek doesn't show up in the Xorg.0.log.  Instead it's the evdev driver trying to configure the tablet.  Since you have the xorg-xserver-input-aiptek package, or whatever it's called, installed it suggests the match line in the .fdi isn't pulling the tablet out.

Let's look at your lshal for match lines:
```
lshal>knurledflanges_lshal.txt
```
Compress it by right clicking on it and using Create Archive then attach it to your next post using Manage Attachments.

---

### Post by knurledflanges on 2010-08-10
Oops, I goofed, I just copied the log file immediately after re-installing the aiptek package but without the tablet plugged in. It's different when I check the log file after I plug it in:

```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux huntingmoa 2.6.31-22-generic #61-Ubuntu SMP Wed Jul 28 01:57:06 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=UUID=a48b33be-47d9-40e2-b07f-e4e908b31c34 ro quiet splash
Build Date: 06 May 2010  09:30:46PM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 10 14:34:11 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
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

(--) PCI:*(0:1:0:0) 10de:0221:1458:343c nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.a2.10.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     ACI ASUS VH242H (DFP-0)
(--) NVIDIA(0): ACI ASUS VH242H (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): ACI ASUS VH242H (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
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
(II) Initializing extension GLX
(II) config/hal: Adding input device Aiptek
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Option "SendCoreEvents" "true "
(**) Aiptek: always reports core events
(**) Aiptek: Device: "/dev/input/event6"
(II) Aiptek: Found 3 mouse buttons
(II) Aiptek: Found x and y relative axes
(II) Aiptek: Found scroll wheel(s)
(II) Aiptek: Found x and y absolute axes
(II) Aiptek: Found absolute touchpad
(II) Aiptek: Found keys
(II) Aiptek: Configuring as touchpad
(II) Aiptek: Configuring as keyboard
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(WW) Aiptek: touchpads and touchscreens ignore relative axes.
(**) Aiptek: (accel) keeping acceleration scheme 1
(**) Aiptek: (accel) filter chain progression: 2.00
(**) Aiptek: (accel) filter stage 0: 20.00 ms
(**) Aiptek: (accel) set acceleration profile 0
(II) Aiptek: initialized for absolute axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event5"
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) set acceleration profile 0
(II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
(II) config/hal: removing device Aiptek
(II) Aiptek: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Aiptek
(**) Option "SendCoreEvents" "true "
(**) Aiptek: always reports core events
(**) Aiptek: Device: "/dev/input/event6"
(II) Aiptek: Found 3 mouse buttons
(II) Aiptek: Found x and y relative axes
(II) Aiptek: Found scroll wheel(s)
(II) Aiptek: Found x and y absolute axes
(II) Aiptek: Found absolute touchpad
(II) Aiptek: Found keys
(II) Aiptek: Configuring as touchpad
(II) Aiptek: Configuring as keyboard
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(WW) Aiptek: touchpads and touchscreens ignore relative axes.
(**) Aiptek: (accel) keeping acceleration scheme 1
(**) Aiptek: (accel) filter chain progression: 2.00
(**) Aiptek: (accel) filter stage 0: 20.00 ms
(**) Aiptek: (accel) set acceleration profile 0
(II) Aiptek: initialized for absolute axes.

```

Which is what I get immediately after plugging it in. In this state, the pen is moving the cursor when the pen touches but that's about all. "Hovering" the pen doesn't work except for, I believe, the first time it's plugged in after the machine starts.  Clicking/pressure doesn't work, except while either pen button is clicked and held down the pen won't move the cursor.

Thanks for your help!

---

### Post by Favux on 2010-08-10
Alright, the evdev driver is still grabbing it but then releases it when the Aiptek driver claims it:
```
(II) config/hal: removing device Aiptek
(II) Aiptek: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Aiptek
(**) Option "SendCoreEvents" "true "
(**) Aiptek: always reports core events
(**) Aiptek: Device: "/dev/input/event6"
(II) Aiptek: Found 3 mouse buttons
(II) Aiptek: Found x and y relative axes
(II) Aiptek: Found scroll wheel(s)
(II) Aiptek: Found x and y absolute axes
(II) Aiptek: Found absolute touchpad
(II) Aiptek: Found keys
(II) Aiptek: Configuring as touchpad
(II) Aiptek: Configuring as keyboard
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(WW) Aiptek: touchpads and touchscreens ignore relative axes.
(**) Aiptek: (accel) keeping acceleration scheme 1
(**) Aiptek: (accel) filter chain progression: 2.00
(**) Aiptek: (accel) filter stage 0: 20.00 ms
(**) Aiptek: (accel) set acceleration profile 0
(II) Aiptek: initialized for absolute axes.
```
Is there an Aiptek manual?  In a terminal enter:
```
man aiptek
```
Also do you have any spec.s?  How many levels of pressure your tablet has, etc.?  Also is the battery in the stylus fresh?

---

### Post by knurledflanges on 2010-08-10
It does have a manual, mostly about the various options such as ```
Option "Type" "stylus"|"eraser"|"cursor"
```. All I did to get the .fdi file I've been going off is copy and paste from the community help page; should I try various options from the manual?

I do notice that there's no path option in the .fdi file I have, but the manual says```
 Option "Device" "path"
                   sets the path to the special file which represents serial line where
                   the  tablet  is plugged.  You have to specify it for each subsection
                   with the same value if you want to have multiple  devices  with  the
                   same tablet.  This option is mandatory.
``` 

Mandatory seems to mean that it needs to be there, but since it's able to move the cursor with the tablet, doesn't that mean it's at least able to know where it is?

The tablet has 512 levels with a 2-button stylus that, many years ago when I had it on a Windows machine, corresponded to left and right mouse clicks. No eraser. It came with a 3-button mouse and the tablet itself has F-Key shortcuts (which I don't care about).

Brand new battery, and I tested it on a Windows machine and it worked perfectly. Thanks for your help!

---

### Post by Favux on 2010-08-10
Could you post the manual?  We'll probably need to go through it to get the .fdi working right.

---

### Post by knurledflanges on 2010-08-11
```

AIPTEK(4)                                 AIPTEK(4)



NAME
       aiptek - Aiptek USB Digital Tablet Input Driver for Linux

SYNOPSIS
       Section "InputDevice"
     Identifier "idevname"
     Driver "aiptek"
     Option "Device"   "devpath"
     ...
       EndSection

DESCRIPTION
       aiptek  is  an  Xorg  input driver for Aiptek HyperPen USB-based tablet
       devices.  This driver only supports the USB protocol,  and  only  under
       Linux; for RS-232C-based HyperPens, please see the "hyperpen" driver.

       The  aiptek driver functions as a pointer input device, and may be used
       as the X server's core pointer.

SUPPORTED HARDWARE
       This driver supports the Aiptek HyperPen 4000U, 5000U, 6000U, 8000U and
       12000U USB-based input tablet on some Linux platforms.

CONFIGURATION DETAILS
       Please  refer to xorg.conf(5) for general configuration details and for
       options that can be used with all input    drivers.   This  section  only
       covers configuration details specific to this driver.

       Multiple  instances of the Aiptek devices can cohabit. It can be useful
       to define multiple devices with different  active  zones.  Each    device
       supports the following entries:

           Option "Type" "stylus"|"eraser"|"cursor"
           sets  the type of tool the device represent. This option is
           mandatory.

           Option "Device" "path"
           sets the path to the special file which  represents    serial
           line  where    the tablet is plugged.    You have to specify it
           for each subsection with the same value if you want to have
           multiple  devices  with  the  same  tablet.    This option is
           mandatory.

           Option "USB" "on"
           specifies that you are using the  USB  bus  to  communicate
           with your tablet.  This setting is mandatory, as USB is the
           only protocol supported by this driver.

           Option "DeviceName" "name"
           sets the name of the X device.

           Option "Mode" "Relative"|"Absolute"
           sets the mode of the device.

           Option "HistorySize" "number"
           sets the motion history size. By default the value is zero.

           Option "AlwaysCore" "on"
           enables the sharing of the core pointer. When this  feature
           is  enabled,  the  device  will  take  control  of the core
           pointer (and thus will emit core events) and  at  the  same
           time  will  be  able,  when    asked  so,  to report extended
           events.  You can use the last available integer feedback to
           control  this  feature.  When  the value of the feedback is
           zero, the feature is disabled. The feature is  enabled  for
           any other value.

           Option "XTop" "number"
           First  of  three sets of parameters to set the active zone.
           This sets the X coordinate of the top corner of the    active
           zone. "TopX" is a synonym.

           Option "YTop" "number"
           First  of  three sets of parameters to set the active zone.
           This sets the Y coordinate of the top corner of the    active
           zone. "TopY" is a synonym.

           Option "XBottom" "Inumber"
           First  of  three sets of parameters to set the active zone.
           This sets the X coordinate of  the  bottom  corner  of  the
           active zone. "BottomX" is a synonym.

           Option "YBottom" "number"
           First  of  three sets of parameters to set the active zone.
           This sets the Y coordinate of  the  bottom  corner  of  the
           active zone. "BottomY" is a synonym.

           Option "XMax" "number"
           Second  of three sets of parameters to set the active zone.
           This sets the the X coordinate of the bottom corner of  the
           active  zone.  The Top X corner's coordinate is fixed at 0.
           "MaxX" is a synonym.

           Option "YMax" "number"
           Second of three sets of parameters to set the active  zone.
           This  sets the the Y coordinate of the bottom corner of the
           active zone. The Top Y corner's coordinate is fixed    at  0.
           "MaxY" is a synonym.

           Option "XOffset" "number"
           Third  of  three sets of parameters to set the active zone.
           This sets the X coordinate of the top corner of the    active
           zone. "OffsetX" is a synonym.

           Option "YOffset" "number"
           Third  of  three sets of parameters to set the active zone.
           This sets the Y coordinate of the top corner of the    active
           zone. "OffsetY" is a synonym.

           Option "XSize" "number"
           Third  of  three sets of parameters to set the active zone.
           This sets the X coordinate of  the  bottom  corner  of  the
           active  zone. Unlike others, this parameter is expressed in
           relative coordinates from the "XOffset" parameter.  "XSize"
           is a synonym.

           Option "YSize" "number"
           Third  of  three sets of parameters to set the active zone.
           This sets the Y coordinate of  the  bottom  corner  of  the
           active  zone. Unlike others, this parameter is expressed in
           relative coordinates from the "YOffset" parameter.  "YSize"
           is a synonym.

           Option "ZMin" "number"
           Minimum  pressure  reading  that  will be accepted from the
           Stylus tool. "MinZ" is a synonym.

           Option "ZMax" "number"
           Maximum pressure reading that will  be  accepted  from  the
           Stylus tool. "MaxZ" is a synonym.

           Option "XThreshold" "number"
           Minimal  change  in    X  coordinate  position  that  will be
           accepted as data input.  "ThresholdX" is a synonym.

           Option "YThreshold" "number"
           Minimal change  in  Y  coordinate  position    that  will  be
           accepted as data input.  "ThresholdY" is a synonym.

           Option "ZThreshold" "number"
           Minimal change in pressure reading that will be accepted as
           data input.    "ThresholdZ" is a synonym.

           Option "InvX" "on"
           Inverts X coordinate reports. "XInv" is a synonym.

           Option "InvY" "on"
           Inverts Y coordinate reports. "YInv" is a synonym.

           Option "Pressure" "soft"|"hard"|"linear"
           Pressure reports either delivered in  linearly  incremental
           values  (default),  or  perturbed  by one of two log-linear
           algorithms ("soft" or "hard".)

           Option "KeepShape" "on"
           When this  option  is  enabled,  the  active  zone    begins
           according  to TopX and TopY.  The bottom corner is adjusted
           to keep the ratio width/height of the active zone the  same
           as  the  screen  while maximizing the area described by the
           active area set of  parameters,  XTop/YTop/XBottom/YBottom,
           XMax/YMax, or XOffset/YOffset/XSize/YSize.

           Option "DebugLevel" number
           sets the level of debugging info reported.

       This driver is currently Linux specific.

SEE ALSO
       Xorg(1), xorg.conf(5), Xserver(1), X(7), hyperpen(4).

AUTHORS
       Bryan W. Headley <bheadley@earthlink.net>

PROJECT PAGE
       http://aiptektablet.sourceforge.net  tracks ongoing development of this
       driver, the Linux kernel driver, and a GUI front-end  application  that
       works in concert with the above.



X Version 11            xf86-input-aiptek 1.2.0             AIPTEK(4)

```Thanks so much for your help.

---

### Post by Favux on 2010-08-11
Here's an Aiptek .fdi I worked on with some folks a while ago:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

    <!-- Aiptek:  Medion Md9570; Trust Wireless Tablet TB-3100 -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
        <merge key="input.x11_options.ZThreshold" type="string">5</merge>
        <merge key="input.x11_options.Pressure" type="string">linear</merge>
    </match>
  </device>
</deviceinfo>
```
From:  [http://ubuntuforums.org/showpost.php?p=7604483&postcount=50](http://ubuntuforums.org/showpost.php?p=7604483&postcount=50)  The thing that stands out to me is yours lacks the SendCoreEvents line.

---

### Post by knurledflanges on 2010-08-11
I put in the Sendcoreevents line and still no luck.
Two things I haven't mentioned:
In GIMP, when the tablet is set up in Extended Input Devices, it doesn't work but it also doesn't let me use my normal mouse with any tools that the tablet would work with, eg the paintbrush. Clicking the mouse for other purposes, ie menu and tool selection, works like normal.
About half the time, when I plug the tablet in or start with it plugged in, it doesn't work at all unless I go through a procedure I found somewhere on here, where I do:
```
me@computer:/sys/bus/usb/drivers/aiptek/3-2:1.0$ sudo echo absolute > ./coordinate_mode &&  sudo echo anything > ./execute
```
about 5 or 6 times, then it goes to its usual mode of moving the cursor but that's it.

I don't understand the architecture of all this, but the behavior where it lets me "hover" the cursor (move the mouse cursor without touching the pen down) up until the point where I touch it down once, and then no more without the pen touched down has me wondering if I'm dealing with a straight up bug.

---

### Post by Favux on 2010-08-11
There's a couple of similar bug reports on launchpad.  Some folks seem to be using the WizardPen driver.

I found what may be a specific driver for your tablet, but I can't find the dates for the deb.s.  At least the git had an entry from 5/10 and it was updated for Xserver 1.7 (Lucid).

Source package-git and cvs:  [http://packages.debian.org/source/lenny/xserver-xorg-input-hyperpen](http://packages.debian.org/source/lenny/xserver-xorg-input-hyperpen)

xserver-xorg-input-hyperpen (1:1.2.0-1) - This package provides the driver for Aiptek HyperPen 6000 graphics tablets.:  [http://packages.debian.org/lenny/xserver-xorg-input-hyperpen](http://packages.debian.org/lenny/xserver-xorg-input-hyperpen)

---

### Post by knurledflanges on 2010-08-13
I get this error when I try to install it:
```

 xserver-xorg-core conflicts with xserver-xorg-input-2
  xserver-xorg-input-hyperpen provides xserver-xorg-input-2 and is to be installed.

```

Does this mean it's too old to work?

---

### Post by Favux on 2010-08-13
Hi knurledflanges,

I think it's the other way around, xserver-xorg-input-2 is newer and conflicts with the default Lucid xserver-xorg-core (or maybe the xserver-xorg-input-all), see:  [http://packages.debian.org/sid/xserver-xorg-input-2](http://packages.debian.org/sid/xserver-xorg-input-2) So we're stuck since upgrading(?) to it will probably break stuff.  So you may have to update other stuff, which could get complicated.

Just to be sure the tablets full name is the Aiptek HyperPen 6000, correct?  In which case I found an even newer one (xserver-xorg-input-hyperpen (1:1.3.0-1 and others) ):  [http://packages.debian.org/sid/xserver-xorg-input-hyperpen](http://packages.debian.org/sid/xserver-xorg-input-hyperpen)

But anyway if that's the right tablet name you see why I think it may require, or at least do better, with a driver other that the vanilla Aiptek.  That may be causing the problems you're seeing.  I don't think it's in Synaptic Package Manager, so then I guess the question becomes can we get the vanilla Aiptek driver to work somehow.

---

### Post by knurledflanges on 2010-08-16
Model printed on the back is "T-6000U," front says Aiptek, and I'm pretty sure the "T" stands for "teal," which it is. It's the USB version; I understand there's an old serial version without the "U" in the title that's still in relatively wide use for some reason. 

I was actually able to install the newer driver using gdebi; however looking at the page I realize it may be for the serial version, since it doesn't say USB. It's not working at any rate; do I need to make a config file somewhere?

I think I'm just going to update to 10.4 and accept some downtime on various other things while I get them working; I really want to use my tablet...

Thanks for your help!

---

### Post by knurledflanges on 2010-08-16
Well, good news. I upgraded to 10.4, followed the instructions for 10.4 on the Aiptek community driver page and it works! Well, movement and tip pressure work; the pen buttons don't do anything but that's not important to me.

I'm using the 10-aiptek.conf file just as it's presented [here.]("https://help.ubuntu.com/community/AiptekTablet#Ubuntu%2010.04%20%28Lucid%20Lynx%29")

I still wish I understood more about the architecture/rules of how exactly all this works. Like for example what the page means when it says "something like this" for making the rules.d file. I've tried reading through the xorg-conf manual but it's pretty dense.

Thanks for your help!

---

### Post by Favux on 2010-08-16
Hi knurledflanges,

Nice work!

For the stylus buttons did you try the xinput button map stuff on Aiptek wiki?

Using the Aiptek manual we should be able to add options to the aiptek.conf.  What did you want to do?

---

### Post by Joundill on 2010-08-19
Hey guys, I recently got my Aiptek 6000U tablet working, here's my fdi file if you want it, I'm running Jaunty.

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
      <merge key="input.x11_options.zMax" type="string">511</merge>
    </match>
  </device>
</deviceinfo>

```

I have it in /etc/hal/fdi/policy/

I'm still working on getting the hotkey functions working, then I'll be done.

Pressure and buttons are all working.

---

