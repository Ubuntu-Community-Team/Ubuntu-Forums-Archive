---
title: "Is there an equivalent for &quot;Device Manager&quot; from Windows in Ubuntu?"
date: 2020-08-30
forum: Hardware
---

### Post by furesuka on 2020-08-30
Title says it all. I'm not just talking about things like Ubuntu's "Additional Drivers", it doesn't display anything at all. I'm talking about one that really can manage drivers like Window's. And I just thought Id't be helpful to have one of these around.
I need one with as much features as Window's Hardware Device Manager as possible. Disable, uninstall, install, etc. all drivers in the system if Ubuntu has one.

---

### Post by Autodave on 2020-08-30
You really do NOT want to just delete and install different drivers in Linux.  Unless there is something specific that you need, your drivers all came with the kernel and will be updated as needed.

If you start installing other drivers, they are NOT updated automatically and can cause more damage to the system than they will help.

Again, unless you are now having a problem or need something very specific, leave it alone.

---

### Post by SeijiSensei on 2020-08-30
Most every driver you'll ever need comes packaged with the kernel. Those that are not open sourced, like NVIDIA's graphics drivers, are available through Additional Drivers. As Autodave said, leave it alone.

Linux is not Windows.

---

### Post by furesuka on 2020-08-30
I understood, I'm not looking for a driver manager anymore. In fact the only reason I'm looking for one is that I want to disable my GPU drivers so Ubuntu won't use it anymore. In other words, I want Ubuntu to use the CPU's integrated graphics feature instead of the GPU because it's broken and basically unusable. Can you guys help me with this?

---

### Post by CelticWarrior on 2020-08-30
Two solutions:

If the BIOS/UEFI has a setting for which graphics to use, just set it to the iGPU. By far this is the best solution.
In the absence of the above and if you have Nvidia, just make sure the proper Nvidia drivers ARE installed - yes, the opposite of what you think is the solution (spoiler alert: it's not, it's nonsense) - and then open Nvidia X Sever Settings and select the iGPU profile and reboot. This setting will be permanent unless you later toggle it to the high performance profile.

---

### Post by Yellow Pasque on 2020-08-30
Desktop or laptop?
What is output of:
```
lspci
```

---

### Post by furesuka on 2020-08-30
Okay I made a mistake not stating my laptop specs which is [here]("https://support.hp.com/ph-en/document/c02981969")
BIOS settings only shows a setting about "Fixed/Dynamic" graphics mode which I have no idea about, and I don't think Nvidia drivers will work in my system.

Output of command "lspci":
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)



```

---

### Post by Yellow Pasque on 2020-08-31
> **furesuka said:**
> BIOS settings only shows a setting about "Fixed/Dynamic" graphics mode which I have no idea about
It's more applicable to Windows, but see: [https://support.hp.com/us-en/document/c03048374](https://support.hp.com/us-en/document/c03048374)

> I don't think Nvidia drivers will work in my system.
True. For some reason, CelticWarrior just assumed you had an Nvidia GPU.

> I want Ubuntu to use the CPU's integrated graphics feature instead of the GPU because it's broken and basically unusable.
This is how it should be setup by default. In other words, the Intel GPU should be used for all graphics unless you explicitly specify something to run on the AMD GPU with DRI_PRIME . To verify, look at output of:
```
glxinfo -B
DRI_PRIME=1 glxinfo -B
```

---

### Post by furesuka on 2020-08-31
The terminal didn't find a "glxinfo" command but said it can be installed with mesa-utils, so I did.
(I was not sure if those are two commands but both seem to give the same output so I will only post one)

output of "glxinfo -B":
```
name of display: :1display: :1  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: VMware, Inc. (0xffffffff)
    Device: llvmpipe (LLVM 10.0.0, 256 bits) (0xffffffff)
    Version: 20.0.8
    Accelerated: no
    Video memory: 3882MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 10.0.0, 256 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 20.0.8
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 3.1 Mesa 20.0.8
OpenGL shading language version string: 1.40
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
```

---

### Post by Yellow Pasque on 2020-08-31
^That's bad. Your graphics aren't working correctly. Have you tried any modifications to fix your issue before you posted this thread?

Can you copy/paste contents of /var/log/Xorg.0.log file?

---

### Post by furesuka on 2020-08-31
I don't think I made any modifications for this issue since I just installed Ubuntu yesterday. I previously had Linux Mint, which had the same problem so I tried switching OS but it seems that the problem didn't go away.
Something to note is that I use "nomodeset" command (I followed this [thread]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/38782#38782")) for booting because otherwise Ubuntu won't boot at all (same goes for my previous Mint).
Xorg.0.log contents:
```
[    53.474] (--) Log file renamed from "/var/log/Xorg.pid-1246.log" to "/var/log/Xorg.0.log"[    53.492] 
X.Org X Server 1.20.8
X Protocol Version 11, Revision 0
[    53.492] Build Operating System: Linux 4.4.0-184-generic x86_64 Ubuntu
[    53.492] Current Operating System: Linux furesuka-PC 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64
[    53.492] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-42-generic root=UUID=dd16bcae-dd0c-4071-bcae-7a10193e0f57 ro nomodeset quiet splash nomodeset vt.handoff=7
[    53.492] Build Date: 24 June 2020  06:00:21AM
[    53.492] xorg-server 2:1.20.8-2ubuntu2.2 (For technical support please see http://www.ubuntu.com/support) 
[    53.492] Current version of pixman: 0.38.4
[    53.492]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    53.492] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    53.492] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 31 13:13:14 2020
[    53.523] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    53.539] (==) No Layout section.  Using the first Screen section.
[    53.539] (==) No screen section available. Using defaults.
[    53.539] (**) |-->Screen "Default Screen Section" (0)
[    53.540] (**) |   |-->Monitor "<default monitor>"
[    53.550] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    53.550] (==) Automatically adding devices
[    53.550] (==) Automatically enabling devices
[    53.550] (==) Automatically adding GPU devices
[    53.550] (==) Automatically binding GPU devices
[    53.550] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    53.574] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    53.574]     Entry deleted from font path.
[    53.574] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    53.574]     Entry deleted from font path.
[    53.574] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    53.574]     Entry deleted from font path.
[    53.575] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    53.575]     Entry deleted from font path.
[    53.575] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    53.575]     Entry deleted from font path.
[    53.575] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    53.575] (==) ModulePath set to "/usr/lib/xorg/modules"
[    53.575] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    53.575] (II) Loader magic: 0x558f2e0b5020
[    53.575] (II) Module ABI versions:
[    53.575]     X.Org ANSI C Emulation: 0.4
[    53.575]     X.Org Video Driver: 24.1
[    53.575]     X.Org XInput driver : 24.1
[    53.575]     X.Org Server Extension : 10.0
[    53.577] (++) using VT number 1


[    53.583] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c2
[    53.589] (--) PCI:*(0@0:2:0) 8086:0116:103c:1657 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00006000/64, BIOS @ 0x????????/131072
[    53.589] (--) PCI: (1@0:0:0) 1002:6740:103c:1657 rev 0, Mem @ 0xa0000000/268435456, 0xc6500000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
[    53.603] (II) LoadModule: "glx"
[    53.645] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    53.657] (II) Module glx: vendor="X.Org Foundation"
[    53.657]     compiled for 1.20.8, module version = 1.0.0
[    53.657]     ABI class: X.Org Server Extension, version 10.0
[    53.658] (==) Matched modesetting as autoconfigured driver 0
[    53.658] (==) Matched fbdev as autoconfigured driver 1
[    53.658] (==) Matched vesa as autoconfigured driver 2
[    53.658] (==) Assigned the driver to the xf86ConfigLayout
[    53.658] (II) LoadModule: "modesetting"
[    53.658] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    53.667] (II) Module modesetting: vendor="X.Org Foundation"
[    53.667]     compiled for 1.20.8, module version = 1.20.8
[    53.667]     Module class: X.Org Video Driver
[    53.667]     ABI class: X.Org Video Driver, version 24.1
[    53.667] (II) LoadModule: "fbdev"
[    53.668] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    53.668] (II) Module fbdev: vendor="X.Org Foundation"
[    53.668]     compiled for 1.20.1, module version = 0.5.0
[    53.668]     Module class: X.Org Video Driver
[    53.669]     ABI class: X.Org Video Driver, version 24.0
[    53.669] (II) LoadModule: "vesa"
[    53.669] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    53.676] (II) Module vesa: vendor="X.Org Foundation"
[    53.676]     compiled for 1.20.4, module version = 2.4.0
[    53.676]     Module class: X.Org Video Driver
[    53.676]     ABI class: X.Org Video Driver, version 24.0
[    53.676] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    53.677] (II) FBDEV: driver for framebuffer: fbdev
[    53.677] (II) VESA: driver for VESA chipsets: vesa
[    53.677] (EE) open /dev/dri/card0: No such file or directory
[    53.677] (WW) Falling back to old probe method for modesetting
[    53.677] (EE) open /dev/dri/card0: No such file or directory
[    53.677] (II) Loading sub module "fbdevhw"
[    53.677] (II) LoadModule: "fbdevhw"
[    53.677] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    53.688] (II) Module fbdevhw: vendor="X.Org Foundation"
[    53.688]     compiled for 1.20.8, module version = 0.0.2
[    53.689]     ABI class: X.Org Video Driver, version 24.1
[    53.689] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    53.689] (II) FBDEV(1): using default device
[    53.689] (EE) Screen 0 deleted because of no matching config section.
[    53.689] (II) UnloadModule: "modesetting"
[    53.689] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    53.689] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    53.689] (==) FBDEV(0): RGB weight 888
[    53.689] (==) FBDEV(0): Default visual is TrueColor
[    53.689] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    53.689] (II) FBDEV(0): hardware: VESA VGA (video memory: 3072kB)
[    53.689] (II) FBDEV(0): checking modes against framebuffer device...
[    53.689] (II) FBDEV(0): checking modes against monitor...
[    53.690] (II) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    53.690] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[    53.690] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[    53.690] (==) FBDEV(0): DPI set to (96, 96)
[    53.690] (II) Loading sub module "fb"
[    53.690] (II) LoadModule: "fb"
[    53.690] (II) Loading /usr/lib/xorg/modules/libfb.so
[    53.699] (II) Module fb: vendor="X.Org Foundation"
[    53.699]     compiled for 1.20.8, module version = 1.0.0
[    53.699]     ABI class: X.Org ANSI C Emulation, version 0.4
[    53.699] (**) FBDEV(0): using shadow framebuffer
[    53.699] (II) Loading sub module "shadow"
[    53.699] (II) LoadModule: "shadow"
[    53.700] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    53.700] (II) Module shadow: vendor="X.Org Foundation"
[    53.700]     compiled for 1.20.8, module version = 1.1.0
[    53.700]     ABI class: X.Org ANSI C Emulation, version 0.4
[    53.700] (II) UnloadModule: "vesa"
[    53.700] (II) Unloading vesa
[    53.701] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    53.721] (==) FBDEV(0): Backing store enabled
[    53.723] (==) FBDEV(0): DPMS enabled
[    53.723] (II) Found 2 VGA devices: arbiter wrapping enabled
[    53.723] (II) Initializing extension Generic Event Extension
[    53.723] (II) Initializing extension SHAPE
[    53.724] (II) Initializing extension MIT-SHM
[    53.724] (II) Initializing extension XInputExtension
[    53.725] (II) Initializing extension XTEST
[    53.726] (II) Initializing extension BIG-REQUESTS
[    53.726] (II) Initializing extension SYNC
[    53.727] (II) Initializing extension XKEYBOARD
[    53.727] (II) Initializing extension XC-MISC
[    53.728] (II) Initializing extension SECURITY
[    53.728] (II) Initializing extension XFIXES
[    53.728] (II) Initializing extension RENDER
[    53.729] (II) Initializing extension RANDR
[    53.729] (II) Initializing extension COMPOSITE
[    53.730] (II) Initializing extension DAMAGE
[    53.730] (II) Initializing extension MIT-SCREEN-SAVER
[    53.730] (II) Initializing extension DOUBLE-BUFFER
[    53.730] (II) Initializing extension RECORD
[    53.730] (II) Initializing extension DPMS
[    53.730] (II) Initializing extension Present
[    53.731] (II) Initializing extension DRI3
[    53.731] (II) Initializing extension X-Resource
[    53.731] (II) Initializing extension XVideo
[    53.731] (II) Initializing extension XVideo-MotionCompensation
[    53.731] (II) Initializing extension SELinux
[    53.731] (II) SELinux: Disabled on system
[    53.731] (II) Initializing extension GLX
[    53.731] (II) AIGLX: Screen 0 is not DRI2 capable
[    55.213] (II) IGLX: Loaded and initialized swrast
[    55.214] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    55.214] (II) Initializing extension XFree86-VidModeExtension
[    55.214] (II) Initializing extension XFree86-DGA
[    55.214] (II) Initializing extension XFree86-DRI
[    55.236] (II) Initializing extension DRI2
[    55.558] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    55.558] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    55.558] (II) LoadModule: "libinput"
[    55.558] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    55.574] (II) Module libinput: vendor="X.Org Foundation"
[    55.574]     compiled for 1.20.4, module version = 0.29.0
[    55.574]     Module class: X.Org XInput Driver
[    55.574]     ABI class: X.Org XInput driver, version 24.1
[    55.574] (II) Using input driver 'libinput' for 'Power Button'
[    55.576] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 22 paused 0
[    55.576] (**) Power Button: always reports core events
[    55.576] (**) Option "Device" "/dev/input/event2"
[    55.576] (**) Option "_source" "server/udev"
[    55.607] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    55.607] (II) event2  - Power Button: device is a keyboard
[    55.608] (II) event2  - Power Button: device removed
[    55.608] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    55.608] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    55.608] (**) Option "xkb_model" "pc105"
[    55.608] (**) Option "xkb_layout" "us"
[    55.611] (II) event2  - Power Button: is tagged by udev as: Keyboard
[    55.612] (II) event2  - Power Button: device is a keyboard
[    55.614] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    55.614] (II) No input driver specified, ignoring this device.
[    55.614] (II) This device may have been added with another device file.
[    55.614] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    55.614] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    55.614] (II) Using input driver 'libinput' for 'Power Button'
[    55.617] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 25 paused 0
[    55.617] (**) Power Button: always reports core events
[    55.617] (**) Option "Device" "/dev/input/event1"
[    55.617] (**) Option "_source" "server/udev"
[    55.618] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    55.618] (II) event1  - Power Button: device is a keyboard
[    55.618] (II) event1  - Power Button: device removed
[    55.618] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    55.618] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    55.618] (**) Option "xkb_model" "pc105"
[    55.618] (**) Option "xkb_layout" "us"
[    55.619] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    55.619] (II) event1  - Power Button: device is a keyboard
[    55.620] (II) config/udev: Adding input device HP TrueVision HD
: HP TrueVisio (/dev/input/event7)
[    55.620] (**) HP TrueVision HD
: HP TrueVisio: Applying InputClass "libinput keyboard catchall"
[    55.620] (II) Using input driver 'libinput' for 'HP TrueVision HD
: HP TrueVisio'
[    55.622] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 26 paused 0
[    55.622] (**) HP TrueVision HD
: HP TrueVisio: always reports core events
[    55.622] (**) Option "Device" "/dev/input/event7"
[    55.622] (**) Option "_source" "server/udev"
[    55.624] (II) event7  - HP TrueVision HD
: HP TrueVisio: is tagged by udev as: Keyboard
[    55.624] (II) event7  - HP TrueVision HD
: HP TrueVisio: device is a keyboard
[    55.624] (II) event7  - HP TrueVision HD
: HP TrueVisio: device removed
[    55.624] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input8/event7"
[    55.624] (II) XINPUT: Adding extended input device "HP TrueVision HD
: HP TrueVisio" (type: KEYBOARD, id 8)
[    55.624] (**) Option "xkb_model" "pc105"
[    55.624] (**) Option "xkb_layout" "us"
[    55.626] (II) event7  - HP TrueVision HD
: HP TrueVisio: is tagged by udev as: Keyboard
[    55.626] (II) event7  - HP TrueVision HD
: HP TrueVisio: device is a keyboard
[    55.626] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    55.626] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    55.626] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    55.628] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 27 paused 0
[    55.628] (**) AT Translated Set 2 keyboard: always reports core events
[    55.628] (**) Option "Device" "/dev/input/event3"
[    55.628] (**) Option "_source" "server/udev"
[    55.629] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    55.629] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    55.630] (II) event3  - AT Translated Set 2 keyboard: device removed
[    55.630] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    55.630] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    55.630] (**) Option "xkb_model" "pc105"
[    55.630] (**) Option "xkb_layout" "us"
[    55.631] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    55.631] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[    55.632] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    55.632] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[    55.632] (II) Using input driver 'libinput' for 'SynPS/2 Synaptics TouchPad'
[    55.633] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 28 paused 0
[    55.633] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    55.633] (**) Option "Device" "/dev/input/event4"
[    55.633] (**) Option "_source" "server/udev"
[    55.635] (II) event4  - SynPS/2 Synaptics TouchPad: is tagged by udev as: Touchpad
[    55.636] (II) event4  - SynPS/2 Synaptics TouchPad: device is a touchpad
[    55.636] (II) event4  - SynPS/2 Synaptics TouchPad: device removed
[    55.636] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    55.636] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    55.637] (**) Option "AccelerationScheme" "none"
[    55.637] (**) SynPS/2 Synaptics TouchPad: (accel) selected scheme none/0
[    55.637] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    55.637] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    55.638] (II) event4  - SynPS/2 Synaptics TouchPad: is tagged by udev as: Touchpad
[    55.639] (II) event4  - SynPS/2 Synaptics TouchPad: device is a touchpad
[    55.639] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    55.639] (II) No input driver specified, ignoring this device.
[    55.639] (II) This device may have been added with another device file.
[    55.640] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    55.640] (II) No input driver specified, ignoring this device.
[    55.640] (II) This device may have been added with another device file.
[    55.640] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    55.640] (II) No input driver specified, ignoring this device.
[    55.640] (II) This device may have been added with another device file.
[    55.643] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    55.643] (**) HP WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    55.643] (II) Using input driver 'libinput' for 'HP WMI hotkeys'
[    55.644] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 29 paused 0
[    55.644] (**) HP WMI hotkeys: always reports core events
[    55.644] (**) Option "Device" "/dev/input/event5"
[    55.644] (**) Option "_source" "server/udev"
[    55.646] (II) event5  - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[    55.646] (II) event5  - HP WMI hotkeys: device is a keyboard
[    55.646] (II) event5  - HP WMI hotkeys: device removed
[    55.646] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event5"
[    55.646] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 11)
[    55.646] (**) Option "xkb_model" "pc105"
[    55.646] (**) Option "xkb_layout" "us"
[    55.648] (II) event5  - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[    55.648] (II) event5  - HP WMI hotkeys: device is a keyboard
[    75.498] (**) Option "fd" "22"
[    75.498] (II) event2  - Power Button: device removed
[    75.499] (**) Option "fd" "25"
[    75.499] (II) event1  - Power Button: device removed
[    75.499] (**) Option "fd" "26"
[    75.499] (II) event7  - HP TrueVision HD
: HP TrueVisio: device removed
[    75.499] (**) Option "fd" "27"
[    75.500] (II) event3  - AT Translated Set 2 keyboard: device removed
[    75.500] (**) Option "fd" "28"
[    75.500] (II) event4  - SynPS/2 Synaptics TouchPad: device removed
[    75.500] (**) Option "fd" "29"
[    75.500] (II) event5  - HP WMI hotkeys: device removed
[    75.501] (II) systemd-logind: got pause for 13:71
[    75.501] (II) systemd-logind: got pause for 13:68
[    75.501] (II) systemd-logind: got pause for 13:67
[    75.501] (II) systemd-logind: got pause for 13:65
[    75.501] (II) systemd-logind: got pause for 13:66
[    75.501] (II) systemd-logind: got pause for 13:69
[    83.486] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    83.486] (II) No input driver specified, ignoring this device.
[    83.486] (II) This device may have been added with another device file.
[    83.486] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[    83.486] (II) No input driver specified, ignoring this device.
[    83.486] (II) This device may have been added with another device file.
```

---

### Post by Yellow Pasque on 2020-08-31
Well, 'nomodeset' is what's disabling the 3D acceleration. You're not going to get a good experience booting with it. Have you tried booting without it after applying all updates?

---

### Post by furesuka on 2020-08-31
I tried again, removed "nomodeset" and left quiet splash alone manually on grub and sure enough, it was just a black screen. Doesn't respond to any key I pressed or doesn't detect any usb sticks (when I insert my usb stick it gives off a light to let me know it connected, this time it isn't)

---

### Post by Yellow Pasque on 2020-08-31
After you reboot (using nomodeset), see if there are any clues in the journal of the previous boot:
```
sudo journalctl -b -1
```

> BIOS settings only shows a setting about "Fixed/Dynamic" graphics mode
Have you tried toggling this and then booting without nomodeset?

---

### Post by furesuka on 2020-08-31
Output of "sudo journalctl -b -1":
```
Specifying boot ID or boot offset has no effect, no persistent journal was found.


```

Yesterday the setting was on fixed mode and booting without nomodeset results in a black screen, and recently I switched it over to dynamic mode and booted without nomodeset, sadly the results were the same.

---

### Post by furesuka on 2020-08-31
Update:
I tried booting on fixed mode without nomodeset and resulted displaying these texts but freezes there too eventually:
[IMG]https://i.ibb.co/Nnp76Qt/IMG-20200831-150541.jpg[/IMG]

might be helpful, idk

---

### Post by CelticWarrior on 2020-09-01
It isn't helpful. Those errors are likely harmless, don't prevent boot and will be there even if you don't see them (splash screen). The problem is the graphical environment not booting.

> [COLOR=#000000]True. For some reason, CelticWarrior just assumed you had an Nvidia GPU.[/COLOR]


No, I didn't. "[COLOR=#000000]In the absence of the above and *if you have Nvidia*". If is a conditional, not an assertion [/COLOR];)[COLOR=#000000] [/COLOR]

---

### Post by SeijiSensei on 2020-09-01
I used the "fixed/dynamic" option in the BIOS to force an HP machine to use the ATI/AMD adapter. Don't recall which choice was the right one though. It's been quite a while.

---

### Post by Yellow Pasque on 2020-09-01
> **CelticWarrior said:**
> No, I didn't. "[COLOR=#000000]In the absence of the above and *if you have Nvidia*". If is a conditional, not an assertion [/COLOR];)[COLOR=#000000] [/COLOR]

I see. My apologies.

---

### Post by marvin20867 on 2020-09-03
Here is link that might be useful for you.

Linux Driver Management provides a core library and some tooling to  enable the quick and easy enumeration of system devices, and  functionality to match devices to packages/drivers. This is designed to  be as agnostic as feasible whilst supporting a wide range of device  classes, to provide a building block for driver management and discovery  in Linux distributions.

[https://github.com/solus-project/linux-driver-management](https://github.com/solus-project/linux-driver-management)

---

### Post by pmaff on 2020-09-03
> **furesuka said:**
> I tried again, removed "nomodeset" and left quiet splash alone manually on grub and sure enough, it was just a black screen. Doesn't respond to any key I pressed or doesn't detect any usb sticks (when I insert my usb stick it gives off a light to let me know it connected, this time it isn't)  

That blank/black screen stuff reminded me of my first install with my nVidia 1050Ti.

 This webpage was helpful: [https://askubuntu.com/questions/949496/installing-ubuntu-16-04-on-msi-ge72mvr-system-freezes-when-i-restart](https://askubuntu.com/questions/949496/installing-ubuntu-16-04-on-msi-ge72mvr-system-freezes-when-i-restart) 

 So maybe there is an equivalent for the RADEON HD 6730M/6770M/7690M graphic card. 
Just a quick search gave me: [URL="https://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/"]
https://xpressrazor.wordpress.com/2013/01/13/how-to-setup-amdintel-hybrid-graphics-cards-in-linux-ubuntu/[/URL] 
but of course I cannot try this with my nVidia.  

One more question: do you get a terminal window if you do CTRL+ALT+F1 when the boot stops in this black screen?

Good luck!

Edit: I see that you have nomodeset 2 times:
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-42-generic root=UUID=dd16bcae-dd0c-4071-bcae-7a10193e0f57 ro nomodeset quiet splash nomodeset vt.handoff=7

---

### Post by furesuka on 2020-09-04
Holy cow I am able to boot now without the nomodeset option after installing [Ubuntu drivers]("https://www.amd.com/en/support/graphics/amd-radeon-hd/amd-radeon-hd-7000m-series/amd-radeon-hd-7690m-xt") from the official website thanks to pmaff's suggestion. Thanks! I thought my GPU was totally broken because it didn't work when installing its drivers in Windows 7 but here it is!
Even though it seems like the GPU is working now, AMD Catalyst Control Center is not working, it shows me this error:

[IMG]https://i.ibb.co/ZK8PfCr/Screenshot-from-2020-09-04-17-52-29.png[/IMG]

and I remember when installing the drivers I saw something like dependency errors or something, anyone know what's still wrong?

Regarding those "device descriptor" errors, okay I understand that I should ignore them.

The "fixed/dynamic" option doesn't do any work for me tho.

thanks for the linux driver management thing, I'll go check it out.

And about the "[COLOR=#000000]CTRL+ALT+F1 when the boot stops in this black screen[/COLOR]" thing, maybe I'll go try it if I switch to another distro again (currently distro-hopping)

---

### Post by Yellow Pasque on 2020-09-04
> **furesuka said:**
> Holy cow I am able to boot now without the nomodeset option after installing [Ubuntu drivers]("https://www.amd.com/en/support/graphics/amd-radeon-hd/amd-radeon-hd-7000m-series/amd-radeon-hd-7690m-xt") from the official website 

fglrx/Catalyst does not work on modern versions of Ubuntu and installing it probably conflicts with the open source driver used for your Intel GPU.
In other words, the system probably only "works" with Catalyst because it screws up kernel modesetting (KMS), the same way as 'nomodeset' disables it.
If glxinfo command still shows "OpenGL renderer string: llvmpipe (LLVM 10.0.0, 256 bits)", then your GPU(s) is not being used for 3D acceleration.

---

### Post by furesuka on 2020-09-05
from the output of glxinfo I see something similar: "OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 3000 (SNB GT2)"
does that mean my CPU is doing all the work instead of what I think it is?

```
name of display: :0display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_no_error, 
    GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_libglvnd, GLX_EXT_no_config_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_context_flush_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_no_error, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_create_context_es_profile, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_no_error, 
    GLX_ARB_create_context_profile, GLX_ARB_create_context_robustness, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_buffer_age, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_query_renderer, GLX_MESA_swap_control, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) HD Graphics 3000 (SNB GT2) (0x116)
    Version: 20.0.8
    Accelerated: yes
    Video memory: 1536MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 3000 (SNB GT2)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 20.0.8
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_3DFX_texture_compression_FXT1, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_trinary_minmax, 
    GL_AMD_texture_texture4, GL_AMD_vertex_shader_layer, 
    GL_AMD_vertex_shader_viewport_index, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_object_purgeable, 
    GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility, 
    GL_ARB_arrays_of_arrays, GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_buffer_storage, GL_ARB_clear_buffer_object, GL_ARB_clear_texture, 
    GL_ARB_clip_control, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_cull_distance, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_direct_state_access, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_enhanced_layouts, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_get_texture_sub_image, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_internalformat_query, GL_ARB_internalformat_query2, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_occlusion_query2, 
    GL_ARB_parallel_shader_compile, GL_ARB_pipeline_statistics_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_sprite, 
    GL_ARB_polygon_offset_clamp, GL_ARB_program_interface_query, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sample_shading, 
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_draw_parameters, 
    GL_ARB_shader_group_vote, GL_ARB_shader_objects, GL_ARB_shader_subroutine, 
    GL_ARB_shader_texture_lod, GL_ARB_shader_viewport_layer_array, 
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include, 
    GL_ARB_shading_language_packing, GL_ARB_sync, GL_ARB_texture_barrier, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_filter_anisotropic, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_levels, 
    GL_ARB_texture_query_lod, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback_overflow_query, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_shader, GL_ARB_vertex_type_10f_11f_11f_rev, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_float, 
    GL_EXT_EGL_image_storage, GL_EXT_EGL_sync, GL_EXT_abgr, 
    GL_EXT_blend_equation_separate, GL_EXT_demote_to_helper_invocation, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, 
    GL_EXT_pixel_buffer_object, GL_EXT_polygon_offset_clamp, 
    GL_EXT_provoking_vertex, GL_EXT_shader_framebuffer_fetch_non_coherent, 
    GL_EXT_shader_integer_mix, GL_EXT_texture_array, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_R8, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shadow_lod, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback, 
    GL_EXT_vertex_array_bgra, GL_IBM_multimode_draw_arrays, 
    GL_INTEL_performance_query, GL_KHR_blend_equation_advanced, 
    GL_KHR_context_flush_control, GL_KHR_debug, GL_KHR_no_error, 
    GL_KHR_parallel_shader_compile, GL_KHR_robustness, GL_MESA_pack_invert, 
    GL_MESA_shader_integer_functions, GL_MESA_texture_signed_rgba, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil, 
    GL_NV_texture_barrier, GL_OES_EGL_image, GL_S3_s3tc


OpenGL version string: 3.0 Mesa 20.0.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_3DFX_texture_compression_FXT1, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_trinary_minmax, 
    GL_AMD_texture_texture4, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_object_purgeable, 
    GL_APPLE_packed_pixels, GL_ARB_ES2_compatibility, 
    GL_ARB_ES3_compatibility, GL_ARB_arrays_of_arrays, 
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage, 
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, GL_ARB_clip_control, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_ARB_cull_distance, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_layer_viewport, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_get_program_binary, GL_ARB_get_texture_sub_image, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_internalformat_query2, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_parallel_shader_compile, 
    GL_ARB_pipeline_statistics_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_polygon_offset_clamp, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_seamless_cubemap_per_texture, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_draw_parameters, GL_ARB_shader_group_vote, 
    GL_ARB_shader_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_include, GL_ARB_shading_language_packing, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_texture_barrier, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_filter_anisotropic, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_storage, GL_ARB_texture_storage_multisample, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback_overflow_query, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_EGL_image_storage, GL_EXT_EGL_sync, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_demote_to_helper_invocation, 
    GL_EXT_direct_state_access, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset_clamp, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, 
    GL_EXT_shader_framebuffer_fetch_non_coherent, GL_EXT_shader_integer_mix, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod_bias, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_R8, 
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shadow_lod, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_INTEL_performance_query, GL_KHR_blend_equation_advanced, 
    GL_KHR_context_flush_control, GL_KHR_debug, GL_KHR_no_error, 
    GL_KHR_parallel_shader_compile, GL_KHR_robustness, GL_MESA_pack_invert, 
    GL_MESA_shader_integer_functions, GL_MESA_texture_signed_rgba, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_depth_clamp, GL_NV_fog_distance, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_primitive_restart, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_OES_EGL_image, 
    GL_OES_read_format, GL_S3_s3tc, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays


OpenGL ES profile version string: OpenGL ES 3.0 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_texture_max_level, GL_EXT_EGL_image_storage, 
    GL_EXT_base_instance, GL_EXT_blend_func_extended, GL_EXT_blend_minmax, 
    GL_EXT_clip_control, GL_EXT_clip_cull_distance, GL_EXT_color_buffer_float, 
    GL_EXT_compressed_ETC1_RGB8_sub_texture, 
    GL_EXT_demote_to_helper_invocation, GL_EXT_depth_clamp, 
    GL_EXT_discard_framebuffer, GL_EXT_disjoint_timer_query, 
    GL_EXT_draw_buffers, GL_EXT_draw_buffers_indexed, 
    GL_EXT_draw_elements_base_vertex, GL_EXT_float_blend, GL_EXT_frag_depth, 
    GL_EXT_map_buffer_range, GL_EXT_multi_draw_arrays, 
    GL_EXT_occlusion_query_boolean, GL_EXT_polygon_offset_clamp, 
    GL_EXT_read_format_bgra, GL_EXT_robustness, GL_EXT_sRGB_write_control, 
    GL_EXT_separate_shader_objects, 
    GL_EXT_shader_framebuffer_fetch_non_coherent, GL_EXT_shader_integer_mix, 
    GL_EXT_texture_border_clamp, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_compression_s3tc_srgb, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_format_BGRA8888, GL_EXT_texture_query_lod, 
    GL_EXT_texture_rg, GL_EXT_texture_sRGB_R8, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shadow_lod, GL_EXT_texture_type_2_10_10_10_REV, 
    GL_EXT_unpack_subimage, GL_INTEL_performance_query, 
    GL_KHR_blend_equation_advanced, GL_KHR_context_flush_control, 
    GL_KHR_debug, GL_KHR_no_error, GL_KHR_parallel_shader_compile, 
    GL_KHR_robustness, GL_MESA_framebuffer_flip_y, 
    GL_MESA_shader_integer_functions, GL_NV_conditional_render, 
    GL_NV_draw_buffers, GL_NV_fbo_color_attachments, GL_NV_read_buffer, 
    GL_NV_read_depth, GL_NV_read_depth_stencil, GL_NV_read_stencil, 
    GL_OES_EGL_image, GL_OES_EGL_image_external, 
    GL_OES_EGL_image_external_essl3, GL_OES_EGL_sync, 
    GL_OES_compressed_ETC1_RGB8_texture, GL_OES_depth24, GL_OES_depth_texture, 
    GL_OES_depth_texture_cube_map, GL_OES_draw_buffers_indexed, 
    GL_OES_draw_elements_base_vertex, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_required_internalformat, 
    GL_OES_rgb8_rgba8, GL_OES_sample_shading, GL_OES_sample_variables, 
    GL_OES_shader_multisample_interpolation, GL_OES_standard_derivatives, 
    GL_OES_stencil8, GL_OES_surfaceless_context, GL_OES_texture_3D, 
    GL_OES_texture_border_clamp, GL_OES_texture_float, 
    GL_OES_texture_float_linear, GL_OES_texture_half_float, 
    GL_OES_texture_half_float_linear, GL_OES_texture_npot, 
    GL_OES_vertex_array_object, GL_OES_vertex_half_float


74 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0fa 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0fb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0fd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0fe 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0ff 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x100 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x101 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x102 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x103 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x104 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x105 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x106 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x108 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x109 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x10a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x10b 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x10c 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x10d 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x10e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x10f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x110 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x111 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x112 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x113 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x114 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x115 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x116 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x117 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x118 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x119 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x11c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x11d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x11e 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x11f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x120 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x121 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x122 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x123 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x124 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x125 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x126 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x127 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x128 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x129 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x12a 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x12b 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x12c 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x12d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x12e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x12f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x130 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x131 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x132 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x133 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x134 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x09c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x135 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x136 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x137 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x138 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x139 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x13a 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x13b 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x13c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x13d 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None


90 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x09d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0aa 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0ab 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0ac 24 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0ad 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x0ae 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x0af 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x0b0 24 tc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x0b1  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b7 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0b8 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0b9 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x0ba 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x0bb  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0bc  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0bd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0be 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0bf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0c0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0c1 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x0c2 24 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x0c3 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x0c4 24 tc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x0c5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ca 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0cb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0cc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0cd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ce 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0cf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d1 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0d2 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0d3 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0d4 24 dc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0d5 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x0d6 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0  0  0  0  0  0  0  0 0 None
0x0d7 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x0d8 24 dc  0  24  0 r  . .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x0d9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0da  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0db 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0dc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0dd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0de 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0df 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0e0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8 16 16 16 16  0 0 Slow
0x0e1 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  0 0 None
0x0e2 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8 16 16 16  0  0 0 Slow
0x0e3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0e5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x0e6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0e7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0e8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0e9 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  4 1 None
0x0ea 24 dc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  4 1 None
0x0eb 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0  0  0  0  0  0  0  4 1 None
0x0ec 24 dc  0  24  0 r  y .   8  8  8  0 .  s  0 24  8  0  0  0  0  4 1 None
0x0ed 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ee 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ef 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f0 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f1 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0f2 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0  0  0  0  0  0  0  0 0 None
0x0f3 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0f4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None
0x0f5 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  0 24  8  0  0  0  0  0 0 None



```

---

### Post by Yellow Pasque on 2020-09-05
Yes, that's good. Don't ask me how installing Catalyst made the Intel GPU work. Maybe there's a problem with KMS on the AMD GPU. In other words, maybe you could have booted with 'radeon.modeset=0' instead of 'nomodeset'.

If you care about using the AMD GPU, you may want to check:
```
DRI_PRIME=1 glxinfo -B
```

Then again, if everything works with the integrated GPU and you're happy with that, I guess this is Solved?

---

### Post by kurt18947 on 2020-09-05
Here is something that tweaked my interest:
```
name of display: :1display: :1  screen: 0
direct rendering: Yes
[B]Extended renderer info (GLX_MESA_query_renderer):
    Vendor: VMware, Inc. (0xffffffff)[/B]
    Device: llvmpipe (LLVM 10.0.0, 256 bits) (0xffffffff)
    Version: 20.0.8
    Accelerated: no
    Video memory: 3882MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
[B]OpenGL vendor string: VMware, Inc.
[/B]
```

Is this running in a virtual machine? That may change things I expect though I'm certainly no expert
in such matters. AMD is pretty simple with Ubuntu since they ditched their proprietary drivers. There are two 
AMD drivers, Radeon and AMDGPU. Radeon on older chipsets, AMDGPU on newer. The correct driver will be installed
automatically.

---

### Post by Yellow Pasque on 2020-09-05
llvmpipe does not mean it's a VM. While it was originally written by someone at VMWare (and is used in their VM's), llvmpipe is the default software rasterizer in Ubuntu (and I guess mesa in general). It outperforms the old "softpipe" implementation.

---

### Post by furesuka on 2020-09-05
(Nope this is not a VM, I don't have a machine that can even handle that)
Oh yeah, I'm definitely happy with this now!
I don't care if you only replied once to my thread, thanks for everyone that replied to my thread:
[Autodave]("https://ubuntuforums.org/member.php?u=917298")
[SeijiSensei]("https://ubuntuforums.org/member.php?u=698195")
[CelticWarrior]("https://ubuntuforums.org/member.php?u=1826209")
[Yellow Pasque]("https://ubuntuforums.org/member.php?u=327594")
[marvin20867]("https://ubuntuforums.org/member.php?u=2150449")
[pmaff]("https://ubuntuforums.org/member.php?u=2115469")
[kurt18947]("https://ubuntuforums.org/member.php?u=1447222")

I'm glad the forums are much nicer than majority of the internet. Fixing problems in Linux are definitely harder than in Windows but we successfully fixed it! Thank you to all of you!
And with that, I'll gladly mark this thread as solved.

---

