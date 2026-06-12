---
title: "Synaptics touchpad - no multitouch support"
date: 2010-06-17
forum: Hardware
---

### Post by teo_rossi on 2010-06-17
Hi, I have a Sony VAIO CW2C5E laptop with a multitouch synaptics touchpad (real multitouch, checked using windows synaptics driver). 

Ubuntu does not recognize the touchpad as MT enabled so two finger scrolling option is grayed out and sometimes, when touching the pad with two fingers the pointer goes crazy. 

Following suggestions on other threads, I checked with synclient and only 1 finger is detected. 

I paste some info that might be useful. Please tell me if more info is needed

```

$ cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Keys"
P: Phys=
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input4
U: Uniq=
H: Handlers=rfkill kbd event4 
B: EV=13
B: KEY=1f160f0000 c00000000 10000000000000 200000000 600b00102c00 380000240300400 e000000000000 0
B: MSC=10

I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Jogdial"
P: Phys=
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=7
B: KEY=40000 0 0 0 0
B: REL=100

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input7
U: Uniq=
H: Handlers=mouse2 event7 
B: EV=b
B: KEY=420 70000 0 0 0 0
B: ABS=11000003

```

```

$ dmesg | grep "Synaptics"
[   28.050268] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   28.099400] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7

```

```
$ cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection

Section "InputDevice"
	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Sony"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0:/etc/X11/edid2.bin"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

```
$ cat /var/log/Xorg.0.log
[    30.465] 
X.Org X Server 1.8.1.901 (1.8.2 RC 1)
Release Date: 2010-05-11
[    30.465] X Protocol Version 11, Revision 0
[    30.465] Build Operating System: Linux 2.6.24-28-xen x86_64 Ubuntu
[    30.465] Current Operating System: Linux matteo-vaio 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64
[    30.465] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=fe1a051b-27ef-43bd-88c8-fbfd8f3d4e7f ro quiet splash
[    30.466] Build Date: 14 June 2010  04:55:32AM
[    30.466] xorg-server 2:1.8.1.901+git20100613+server-1.8-branch.e50f84d6-0ubuntu0sarvatt2~lucid (For technical support please see http://www.ubuntu.com/support) 
[    30.466] Current version of pixman: 0.19.1
[    30.466] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    30.466] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.466] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 17 10:47:57 2010
[    30.466] (==) Using config file: "/etc/X11/xorg.conf"
[    30.466] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.466] (==) ServerLayout "Layout0"
[    30.466] (**) |-->Screen "Screen0" (0)
[    30.466] (**) |   |-->Monitor "Monitor0"
[    30.466] (**) |   |-->Device "Device0"
[    30.466] (**) |-->Input Device "Keyboard0"
[    30.466] (**) |-->Input Device "Synaptics Touchpad"
[    30.466] (==) Automatically adding devices
[    30.466] (==) Automatically enabling devices
[    30.466] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.466] 	Entry deleted from font path.
[    30.466] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    30.466] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.466] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.466] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    30.466] (WW) Disabling Keyboard0
[    30.466] (II) Loader magic: 0x7cf8e0
[    30.466] (II) Module ABI versions:
[    30.466] 	X.Org ANSI C Emulation: 0.4
[    30.466] 	X.Org Video Driver: 7.0
[    30.466] 	X.Org XInput driver : 9.0
[    30.466] 	X.Org Server Extension : 3.0
[    30.484] (--) PCI:*(0:1:0:0) 10de:0a75:104d:9072 nVidia Corporation GT218 [GeForce 310M] rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    30.484] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.484] (II) LoadModule: "extmod"
[    30.496] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.496] (II) Module extmod: vendor="X.Org Foundation"
[    30.496] 	compiled for 1.8.1.901, module version = 1.0.0
[    30.496] 	Module class: X.Org Server Extension
[    30.496] 	ABI class: X.Org Server Extension, version 3.0
[    30.496] (II) Loading extension MIT-SCREEN-SAVER
[    30.496] (II) Loading extension XFree86-VidModeExtension
[    30.496] (II) Loading extension XFree86-DGA
[    30.496] (II) Loading extension DPMS
[    30.496] (II) Loading extension XVideo
[    30.496] (II) Loading extension XVideo-MotionCompensation
[    30.496] (II) Loading extension X-Resource
[    30.496] (II) LoadModule: "dbe"
[    30.496] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.496] (II) Module dbe: vendor="X.Org Foundation"
[    30.496] 	compiled for 1.8.1.901, module version = 1.0.0
[    30.496] 	Module class: X.Org Server Extension
[    30.496] 	ABI class: X.Org Server Extension, version 3.0
[    30.496] (II) Loading extension DOUBLE-BUFFER
[    30.496] (II) LoadModule: "glx"
[    30.496] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    30.501] (II) Module glx: vendor="NVIDIA Corporation"
[    30.501] 	compiled for 4.0.2, module version = 1.0.0
[    30.501] 	Module class: X.Org Server Extension
[    30.501] (II) NVIDIA GLX Module  256.29  Thu May 27 17:48:26 PDT 2010
[    30.501] (II) Loading extension GLX
[    30.501] (II) LoadModule: "record"
[    30.501] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.502] (II) Module record: vendor="X.Org Foundation"
[    30.502] 	compiled for 1.8.1.901, module version = 1.13.0
[    30.502] 	Module class: X.Org Server Extension
[    30.502] 	ABI class: X.Org Server Extension, version 3.0
[    30.502] (II) Loading extension RECORD
[    30.502] (II) LoadModule: "dri"
[    30.502] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.502] (II) Module dri: vendor="X.Org Foundation"
[    30.502] 	compiled for 1.8.1.901, module version = 1.0.0
[    30.502] 	ABI class: X.Org Server Extension, version 3.0
[    30.502] (II) Loading extension XFree86-DRI
[    30.502] (II) LoadModule: "dri2"
[    30.502] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.502] (II) Module dri2: vendor="X.Org Foundation"
[    30.502] 	compiled for 1.8.1.901, module version = 1.2.0
[    30.502] 	ABI class: X.Org Server Extension, version 3.0
[    30.502] (II) Loading extension DRI2
[    30.502] (II) LoadModule: "nvidia"
[    30.502] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    30.502] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.502] 	compiled for 4.0.2, module version = 1.0.0
[    30.502] 	Module class: X.Org Video Driver
[    30.503] (II) LoadModule: "synaptics"
[    30.503] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.503] (II) Module synaptics: vendor="X.Org Foundation"
[    30.503] 	compiled for 1.8.1.901, module version = 1.2.99
[    30.503] 	Module class: X.Org XInput Driver
[    30.503] 	ABI class: X.Org XInput driver, version 9.0
[    30.503] (II) NVIDIA dlloader X Driver  256.29  Thu May 27 17:28:03 PDT 2010
[    30.503] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.503] (++) using VT number 7

[    30.503] (II) Primary Device is: PCI 01@00:00:0
[    30.503] (II) Loading sub module "fb"
[    30.503] (II) LoadModule: "fb"
[    30.503] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.503] (II) Module fb: vendor="X.Org Foundation"
[    30.503] 	compiled for 1.8.1.901, module version = 1.0.0
[    30.503] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.503] (II) Loading sub module "wfb"
[    30.503] (II) LoadModule: "wfb"
[    30.503] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.503] (II) Module wfb: vendor="X.Org Foundation"
[    30.503] 	compiled for 1.8.1.901, module version = 1.0.0
[    30.503] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.503] (II) Loading sub module "ramdac"
[    30.503] (II) LoadModule: "ramdac"
[    30.503] (II) Module "ramdac" already built-in

 [...] NVIDIA stuff [...]

[    32.816] (II) Initializing built-in extension Generic Event Extension
[    32.816] (II) Initializing built-in extension SHAPE
[    32.816] (II) Initializing built-in extension MIT-SHM
[    32.816] (II) Initializing built-in extension XInputExtension
[    32.816] (II) Initializing built-in extension XTEST
[    32.816] (II) Initializing built-in extension BIG-REQUESTS
[    32.816] (II) Initializing built-in extension SYNC
[    32.816] (II) Initializing built-in extension XKEYBOARD
[    32.816] (II) Initializing built-in extension XC-MISC
[    32.816] (II) Initializing built-in extension SECURITY
[    32.816] (II) Initializing built-in extension XINERAMA
[    32.816] (II) Initializing built-in extension XFIXES
[    32.816] (II) Initializing built-in extension RENDER
[    32.816] (II) Initializing built-in extension RANDR
[    32.816] (II) Initializing built-in extension COMPOSITE
[    32.816] (II) Initializing built-in extension DAMAGE
[    32.817] (II) Initializing extension GLX
[    32.837] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.838] (II) Synaptics touchpad driver version 1.2.99
[    34.370] (--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
[    34.530] (**) Option "Device" "/dev/input/event7"
[    34.880] (--) Synaptics Touchpad: x-axis range 1472 - 5472
[    34.880] (--) Synaptics Touchpad: y-axis range 1408 - 4448
[    34.880] (--) Synaptics Touchpad: pressure range 0 - 255
[    34.880] (--) Synaptics Touchpad: finger width range 0 - 0
[    34.880] (--) Synaptics Touchpad: buttons: left right middle
[    34.880] (**) Option "SHMConfig" "on"
[    34.880] (**) Option "HorizScrollDelta" "0"
[    35.050] (--) Synaptics Touchpad: touchpad found
[    35.050] (**) Option "SendCoreEvents" "true"
[    35.050] (**) Synaptics Touchpad: always reports core events
[    35.210] (II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: TOUCHPAD)
[    35.210] (**) Synaptics Touchpad: (accel) keeping acceleration scheme 1
[    35.210] (**) Synaptics Touchpad: (accel) acceleration profile 0
[    35.210] (**) Synaptics Touchpad: (accel) acceleration factor: 2.000
[    35.210] (**) Synaptics Touchpad: (accel) acceleration threshold: 4
[    35.450] (--) Synaptics Touchpad: touchpad found
[    35.455] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event4)
[    35.455] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    35.455] (II) LoadModule: "evdev"
[    35.455] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.456] (II) Module evdev: vendor="X.Org Foundation"
[    35.456] 	compiled for 1.8.1.901, module version = 2.4.99
[    35.456] 	Module class: X.Org XInput Driver
[    35.456] 	ABI class: X.Org XInput driver, version 9.0
[    35.456] (**) Sony Vaio Keys: always reports core events
[    35.456] (**) Sony Vaio Keys: Device: "/dev/input/event4"
[    35.530] (--) Sony Vaio Keys: Found keys
[    35.530] (II) Sony Vaio Keys: Configuring as keyboard
[    35.530] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
[    35.530] (**) Option "xkb_rules" "evdev"
[    35.530] (**) Option "xkb_model" "pc105"
[    35.530] (**) Option "xkb_layout" "it"
[    35.532] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    35.534] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    35.534] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.534] (**) Video Bus: always reports core events
[    35.534] (**) Video Bus: Device: "/dev/input/event6"
[    35.650] (--) Video Bus: Found keys
[    35.650] (II) Video Bus: Configuring as keyboard
[    35.650] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    35.650] (**) Option "xkb_rules" "evdev"
[    35.650] (**) Option "xkb_model" "pc105"
[    35.650] (**) Option "xkb_layout" "it"
[    35.669] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    35.669] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.669] (**) Power Button: always reports core events
[    35.669] (**) Power Button: Device: "/dev/input/event1"
[    35.691] (--) Power Button: Found keys
[    35.691] (II) Power Button: Configuring as keyboard
[    35.692] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    35.692] (**) Option "xkb_rules" "evdev"
[    35.692] (**) Option "xkb_model" "pc105"
[    35.692] (**) Option "xkb_layout" "it"
[    35.692] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    35.692] (II) No input driver/identifier specified (ignoring)
[    35.693] (II) config/udev: Adding input device UVC Camera (05ca:18b5) (/dev/input/event8)
[    35.693] (**) UVC Camera (05ca:18b5): Applying InputClass "evdev keyboard catchall"
[    35.693] (**) UVC Camera (05ca:18b5): always reports core events
[    35.693] (**) UVC Camera (05ca:18b5): Device: "/dev/input/event8"
[    35.751] (--) UVC Camera (05ca:18b5): Found keys
[    35.752] (II) UVC Camera (05ca:18b5): Configuring as keyboard
[    35.752] (II) XINPUT: Adding extended input device "UVC Camera (05ca:18b5)" (type: KEYBOARD)
[    35.752] (**) Option "xkb_rules" "evdev"
[    35.752] (**) Option "xkb_model" "pc105"
[    35.752] (**) Option "xkb_layout" "it"
[    35.752] (II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
[    35.752] (II) No input driver/identifier specified (ignoring)
[    35.755] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    35.755] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    35.755] (**) AT Translated Set 2 keyboard: always reports core events
[    35.755] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    35.832] (--) AT Translated Set 2 keyboard: Found keys
[    35.832] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    35.832] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    35.832] (**) Option "xkb_rules" "evdev"
[    35.832] (**) Option "xkb_model" "pc105"
[    35.832] (**) Option "xkb_layout" "it"
[    35.832] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    35.832] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    35.832] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    35.832] (II) Synaptics touchpad driver version 1.2.99
[    35.832] (**) Option "Device" "/dev/input/event7"
[    35.952] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[    35.952] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[    36.031] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[    36.031] (II) UnloadModule: "synaptics"
[    36.032] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[    36.032] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    36.032] (II) Synaptics touchpad driver version 1.2.99
[    40.871] (EE) SynPS/2 Synaptics TouchPad no synaptics event device found
[    40.872] (**) Option "Device" "/dev/input/mouse2"
[    40.972] (EE) Query no Synaptics: 6003C8
[    40.972] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[    40.972] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[    41.111] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[    41.111] (II) UnloadModule: "synaptics"
[    41.114] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
[    41.114] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    41.114] (**) Macintosh mouse button emulation: always reports core events
[    41.114] (**) Macintosh mouse button emulation: Device: "/dev/input/event2"
[    41.192] (--) Macintosh mouse button emulation: Found 3 mouse buttons
[    41.192] (--) Macintosh mouse button emulation: Found relative axes
[    41.192] (--) Macintosh mouse button emulation: Found x and y relative axes
[    41.192] (II) Macintosh mouse button emulation: Configuring as mouse
[    41.192] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    41.192] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    41.192] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    41.192] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    41.192] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    41.192] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    41.192] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    41.192] (II) Macintosh mouse button emulation: initialized for relative axes.
[    41.192] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
[    41.192] (II) No input driver/identifier specified (ignoring)
[    41.192] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event5)
[    41.192] (II) No input driver/identifier specified (ignoring)
[    41.192] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse1)
[    41.192] (II) No input driver/identifier specified (ignoring)

```

---

### Post by zecapistolas on 2010-08-28
Hello,

Recently i buy new laptop, Sony Vaio VPCS12M9E but most hardware on this laptop does not work with Ubuntu 10.10 Maverick 32bits, including TouchPad.... 

What driver or packages you install?

---

