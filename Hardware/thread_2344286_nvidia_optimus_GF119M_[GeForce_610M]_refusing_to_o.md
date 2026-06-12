---
title: "nvidia optimus GF119M [GeForce 610M] refusing to oprate on 16.04 LTS"
date: 2016-11-23
forum: Hardware
---

### Post by mr.man2 on 2016-11-23
Dear Masters of Ubuntu, 

i left windows for good a  month ago for ubuntu, so it's safe to say that i'm as green as it gets.  Nevertheless it was fairly easy to get OS the up and running on my Samsung E100 save for GPU (GF119M [GeForce 610M]). I followed a handful of instructions trying to get nvidia drivers with & without bumblebee to spin the GPU but either worked, except [this one]("http://lenovolinux.blogspot.hu/"). Unfortunately the driver here used is the transitional nvidia-361, it wasn't long after that an update pushed it to 367, after which the config ceased to work. After recallibrating the affected parameters ([FONT=&amp]/etc/bumblebee/bumblebee.conf i didn't dare touch the other confs though)[/FONT] to point towards the freshly installed driver, i was greeted with a black screen occasionally re-starting only to give black each time. i've tried experimenting on a Mint Rosa, hoping an older kernel would be a gamechanger, but i ended up  with the same results. By now i've read & tried so many options i feel completly lost. As of now, i'm sporting a fresh install of the ubuntu 16,04 LTS, nouveau wouldn't let my computer boot unless i do so in ```
nomodeset
```. So if you feel pluck, please care to help this here suffering feller, i can barelly get neverball to run :(

here's some relevant intel

```
lspci | egrep "3D|VGA"
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev a1)
```

```
uname-a 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

when i tried to install nvidia-367 via "additional drivers" dmesg gave me the error: nvrm xid 44 > Graphics Engine fault during context switch

should this be insufficient, do point out! Thanks in advance & please have a nice day!

Mortzi

---

### Post by Bashing-om on 2016-11-23
mr.man2; Hello : Welcome to the forum.

On that card when checking I was surprised to see that nVidia recommends the 375 version driver for that card.
As an added aside, BumbleBee has been depreciated in favor of nvidia-prime to control the graphic's sets .
I would expect the 367 version driver to work, and it is in xenial's software repository ( 375 in our trusted PPA ).
On a fresh install with BumblebEE not a factor ( not installed ):
Let's try this :
```

sudo rm /etc/X11/Xorg.conf
sudo apt purge nvidia*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

Reboot to see the effect .

Where I expect the installer to select and install the 367 version driver  and as well nvidia-setting and nvidia-prime.

[INDENT][INDENT]maybe Yes !
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-23
Dear Bashing-om, thanks for your care, however the proposed steps didn't yet solve my issue. After the reboot it went swell until the credentials' screen & after having authenticated, the very same screen would pop back up, demanding the credentials ad infinitum. Once i authenticated i passed to tty1 to grasp any sort of error message, and there were indeed two lines that flashed, i was unable even after several attempts to discern what was written there & i'm unsure of the whereabouts of the boot log & even if that would be there. after that i went for a 
```
sudo apt purge nvidia*
``` 
& now i'm back in the system

---

### Post by Bashing-om on 2016-11-23
mr.man2; Well ..

That ain't good ..
Not supposed to happen thata way .
OK, does the system see the nvidia card ( disabled in bios ??) ? and what does X presently think :
Paste back the output of terminal command:
```

cat /var/log/Xorg.0.log

```
which is the log file of what X is setting up .

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-24
Here u go Bashing-om

```
[    66.519] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    66.519] X Protocol Version 11, Revision 0
[    66.519] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[    66.519] Current Operating System: Linux killer-300E4C-300E5C-300E7C 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64
[    66.519] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-47-generic root=UUID=a3415d70-ffc8-4278-905a-6134cd332c0c ro nomodeset quiet splash vt.handoff=7
[    66.519] Build Date: 02 November 2016  10:06:10PM
[    66.519] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    66.519] Current version of pixman: 0.33.6
[    66.519]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    66.519] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    66.519] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 24 09:02:32 2016
[    66.546] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    66.546] (==) No Layout section.  Using the first Screen section.
[    66.546] (==) No screen section available. Using defaults.
[    66.546] (**) |-->Screen "Default Screen Section" (0)
[    66.546] (**) |   |-->Monitor "<default monitor>"
[    66.559] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    66.559] (==) Automatically adding devices
[    66.559] (==) Automatically enabling devices
[    66.559] (==) Automatically adding GPU devices
[    66.559] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    66.559] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    66.559]     Entry deleted from font path.
[    66.559] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    66.559]     Entry deleted from font path.
[    66.559] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    66.559]     Entry deleted from font path.
[    66.559] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    66.559]     Entry deleted from font path.
[    66.559] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    66.559]     Entry deleted from font path.
[    66.559] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    66.559] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    66.559] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    66.577] (II) Loader magic: 0x564f21eeedc0
[    66.577] (II) Module ABI versions:
[    66.577]     X.Org ANSI C Emulation: 0.4
[    66.577]     X.Org Video Driver: 20.0
[    66.577]     X.Org XInput driver : 22.1
[    66.577]     X.Org Server Extension : 9.0
[    66.577] (++) using VT number 7

[    66.577] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    66.578] (--) PCI:*(0:0:2:0) 8086:0166:144d:c652 rev 9, Mem @ 0xdb000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    66.578] (--) PCI: (0:1:0:0) 10de:1058:144d:c652 rev 161, Mem @ 0xda000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @ 0x00003000/128
[    66.578] (II) LoadModule: "glx"
[    66.596] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    66.719] (II) Module glx: vendor="X.Org Foundation"
[    66.719]     compiled for 1.18.4, module version = 1.0.0
[    66.719]     ABI class: X.Org Server Extension, version 9.0
[    66.719] (==) AIGLX enabled
[    66.719] (==) Matched intel as autoconfigured driver 0
[    66.719] (==) Matched modesetting as autoconfigured driver 1
[    66.719] (==) Matched fbdev as autoconfigured driver 2
[    66.719] (==) Matched vesa as autoconfigured driver 3
[    66.719] (==) Assigned the driver to the xf86ConfigLayout
[    66.719] (II) LoadModule: "intel"
[    66.719] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    66.728] (II) Module intel: vendor="X.Org Foundation"
[    66.728]     compiled for 1.18.3, module version = 2.99.917
[    66.728]     Module class: X.Org Video Driver
[    66.728]     ABI class: X.Org Video Driver, version 20.0
[    66.728] (II) LoadModule: "modesetting"
[    66.728] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    66.728] (II) Module modesetting: vendor="X.Org Foundation"
[    66.728]     compiled for 1.18.4, module version = 1.18.4
[    66.728]     Module class: X.Org Video Driver
[    66.728]     ABI class: X.Org Video Driver, version 20.0
[    66.728] (II) LoadModule: "fbdev"
[    66.728] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    66.728] (II) Module fbdev: vendor="X.Org Foundation"
[    66.728]     compiled for 1.18.1, module version = 0.4.4
[    66.728]     Module class: X.Org Video Driver
[    66.728]     ABI class: X.Org Video Driver, version 20.0
[    66.728] (II) LoadModule: "vesa"
[    66.728] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    66.728] (II) Module vesa: vendor="X.Org Foundation"
[    66.728]     compiled for 1.18.1, module version = 2.3.4
[    66.728]     Module class: X.Org Video Driver
[    66.728]     ABI class: X.Org Video Driver, version 20.0
[    66.728] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    66.728] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    66.728] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    66.728] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    66.728] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    66.728] (II) FBDEV: driver for framebuffer: fbdev
[    66.728] (II) VESA: driver for VESA chipsets: vesa
[    66.783] (EE) open /dev/dri/card0: No such file or directory
[    66.783] (WW) Falling back to old probe method for modesetting
[    66.783] (EE) open /dev/dri/card0: No such file or directory
[    66.783] (II) Loading sub module "fbdevhw"
[    66.783] (II) LoadModule: "fbdevhw"
[    66.783] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    66.783] (II) Module fbdevhw: vendor="X.Org Foundation"
[    66.783]     compiled for 1.18.4, module version = 0.0.2
[    66.783]     ABI class: X.Org Video Driver, version 20.0
[    66.783] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    66.783] (II) FBDEV(1): using default device
[    66.783] (WW) Falling back to old probe method for vesa
[    66.783] (EE) Screen 0 deleted because of no matching config section.
[    66.783] (II) UnloadModule: "modesetting"
[    66.783] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    66.783] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    66.783] (==) FBDEV(0): RGB weight 888
[    66.783] (==) FBDEV(0): Default visual is TrueColor
[    66.783] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    66.783] (II) FBDEV(0): hardware: VESA VGA (video memory: 4160kB)
[    66.783] (II) FBDEV(0): checking modes against framebuffer device...
[    66.783] (II) FBDEV(0): checking modes against monitor...
[    66.783] (--) FBDEV(0): Virtual size is 1366x768 (pitch 1366)
[    66.783] (**) FBDEV(0):  Built-in mode "current": 104.9 MHz, 60.5 kHz, 76.4 Hz
[    66.783] (II) FBDEV(0): Modeline "current"x0.0  104.92  1366 1398 1566 1734  768 772 776 792 -hsync -vsync -csync (60.5 kHz b)
[    66.783] (==) FBDEV(0): DPI set to (96, 96)
[    66.783] (II) Loading sub module "fb"
[    66.783] (II) LoadModule: "fb"
[    66.783] (II) Loading /usr/lib/xorg/modules/libfb.so
[    66.784] (II) Module fb: vendor="X.Org Foundation"
[    66.784]     compiled for 1.18.4, module version = 1.0.0
[    66.784]     ABI class: X.Org ANSI C Emulation, version 0.4
[    66.784] (**) FBDEV(0): using shadow framebuffer
[    66.784] (II) Loading sub module "shadow"
[    66.784] (II) LoadModule: "shadow"
[    66.784] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    66.784] (II) Module shadow: vendor="X.Org Foundation"
[    66.784]     compiled for 1.18.4, module version = 1.1.0
[    66.784]     ABI class: X.Org ANSI C Emulation, version 0.4
[    66.784] (II) UnloadModule: "vesa"
[    66.784] (II) Unloading vesa
[    66.784] (==) Depth 24 pixmap format is 32 bpp
[    66.784] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    66.817] (==) FBDEV(0): Backing store enabled
[    66.818] (==) FBDEV(0): DPMS enabled
[    66.818] (==) RandR enabled
[    66.819] (II) Found 2 VGA devices: arbiter wrapping enabled
[    66.822] (II) SELinux: Disabled on system
[    66.823] (II) AIGLX: Screen 0 is not DRI2 capable
[    66.823] (EE) AIGLX: reverting to software rendering
[    68.499] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    68.500] (II) AIGLX: Loaded and initialized swrast
[    68.500] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    68.703] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    68.703] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    68.703] (II) LoadModule: "evdev"
[    68.704] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    68.790] (II) Module evdev: vendor="X.Org Foundation"
[    68.790]     compiled for 1.18.1, module version = 2.10.1
[    68.790]     Module class: X.Org XInput Driver
[    68.790]     ABI class: X.Org XInput driver, version 22.1
[    68.790] (II) Using input driver 'evdev' for 'Power Button'
[    68.790] (**) Power Button: always reports core events
[    68.790] (**) evdev: Power Button: Device: "/dev/input/event2"
[    68.790] (--) evdev: Power Button: Vendor 0 Product 0x1
[    68.790] (--) evdev: Power Button: Found keys
[    68.790] (II) evdev: Power Button: Configuring as keyboard
[    68.790] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    68.790] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    68.790] (**) Option "xkb_rules" "evdev"
[    68.790] (**) Option "xkb_model" "pc105"
[    68.790] (**) Option "xkb_layout" "hu"
[    68.807] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    68.807] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    68.807] (II) Using input driver 'evdev' for 'Power Button'
[    68.807] (**) Power Button: always reports core events
[    68.807] (**) evdev: Power Button: Device: "/dev/input/event1"
[    68.808] (--) evdev: Power Button: Vendor 0 Product 0x1
[    68.808] (--) evdev: Power Button: Found keys
[    68.808] (II) evdev: Power Button: Configuring as keyboard
[    68.808] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    68.808] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    68.808] (**) Option "xkb_rules" "evdev"
[    68.808] (**) Option "xkb_model" "pc105"
[    68.808] (**) Option "xkb_layout" "hu"
[    68.808] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    68.808] (II) No input driver specified, ignoring this device.
[    68.808] (II) This device may have been added with another device file.
[    68.808] (II) config/udev: Adding input device WebCam SC-03FFL11939N (/dev/input/event5)
[    68.808] (**) WebCam SC-03FFL11939N: Applying InputClass "evdev keyboard catchall"
[    68.808] (II) Using input driver 'evdev' for 'WebCam SC-03FFL11939N'
[    68.809] (**) WebCam SC-03FFL11939N: always reports core events
[    68.809] (**) evdev: WebCam SC-03FFL11939N: Device: "/dev/input/event5"
[    68.809] (--) evdev: WebCam SC-03FFL11939N: Vendor 0x2232 Product 0x1028
[    68.809] (--) evdev: WebCam SC-03FFL11939N: Found keys
[    68.809] (II) evdev: WebCam SC-03FFL11939N: Configuring as keyboard
[    68.809] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6/event5"
[    68.809] (II) XINPUT: Adding extended input device "WebCam SC-03FFL11939N" (type: KEYBOARD, id 8)
[    68.809] (**) Option "xkb_rules" "evdev"
[    68.809] (**) Option "xkb_model" "pc105"
[    68.809] (**) Option "xkb_layout" "hu"
[    68.809] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event6)
[    68.809] (II) No input driver specified, ignoring this device.
[    68.809] (II) This device may have been added with another device file.
[    68.809] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event7)
[    68.809] (II) No input driver specified, ignoring this device.
[    68.809] (II) This device may have been added with another device file.
[    68.809] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[    68.809] (II) No input driver specified, ignoring this device.
[    68.809] (II) This device may have been added with another device file.
[    68.810] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    68.810] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    68.810] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    68.810] (**) AT Translated Set 2 keyboard: always reports core events
[    68.810] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    68.810] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    68.810] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    68.810] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    68.810] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    68.810] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    68.810] (**) Option "xkb_rules" "evdev"
[    68.810] (**) Option "xkb_model" "pc105"
[    68.810] (**) Option "xkb_layout" "hu"
[    68.810] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event4)
[    68.810] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    68.810] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[    68.810] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    68.810] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    68.810] (II) LoadModule: "synaptics"
[    68.810] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    68.810] (II) Module synaptics: vendor="X.Org Foundation"
[    68.810]     compiled for 1.18.1, module version = 1.8.2
[    68.810]     Module class: X.Org XInput Driver
[    68.810]     ABI class: X.Org XInput driver, version 22.1
[    68.810] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    68.810] (**) ETPS/2 Elantech Touchpad: always reports core events
[    68.811] (**) Option "Device" "/dev/input/event4"
[    68.872] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    68.872] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 31)
[    68.872] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1400 (res 31)
[    68.872] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    68.872] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    68.872] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    68.872] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    68.872] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    68.872] (**) ETPS/2 Elantech Touchpad: always reports core events
[    68.896] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    68.896] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 10)
[    68.896] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    68.896] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    68.896] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.061
[    68.896] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    68.896] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    68.896] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    68.896] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    68.896] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    68.896] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    68.896] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
```
with my current version of BIOS in its GUI i am unable to see present components let alone modify them :( like [this]("http://www.top-password.com/blog/wp-content/uploads/2013/06/samsung-bios-mode.jpg"), only it's parametered differently. I've read somewhere that if the GPU was to be configured correctly it would show in 
```
lspci | egrep "3D|VGA"
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev a1)
```
as a 3D accelerator, not annother VGA controller.

---

### Post by Bashing-om on 2016-11-24
mr.man2; Well ...

The good news is that both graphic's sets are identified .
The not so good is booting up with nomodeset:
> 
[ 66.519] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-47-generic root=UUID=a3415d70-ffc8-4278-905a-6134cd332c0c ro [color=red]nomodeset[/color] quiet splash vt.handoff=7

As this boot parameter disables Kernel Mode Setting and forces the fall back driver to load .

So, how about removing that boot parameter, install again the nVidia proprietary driver and we see if things

[INDENT][INDENT]appear in a brighter light
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-24
okay so i went for a ```
sudo nano /etc/default/grub
``` 
so that it looks like:
> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""


went for a
```
sudo update-grub
```
repeated the steps
```
sudo rm /etc/X11/Xorg.conf
sudo apt purge nvidia*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall
```

and had the black screen phenomenon re-appear only it went to notify me that the system is currently in low graphics mode, even though the boot text stated that the nvidia modules & persistence daemon started OK. i'm back with a purged nvidia & nomodeset back on

p.s. thanks for your care it means a lot!!

---

### Post by Bashing-om on 2016-11-24
mr.man2; Hummm ..

Might be informative to know what driver "autoinstall" chooses and if the supporting packages also are installed along with the driver .
```

dpkg -l | grep -i nvidia

```

Take a look at the config file, insure that the Nvidia driver is "in-use" and Intel is available.
```

cat /etc/X11/Xorg.conf

```
That file MUST exist and be in a consistent state to control the graphic's sets .

Maybe also take nVidia's recommendation and see what results installing the 375 version ?

[INDENT][INDENT]a case here
[INDENT][INDENT][INDENT]of sometimes I wonder
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-24
> killer@killer-300E4C-300E5C-300E7C:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
killer@killer-300E4C-300E5C-300E7C:~$ cat /etc/X11/Xorg.conf
cat: /etc/X11/Xorg.conf: No such file or directory



this is what came out, after having undone the effects of

```
 
sudo ubuntu-drivers autoinstall


```

should i re-implement it & check after?

---

### Post by Bashing-om on 2016-11-24
mr.man2; Uh Huh :
> 
should i re-implement it & check after?


See then what driver and packages are installed.. and then what the config file contains.

[INDENT][INDENT]something to bite on
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-24
Dear Bashing-Om,

thanks for your patience, here's what i found:
[IMG]https://scontent-vie1-1.xx.fbcdn.net/v/t34.0-12/15240313_10202544858380416_328415554_n.jpg?oh=0179bd4d1683d593a5896012dd1c264e&oe=5839F980[/IMG]
[IMG]https://scontent-vie1-1.xx.fbcdn.net/v/t34.0-12/15211541_10202544858820427_1115622401_n.jpg?oh=ab3019f595c2b3ebd034b5cc6e286481&oe=5839AEE5[/IMG]
[IMG]https://scontent-vie1-1.xx.fbcdn.net/v/t34.0-12/15174554_10202545011144235_1436881102_n.jpg?oh=1d5af82db13add8ca0e08ea5c42c7c9d&oe=583999BD[/IMG]

i've tried several drivers (375,370,367,358,340) which always gave me the low graphics mode boot, & nvidia error ID xid 44.

to install i merely used ```
sudo apt-get install nvidia-340 nvidia-prime
``` for the 340 and so on & so forth. Also it might be worth mentionning, but after having tried to install 375, ```

sudo ubuntu-drivers autoinstall 
``` invited me to install 375 instead of 367  i feel like i'M missing out something trivial

---

### Post by Bashing-om on 2016-11-24
mr.man2; Uh Huh !

That all looks good at this time . I would expect you to be able to boot to a GUI.
If you can not .. reboot and at the login screen key combo ctl+alt+F1 to gain a console and login to the system here .
Now what results :
```

ls -al .ICEauthority .Xauthority

```
should have "YOU" as the owner and group .
As in my example:
> 
sysop@1404mini:~$ ls -al .ICEauthority .Xauthority
-rw------- 1 sysop sysop 1630 Nov 24 07:41 .ICEauthority
-rw------- 1 sysop sysop  209 Jul 28 15:28 .Xauthority
sysop@1404mini:~$

where I am "sysop" .
We want to know that "YOU" are authorized to access your desktop .

[INDENT][INDENT]gotta be a reason
[INDENT][INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-25
Dear Bashing-Om, 

i've just verified this with the autoinstalled nvidia-375, & i can confirm i am authorized both on .ICE & .X 

same goes when it's uninstalled

---

### Post by Bashing-om on 2016-11-25
mr.man2; Yuk ...

Curious and curiouser ...

OK, got to be a reason ... got to be !

Let's make sure that X does not show a problem - with the 375 driver loaded .
show - between code tags to maintain formatting :
```

cat /var/log/Xorg.0.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see if this is a system problem OR a config issue in your account:
can you log into the system from the guest account at the login screen ?
If you can login via the guest account .. then yep, a config issue in your own account .

[INDENT][INDENT]still. after all this time
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-27
Dear Bashing-Om

here's what i got, it was a bit Xtra hard because  nouveau seemed to start simultaneously, but i blacklisted it & got  what's below

```
[    37.675] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    37.675] X Protocol Version 11, Revision 0
[    37.675] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[     37.675] Current Operating System: Linux killer-300E4C-300E5C-300E7C  4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64
[     37.675] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-47-generic  root=UUID=a3415d70-ffc8-4278-905a-6134cd332c0c ro text
[    37.675] Build Date: 02 November 2016  10:06:10PM
[    37.675] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[    37.675] Current version of pixman: 0.33.6
[    37.675]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    37.675] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    37.675] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 27 11:21:06 2016
[    37.773] (==) Using config file: "/etc/X11/xorg.conf"
[    37.773] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    37.811] (==) ServerLayout "layout"
[    37.811] (**) |-->Screen "nvidia" (0)
[    37.811] (**) |   |-->Monitor "<default monitor>"
[    37.883] (**) |   |-->Device "nvidia"
[    37.883] (**) |   |-->GPUDevice "nvidia"
[    37.883] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    37.883] (**) |-->Inactive Device "intel"
[    37.883] (==) Automatically adding devices
[    37.883] (==) Automatically enabling devices
[    37.883] (==) Automatically adding GPU devices
[    37.883] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    37.884] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    37.884]     Entry deleted from font path.
[    37.884] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    37.884]     Entry deleted from font path.
[    37.884] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    37.884]     Entry deleted from font path.
[    37.884] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    37.884]     Entry deleted from font path.
[    37.884] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    37.884]     Entry deleted from font path.
[    37.884] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     37.884] (==) ModulePath set to  "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    37.884] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    37.956] (II) Loader magic: 0x55bc7d290dc0
[    37.956] (II) Module ABI versions:
[    37.956]     X.Org ANSI C Emulation: 0.4
[    37.956]     X.Org Video Driver: 20.0
[    37.956]     X.Org XInput driver : 22.1
[    37.956]     X.Org Server Extension : 9.0
[    37.957] (++) using VT number 7

[     37.957] (II) systemd-logind: logind integration requires -keeptty and  -keeptty was not provided, disabling logind integration
[    37.957] (II) xfree86: Adding drm device (/dev/dri/card0)
[    37.957] (II) xfree86: Adding drm device (/dev/dri/card1)
[    37.958] (--) PCI:*(0:0:2:0) 8086:0166:144d:c652 rev 9, Mem @ 0xdb000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[     37.958] (--) PCI: (0:1:0:0) 10de:1058:144d:c652 rev 161, Mem @  0xda000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @  0x00003000/128
[    37.958] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    37.958] (II) "glx" will be loaded by default.
[    37.958] (II) LoadModule: "glx"
[    37.959] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    39.929] (II) Module glx: vendor="NVIDIA Corporation"
[    39.929]     compiled for 4.0.2, module version = 1.0.0
[    39.929]     Module class: X.Org Server Extension
[    39.941] (II) NVIDIA GLX Module  375.20  Tue Nov 15 16:38:52 PST 2016
[    39.941] (II) LoadModule: "nvidia"
[    39.941] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    39.974] (II) Module nvidia: vendor="NVIDIA Corporation"
[    39.974]     compiled for 4.0.2, module version = 1.0.0
[    39.974]     Module class: X.Org Video Driver
[    39.974] (II) LoadModule: "modesetting"
[    39.974] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    39.974] (II) Module modesetting: vendor="X.Org Foundation"
[    39.974]     compiled for 1.18.4, module version = 1.18.4
[    39.974]     Module class: X.Org Video Driver
[    39.974]     ABI class: X.Org Video Driver, version 20.0
[    39.974] (II) NVIDIA dlloader X Driver  375.20  Tue Nov 15 16:15:23 PST 2016
[    39.974] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    39.985] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    39.988] (II) Loading sub module "fb"
[    39.988] (II) LoadModule: "fb"
[    39.988] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.011] (II) Module fb: vendor="X.Org Foundation"
[    40.011]     compiled for 1.18.4, module version = 1.0.0
[    40.011]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.011] (II) Loading sub module "wfb"
[    40.011] (II) LoadModule: "wfb"
[    40.011] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    40.017] (II) Module wfb: vendor="X.Org Foundation"
[    40.017]     compiled for 1.18.4, module version = 1.0.0
[    40.017]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.017] (II) Loading sub module "ramdac"
[    40.017] (II) LoadModule: "ramdac"
[    40.017] (II) Module "ramdac" already built-in
[    40.036] (II) modeset(G0): using drv /dev/dri/card1
[    40.036] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    40.036] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    40.036] (==) NVIDIA(0): RGB weight 888
[    40.036] (==) NVIDIA(0): Default visual is TrueColor
[    40.036] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    40.037] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    40.037] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    40.037] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    40.037] (**) NVIDIA(0): Enabling 2D acceleration
[    44.658] (II) NVIDIA(0): NVIDIA GPU GeForce 610M (GF119) at PCI:1:0:0 (GPU-0)
[    44.658] (--) NVIDIA(0): Memory: 1048576 kBytes
[    44.658] (--) NVIDIA(0): VideoBIOS: 75.19.54.00.06
[    44.658] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    44.658] (II) NVIDIA(0): Validated MetaModes:
[    44.659] (II) NVIDIA(0):     "NULL"
[    44.659] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    44.659] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    44.659] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    44.659] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    44.659] (**) modeset(G0): Option "AccelMethod" "None"
[    44.659] (==) modeset(G0): RGB weight 888
[    44.659] (==) modeset(G0): Default visual is TrueColor
[    44.659] (**) modeset(G0): glamor disabled
[    44.659] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    44.659] (II) modeset(G0): Output LVDS-1-1 has no monitor section
[    44.659] (II) modeset(G0): Output VGA-1-1 has no monitor section
[    44.788] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[    44.788] (II) modeset(G0): Output DP-1-1 has no monitor section
[    44.788] (II) modeset(G0): EDID for output LVDS-1-1
[    44.788] (II) modeset(G0): Manufacturer: SEC  Model: 384a  Serial#: 0
[    44.788] (II) modeset(G0): Year: 2011  Week: 0
[    44.788] (II) modeset(G0): EDID Version: 1.3
[    44.788] (II) modeset(G0): Digital Display Input
[    44.788] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    44.788] (II) modeset(G0): Gamma: 2.20
[    44.788] (II) modeset(G0): No DPMS capabilities specified
[    44.788] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    44.788] (II) modeset(G0): First detailed timing is preferred mode
[    44.788] (II) modeset(G0): redX: 0.615 redY: 0.355   greenX: 0.355 greenY: 0.610
[    44.788] (II) modeset(G0): blueX: 0.150 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    44.788] (II) modeset(G0): Manufacturer's mask: 0
[    44.788] (II) modeset(G0): Supported detailed timing:
[    44.788] (II) modeset(G0): clock: 70.7 MHz   Image Size:  344 x 194 mm
[    44.788] (II) modeset(G0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    44.788] (II) modeset(G0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 792 v_border: 0
[    44.788] (II) modeset(G0): Unknown vendor-specific block f
[    44.788] (II) modeset(G0):  SAMSUNG
[    44.788] (II) modeset(G0):  LTN156AT248
[    44.788] (II) modeset(G0): EDID (in hex):
[    44.788] (II) modeset(G0):     00ffffffffffff004ca34a3800000000
[    44.788] (II) modeset(G0):     00150103802213780a81a59d5b5b9c26
[    44.788] (II) modeset(G0):     19505400000001010101010101010101
[    44.788] (II) modeset(G0):     0101010101019e1b5678500018303020
[    44.788] (II) modeset(G0):     250058c2100000190000000f00000000
[    44.788] (II) modeset(G0):     00000000001eb4021500000000fe0053
[    44.788] (II) modeset(G0):     414d53554e470a2020202020000000fe
[    44.788] (II) modeset(G0):     004c544e31353641543234380a2000c3
[    44.788] (II) modeset(G0): Printing probed modes for output LVDS-1-1
[     44.788] (II) modeset(G0): Modeline "1366x768"x60.1   70.70  1366 1414  1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz eP)
[    44.788] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    44.788] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[     44.788] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100  1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    44.788] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[     44.788] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024  1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[     44.788] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976  1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[     44.788] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960  1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[     44.788] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984  1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[     44.788] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984  1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[     44.788] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928  1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    44.788] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    44.788] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[     44.788] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980  1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[     44.788] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880  920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[     44.788] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828  832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[     44.788] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820  940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[     44.788] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720  844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[     44.789] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836  952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[     44.789] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744  900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    44.789] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[     44.789] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784  888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[     44.789] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720  760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[     44.789] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668  760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[     44.789] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592  672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[     44.789] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484  528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[     44.789] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448  512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[     44.789] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376  400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    44.789] (II) modeset(G0): EDID for output VGA-1-1
[    44.916] (II) modeset(G0): EDID for output HDMI-1-1
[    44.916] (II) modeset(G0): EDID for output DP-1-1
[    44.916] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    44.916] (==) modeset(G0): DPI set to (96, 96)
[    44.916] (II) Loading sub module "fb"
[    44.916] (II) LoadModule: "fb"
[    44.916] (II) Loading /usr/lib/xorg/modules/libfb.so
[    44.916] (II) Module fb: vendor="X.Org Foundation"
[    44.916]     compiled for 1.18.4, module version = 1.0.0
[    44.916]     ABI class: X.Org ANSI C Emulation, version 0.4
[    44.916] (II) Loading sub module "shadow"
[    44.916] (II) LoadModule: "shadow"
[    44.916] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    44.917] (II) Module shadow: vendor="X.Org Foundation"
[    44.917]     compiled for 1.18.4, module version = 1.1.0
[    44.917]     ABI class: X.Org ANSI C Emulation, version 0.4
[    44.917] (--) Depth 24 pixmap format is 32 bpp
[    44.946] (==) modeset(G0): Backing store enabled
[    44.946] (==) modeset(G0): Silken mouse enabled
[    44.946] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    44.947] (==) modeset(G0): DPMS enabled
[    44.947] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    44.947] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    45.491] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[    45.491] (II) NVIDIA:     access.
[    53.648] (EE) 
Fatal server error:
[    53.648] (EE) NVIDIA: A GPU exception occurred during X server initialization(EE) 
[    53.648] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    53.648] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    53.648] (EE) 
[    53.686] (EE) Server terminated with error (1). Closing log file.
```

w/

```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 375.20                 Driver Version: 375.20                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce 610M        Off  | 0000:01:00.0     N/A |                  N/A |
| N/A   44C    P0    N/A /  N/A |      0MiB /   994MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0                  Not Supported                                         |
+-----------------------------------------------------------------------------+
```

also  installing the legacy driver nvidia-current (304 i assume) works swell,  but unfortunately it's obsolete & gives performance below the  capabilities of the GPU

---

### Post by oldfred on 2016-11-27
It looks like you at some time installed bumblebee.
And then those files interfere, so just like purging nvidia, you must totally remove bumblebee.

You showed this file which still needs to be removed.
bbswitch-dkms

       remove bumblebee
[http://ubuntuforums.org/showthread.php?t=2292628](http://ubuntuforums.org/showthread.php?t=2292628)
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms

---

### Post by mr.man2 on 2016-11-27
p.s.: here are the results of the 367 driver test.

```
[    54.193] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    54.193] X Protocol Version 11, Revision 0
[    54.193] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[    54.193] Current Operating System: Linux killer-300E4C-300E5C-300E7C 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64
[    54.193] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-47-generic root=UUID=a3415d70-ffc8-4278-905a-6134cd332c0c ro text
[    54.193] Build Date: 02 November 2016  10:06:10PM
[    54.193] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[    54.193] Current version of pixman: 0.33.6
[    54.193]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    54.193] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    54.193] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 27 16:31:25 2016
[    54.381] (==) Using config file: "/etc/X11/xorg.conf"
[    54.381] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    54.819] (==) ServerLayout "layout"
[    54.819] (**) |-->Screen "nvidia" (0)
[    54.819] (**) |   |-->Monitor "<default monitor>"
[    54.944] (**) |   |-->Device "nvidia"
[    54.944] (**) |   |-->GPUDevice "nvidia"
[    54.944] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    54.944] (**) |-->Inactive Device "intel"
[    54.944] (==) Automatically adding devices
[    54.944] (==) Automatically enabling devices
[    54.944] (==) Automatically adding GPU devices
[    54.944] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    55.240] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    55.240]     Entry deleted from font path.
[    55.240] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    55.240]     Entry deleted from font path.
[    55.240] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    55.240]     Entry deleted from font path.
[    55.241] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    55.241]     Entry deleted from font path.
[    55.241] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    55.241]     Entry deleted from font path.
[    55.241] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    55.241] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    55.241] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    55.283] (II) Loader magic: 0x55f1b7506dc0
[    55.283] (II) Module ABI versions:
[    55.283]     X.Org ANSI C Emulation: 0.4
[    55.283]     X.Org Video Driver: 20.0
[    55.283]     X.Org XInput driver : 22.1
[    55.283]     X.Org Server Extension : 9.0
[    55.284] (++) using VT number 7

[    55.284] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    55.285] (II) xfree86: Adding drm device (/dev/dri/card1)
[    55.285] (II) xfree86: Adding drm device (/dev/dri/card0)
[    55.286] (--) PCI:*(0:0:2:0) 8086:0166:144d:c652 rev 9, Mem @ 0xdb000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    55.286] (--) PCI: (0:1:0:0) 10de:1058:144d:c652 rev 161, Mem @ 0xda000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @ 0x00003000/128
[    55.286] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    55.286] (II) "glx" will be loaded by default.
[    55.286] (II) LoadModule: "glx"
[    55.286] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    57.483] (II) Module glx: vendor="NVIDIA Corporation"
[    57.483]     compiled for 4.0.2, module version = 1.0.0
[    57.483]     Module class: X.Org Server Extension
[    57.505] (II) NVIDIA GLX Module  367.57  Mon Oct  3 20:28:17 PDT 2016
[    57.559] (II) LoadModule: "nvidia"
[    57.559] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    57.674] (II) Module nvidia: vendor="NVIDIA Corporation"
[    57.674]     compiled for 4.0.2, module version = 1.0.0
[    57.674]     Module class: X.Org Video Driver
[    57.692] (II) LoadModule: "modesetting"
[    57.757] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    57.769] (II) Module modesetting: vendor="X.Org Foundation"
[    57.770]     compiled for 1.18.4, module version = 1.18.4
[    57.770]     Module class: X.Org Video Driver
[    57.770]     ABI class: X.Org Video Driver, version 20.0
[    57.770] (II) NVIDIA dlloader X Driver  367.57  Mon Oct  3 20:03:48 PDT 2016
[    57.770] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    57.770] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    57.789] (II) Loading sub module "fb"
[    57.789] (II) LoadModule: "fb"
[    57.789] (II) Loading /usr/lib/xorg/modules/libfb.so
[    57.791] (II) Module fb: vendor="X.Org Foundation"
[    57.791]     compiled for 1.18.4, module version = 1.0.0
[    57.791]     ABI class: X.Org ANSI C Emulation, version 0.4
[    57.791] (II) Loading sub module "wfb"
[    57.791] (II) LoadModule: "wfb"
[    57.791] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    57.822] (II) Module wfb: vendor="X.Org Foundation"
[    57.822]     compiled for 1.18.4, module version = 1.0.0
[    57.822]     ABI class: X.Org ANSI C Emulation, version 0.4
[    57.822] (II) Loading sub module "ramdac"
[    57.822] (II) LoadModule: "ramdac"
[    57.822] (II) Module "ramdac" already built-in
[    57.840] (II) modeset(G0): using drv /dev/dri/card0
[    57.840] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    57.840] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    57.840] (==) NVIDIA(0): RGB weight 888
[    57.840] (==) NVIDIA(0): Default visual is TrueColor
[    57.840] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    57.841] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    57.841] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    57.841] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    57.841] (**) NVIDIA(0): Enabling 2D acceleration
[    62.714] (II) NVIDIA(0): NVIDIA GPU GeForce 610M (GF119) at PCI:1:0:0 (GPU-0)
[    62.714] (--) NVIDIA(0): Memory: 1048576 kBytes
[    62.714] (--) NVIDIA(0): VideoBIOS: 75.19.54.00.06
[    62.714] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    62.714] (II) NVIDIA(0): Validated MetaModes:
[    62.714] (II) NVIDIA(0):     "NULL"
[    62.714] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    62.714] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    62.714] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    62.714] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    62.714] (**) modeset(G0): Option "AccelMethod" "None"
[    62.714] (==) modeset(G0): RGB weight 888
[    62.714] (==) modeset(G0): Default visual is TrueColor
[    62.714] (**) modeset(G0): glamor disabled
[    62.714] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    62.714] (II) modeset(G0): Output LVDS-1-1 has no monitor section
[    62.715] (II) modeset(G0): Output VGA-1-1 has no monitor section
[    62.840] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[    62.840] (II) modeset(G0): Output DP-1-1 has no monitor section
[    62.840] (II) modeset(G0): EDID for output LVDS-1-1
[    62.840] (II) modeset(G0): Manufacturer: SEC  Model: 384a  Serial#: 0
[    62.840] (II) modeset(G0): Year: 2011  Week: 0
[    62.840] (II) modeset(G0): EDID Version: 1.3
[    62.840] (II) modeset(G0): Digital Display Input
[    62.840] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    62.840] (II) modeset(G0): Gamma: 2.20
[    62.840] (II) modeset(G0): No DPMS capabilities specified
[    62.840] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    62.840] (II) modeset(G0): First detailed timing is preferred mode
[    62.840] (II) modeset(G0): redX: 0.615 redY: 0.355   greenX: 0.355 greenY: 0.610
[    62.840] (II) modeset(G0): blueX: 0.150 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    62.840] (II) modeset(G0): Manufacturer's mask: 0
[    62.840] (II) modeset(G0): Supported detailed timing:
[    62.840] (II) modeset(G0): clock: 70.7 MHz   Image Size:  344 x 194 mm
[    62.840] (II) modeset(G0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    62.840] (II) modeset(G0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 792 v_border: 0
[    62.840] (II) modeset(G0): Unknown vendor-specific block f
[    62.840] (II) modeset(G0):  SAMSUNG
[    62.840] (II) modeset(G0):  LTN156AT248
[    62.840] (II) modeset(G0): EDID (in hex):
[    62.841] (II) modeset(G0):     00ffffffffffff004ca34a3800000000
[    62.841] (II) modeset(G0):     00150103802213780a81a59d5b5b9c26
[    62.841] (II) modeset(G0):     19505400000001010101010101010101
[    62.841] (II) modeset(G0):     0101010101019e1b5678500018303020
[    62.841] (II) modeset(G0):     250058c2100000190000000f00000000
[    62.841] (II) modeset(G0):     00000000001eb4021500000000fe0053
[    62.841] (II) modeset(G0):     414d53554e470a2020202020000000fe
[    62.841] (II) modeset(G0):     004c544e31353641543234380a2000c3
[    62.841] (II) modeset(G0): Printing probed modes for output LVDS-1-1
[    62.841] (II) modeset(G0): Modeline "1366x768"x60.1   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz eP)
[    62.841] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    62.841] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    62.841] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    62.841] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    62.841] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    62.841] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    62.841] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    62.841] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    62.841] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    62.841] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    62.841] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    62.841] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    62.841] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    62.841] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    62.841] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    62.841] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    62.841] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    62.841] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    62.841] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    62.841] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    62.841] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    62.841] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    62.841] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    62.841] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    62.841] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    62.841] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    62.841] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    62.842] (II) modeset(G0): EDID for output VGA-1-1
[    62.968] (II) modeset(G0): EDID for output HDMI-1-1
[    62.968] (II) modeset(G0): EDID for output DP-1-1
[    62.968] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    62.968] (==) modeset(G0): DPI set to (96, 96)
[    62.968] (II) Loading sub module "fb"
[    62.968] (II) LoadModule: "fb"
[    62.968] (II) Loading /usr/lib/xorg/modules/libfb.so
[    62.968] (II) Module fb: vendor="X.Org Foundation"
[    62.968]     compiled for 1.18.4, module version = 1.0.0
[    62.968]     ABI class: X.Org ANSI C Emulation, version 0.4
[    62.968] (II) Loading sub module "shadow"
[    62.968] (II) LoadModule: "shadow"
[    62.968] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    62.981] (II) Module shadow: vendor="X.Org Foundation"
[    62.981]     compiled for 1.18.4, module version = 1.1.0
[    62.981]     ABI class: X.Org ANSI C Emulation, version 0.4
[    62.981] (--) Depth 24 pixmap format is 32 bpp
[    63.005] (==) modeset(G0): Backing store enabled
[    63.005] (==) modeset(G0): Silken mouse enabled
[    63.006] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    63.006] (==) modeset(G0): DPMS enabled
[    63.006] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    63.006] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    63.546] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[    63.546] (II) NVIDIA:     access.
[    76.207] (EE) 
Fatal server error:
[    76.207] (EE) NVIDIA: A GPU exception occurred during X server initialization(EE) 
[    76.207] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    76.207] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    76.207] (EE) 
[    76.245] (EE) Server terminated with error (1). Closing log file.
```

but the boot sequence also failed to load the nvidia persistenced daemon as such:

```
systemctl status nvidia-persistenced

 nvidia-persistenced.service - NVIDIA Persistence Daemon
   Loaded: loaded (/lib/systemd/system/nvidia-persistenced.service; static; vendor preset: enabled)
   Active: inactive (dead)

nov 27 17:17:00 killer-300E4C-300E5C-300E7C systemd[1]: Starting NVIDIA Persistence Daemon...
nov 27 17:17:00 killer-300E4C-300E5C-300E7C nvidia-persistenced[1135]: Verbose syslog connection opened
nov 27 17:17:00 killer-300E4C-300E5C-300E7C nvidia-persistenced[1135]: Now running with user ID 121 and group ID 129
nov 27 17:17:00 killer-300E4C-300E5C-300E7C nvidia-persistenced[1135]: Started (1135)
nov 27 17:17:00 killer-300E4C-300E5C-300E7C systemd[1]: Started NVIDIA Persistence Daemon.
nov 27 17:17:04 killer-300E4C-300E5C-300E7C nvidia-persistenced[1135]: device 0000:01:00.0 - registered
nov 27 17:17:04 killer-300E4C-300E5C-300E7C nvidia-persistenced[1135]: Local RPC service initialized
nov 27 17:17:20 killer-300E4C-300E5C-300E7C systemd[1]: Stopping NVIDIA Persistence Daemon...
nov 27 17:17:20 killer-300E4C-300E5C-300E7C nvidia-persistenced[1135]: Received signal 15
nov 27 17:17:20 killer-300E4C-300E5C-300E7C systemd[1]: Stopped NVIDIA Persistence Daemon.
killer@killer-300E4C-300E5C-300E7C:~$ sudo screendump 1 > /home/killer/Documents/persdaemon.txt


```

---

### Post by mr.man2 on 2016-11-27
interesting, i re-installed the OS after i failed all my BB experiments & never dared re-downloading it conciously,  thanks for the tip going for the removal & 

```

sudo ubuntu-drivers autoinstall


```

test

---

### Post by mr.man2 on 2016-11-27
p.p.s. 
```

killer@killer-300E4C-300E5C-300E7C:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  xserver-xorg-legacy
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  bbswitch-dkms libcuda1-375 nvidia-opencl-icd-375 nvidia-prime
  nvidia-settings
Suggested packages:
  bumblebee
The following packages will be REMOVED:
  libcuda1-304
The following NEW packages will be installed:
  bbswitch-dkms libcuda1-375 nvidia-375 nvidia-opencl-icd-375 nvidia-prime
  nvidia-settings

```

so autoinstall implements it indeed :&#272;

---

### Post by Bashing-om on 2016-11-27
mr.man2; Humm ..

Do not know the why, but X is not happy:
We have from the log file:
> 
76.207] (EE) NVIDIA: A GPU exception occurred during X server initialization(EE)

Whereas also is:
> 
Manufacturer: SEC  Model: 384a
62.840] (II) modeset(G0):  SAMSUNG
62.840] (II) modeset(G0):  LTN156AT248

which raises the question of how many monitors are you attempting to drive ? And how is the primary monitor connected ? An adapter in the equation ? Is the cable to the monitor known to be good and securely connected ?

[INDENT][INDENT]again, there has to be a reason
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-27
hey, so basically the monitor in question is a built in monitor for my samsung 300e series laptop, that's the sole monitor i'm trying to operate & it's surely well connected, didn't pose hardships on Windows

---

### Post by Bashing-om on 2016-11-28
mr.man2; Another thought .

As I can come up with no other explanation - secure boot ?
When you:
```

sudo apt update
sudo apt full-upgrade

```
do you see something similar :
> 
If Secure Boot remains enabled on your system, your system may still boot but any hardware that requires third-party drivers to                  work correctly may not  be usable.


[INDENT][INDENT]seeking to know that why
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-28
no such thing present, should i reinstall the OS?

---

### Post by Bashing-om on 2016-11-28
mr.man2; Well.

It is considered that "nuclear solution" a re-install while always effective, one learns little about the operating system.
The decision to RE-install is up to you . Depending on the backup situation, 30 minutes and all done and over with .
It is our philosophy that 'buntu is always fixable .. given the time and effort .

Presently though I am stuck on how to proceed and what to do next to isolate .

[INDENT][INDENT][INDENT]but
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-28
Dear Bashing-Om

i'm not really hellbent on re-installing, however i must note that i've already tried it prior, w/ "autoinstall" and it didn't sort the issue out, precisely eversince nvidia-367's release it never worked, maybe if i tried experimenting w/ kernel versions or ubuntu flavours? what do you reckon i should check? thanks for your enthousiasm mack!

---

### Post by oldfred on 2016-11-28
Did you houseclean out all the Bumblebee code including bbswitch?

---

### Post by mr.man2 on 2016-11-28
i'm pretty positive on that, but being a novice, i might need a means to double-check

---

### Post by mr.man2 on 2016-11-28
also i've stated previously that autoinstall installs BB modules by default

---

### Post by Bashing-om on 2016-11-28
mr.man2; Hey !

Believe me I am all for the learning curve, even to the point of demonstrating my ignorance.

Now we know we have a interfacing issue with this card cause the log file tells us so . But gives no hint where or why .

Now, if ya want to poke at it, In my opinion the better way to poke and get some answers is booting up to terminal from grub .. and seeing what all the kernel has to relate . Now, this might be real time consuming . BUT it is the way in which I found that 14.04 open source driver does not support my new nVidia card. In systemd can be a very vexing - as my familiarity with systemd is more than lacking .

However, if you want to start down this trail, I am more than willing to see what we can do . The kernel does talk . Ya just got to tell it what you want to know . And that is an art in and of it's self .

In grub with upstart I am fairly comfortable . I have much much more to learn about grub in systemd .

[INDENT][INDENT][INDENT]shall we begin 
[/INDENT][/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-28
absolutely yes :&#272;

---

### Post by mr.man2 on 2016-11-28
i beleive it would be most tiresome to do this interactively so if you would be kind enough to dump reference i would be most grateful <3

---

### Post by Bashing-om on 2016-11-28
mr.man2; Hey ....

I do this by the seat of my pants. I have no references to pass on .

And yes it is going to be s l o w and tiresome . Mainly because we do not have the amenities of a terminal emulator for copy and paste, and because I am not looking over your shoulder at your terminal.

For starters. show me what we are going to tell grub about the location of the boot files:
Post back:
```

sudo parted -l

```
If this turns out to be GPT/EFI partitioning, welp - I need to get my learning cap on . Just because I know of it does not mean I have the experience.  Here in my area I have yet to encounter the later partitioning schemes and firmware .

But we will figure out how to boot this sucker from grub and see all the boot messages .
Grub is some kind of smart !

[INDENT][INDENT]we can flounder through
[INDENT][INDENT][INDENT]together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-11-29
Dear Bashing-Om here are the results:

```
killer@killer-300E4C-300E5C-300E7C:~$ sudo parted -l
[sudo] password for killer: 
Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  746GB  746GB   primary   ext4            boot
 2      746GB   750GB  4063MB  extended
 5      746GB   750GB  4063MB  logical   linux-swap(v1)


killer@killer-300E4C-300E5C-300E7C:~$ 


```

---

### Post by oldfred on 2016-11-29
I am pretty sure in one thread a user un-installed bbswitch and then everything worked.

I do not know the use of bbswitch, but thought is was part of Bumblebee, so surprised it is being installed as part of nVidia.

Checking it says bbswitch is for certain types of Optimus, so it may be used for switching video modes, which has not always worked.
Some have posted that they can change in UEFI/BIOS which video they use and that also works.

---

### Post by Bashing-om on 2016-11-29
mr.man2; Great !

Legacy partitioning - I can deal with that ! . And we know that root is in the sda1 partition and that there is no other operating system to contend with,

So let's see what the kernel has to say when booting up.
Boot to the grub boot menu and press the 'c' key for a Command line.
Now here tell grub we want to "page" through the messaging:
```

set pager=1

```
And tell grub we want to see all the messaging:
```

set debug=all

```

And now to tell grub what to boot and where:
We do not need to get fancy here, just the basics as grub's files are consistent, and grub is aware of what is what and where:
We just tell grub we are booting the operating system on sda1: 
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
most excellent tutorial on grub and what we are doing:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) <=drs305 all about grub 2

Now as the system boots, the messaging is 1 page at a time - awaiting a return key from you as the signal to continue.
Your mission here is to look for anomalies - errors and warning - as the kernel transfers from kernel space to user space and hands over control to you .

If at this point once booted, and the kernel does not report any problems, then the issue does not reside in the kernel's space; rather in the X layer that is on top of the kernel . Here then next we reboot and start the GUI from grub booted to a terminal rather than to a command line interface .

We do this, however, one step at a time in our attempt to identify where the failure occurs to interface the hardware ( graphic's card ) into the kernel and/or the X-server .

[INDENT][INDENT]it's all an adventure
[INDENT][INDENT]in this process of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-12-01
mr.man2; Hey !

Did I loose you ? ... did you get frustrated and give up ?  Did you take that nuclear option and RE-install ?

[INDENT][INDENT]car 54 where are you
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-12-05
Dear Bashing-Om, 

i went full nuclear but not because i was frustrated. It happened merely because i wanted to give xubuntu a no install spin, i didn't do anything in particular, just browsing the features, & didn't install xub, for we were having this investigation going on, however rebooting to ubuntu gave me the unknown filesystem error. Being stuck with an unlaunchable OS & the xub install disk, i re-installed it. it works swell, & i'm having no issues save for the GPU which produces the exact same symptoms!! I went for the driver auto-install as well which downloaded bumblebee modules by default & (nvidia-367) booted me to low graphics mode (or its xubuntu respective non-responsive login screen) i removed only the bumblebee modules, to fall on the same screen. the live boot-sequence gave no error messages except for the NVRM: xid 44 like it did previously. i'm more than willing to proceed however should i pass back to Ubuntu to go on, or can we push it on xub? Thanks for your persistence its legendary

---

### Post by Bashing-om on 2016-12-05
mr.man2; Well !

I am flabbergasted that a fresh install of xubuntu and still the GPU is not reconciled !

Happens to be that xfce is also my preferred Desktop Environment .

As to my "persistence its legendary" state; well, so long as you are willing and I am able there is not quit in my nature . I have that much faith and devotion to this operating system.

All depends on what you want to do - which DE do you prefer ? Use what you are the more comfortable with - for whatever reason you are the more comfortable.

In any event, we start again from square ONE ->
Show me all of:

We still on 16.04 ?
```

lsb_release -a

```

Hardware identified ?
```

lspci -nnk | grep -iA3 vga

```

driver loaded ?
```

sudo lshw -C display

```

Any conflicts, and are the supporting components of the desired driver installed ?
```

dpkg -l | grep -i nvidia
dpkg -l | grep -i nouveau

```

And does the GUI/X give us any hints of what is not taking place ?
```

cat .xsession-errors
cat /var/log/Xorg.0.log

```
-I will cringe if I see "nomodeset" in the boot line ! - If so we back up and regroup with a new plan of attack- 

And:
```

cat /var/log/gpu-manager.log

```
Where I can accept that the log file does not exist IF the nouveau driver is in use .

Mind ya Mr. Man there is a lot I do not know, However I sure want to know more.

[INDENT][INDENT][INDENT]inquiring minds ..............
[/INDENT][/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-12-07
Dear Bashing-Om

upon autoinstall the following is displayed:

```
The following additional packages will be installed:
  bbswitch-dkms iucode-tool libcuda1-367 nvidia-opencl-icd-367 nvidia-prime
  nvidia-settings
Suggested packages:
  bumblebee
The following packages will be REMOVED:
  libcuda1-304
The following NEW packages will be installed:
  bbswitch-dkms intel-microcode iucode-tool libcuda1-367 nvidia-367
  nvidia-opencl-icd-367 nvidia-prime nvidia-settings


```
what might be noteworthy is that bumblebee modules are still installed by default. 
however below are the excavations:
yes we are on xenial xub
```
killer@killer-300E4C-300E5C-300E7C:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
```

lspci -nnk | grep -iA3 vga:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Samsung Electronics Co Ltd 3rd Gen Core processor Graphics Controller [144d:c652]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119M [GeForce 610M] [10de:1058] (rev a1)
    Subsystem: Samsung Electronics Co Ltd GF119M [GeForce 610M] [144d:c652]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm


```
sudo lshw -C display:
```
  *-display
       description: VGA compatible controller
       product: GF119M [GeForce 610M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:29 memory:da000000-daffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:3000(size=128)
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:db000000-db3fffff memory:c0000000-cfffffff ioport:4000(size=64)


```
dpkg -l | grep -i nvidia:
```
ii  bbswitch-dkms                               0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-367                                367.57-0ubuntu0.16.04.1                       amd64        NVIDIA CUDA runtime library
ii  nvidia-367                                  367.57-0ubuntu0.16.04.1                       amd64        NVIDIA binary driver - version 367.57
ii  nvidia-opencl-icd-367                       367.57-0ubuntu0.16.04.1                       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver


```
dpkg -l | grep -i nouveau:
```
ii  libdrm-nouveau2:amd64                       2.4.67-1ubuntu0.16.04.2                       amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                        2.4.67-1ubuntu0.16.04.2                       i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  xserver-xorg-video-nouveau                  1:1.0.12-1build2                              amd64        X.Org X server -- Nouveau display driver


```
cat .xsession-errors
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: startxfce4 main process (1457) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: job upstart-udev-bridge failed to stop
upstart: job dbus failed to stop
upstart: job upstart-dbus-session-bridge failed to stop
upstart: job gpg-agent failed to stop
upstart: job upstart-dbus-system-bridge failed to stop
upstart: job upstart-file-bridge failed to stop


```
cat /var/log/Xorg.0.log
```
[    39.902] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    39.902] X Protocol Version 11, Revision 0
[    39.902] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[    39.902] Current Operating System: Linux killer-300E4C-300E5C-300E7C 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
[    39.902] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=dee094b4-f587-4a44-accc-ffc9b957f7ee ro text
[    39.902] Build Date: 02 November 2016  10:06:10PM
[    39.902] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[    39.902] Current version of pixman: 0.33.6
[    39.902]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    39.902] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    39.903] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec  7 15:24:25 2016
[    40.056] (==) Using config file: "/etc/X11/xorg.conf"
[    40.056] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    40.085] (==) ServerLayout "layout"
[    40.086] (**) |-->Screen "nvidia" (0)
[    40.086] (**) |   |-->Monitor "<default monitor>"
[    40.119] (**) |   |-->Device "nvidia"
[    40.119] (**) |   |-->GPUDevice "nvidia"
[    40.119] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    40.119] (**) |-->Inactive Device "intel"
[    40.119] (==) Automatically adding devices
[    40.119] (==) Automatically enabling devices
[    40.119] (==) Automatically adding GPU devices
[    40.119] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    40.119] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    40.119]     Entry deleted from font path.
[    40.119] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    40.119]     Entry deleted from font path.
[    40.119] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    40.119]     Entry deleted from font path.
[    40.119] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    40.119]     Entry deleted from font path.
[    40.119] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    40.119]     Entry deleted from font path.
[    40.119] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    40.119] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    40.119] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    40.205] (II) Loader magic: 0x55e0536b0dc0
[    40.205] (II) Module ABI versions:
[    40.205]     X.Org ANSI C Emulation: 0.4
[    40.205]     X.Org Video Driver: 20.0
[    40.205]     X.Org XInput driver : 22.1
[    40.205]     X.Org Server Extension : 9.0
[    40.205] (++) using VT number 7

[    40.205] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    40.206] (II) xfree86: Adding drm device (/dev/dri/card0)
[    40.206] (II) xfree86: Adding drm device (/dev/dri/card1)
[    40.207] (--) PCI:*(0:0:2:0) 8086:0166:144d:c652 rev 9, Mem @ 0xdb000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    40.207] (--) PCI: (0:1:0:0) 10de:1058:144d:c652 rev 161, Mem @ 0xda000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @ 0x00003000/128
[    40.207] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    40.207] (II) "glx" will be loaded by default.
[    40.207] (II) LoadModule: "glx"
[    40.207] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    42.455] (II) Module glx: vendor="NVIDIA Corporation"
[    42.455]     compiled for 4.0.2, module version = 1.0.0
[    42.455]     Module class: X.Org Server Extension
[    42.455] (II) NVIDIA GLX Module  367.57  Mon Oct  3 20:28:17 PDT 2016
[    42.455] (II) LoadModule: "nvidia"
[    42.455] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    42.516] (II) Module nvidia: vendor="NVIDIA Corporation"
[    42.516]     compiled for 4.0.2, module version = 1.0.0
[    42.516]     Module class: X.Org Video Driver
[    42.516] (II) LoadModule: "modesetting"
[    42.516] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    42.516] (II) Module modesetting: vendor="X.Org Foundation"
[    42.516]     compiled for 1.18.4, module version = 1.18.4
[    42.516]     Module class: X.Org Video Driver
[    42.516]     ABI class: X.Org Video Driver, version 20.0
[    42.516] (II) NVIDIA dlloader X Driver  367.57  Mon Oct  3 20:03:48 PDT 2016
[    42.516] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    42.516] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    42.530] (II) Loading sub module "fb"
[    42.530] (II) LoadModule: "fb"
[    42.548] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.568] (II) Module fb: vendor="X.Org Foundation"
[    42.568]     compiled for 1.18.4, module version = 1.0.0
[    42.568]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.568] (II) Loading sub module "wfb"
[    42.568] (II) LoadModule: "wfb"
[    42.568] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    42.574] (II) Module wfb: vendor="X.Org Foundation"
[    42.574]     compiled for 1.18.4, module version = 1.0.0
[    42.574]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.574] (II) Loading sub module "ramdac"
[    42.574] (II) LoadModule: "ramdac"
[    42.574] (II) Module "ramdac" already built-in
[    42.598] (II) modeset(G0): using drv /dev/dri/card1
[    42.598] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    42.598] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    42.598] (==) NVIDIA(0): RGB weight 888
[    42.598] (==) NVIDIA(0): Default visual is TrueColor
[    42.598] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    42.616] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    42.616] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    42.616] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    42.616] (**) NVIDIA(0): Enabling 2D acceleration
[    42.727] (II) NVIDIA(0): NVIDIA GPU GeForce 610M (GF119) at PCI:1:0:0 (GPU-0)
[    42.727] (--) NVIDIA(0): Memory: 1048576 kBytes
[    42.727] (--) NVIDIA(0): VideoBIOS: 75.19.54.00.06
[    42.727] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    42.727] (II) NVIDIA(0): Validated MetaModes:
[    42.727] (II) NVIDIA(0):     "NULL"
[    42.727] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    42.727] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    42.727] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    42.727] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    42.727] (**) modeset(G0): Option "AccelMethod" "None"
[    42.727] (==) modeset(G0): RGB weight 888
[    42.727] (==) modeset(G0): Default visual is TrueColor
[    42.727] (**) modeset(G0): glamor disabled
[    42.727] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    42.727] (II) modeset(G0): Output LVDS-1-1 has no monitor section
[    42.728] (II) modeset(G0): Output VGA-1-1 has no monitor section
[    42.728] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[    42.728] (II) modeset(G0): Output DP-1-1 has no monitor section
[    42.729] (II) modeset(G0): EDID for output LVDS-1-1
[    42.729] (II) modeset(G0): Manufacturer: SEC  Model: 384a  Serial#: 0
[    42.729] (II) modeset(G0): Year: 2011  Week: 0
[    42.729] (II) modeset(G0): EDID Version: 1.3
[    42.729] (II) modeset(G0): Digital Display Input
[    42.729] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    42.729] (II) modeset(G0): Gamma: 2.20
[    42.729] (II) modeset(G0): No DPMS capabilities specified
[    42.729] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    42.729] (II) modeset(G0): First detailed timing is preferred mode
[    42.729] (II) modeset(G0): redX: 0.615 redY: 0.355   greenX: 0.355 greenY: 0.610
[    42.729] (II) modeset(G0): blueX: 0.150 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    42.729] (II) modeset(G0): Manufacturer's mask: 0
[    42.729] (II) modeset(G0): Supported detailed timing:
[    42.729] (II) modeset(G0): clock: 70.7 MHz   Image Size:  344 x 194 mm
[    42.729] (II) modeset(G0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    42.729] (II) modeset(G0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 792 v_border: 0
[    42.729] (II) modeset(G0): Unknown vendor-specific block f
[    42.729] (II) modeset(G0):  SAMSUNG
[    42.729] (II) modeset(G0):  LTN156AT248
[    42.729] (II) modeset(G0): EDID (in hex):
[    42.729] (II) modeset(G0):     00ffffffffffff004ca34a3800000000
[    42.729] (II) modeset(G0):     00150103802213780a81a59d5b5b9c26
[    42.729] (II) modeset(G0):     19505400000001010101010101010101
[    42.729] (II) modeset(G0):     0101010101019e1b5678500018303020
[    42.729] (II) modeset(G0):     250058c2100000190000000f00000000
[    42.729] (II) modeset(G0):     00000000001eb4021500000000fe0053
[    42.729] (II) modeset(G0):     414d53554e470a2020202020000000fe
[    42.729] (II) modeset(G0):     004c544e31353641543234380a2000c3
[    42.729] (II) modeset(G0): Printing probed modes for output LVDS-1-1
[    42.729] (II) modeset(G0): Modeline "1366x768"x60.1   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz eP)
[    42.729] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    42.729] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    42.729] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    42.729] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    42.729] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    42.729] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    42.729] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    42.729] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    42.729] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    42.729] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    42.729] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    42.729] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    42.729] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    42.729] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    42.729] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    42.729] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    42.729] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    42.729] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    42.729] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    42.729] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    42.729] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    42.729] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    42.729] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    42.729] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    42.729] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    42.729] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    42.729] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    42.730] (II) modeset(G0): EDID for output VGA-1-1
[    42.730] (II) modeset(G0): EDID for output HDMI-1-1
[    42.730] (II) modeset(G0): EDID for output DP-1-1
[    42.730] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    42.730] (==) modeset(G0): DPI set to (96, 96)
[    42.730] (II) Loading sub module "fb"
[    42.730] (II) LoadModule: "fb"
[    42.731] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.731] (II) Module fb: vendor="X.Org Foundation"
[    42.731]     compiled for 1.18.4, module version = 1.0.0
[    42.731]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.731] (II) Loading sub module "shadow"
[    42.731] (II) LoadModule: "shadow"
[    42.731] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    42.731] (II) Module shadow: vendor="X.Org Foundation"
[    42.731]     compiled for 1.18.4, module version = 1.1.0
[    42.731]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.731] (--) Depth 24 pixmap format is 32 bpp
[    42.755] (==) modeset(G0): Backing store enabled
[    42.755] (==) modeset(G0): Silken mouse enabled
[    42.755] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    42.756] (==) modeset(G0): DPMS enabled
[    42.756] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    42.756] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    43.306] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[    43.306] (II) NVIDIA:     access.
[    43.419] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    43.419] (II) NVIDIA(0): Setting mode "NULL"
[    43.433] (==) NVIDIA(0): Disabling shared memory pixmaps
[    43.433] (==) NVIDIA(0): Backing store enabled
[    43.433] (==) NVIDIA(0): Silken mouse enabled
[    43.433] (==) NVIDIA(0): DPMS enabled
[    43.454] (II) Loading sub module "dri2"
[    43.454] (II) LoadModule: "dri2"
[    43.454] (II) Module "dri2" already built-in
[    43.454] (II) NVIDIA(0): [DRI2] Setup complete
[    43.454] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    43.454] (--) RandR disabled
[    43.457] (II) SELinux: Disabled on system
[    43.458] (II) Initializing extension GLX
[    43.458] (II) Indirect GLX disabled.
[    43.459] (II) modeset(G0): Damage tracking initialized
[    43.631] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    43.631] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.631] (II) LoadModule: "evdev"
[    43.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    43.665] (II) Module evdev: vendor="X.Org Foundation"
[    43.665]     compiled for 1.18.1, module version = 2.10.1
[    43.665]     Module class: X.Org XInput Driver
[    43.665]     ABI class: X.Org XInput driver, version 22.1
[    43.665] (II) Using input driver 'evdev' for 'Power Button'
[    43.665] (**) Power Button: always reports core events
[    43.665] (**) evdev: Power Button: Device: "/dev/input/event2"
[    43.665] (--) evdev: Power Button: Vendor 0 Product 0x1
[    43.665] (--) evdev: Power Button: Found keys
[    43.665] (II) evdev: Power Button: Configuring as keyboard
[    43.665] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    43.665] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    43.665] (**) Option "xkb_rules" "evdev"
[    43.665] (**) Option "xkb_model" "pc105"
[    43.665] (**) Option "xkb_layout" "hu"
[    43.678] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    43.678] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    43.678] (II) Using input driver 'evdev' for 'Video Bus'
[    43.678] (**) Video Bus: always reports core events
[    43.678] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    43.678] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    43.678] (--) evdev: Video Bus: Found keys
[    43.678] (II) evdev: Video Bus: Configuring as keyboard
[    43.678] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input9/event7"
[    43.678] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    43.678] (**) Option "xkb_rules" "evdev"
[    43.678] (**) Option "xkb_model" "pc105"
[    43.678] (**) Option "xkb_layout" "hu"
[    43.678] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    43.678] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    43.678] (II) Using input driver 'evdev' for 'Video Bus'
[    43.678] (**) Video Bus: always reports core events
[    43.678] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    43.678] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    43.678] (--) evdev: Video Bus: Found keys
[    43.678] (II) evdev: Video Bus: Configuring as keyboard
[    43.678] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:39/LNXVIDEO:00/input/input7/event5"
[    43.678] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    43.678] (**) Option "xkb_rules" "evdev"
[    43.678] (**) Option "xkb_model" "pc105"
[    43.678] (**) Option "xkb_layout" "hu"
[    43.679] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    43.679] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    43.679] (II) Using input driver 'evdev' for 'Power Button'
[    43.679] (**) Power Button: always reports core events
[    43.679] (**) evdev: Power Button: Device: "/dev/input/event1"
[    43.679] (--) evdev: Power Button: Vendor 0 Product 0x1
[    43.679] (--) evdev: Power Button: Found keys
[    43.679] (II) evdev: Power Button: Configuring as keyboard
[    43.679] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    43.679] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    43.679] (**) Option "xkb_rules" "evdev"
[    43.679] (**) Option "xkb_model" "pc105"
[    43.679] (**) Option "xkb_layout" "hu"
[    43.679] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    43.679] (II) No input driver specified, ignoring this device.
[    43.679] (II) This device may have been added with another device file.
[    43.680] (II) config/udev: Adding input device DaKai 2.4G RX (/dev/input/event4)
[    43.680] (**) DaKai 2.4G RX: Applying InputClass "evdev keyboard catchall"
[    43.680] (II) Using input driver 'evdev' for 'DaKai 2.4G RX'
[    43.680] (**) DaKai 2.4G RX: always reports core events
[    43.680] (**) evdev: DaKai 2.4G RX: Device: "/dev/input/event4"
[    43.680] (--) evdev: DaKai 2.4G RX: Vendor 0xe8f Product 0xa7
[    43.680] (--) evdev: DaKai 2.4G RX: Found keys
[    43.680] (II) evdev: DaKai 2.4G RX: Configuring as keyboard
[    43.680] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:0E8F:00A7.0001/input/input6/event4"
[    43.680] (II) XINPUT: Adding extended input device "DaKai 2.4G RX" (type: KEYBOARD, id 10)
[    43.680] (**) Option "xkb_rules" "evdev"
[    43.680] (**) Option "xkb_model" "pc105"
[    43.680] (**) Option "xkb_layout" "hu"
[    43.680] (II) config/udev: Adding input device DaKai 2.4G RX (/dev/input/event6)
[    43.680] (**) DaKai 2.4G RX: Applying InputClass "evdev pointer catchall"
[    43.680] (**) DaKai 2.4G RX: Applying InputClass "evdev keyboard catchall"
[    43.680] (II) Using input driver 'evdev' for 'DaKai 2.4G RX'
[    43.680] (**) DaKai 2.4G RX: always reports core events
[    43.680] (**) evdev: DaKai 2.4G RX: Device: "/dev/input/event6"
[    43.680] (--) evdev: DaKai 2.4G RX: Vendor 0xe8f Product 0xa7
[    43.680] (--) evdev: DaKai 2.4G RX: Found 9 mouse buttons
[    43.680] (--) evdev: DaKai 2.4G RX: Found scroll wheel(s)
[    43.680] (--) evdev: DaKai 2.4G RX: Found relative axes
[    43.680] (--) evdev: DaKai 2.4G RX: Found x and y relative axes
[    43.680] (--) evdev: DaKai 2.4G RX: Found absolute axes
[    43.680] (II) evdev: DaKai 2.4G RX: Forcing absolute x/y axes to exist.
[    43.680] (--) evdev: DaKai 2.4G RX: Found keys
[    43.680] (II) evdev: DaKai 2.4G RX: Configuring as mouse
[    43.680] (II) evdev: DaKai 2.4G RX: Configuring as keyboard
[    43.680] (II) evdev: DaKai 2.4G RX: Adding scrollwheel support
[    43.680] (**) evdev: DaKai 2.4G RX: YAxisMapping: buttons 4 and 5
[    43.680] (**) evdev: DaKai 2.4G RX: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    43.680] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/0003:0E8F:00A7.0002/input/input8/event6"
[    43.680] (II) XINPUT: Adding extended input device "DaKai 2.4G RX" (type: KEYBOARD, id 11)
[    43.680] (**) Option "xkb_rules" "evdev"
[    43.680] (**) Option "xkb_model" "pc105"
[    43.680] (**) Option "xkb_layout" "hu"
[    43.681] (II) evdev: DaKai 2.4G RX: initialized for relative axes.
[    43.681] (WW) evdev: DaKai 2.4G RX: ignoring absolute axes.
[    43.681] (**) DaKai 2.4G RX: (accel) keeping acceleration scheme 1
[    43.681] (**) DaKai 2.4G RX: (accel) acceleration profile 0
[    43.681] (**) DaKai 2.4G RX: (accel) acceleration factor: 2.000
[    43.681] (**) DaKai 2.4G RX: (accel) acceleration threshold: 4
[    43.681] (II) config/udev: Adding input device DaKai 2.4G RX (/dev/input/mouse0)
[    43.681] (II) No input driver specified, ignoring this device.
[    43.681] (II) This device may have been added with another device file.
[    43.681] (II) config/udev: Adding input device WebCam SC-03FFL11939N (/dev/input/event12)
[    43.681] (**) WebCam SC-03FFL11939N: Applying InputClass "evdev keyboard catchall"
[    43.681] (II) Using input driver 'evdev' for 'WebCam SC-03FFL11939N'
[    43.681] (**) WebCam SC-03FFL11939N: always reports core events
[    43.681] (**) evdev: WebCam SC-03FFL11939N: Device: "/dev/input/event12"
[    43.681] (--) evdev: WebCam SC-03FFL11939N: Vendor 0x2232 Product 0x1028
[    43.681] (--) evdev: WebCam SC-03FFL11939N: Found keys
[    43.681] (II) evdev: WebCam SC-03FFL11939N: Configuring as keyboard
[    43.681] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input13/event12"
[    43.681] (II) XINPUT: Adding extended input device "WebCam SC-03FFL11939N" (type: KEYBOARD, id 12)
[    43.681] (**) Option "xkb_rules" "evdev"
[    43.681] (**) Option "xkb_model" "pc105"
[    43.681] (**) Option "xkb_layout" "hu"
[    43.682] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[    43.682] (II) No input driver specified, ignoring this device.
[    43.682] (II) This device may have been added with another device file.
[    43.682] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    43.682] (II) No input driver specified, ignoring this device.
[    43.682] (II) This device may have been added with another device file.
[    43.682] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[    43.682] (II) No input driver specified, ignoring this device.
[    43.682] (II) This device may have been added with another device file.
[    43.682] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    43.682] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    43.682] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    43.682] (**) AT Translated Set 2 keyboard: always reports core events
[    43.682] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    43.682] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    43.682] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    43.682] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    43.682] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    43.682] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    43.682] (**) Option "xkb_rules" "evdev"
[    43.682] (**) Option "xkb_model" "pc105"
[    43.682] (**) Option "xkb_layout" "hu"
[    43.683] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    43.683] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    43.683] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[    43.683] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    43.683] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    43.683] (II) LoadModule: "synaptics"
[    43.683] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    43.683] (II) Module synaptics: vendor="X.Org Foundation"
[    43.683]     compiled for 1.18.1, module version = 1.8.2
[    43.683]     Module class: X.Org XInput Driver
[    43.683]     ABI class: X.Org XInput driver, version 22.1
[    43.683] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    43.683] (**) ETPS/2 Elantech Touchpad: always reports core events
[    43.683] (**) Option "Device" "/dev/input/event8"
[    43.732] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    43.732] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 31)
[    43.732] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1400 (res 31)
[    43.732] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    43.732] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    43.732] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    43.732] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    43.732] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    43.732] (**) ETPS/2 Elantech Touchpad: always reports core events
[    43.756] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event8"
[    43.756] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    43.756] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    43.756] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    43.756] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.061
[    43.756] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    43.756] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    43.756] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    43.756] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    43.756] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    43.756] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    43.756] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"


```
cat /var/log/gpu-manager.log
```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-53-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-53-generic/updates/dkms
Found nvidia module: nvidia_367_modeset.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:166
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1058
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Found "/dev/dri/card1", driven by "i915"
output 0:
    card1-LVDS-1
Number of connected outputs for /dev/dri/card1: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-367/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-367/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Intel IGP detected
Intel hybrid system
Nvidia driver version 367.57 detected
/sys/class/dmi/id/product_version="0.1"
/sys/class/dmi/id/product_name="300E4C/300E5C/300E7C"
1st try: bbswitch without quirks
Loading bbswitch with "load_state=-1 unload_state=1" parameters
intel_matches: 1, nvidia_matches: 1, intel_set: 1, nvidia_set: 1 x_options_matches: 4, accel_method_matches: 1
No need to modify xorg.conf. Path: /etc/X11/xorg.conf
No need to change the current bbswitch status


```

what would u reckon as FUP? should i page thu the boot sequence for errors? Thanks in advance, looking forward to how this case will unfold

---

### Post by Bashing-om on 2016-12-07
mr.man2; Sheeeshhh ...

Ya got me ..
1: driver(s) are loaded
2: supporting driver components are installed
3: No 'direct' driver conflict - with a reseravation
4: X appears happy and reports no issues
5: gpu-manager.log says that nouveau is blacklisted, and should not even be in the picture .


Now the things I do not understand:
1: .xsession-errors ; Huh ? How does upstart play into a systemd initit system ??
2: Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm; Huh ?? why would both nouveau and nVidia modules be available ? Should there be only one ?
3: " ii  libdrm-nouveau2:i386  " Huh ?? why both 32 bit and 64 bit packages installed ? I can not fathom a reason in a default system for this to occur .
4: Why have both xserver-xorg-video-nouveau driver and nvidia-367 installed ? It should be one or the other , yes ?
-------------------------------

So, OK --- what are we going to do ?
1st as Nvidia driver is installed, what is nouveau doing ? 
```

lsmod | grep -i nouveau

```
I would not expect it to even be in the picture - but I am willing to learn how otherwise !

and I see no reason to have a 32 bit driver in this install - You may tell me otherwise .
I do suggest we remove that 32 bit package:
```

sudo apt purge libdrm-nouveau2:i386

```
reboot and see if there is a positive effect.

And It do look as if we will purge all and re-install the graphic's driver. perhaps rebuild initramfs ; as I just do not feel good about having both xserver-xorg-video-nouveau and nvidia-367 installed at the same time. But let's see what happens when  libdrm-nouveau2:i386 is removed and system rebooted .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by mr.man2 on 2016-12-11
Dear Bashing-Om,

```

sudo apt purge libdrm-nouveau2:i386
```
yielded promising results! @ first the system wasn't able to locate the drivers & relied on nouveau (giving utter chaos) but after a purge & reinstall not via ubuntu autoinstall but 
```
sudo apt install nvidia-367 primus
```
i witnessed the following: first it booted to a blank screen no error message or whatsoever. Upon second try it gave me the login screen but froze when i was typing in my password, it was with the third go that i managed logging in & got a glitch like screen with bizarre arrangements patches of weird textures, mutating every 2 second or so into different bizarre displays, but it was obvious that the system tried to initialize itself. i fetched the following:
for lsmod | grep -i bbswitch```
bbswitch               16384  0


```
for cat /var/log/gpu-manager.log
```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-53-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-53-generic/updates/dkms
Found nvidia module: nvidia_367_modeset.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:166
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1058
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-LVDS-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-367/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-367/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
Intel IGP detected
Intel hybrid system
Nvidia driver version 367.57 detected
intel_matches: 1, nvidia_matches: 1, intel_set: 1, nvidia_set: 1 x_options_matches: 4, accel_method_matches: 1
No need to modify xorg.conf. Path: /etc/X11/xorg.conf
No need to change the current bbswitch status


```
cat /var/log/Xorg.0.log gave
```
[   154.435] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[   154.435] X Protocol Version 11, Revision 0
[   154.435] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[   154.435] Current Operating System: Linux killer-300E4C-300E5C-300E7C 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
[   154.435] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=dee094b4-f587-4a44-accc-ffc9b957f7ee ro text
[   154.435] Build Date: 02 November 2016  10:06:10PM
[   154.435] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[   154.435] Current version of pixman: 0.33.6
[   154.435]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   154.435] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   154.435] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 11 18:10:12 2016
[   154.436] (==) Using config file: "/etc/X11/xorg.conf"
[   154.436] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   154.436] (==) ServerLayout "layout"
[   154.436] (**) |-->Screen "nvidia" (0)
[   154.436] (**) |   |-->Monitor "<default monitor>"
[   154.436] (**) |   |-->Device "nvidia"
[   154.436] (**) |   |-->GPUDevice "nvidia"
[   154.436] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[   154.436] (**) |-->Inactive Device "intel"
[   154.436] (==) Automatically adding devices
[   154.436] (==) Automatically enabling devices
[   154.436] (==) Automatically adding GPU devices
[   154.436] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   154.436] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   154.436]     Entry deleted from font path.
[   154.436] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   154.436]     Entry deleted from font path.
[   154.436] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   154.436]     Entry deleted from font path.
[   154.436] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   154.436]     Entry deleted from font path.
[   154.436] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   154.436]     Entry deleted from font path.
[   154.436] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   154.436] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   154.436] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   154.436] (II) Loader magic: 0x5649dc34bdc0
[   154.436] (II) Module ABI versions:
[   154.436]     X.Org ANSI C Emulation: 0.4
[   154.436]     X.Org Video Driver: 20.0
[   154.436]     X.Org XInput driver : 22.1
[   154.436]     X.Org Server Extension : 9.0
[   154.437] (++) using VT number 7

[   154.437] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[   154.438] (II) xfree86: Adding drm device (/dev/dri/card1)
[   154.438] (II) xfree86: Adding drm device (/dev/dri/card0)
[   154.439] (--) PCI:*(0:0:2:0) 8086:0166:144d:c652 rev 9, Mem @ 0xdb000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[   154.439] (--) PCI: (0:1:0:0) 10de:1058:144d:c652 rev 161, Mem @ 0xda000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @ 0x00003000/128
[   154.439] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   154.439] (II) "glx" will be loaded by default.
[   154.439] (II) LoadModule: "glx"
[   154.440] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   154.443] (II) Module glx: vendor="NVIDIA Corporation"
[   154.443]     compiled for 4.0.2, module version = 1.0.0
[   154.444]     Module class: X.Org Server Extension
[   154.444] (II) NVIDIA GLX Module  367.57  Mon Oct  3 20:28:17 PDT 2016
[   154.444] (II) LoadModule: "nvidia"
[   154.444] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   154.444] (II) Module nvidia: vendor="NVIDIA Corporation"
[   154.444]     compiled for 4.0.2, module version = 1.0.0
[   154.444]     Module class: X.Org Video Driver
[   154.444] (II) LoadModule: "modesetting"
[   154.444] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   154.444] (II) Module modesetting: vendor="X.Org Foundation"
[   154.444]     compiled for 1.18.4, module version = 1.18.4
[   154.444]     Module class: X.Org Video Driver
[   154.444]     ABI class: X.Org Video Driver, version 20.0
[   154.444] (II) NVIDIA dlloader X Driver  367.57  Mon Oct  3 20:03:48 PDT 2016
[   154.444] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   154.444] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   154.444] (II) Loading sub module "fb"
[   154.444] (II) LoadModule: "fb"
[   154.445] (II) Loading /usr/lib/xorg/modules/libfb.so
[   154.445] (II) Module fb: vendor="X.Org Foundation"
[   154.445]     compiled for 1.18.4, module version = 1.0.0
[   154.445]     ABI class: X.Org ANSI C Emulation, version 0.4
[   154.445] (II) Loading sub module "wfb"
[   154.445] (II) LoadModule: "wfb"
[   154.445] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   154.445] (II) Module wfb: vendor="X.Org Foundation"
[   154.445]     compiled for 1.18.4, module version = 1.0.0
[   154.445]     ABI class: X.Org ANSI C Emulation, version 0.4
[   154.445] (II) Loading sub module "ramdac"
[   154.445] (II) LoadModule: "ramdac"
[   154.445] (II) Module "ramdac" already built-in
[   154.446] (II) modeset(G0): using drv /dev/dri/card0
[   154.446] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[   154.446] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   154.446] (==) NVIDIA(0): RGB weight 888
[   154.446] (==) NVIDIA(0): Default visual is TrueColor
[   154.446] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   154.446] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[   154.446] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[   154.446] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[   154.446] (**) NVIDIA(0): Enabling 2D acceleration
[   154.571] (II) NVIDIA(0): NVIDIA GPU GeForce 610M (GF119) at PCI:1:0:0 (GPU-0)
[   154.571] (--) NVIDIA(0): Memory: 1048576 kBytes
[   154.571] (--) NVIDIA(0): VideoBIOS: 75.19.54.00.06
[   154.571] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   154.571] (II) NVIDIA(0): Validated MetaModes:
[   154.571] (II) NVIDIA(0):     "NULL"
[   154.571] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[   154.571] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[   154.571] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[   154.571] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[   154.571] (**) modeset(G0): Option "AccelMethod" "None"
[   154.571] (==) modeset(G0): RGB weight 888
[   154.571] (==) modeset(G0): Default visual is TrueColor
[   154.571] (**) modeset(G0): glamor disabled
[   154.571] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[   154.572] (II) modeset(G0): Output LVDS-1-1 has no monitor section
[   154.573] (II) modeset(G0): Output VGA-1-1 has no monitor section
[   154.573] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[   154.573] (II) modeset(G0): Output DP-1-1 has no monitor section
[   154.573] (II) modeset(G0): EDID for output LVDS-1-1
[   154.573] (II) modeset(G0): Manufacturer: SEC  Model: 384a  Serial#: 0
[   154.573] (II) modeset(G0): Year: 2011  Week: 0
[   154.573] (II) modeset(G0): EDID Version: 1.3
[   154.573] (II) modeset(G0): Digital Display Input
[   154.573] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[   154.573] (II) modeset(G0): Gamma: 2.20
[   154.573] (II) modeset(G0): No DPMS capabilities specified
[   154.573] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   154.573] (II) modeset(G0): First detailed timing is preferred mode
[   154.573] (II) modeset(G0): redX: 0.615 redY: 0.355   greenX: 0.355 greenY: 0.610
[   154.573] (II) modeset(G0): blueX: 0.150 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[   154.573] (II) modeset(G0): Manufacturer's mask: 0
[   154.573] (II) modeset(G0): Supported detailed timing:
[   154.573] (II) modeset(G0): clock: 70.7 MHz   Image Size:  344 x 194 mm
[   154.573] (II) modeset(G0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[   154.573] (II) modeset(G0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 792 v_border: 0
[   154.573] (II) modeset(G0): Unknown vendor-specific block f
[   154.574] (II) modeset(G0):  SAMSUNG
[   154.574] (II) modeset(G0):  LTN156AT248
[   154.574] (II) modeset(G0): EDID (in hex):
[   154.574] (II) modeset(G0):     00ffffffffffff004ca34a3800000000
[   154.574] (II) modeset(G0):     00150103802213780a81a59d5b5b9c26
[   154.574] (II) modeset(G0):     19505400000001010101010101010101
[   154.574] (II) modeset(G0):     0101010101019e1b5678500018303020
[   154.574] (II) modeset(G0):     250058c2100000190000000f00000000
[   154.574] (II) modeset(G0):     00000000001eb4021500000000fe0053
[   154.574] (II) modeset(G0):     414d53554e470a2020202020000000fe
[   154.574] (II) modeset(G0):     004c544e31353641543234380a2000c3
[   154.574] (II) modeset(G0): Printing probed modes for output LVDS-1-1
[   154.574] (II) modeset(G0): Modeline "1366x768"x60.1   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz eP)
[   154.574] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[   154.574] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[   154.574] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[   154.574] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[   154.574] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[   154.574] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[   154.574] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[   154.574] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[   154.574] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[   154.574] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[   154.574] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[   154.574] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[   154.574] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[   154.574] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[   154.574] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[   154.574] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[   154.574] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[   154.574] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[   154.574] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[   154.574] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[   154.574] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[   154.574] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[   154.574] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[   154.574] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[   154.574] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[   154.574] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[   154.574] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[   154.575] (II) modeset(G0): EDID for output VGA-1-1
[   154.575] (II) modeset(G0): EDID for output HDMI-1-1
[   154.576] (II) modeset(G0): EDID for output DP-1-1
[   154.576] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   154.576] (==) modeset(G0): DPI set to (96, 96)
[   154.576] (II) Loading sub module "fb"
[   154.576] (II) LoadModule: "fb"
[   154.576] (II) Loading /usr/lib/xorg/modules/libfb.so
[   154.576] (II) Module fb: vendor="X.Org Foundation"
[   154.576]     compiled for 1.18.4, module version = 1.0.0
[   154.576]     ABI class: X.Org ANSI C Emulation, version 0.4
[   154.576] (II) Loading sub module "shadow"
[   154.576] (II) LoadModule: "shadow"
[   154.576] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   154.576] (II) Module shadow: vendor="X.Org Foundation"
[   154.576]     compiled for 1.18.4, module version = 1.1.0
[   154.576]     ABI class: X.Org ANSI C Emulation, version 0.4
[   154.576] (--) Depth 24 pixmap format is 32 bpp
[   154.576] (==) modeset(G0): Backing store enabled
[   154.576] (==) modeset(G0): Silken mouse enabled
[   154.577] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   154.577] (==) modeset(G0): DPMS enabled
[   154.577] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[   154.577] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[   155.121] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[   155.121] (II) NVIDIA:     access.
[   155.150] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[   155.150] (II) NVIDIA(0): Setting mode "NULL"
[   155.154] (==) NVIDIA(0): Disabling shared memory pixmaps
[   155.154] (==) NVIDIA(0): Backing store enabled
[   155.154] (==) NVIDIA(0): Silken mouse enabled
[   155.154] (==) NVIDIA(0): DPMS enabled
[   155.155] (II) Loading sub module "dri2"
[   155.155] (II) LoadModule: "dri2"
[   155.155] (II) Module "dri2" already built-in
[   155.155] (II) NVIDIA(0): [DRI2] Setup complete
[   155.155] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   155.155] (--) RandR disabled
[   155.161] (II) SELinux: Disabled on system
[   155.161] (II) Initializing extension GLX
[   155.161] (II) Indirect GLX disabled.
[   155.162] (II) modeset(G0): Damage tracking initialized
[   155.213] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   155.213] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   155.213] (II) LoadModule: "evdev"
[   155.214] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   155.214] (II) Module evdev: vendor="X.Org Foundation"
[   155.214]     compiled for 1.18.1, module version = 2.10.1
[   155.214]     Module class: X.Org XInput Driver
[   155.214]     ABI class: X.Org XInput driver, version 22.1
[   155.214] (II) Using input driver 'evdev' for 'Power Button'
[   155.214] (**) Power Button: always reports core events
[   155.214] (**) evdev: Power Button: Device: "/dev/input/event2"
[   155.214] (--) evdev: Power Button: Vendor 0 Product 0x1
[   155.214] (--) evdev: Power Button: Found keys
[   155.214] (II) evdev: Power Button: Configuring as keyboard
[   155.214] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   155.214] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   155.214] (**) Option "xkb_rules" "evdev"
[   155.214] (**) Option "xkb_model" "pc105"
[   155.214] (**) Option "xkb_layout" "hu"
[   155.235] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[   155.235] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   155.235] (II) Using input driver 'evdev' for 'Video Bus'
[   155.235] (**) Video Bus: always reports core events
[   155.235] (**) evdev: Video Bus: Device: "/dev/input/event7"
[   155.236] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   155.236] (--) evdev: Video Bus: Found keys
[   155.236] (II) evdev: Video Bus: Configuring as keyboard
[   155.236] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input9/event7"
[   155.236] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   155.236] (**) Option "xkb_rules" "evdev"
[   155.236] (**) Option "xkb_model" "pc105"
[   155.236] (**) Option "xkb_layout" "hu"
[   155.236] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   155.236] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   155.236] (II) Using input driver 'evdev' for 'Video Bus'
[   155.236] (**) Video Bus: always reports core events
[   155.236] (**) evdev: Video Bus: Device: "/dev/input/event5"
[   155.236] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   155.236] (--) evdev: Video Bus: Found keys
[   155.236] (II) evdev: Video Bus: Configuring as keyboard
[   155.236] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:39/LNXVIDEO:00/input/input7/event5"
[   155.236] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   155.236] (**) Option "xkb_rules" "evdev"
[   155.236] (**) Option "xkb_model" "pc105"
[   155.236] (**) Option "xkb_layout" "hu"
[   155.237] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   155.237] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   155.237] (II) Using input driver 'evdev' for 'Power Button'
[   155.237] (**) Power Button: always reports core events
[   155.237] (**) evdev: Power Button: Device: "/dev/input/event1"
[   155.237] (--) evdev: Power Button: Vendor 0 Product 0x1
[   155.237] (--) evdev: Power Button: Found keys
[   155.237] (II) evdev: Power Button: Configuring as keyboard
[   155.237] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   155.237] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[   155.237] (**) Option "xkb_rules" "evdev"
[   155.237] (**) Option "xkb_model" "pc105"
[   155.237] (**) Option "xkb_layout" "hu"
[   155.238] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   155.238] (II) No input driver specified, ignoring this device.
[   155.238] (II) This device may have been added with another device file.
[   155.238] (II) config/udev: Adding input device DaKai 2.4G RX (/dev/input/event4)
[   155.238] (**) DaKai 2.4G RX: Applying InputClass "evdev keyboard catchall"
[   155.238] (II) Using input driver 'evdev' for 'DaKai 2.4G RX'
[   155.239] (**) DaKai 2.4G RX: always reports core events
[   155.239] (**) evdev: DaKai 2.4G RX: Device: "/dev/input/event4"
[   155.239] (--) evdev: DaKai 2.4G RX: Vendor 0xe8f Product 0xa7
[   155.239] (--) evdev: DaKai 2.4G RX: Found keys
[   155.239] (II) evdev: DaKai 2.4G RX: Configuring as keyboard
[   155.239] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:0E8F:00A7.0001/input/input6/event4"
[   155.239] (II) XINPUT: Adding extended input device "DaKai 2.4G RX" (type: KEYBOARD, id 10)
[   155.239] (**) Option "xkb_rules" "evdev"
[   155.239] (**) Option "xkb_model" "pc105"
[   155.239] (**) Option "xkb_layout" "hu"
[   155.239] (II) config/udev: Adding input device DaKai 2.4G RX (/dev/input/event6)
[   155.239] (**) DaKai 2.4G RX: Applying InputClass "evdev pointer catchall"
[   155.239] (**) DaKai 2.4G RX: Applying InputClass "evdev keyboard catchall"
[   155.239] (II) Using input driver 'evdev' for 'DaKai 2.4G RX'
[   155.239] (**) DaKai 2.4G RX: always reports core events
[   155.239] (**) evdev: DaKai 2.4G RX: Device: "/dev/input/event6"
[   155.240] (--) evdev: DaKai 2.4G RX: Vendor 0xe8f Product 0xa7
[   155.240] (--) evdev: DaKai 2.4G RX: Found 9 mouse buttons
[   155.240] (--) evdev: DaKai 2.4G RX: Found scroll wheel(s)
[   155.240] (--) evdev: DaKai 2.4G RX: Found relative axes
[   155.240] (--) evdev: DaKai 2.4G RX: Found x and y relative axes
[   155.240] (--) evdev: DaKai 2.4G RX: Found absolute axes
[   155.240] (II) evdev: DaKai 2.4G RX: Forcing absolute x/y axes to exist.
[   155.240] (--) evdev: DaKai 2.4G RX: Found keys
[   155.240] (II) evdev: DaKai 2.4G RX: Configuring as mouse
[   155.240] (II) evdev: DaKai 2.4G RX: Configuring as keyboard
[   155.240] (II) evdev: DaKai 2.4G RX: Adding scrollwheel support
[   155.240] (**) evdev: DaKai 2.4G RX: YAxisMapping: buttons 4 and 5
[   155.240] (**) evdev: DaKai 2.4G RX: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   155.240] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/0003:0E8F:00A7.0002/input/input8/event6"
[   155.240] (II) XINPUT: Adding extended input device "DaKai 2.4G RX" (type: KEYBOARD, id 11)
[   155.240] (**) Option "xkb_rules" "evdev"
[   155.240] (**) Option "xkb_model" "pc105"
[   155.240] (**) Option "xkb_layout" "hu"
[   155.240] (II) evdev: DaKai 2.4G RX: initialized for relative axes.
[   155.240] (WW) evdev: DaKai 2.4G RX: ignoring absolute axes.
[   155.240] (**) DaKai 2.4G RX: (accel) keeping acceleration scheme 1
[   155.240] (**) DaKai 2.4G RX: (accel) acceleration profile 0
[   155.240] (**) DaKai 2.4G RX: (accel) acceleration factor: 2.000
[   155.240] (**) DaKai 2.4G RX: (accel) acceleration threshold: 4
[   155.241] (II) config/udev: Adding input device DaKai 2.4G RX (/dev/input/mouse0)
[   155.241] (II) No input driver specified, ignoring this device.
[   155.241] (II) This device may have been added with another device file.
[   155.241] (II) config/udev: Adding input device WebCam SC-03FFL11939N (/dev/input/event12)
[   155.241] (**) WebCam SC-03FFL11939N: Applying InputClass "evdev keyboard catchall"
[   155.241] (II) Using input driver 'evdev' for 'WebCam SC-03FFL11939N'
[   155.241] (**) WebCam SC-03FFL11939N: always reports core events
[   155.241] (**) evdev: WebCam SC-03FFL11939N: Device: "/dev/input/event12"
[   155.241] (--) evdev: WebCam SC-03FFL11939N: Vendor 0x2232 Product 0x1028
[   155.241] (--) evdev: WebCam SC-03FFL11939N: Found keys
[   155.241] (II) evdev: WebCam SC-03FFL11939N: Configuring as keyboard
[   155.241] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input13/event12"
[   155.241] (II) XINPUT: Adding extended input device "WebCam SC-03FFL11939N" (type: KEYBOARD, id 12)
[   155.241] (**) Option "xkb_rules" "evdev"
[   155.241] (**) Option "xkb_model" "pc105"
[   155.241] (**) Option "xkb_layout" "hu"
[   155.242] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[   155.242] (II) No input driver specified, ignoring this device.
[   155.242] (II) This device may have been added with another device file.
[   155.242] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[   155.242] (II) No input driver specified, ignoring this device.
[   155.242] (II) This device may have been added with another device file.
[   155.242] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[   155.242] (II) No input driver specified, ignoring this device.
[   155.242] (II) This device may have been added with another device file.
[   155.243] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   155.243] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   155.243] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   155.243] (**) AT Translated Set 2 keyboard: always reports core events
[   155.243] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   155.243] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   155.243] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   155.243] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   155.243] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   155.243] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[   155.243] (**) Option "xkb_rules" "evdev"
[   155.243] (**) Option "xkb_model" "pc105"
[   155.243] (**) Option "xkb_layout" "hu"
[   155.243] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[   155.243] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[   155.243] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[   155.243] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[   155.243] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[   155.243] (II) LoadModule: "synaptics"
[   155.244] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   155.244] (II) Module synaptics: vendor="X.Org Foundation"
[   155.244]     compiled for 1.18.1, module version = 1.8.2
[   155.244]     Module class: X.Org XInput Driver
[   155.244]     ABI class: X.Org XInput driver, version 22.1
[   155.244] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[   155.244] (**) ETPS/2 Elantech Touchpad: always reports core events
[   155.244] (**) Option "Device" "/dev/input/event8"
[   155.296] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[   155.296] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 31)
[   155.296] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1400 (res 31)
[   155.296] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[   155.296] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[   155.296] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[   155.296] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[   155.296] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   155.296] (**) ETPS/2 Elantech Touchpad: always reports core events
[   155.320] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event8"
[   155.320] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[   155.320] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[   155.320] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[   155.320] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.061
[   155.320] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[   155.320] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[   155.320] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[   155.320] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[   155.320] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   155.321] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[   155.321] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"


```
cat .xsession-errors:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: update-notifier-crash (/var/crash/_usr_bin_xfwm4.1000.crash) main process (1961) terminated with status 139
upstart: update-notifier-crash (/var/crash/_usr_bin_audacity.1000.crash) main process (1957) terminated with status 139
upstart: update-notifier-crash (/var/crash/_usr_bin_parole.1000.crash) main process (1960) terminated with status 139
upstart: update-notifier-crash (/var/crash/_usr_bin_gnome-software.1000.crash) main process (1959) terminated with status 139
upstart: update-notifier-crash (/var/crash/_usr_share_apport_apport-gtk.1000.crash) main process (2116) terminated with status 139
upstart: update-notifier-crash (/var/crash/_usr_bin_blueman-applet.1000.crash) main process (2163) terminated with status 139
upstart: update-notifier-crash (/var/crash/_usr_share_apport_apport-gtk.0.crash) main process (2302) terminated with status 1


```
with nvidia-smi
```
Sun Dec 11 17:34:34 2016       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 367.57                 Driver Version: 367.57                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce 610M        Off  | 0000:01:00.0     N/A |                  N/A |
| N/A   55C    P8    N/A /  N/A |      1MiB /   964MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0                  Not Supported                                         |
+-----------------------------------------------------------------------------+


```
reverting to nvidia current gave birth to the attached batch of errors affecting various system aspects

i've got a feeling we're slowly getting to the bottom 'o this

---

### Post by mr.man2 on 2016-12-11
hmmm i rerouted where i got libdrm-nouveau2:i386 from. it's in the basic wine install, should i give up on using it in the future?

---

### Post by Bashing-om on 2016-12-11
mr.man2; Hey;

It Is Supposed to just work !

It is not, and we look'n to find that reason why . 
Per the log file X is in a happy state .. no problems with building and loading the 367 version driver .
But the GUI just pukes !

Now we have "primus" installed, Did you purge nvidia-prime ? 
There can be only one to control the graphic's sets .
> 
Primus is currently intended to be used alongside Bumblebee and provides a
 drop-in replacement for optirun (i.e. "primusrun").

Depends: bumblebee, socat, primus-libs

----------------------
As wine needs " libdrm-nouveau2:i386 " and removing it does not help, may as well re-install that lib .

As is now, all I can think of to do is make sure we have no conflicts.
lightdm as the (D)isplay (M)anager ? and then after possible cleanup and a reboot;
see what lightdm's logs have to say :
```

cat /var/log/lightdm/lightdm.log
cat /var/log/lightdm/x-0-greeter.log

```

[INDENT][INDENT]still
[INDENT][INDENT][INDENT]a mystery to me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-12-12
This user finally got it to work.
[https://ubuntuforums.org/showthread.php?t=2344901&p=13579995#post13579995](https://ubuntuforums.org/showthread.php?t=2344901&p=13579995#post13579995)

---

### Post by mr.man2 on 2016-12-14
Hey Oldfred, 

thanks for the tip, i've tried the proposed, omitting the gnome-desktop purge & re-install given that i wasn't sporting it, but nouveau couldn't handle my GPU :( i've then tried to put gnome in the equation, unfortunately without impact. moreover i wasn't able to remove some traces of gnome, in my distaste i went nuclear once more && reinstalled the Xenial Ubuntu, where i executed the same steps without success.

Dear Bashing-Om,

So i'm back with Ubuntu & judging from the preferences i've implemented to mimic Unity in xfce, i've probably grown overly fond of it. But to cut back to the chase the issue persists still. I've used 
```
sudo apt install nvidia-367 primus
``` to fetch the driver to get the GPU working. at first it seemed to work, bringing me a functional login screen. After typing my pwd in, it got stuck in a cycle & brought the login screen back ad infinitum. I noted that installing only nvidia-367 & primus downloads bumblebee & bbswitch so i edited the bumblebee.conf file like i used to when it worked way back. So i pointed all entities in the .conf file to nvidia-367 & not nvidia-current with the boot ending with a black screen, just like old times, except boot sequence this time gave me NVRM: xid 32 (Invalid or corrupted push buffer stream). i also got the following
xsession errors:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (1788) terminated with status 1
upstart: unity-settings-daemon main process (1771) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: logrotate main process (1637) killed by TERM signal
upstart: update-notifier-crash (/var/crash/_usr_bin_compiz.1000.crash) main process (1693) killed by TERM signal
upstart: bamfdaemon main process (1772) killed by TERM signal
upstart: hud main process (1794) killed by TERM signal
upstart: unity-panel-service main process (1792) killed by TERM signal
upstart: job indicator-bluetooth failed to stop
upstart: job window-stack-bridge failed to stop
```
xorg.0.log
```
[    32.282] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    32.282] X Protocol Version 11, Revision 0
[    32.282] Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
[    32.282] Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
[    32.282] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro text
[    32.282] Build Date: 02 November 2016  10:06:10PM
[    32.282] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[    32.282] Current version of pixman: 0.33.6
[    32.282]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    32.282] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.282] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 18:52:51 2016
[    32.484] (==) Using config file: "/etc/X11/xorg.conf"
[    32.484] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.878] (==) ServerLayout "layout"
[    32.878] (**) |-->Screen "nvidia" (0)
[    32.878] (**) |   |-->Monitor "<default monitor>"
[    32.930] (**) |   |-->Device "nvidia"
[    32.931] (**) |   |-->GPUDevice "nvidia"
[    32.931] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    32.931] (**) |-->Inactive Device "intel"
[    32.931] (==) Automatically adding devices
[    32.931] (==) Automatically enabling devices
[    32.931] (==) Automatically adding GPU devices
[    32.931] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    33.137] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.137]     Entry deleted from font path.
[    33.137] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.137]     Entry deleted from font path.
[    33.137] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.137]     Entry deleted from font path.
[    33.183] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.183]     Entry deleted from font path.
[    33.183] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.183]     Entry deleted from font path.
[    33.183] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    33.183] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.183] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.215] (II) Loader magic: 0x55f9a5d2ddc0
[    33.215] (II) Module ABI versions:
[    33.215]     X.Org ANSI C Emulation: 0.4
[    33.215]     X.Org Video Driver: 20.0
[    33.215]     X.Org XInput driver : 22.1
[    33.215]     X.Org Server Extension : 9.0
[    33.216] (++) using VT number 7

[    33.216] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    33.216] (II) xfree86: Adding drm device (/dev/dri/card0)
[    33.216] (II) xfree86: Adding drm device (/dev/dri/card1)
[    33.217] (--) PCI:*(0:0:2:0) 8086:0166:144d:c652 rev 9, Mem @ 0xdb000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[    33.217] (--) PCI: (0:1:0:0) 10de:1058:144d:c652 rev 161, Mem @ 0xda000000/16777216, 0xd0000000/134217728, 0xd8000000/33554432, I/O @ 0x00003000/128
[    33.217] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    33.217] (II) "glx" will be loaded by default.
[    33.217] (II) LoadModule: "glx"
[    33.292] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    35.387] (II) Module glx: vendor="NVIDIA Corporation"
[    35.387]     compiled for 4.0.2, module version = 1.0.0
[    35.387]     Module class: X.Org Server Extension
[    35.398] (II) NVIDIA GLX Module  367.57  Mon Oct  3 20:28:17 PDT 2016
[    35.406] (II) LoadModule: "nvidia"
[    35.406] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    35.488] (II) Module nvidia: vendor="NVIDIA Corporation"
[    35.488]     compiled for 4.0.2, module version = 1.0.0
[    35.488]     Module class: X.Org Video Driver
[    35.504] (II) LoadModule: "modesetting"
[    35.565] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    35.575] (II) Module modesetting: vendor="X.Org Foundation"
[    35.575]     compiled for 1.18.4, module version = 1.18.4
[    35.575]     Module class: X.Org Video Driver
[    35.575]     ABI class: X.Org Video Driver, version 20.0
[    35.575] (II) NVIDIA dlloader X Driver  367.57  Mon Oct  3 20:03:48 PDT 2016
[    35.575] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    35.576] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    35.594] (II) Loading sub module "fb"
[    35.594] (II) LoadModule: "fb"
[    35.594] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.596] (II) Module fb: vendor="X.Org Foundation"
[    35.596]     compiled for 1.18.4, module version = 1.0.0
[    35.596]     ABI class: X.Org ANSI C Emulation, version 0.4
[    35.596] (II) Loading sub module "wfb"
[    35.596] (II) LoadModule: "wfb"
[    35.596] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    35.615] (II) Module wfb: vendor="X.Org Foundation"
[    35.615]     compiled for 1.18.4, module version = 1.0.0
[    35.615]     ABI class: X.Org ANSI C Emulation, version 0.4
[    35.615] (II) Loading sub module "ramdac"
[    35.615] (II) LoadModule: "ramdac"
[    35.615] (II) Module "ramdac" already built-in
[    35.629] (II) modeset(G0): using drv /dev/dri/card1
[    35.629] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    35.629] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    35.629] (==) NVIDIA(0): RGB weight 888
[    35.629] (==) NVIDIA(0): Default visual is TrueColor
[    35.629] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    35.630] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    35.630] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    35.630] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    35.630] (**) NVIDIA(0): Enabling 2D acceleration
[    35.747] (II) NVIDIA(0): NVIDIA GPU GeForce 610M (GF119) at PCI:1:0:0 (GPU-0)
[    35.747] (--) NVIDIA(0): Memory: 1048576 kBytes
[    35.747] (--) NVIDIA(0): VideoBIOS: 75.19.54.00.06
[    35.747] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    35.747] (II) NVIDIA(0): Validated MetaModes:
[    35.747] (II) NVIDIA(0):     "NULL"
[    35.747] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    35.747] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    35.747] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    35.747] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    35.747] (**) modeset(G0): Option "AccelMethod" "None"
[    35.747] (==) modeset(G0): RGB weight 888
[    35.747] (==) modeset(G0): Default visual is TrueColor
[    35.747] (**) modeset(G0): glamor disabled
[    35.747] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    35.748] (II) modeset(G0): Output LVDS-1-1 has no monitor section
[    35.748] (II) modeset(G0): Output VGA-1-1 has no monitor section
[    35.749] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[    35.749] (II) modeset(G0): Output DP-1-1 has no monitor section
[    35.749] (II) modeset(G0): EDID for output LVDS-1-1
[    35.749] (II) modeset(G0): Manufacturer: SEC  Model: 384a  Serial#: 0
[    35.749] (II) modeset(G0): Year: 2011  Week: 0
[    35.749] (II) modeset(G0): EDID Version: 1.3
[    35.749] (II) modeset(G0): Digital Display Input
[    35.749] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    35.749] (II) modeset(G0): Gamma: 2.20
[    35.749] (II) modeset(G0): No DPMS capabilities specified
[    35.749] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    35.749] (II) modeset(G0): First detailed timing is preferred mode
[    35.749] (II) modeset(G0): redX: 0.615 redY: 0.355   greenX: 0.355 greenY: 0.610
[    35.749] (II) modeset(G0): blueX: 0.150 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    35.749] (II) modeset(G0): Manufacturer's mask: 0
[    35.749] (II) modeset(G0): Supported detailed timing:
[    35.749] (II) modeset(G0): clock: 70.7 MHz   Image Size:  344 x 194 mm
[    35.749] (II) modeset(G0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    35.749] (II) modeset(G0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 792 v_border: 0
[    35.749] (II) modeset(G0): Unknown vendor-specific block f
[    35.749] (II) modeset(G0):  SAMSUNG
[    35.749] (II) modeset(G0):  LTN156AT248
[    35.749] (II) modeset(G0): EDID (in hex):
[    35.749] (II) modeset(G0):     00ffffffffffff004ca34a3800000000
[    35.749] (II) modeset(G0):     00150103802213780a81a59d5b5b9c26
[    35.749] (II) modeset(G0):     19505400000001010101010101010101
[    35.749] (II) modeset(G0):     0101010101019e1b5678500018303020
[    35.749] (II) modeset(G0):     250058c2100000190000000f00000000
[    35.749] (II) modeset(G0):     00000000001eb4021500000000fe0053
[    35.749] (II) modeset(G0):     414d53554e470a2020202020000000fe
[    35.749] (II) modeset(G0):     004c544e31353641543234380a2000c3
[    35.749] (II) modeset(G0): Printing probed modes for output LVDS-1-1
[    35.749] (II) modeset(G0): Modeline "1366x768"x60.1   70.70  1366 1414 1446 1486  768 770 775 792 -hsync -vsync (47.6 kHz eP)
[    35.749] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    35.749] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    35.749] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    35.749] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    35.749] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    35.749] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    35.749] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    35.749] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    35.749] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    35.749] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    35.749] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    35.749] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    35.749] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    35.749] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    35.749] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    35.749] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    35.749] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    35.749] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    35.749] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    35.749] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    35.749] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    35.749] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    35.749] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    35.749] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    35.749] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    35.749] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    35.749] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    35.750] (II) modeset(G0): EDID for output VGA-1-1
[    35.751] (II) modeset(G0): EDID for output HDMI-1-1
[    35.751] (II) modeset(G0): EDID for output DP-1-1
[    35.751] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    35.751] (==) modeset(G0): DPI set to (96, 96)
[    35.751] (II) Loading sub module "fb"
[    35.751] (II) LoadModule: "fb"
[    35.751] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.751] (II) Module fb: vendor="X.Org Foundation"
[    35.751]     compiled for 1.18.4, module version = 1.0.0
[    35.751]     ABI class: X.Org ANSI C Emulation, version 0.4
[    35.751] (II) Loading sub module "shadow"
[    35.751] (II) LoadModule: "shadow"
[    35.751] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    35.769] (II) Module shadow: vendor="X.Org Foundation"
[    35.769]     compiled for 1.18.4, module version = 1.1.0
[    35.769]     ABI class: X.Org ANSI C Emulation, version 0.4
[    35.769] (--) Depth 24 pixmap format is 32 bpp
[    35.786] (==) modeset(G0): Backing store enabled
[    35.786] (==) modeset(G0): Silken mouse enabled
[    35.786] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    35.797] (==) modeset(G0): DPMS enabled
[    35.797] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    35.797] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    36.341] (II) NVIDIA: Using 12288.00 MB of virtual memory for indirect memory
[    36.341] (II) NVIDIA:     access.
[    36.378] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    36.385] (II) NVIDIA(0): Setting mode "NULL"
[    36.531] (==) NVIDIA(0): Disabling shared memory pixmaps
[    36.531] (==) NVIDIA(0): Backing store enabled
[    36.531] (==) NVIDIA(0): Silken mouse enabled
[    36.531] (==) NVIDIA(0): DPMS enabled
[    36.572] (II) Loading sub module "dri2"
[    36.572] (II) LoadModule: "dri2"
[    36.573] (II) Module "dri2" already built-in
[    36.573] (II) NVIDIA(0): [DRI2] Setup complete
[    36.573] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    36.573] (--) RandR disabled
[    36.610] (II) SELinux: Disabled on system
[    36.654] (II) Initializing extension GLX
[    36.654] (II) Indirect GLX disabled.
[    36.655] (II) modeset(G0): Damage tracking initialized
[    37.983] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    37.983] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.983] (II) LoadModule: "evdev"
[    38.048] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    38.083] (II) Module evdev: vendor="X.Org Foundation"
[    38.083]     compiled for 1.18.1, module version = 2.10.1
[    38.083]     Module class: X.Org XInput Driver
[    38.083]     ABI class: X.Org XInput driver, version 22.1
[    38.083] (II) Using input driver 'evdev' for 'Power Button'
[    38.083] (**) Power Button: always reports core events
[    38.084] (**) evdev: Power Button: Device: "/dev/input/event2"
[    38.084] (--) evdev: Power Button: Vendor 0 Product 0x1
[    38.084] (--) evdev: Power Button: Found keys
[    38.084] (II) evdev: Power Button: Configuring as keyboard
[    38.084] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    38.084] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    38.084] (**) Option "xkb_rules" "evdev"
[    38.084] (**) Option "xkb_model" "pc105"
[    38.084] (**) Option "xkb_layout" "hu"
[    38.128] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    38.128] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    38.128] (II) Using input driver 'evdev' for 'Video Bus'
[    38.128] (**) Video Bus: always reports core events
[    38.128] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    38.128] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    38.128] (--) evdev: Video Bus: Found keys
[    38.128] (II) evdev: Video Bus: Configuring as keyboard
[    38.128] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7/event5"
[    38.128] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    38.128] (**) Option "xkb_rules" "evdev"
[    38.128] (**) Option "xkb_model" "pc105"
[    38.128] (**) Option "xkb_layout" "hu"
[    38.129] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    38.129] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    38.129] (II) Using input driver 'evdev' for 'Video Bus'
[    38.129] (**) Video Bus: always reports core events
[    38.129] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    38.129] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    38.129] (--) evdev: Video Bus: Found keys
[    38.129] (II) evdev: Video Bus: Configuring as keyboard
[    38.129] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:39/LNXVIDEO:00/input/input6/event4"
[    38.129] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    38.129] (**) Option "xkb_rules" "evdev"
[    38.129] (**) Option "xkb_model" "pc105"
[    38.129] (**) Option "xkb_layout" "hu"
[    38.129] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    38.129] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    38.129] (II) Using input driver 'evdev' for 'Power Button'
[    38.129] (**) Power Button: always reports core events
[    38.129] (**) evdev: Power Button: Device: "/dev/input/event1"
[    38.129] (--) evdev: Power Button: Vendor 0 Product 0x1
[    38.129] (--) evdev: Power Button: Found keys
[    38.129] (II) evdev: Power Button: Configuring as keyboard
[    38.129] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    38.129] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    38.129] (**) Option "xkb_rules" "evdev"
[    38.129] (**) Option "xkb_model" "pc105"
[    38.129] (**) Option "xkb_layout" "hu"
[    38.129] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    38.129] (II) No input driver specified, ignoring this device.
[    38.129] (II) This device may have been added with another device file.
[    38.130] (II) config/udev: Adding input device WebCam SC-03FFL11939N (/dev/input/event10)
[    38.130] (**) WebCam SC-03FFL11939N: Applying InputClass "evdev keyboard catchall"
[    38.130] (II) Using input driver 'evdev' for 'WebCam SC-03FFL11939N'
[    38.130] (**) WebCam SC-03FFL11939N: always reports core events
[    38.130] (**) evdev: WebCam SC-03FFL11939N: Device: "/dev/input/event10"
[    38.130] (--) evdev: WebCam SC-03FFL11939N: Vendor 0x2232 Product 0x1028
[    38.130] (--) evdev: WebCam SC-03FFL11939N: Found keys
[    38.130] (II) evdev: WebCam SC-03FFL11939N: Configuring as keyboard
[    38.130] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input11/event10"
[    38.130] (II) XINPUT: Adding extended input device "WebCam SC-03FFL11939N" (type: KEYBOARD, id 10)
[    38.130] (**) Option "xkb_rules" "evdev"
[    38.130] (**) Option "xkb_model" "pc105"
[    38.130] (**) Option "xkb_layout" "hu"
[    38.130] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    38.131] (II) No input driver specified, ignoring this device.
[    38.131] (II) This device may have been added with another device file.
[    38.131] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event7)
[    38.131] (II) No input driver specified, ignoring this device.
[    38.131] (II) This device may have been added with another device file.
[    38.131] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[    38.131] (II) No input driver specified, ignoring this device.
[    38.131] (II) This device may have been added with another device file.
[    38.131] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    38.131] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    38.131] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    38.131] (**) AT Translated Set 2 keyboard: always reports core events
[    38.131] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    38.131] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    38.131] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    38.131] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    38.131] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    38.131] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    38.131] (**) Option "xkb_rules" "evdev"
[    38.131] (**) Option "xkb_model" "pc105"
[    38.131] (**) Option "xkb_layout" "hu"
[    38.132] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    38.132] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    38.132] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[    38.132] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    38.132] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    38.132] (II) LoadModule: "synaptics"
[    38.132] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    38.154] (II) Module synaptics: vendor="X.Org Foundation"
[    38.154]     compiled for 1.18.1, module version = 1.8.2
[    38.154]     Module class: X.Org XInput Driver
[    38.154]     ABI class: X.Org XInput driver, version 22.1
[    38.154] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    38.154] (**) ETPS/2 Elantech Touchpad: always reports core events
[    38.154] (**) Option "Device" "/dev/input/event6"
[    38.208] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    38.208] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2940 (res 31)
[    38.208] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1400 (res 31)
[    38.208] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    38.208] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    38.208] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    38.208] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    38.208] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    38.208] (**) ETPS/2 Elantech Touchpad: always reports core events
[    38.232] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event6"
[    38.232] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    38.232] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    38.232] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    38.232] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.061
[    38.232] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    38.232] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    38.232] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    38.232] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    38.232] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    38.232] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    38.232] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
```
gpu-manager.log
```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.4.0-53-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.4.0-53-generic/updates/dkms
Found nvidia module: nvidia_367_modeset.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? yes
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:166
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1058
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Found "/dev/dri/card1", driven by "i915"
output 0:
    card1-LVDS-1
Number of connected outputs for /dev/dri/card1: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
The number of cards has changed!
Has the system changed? Yes
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-367/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-367/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no
System configuration has changed
Intel IGP detected
Intel hybrid system
Nvidia driver version 367.57 detected
can't access /etc/prime-discrete
Warning: no settings for prime can be found in /etc/prime-discrete.
Trying to create new settings for prime. Path: /etc/prime-discrete
can't access /etc/X11/xorg.conf
Check failed
Removing xorg.conf. Path: /etc/X11/xorg.conf
Moved /etc/X11/xorg.conf to /etc/X11/xorg.conf.12142016
Regenerating xorg.conf. Path: /etc/X11/xorg.conf
No need to change the current bbswitch status
```
under lightdm i had the following
```
killer@szpiid:~$ ls /var/log/lightdm/lightdm.log  seat0-greeter.log  x-0.log


```
which gave [cont.]

---

### Post by mr.man2 on 2016-12-14
lightdm```
[+0.09s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.09s] DEBUG: Starting Light Display Manager 1.18.2, UID=0 PID=2338
[+0.09s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.09s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.09s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.09s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.09s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.09s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.09s] DEBUG: Registered seat module xlocal
[+0.09s] DEBUG: Registered seat module xremote
[+0.09s] DEBUG: Registered seat module unity
[+0.10s] DEBUG: Monitoring logind for seats
[+0.10s] DEBUG: New seat added from logind: seat0
[+0.10s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.10s] DEBUG: Seat seat0: Starting
[+0.10s] DEBUG: Seat seat0: Creating greeter session
[+0.29s] DEBUG: Seat seat0: Creating display server of type x
[+1.64s] DEBUG: Quitting Plymouth
[+1.66s] DEBUG: Using VT 7
[+1.66s] DEBUG: Seat seat0: Starting local X display on VT 7
[+1.66s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+1.66s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+1.66s] DEBUG: DisplayServer x-0: Launching X Server
[+1.66s] DEBUG: Launching process 2409: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+1.66s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+1.66s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+1.66s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.74s] DEBUG: Loading users from org.freedesktop.Accounts
[+1.74s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+6.76s] DEBUG: Got signal 10 from process 2409
[+6.76s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+6.76s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+6.78s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+6.78s] DEBUG: Session pid=2516: Started with service 'lightdm-greeter', username 'lightdm'
[+7.06s] DEBUG: Session pid=2516: Authentication complete with return value 0: Success
[+7.06s] DEBUG: Seat seat0: Session authenticated, running command
[+7.06s] DEBUG: Session pid=2516: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+7.06s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+7.06s] DEBUG: Session pid=2516: Logging to /var/log/lightdm/seat0-greeter.log
[+7.66s] DEBUG: Activating VT 7
[+7.66s] DEBUG: Activating login1 session c1
[+7.66s] DEBUG: Seat seat0 changes active session to c1
[+7.66s] DEBUG: Session c1 is already active
[+10.22s] DEBUG: Greeter connected version=1.18.2 resettable=false
[+11.64s] DEBUG: Greeter start authentication for killer
[+11.64s] DEBUG: Session pid=2733: Started with service 'lightdm', username 'killer'
[+11.82s] DEBUG: Session pid=2733: Got 1 message(s) from PAM
[+11.82s] DEBUG: Prompt greeter with 1 message(s)
[+13.28s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+33.27s] DEBUG: Continue authentication
[+33.28s] DEBUG: Session pid=2733: Authentication complete with return value 0: Success
[+33.28s] DEBUG: Authenticate result for user killer: Success
[+33.28s] DEBUG: User killer authorized
[+33.33s] DEBUG: Greeter requests default session
[+33.40s] DEBUG: Writing /home/killer/.dmrc
[+33.94s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+33.94s] DEBUG: Session pid=2516: Sending SIGTERM
[+33.97s] DEBUG: Session pid=2516: Exited with return value 0
[+33.97s] DEBUG: Seat seat0: Session stopped
[+33.97s] DEBUG: Seat seat0: Greeter stopped, running session
[+33.97s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+33.97s] DEBUG: Session pid=2733: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+33.97s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+33.97s] DEBUG: Session pid=2733: Logging to .xsession-errors
[+34.03s] DEBUG: Activating VT 7
[+34.03s] DEBUG: Activating login1 session c2
[+34.03s] DEBUG: Seat seat0 changes active session to c2
[+34.03s] DEBUG: Session c2 is already active
[+2317.92s] DEBUG: Session pid=2733: Terminated with signal 1
[+2317.92s] DEBUG: Seat seat0: Session stopped
[+2317.92s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+2317.92s] DEBUG: Sending signal 15 to process 2409
[+2317.94s] DEBUG: Got signal 15 from process 1
[+2317.94s] DEBUG: Caught Terminated signal, shutting down
[+2317.94s] DEBUG: Stopping display manager
[+2317.94s] DEBUG: Seat seat0: Stopping
[+2318.89s] DEBUG: Process 2409 exited with return value 0
[+2318.89s] DEBUG: DisplayServer x-0: X server stopped
[+2318.89s] DEBUG: Releasing VT 7
[+2318.89s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+2318.89s] DEBUG: Seat seat0: Display server stopped
[+2318.89s] DEBUG: Seat seat0: Stopped
[+2318.89s] DEBUG: Display manager stopped
[+2318.89s] DEBUG: Stopping daemon
[+2318.89s] DEBUG: Exiting with return value 0
[+0.05s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.18s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=851
[+0.18s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.18s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.18s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.18s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.18s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.18s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.18s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.18s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.18s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.18s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.18s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.18s] DEBUG: Registered seat module xlocal
[+0.18s] DEBUG: Registered seat module xremote
[+0.18s] DEBUG: Registered seat module unity
[+0.19s] DEBUG: Monitoring logind for seats
[+0.19s] DEBUG: New seat added from logind: seat0
[+0.19s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.19s] DEBUG: Seat seat0: Starting
[+0.19s] DEBUG: Seat seat0: Creating greeter session
[+0.42s] DEBUG: Seat seat0: Creating display server of type x
[+0.44s] DEBUG: Quitting Plymouth
[+0.46s] DEBUG: Using VT 7
[+0.46s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.46s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.46s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.46s] DEBUG: DisplayServer x-0: Launching X Server
[+0.46s] DEBUG: Launching process 862: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.46s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.46s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.46s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.58s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.67s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+9.20s] DEBUG: Got signal 10 from process 862
[+9.20s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+9.20s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+9.20s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+9.20s] DEBUG: Session pid=917: Started with service 'lightdm-greeter', username 'lightdm'
[+9.43s] DEBUG: Session pid=917: Authentication complete with return value 0: Success
[+9.43s] DEBUG: Seat seat0: Session authenticated, running command
[+9.43s] DEBUG: Session pid=917: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+9.43s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+9.43s] DEBUG: Session pid=917: Logging to /var/log/lightdm/seat0-greeter.log
[+9.82s] DEBUG: Activating VT 7
[+9.82s] DEBUG: Activating login1 session c1
[+9.82s] DEBUG: Seat seat0 changes active session to c1
[+9.82s] DEBUG: Session c1 is already active
[+12.84s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+15.05s] DEBUG: Greeter start authentication for killer
[+15.05s] DEBUG: Session pid=982: Started with service 'lightdm', username 'killer'
[+15.20s] DEBUG: Session pid=982: Got 1 message(s) from PAM
[+15.20s] DEBUG: Prompt greeter with 1 message(s)
[+17.98s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+168.19s] DEBUG: Continue authentication
[+168.22s] DEBUG: Session pid=982: Authentication complete with return value 0: Success
[+168.22s] DEBUG: Authenticate result for user killer: Success
[+168.22s] DEBUG: User killer authorized
[+168.22s] DEBUG: Greeter requests session ubuntu
[+168.22s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+168.22s] DEBUG: Session pid=917: Sending SIGTERM
[+168.24s] DEBUG: Session pid=917: Exited with return value 0
[+168.24s] DEBUG: Seat seat0: Session stopped
[+168.24s] DEBUG: Seat seat0: Greeter stopped, running session
[+168.24s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+168.25s] DEBUG: Session pid=982: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+168.25s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+168.25s] DEBUG: Session pid=982: Logging to .xsession-errors
[+168.50s] DEBUG: Activating VT 7
[+168.50s] DEBUG: Activating login1 session c2
[+168.50s] DEBUG: Seat seat0 changes active session to c2
[+168.50s] DEBUG: Session c2 is already active
[+246.44s] DEBUG: Seat seat0 changes active session to 
[+252.53s] DEBUG: Seat seat0 changes active session to 1
[+254.92s] DEBUG: Seat seat0 changes active session to c2
[+254.92s] DEBUG: Session c2 is already active
[+265.16s] DEBUG: Seat seat0 changes active session to 1
[+346.48s] DEBUG: Session pid=982: Terminated with signal 1
[+346.48s] DEBUG: Seat seat0: Session stopped
[+346.48s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+346.48s] DEBUG: Sending signal 15 to process 862
[+346.51s] DEBUG: Got signal 15 from process 1
[+346.54s] DEBUG: Caught Terminated signal, shutting down
[+346.54s] DEBUG: Stopping display manager
[+346.54s] DEBUG: Seat seat0: Stopping
[+346.54s] DEBUG: Process 862 exited with return value 0
[+346.54s] DEBUG: DisplayServer x-0: X server stopped
[+346.54s] DEBUG: Releasing VT 7
[+346.54s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+346.54s] DEBUG: Seat seat0: Display server stopped
[+346.54s] DEBUG: Seat seat0: Stopped
[+346.54s] DEBUG: Display manager stopped
[+346.55s] DEBUG: Stopping daemon
[+346.55s] DEBUG: Exiting with return value 0
[+0.16s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.26s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=766
[+0.26s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.26s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.26s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.26s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.26s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.26s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.26s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.26s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.26s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.26s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.26s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.26s] DEBUG: Registered seat module xlocal
[+0.26s] DEBUG: Registered seat module xremote
[+0.26s] DEBUG: Registered seat module unity
[+0.77s] DEBUG: Monitoring logind for seats
[+0.77s] DEBUG: New seat added from logind: seat0
[+0.77s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.77s] DEBUG: Seat seat0: Starting
[+0.77s] DEBUG: Seat seat0: Creating greeter session
[+0.77s] DEBUG: Seat seat0: Creating display server of type x
[+2.60s] DEBUG: Quitting Plymouth
[+2.63s] DEBUG: Using VT 7
[+2.63s] DEBUG: Seat seat0: Starting local X display on VT 7
[+2.63s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+2.63s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+2.63s] DEBUG: DisplayServer x-0: Launching X Server
[+2.63s] DEBUG: Launching process 853: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+2.63s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+2.63s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+2.63s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.74s] DEBUG: Loading users from org.freedesktop.Accounts
[+2.74s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+6.51s] DEBUG: Got signal 10 from process 853
[+6.51s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+6.51s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+6.52s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+6.52s] DEBUG: Session pid=892: Started with service 'lightdm-greeter', username 'lightdm'
[+6.55s] DEBUG: Session pid=892: Authentication complete with return value 0: Success
[+6.55s] DEBUG: Seat seat0: Session authenticated, running command
[+6.55s] DEBUG: Session pid=892: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+6.55s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+6.55s] DEBUG: Session pid=892: Logging to /var/log/lightdm/seat0-greeter.log
[+6.76s] DEBUG: Activating VT 7
[+6.76s] DEBUG: Activating login1 session c1
[+6.76s] DEBUG: Seat seat0 changes active session to c1
[+6.76s] DEBUG: Session c1 is already active
[+8.07s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+8.79s] DEBUG: Greeter start authentication for killer
[+8.79s] DEBUG: Session pid=950: Started with service 'lightdm', username 'killer'
[+8.80s] DEBUG: Session pid=950: Got 1 message(s) from PAM
[+8.80s] DEBUG: Prompt greeter with 1 message(s)
[+10.16s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+13.67s] DEBUG: Seat seat0 changes active session to 
[+16.04s] DEBUG: Seat seat0 changes active session to c1
[+16.04s] DEBUG: Session c1 is already active
[+20.87s] DEBUG: Continue authentication
[+20.88s] DEBUG: Session pid=950: Authentication complete with return value 0: Success
[+20.88s] DEBUG: Authenticate result for user killer: Success
[+20.88s] DEBUG: User killer authorized
[+20.88s] DEBUG: Greeter requests session ubuntu
[+20.88s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+20.88s] DEBUG: Session pid=892: Sending SIGTERM
[+20.89s] DEBUG: Session pid=892: Exited with return value 0
[+20.89s] DEBUG: Seat seat0: Session stopped
[+20.89s] DEBUG: Seat seat0: Greeter stopped, running session
[+20.89s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+20.90s] DEBUG: Session pid=950: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+20.90s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+20.90s] DEBUG: Session pid=950: Logging to .xsession-errors
[+21.09s] DEBUG: Activating VT 7
[+21.09s] DEBUG: Activating login1 session c2
[+21.10s] DEBUG: Seat seat0 changes active session to c2
[+21.10s] DEBUG: Session c2 is already active
[+35.20s] DEBUG: Seat seat0 changes active session to 
[+44.85s] DEBUG: Seat seat0 changes active session to 1
[+510.16s] DEBUG: Session pid=950: Terminated with signal 1
[+510.16s] DEBUG: Seat seat0: Session stopped
[+510.16s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+510.16s] DEBUG: Sending signal 15 to process 853
[+510.20s] DEBUG: Got signal 15 from process 1
[+510.20s] DEBUG: Caught Terminated signal, shutting down
[+510.20s] DEBUG: Stopping display manager
[+510.20s] DEBUG: Seat seat0: Stopping
[+510.24s] DEBUG: Process 853 exited with return value 0
[+510.24s] DEBUG: DisplayServer x-0: X server stopped
[+510.24s] DEBUG: Releasing VT 7
[+510.24s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+510.24s] DEBUG: Seat seat0: Display server stopped
[+510.24s] DEBUG: Seat seat0: Stopped
[+510.24s] DEBUG: Display manager stopped
[+510.24s] DEBUG: Stopping daemon
[+510.24s] DEBUG: Exiting with return value 0
[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.12s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1004
[+0.12s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.12s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.12s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.12s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.12s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.12s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.12s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.12s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.12s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.12s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.12s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.12s] DEBUG: Registered seat module xlocal
[+0.12s] DEBUG: Registered seat module xremote
[+0.12s] DEBUG: Registered seat module unity
[+0.68s] DEBUG: Monitoring logind for seats
[+0.68s] DEBUG: New seat added from logind: seat0
[+0.68s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.68s] DEBUG: Seat seat0: Starting
[+0.68s] DEBUG: Seat seat0: Creating greeter session
[+0.94s] DEBUG: Seat seat0: Creating display server of type x
[+0.94s] DEBUG: Using VT 7
[+0.94s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.94s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.94s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.94s] DEBUG: DisplayServer x-0: Launching X Server
[+0.94s] DEBUG: Launching process 1012: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.94s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.94s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.94s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.27s] DEBUG: Loading users from org.freedesktop.Accounts
[+1.27s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+9.31s] DEBUG: Got signal 10 from process 1012
[+9.31s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+9.31s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+9.32s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+9.32s] DEBUG: Session pid=1255: Started with service 'lightdm-greeter', username 'lightdm'
[+9.48s] DEBUG: Session pid=1255: Authentication complete with return value 0: Success
[+9.48s] DEBUG: Seat seat0: Session authenticated, running command
[+9.48s] DEBUG: Session pid=1255: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+9.48s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+9.48s] DEBUG: Session pid=1255: Logging to /var/log/lightdm/seat0-greeter.log
[+9.76s] DEBUG: Activating VT 7
[+9.76s] DEBUG: Activating login1 session c1
[+9.76s] DEBUG: Seat seat0 changes active session to c1
[+9.76s] DEBUG: Session c1 is already active
[+12.03s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+14.54s] DEBUG: Greeter start authentication for killer
[+14.54s] DEBUG: Session pid=1338: Started with service 'lightdm', username 'killer'
[+14.71s] DEBUG: Session pid=1338: Got 1 message(s) from PAM
[+14.71s] DEBUG: Prompt greeter with 1 message(s)
[+16.73s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+26.04s] DEBUG: Continue authentication
[+26.05s] DEBUG: Session pid=1338: Authentication complete with return value 0: Success
[+26.05s] DEBUG: Authenticate result for user killer: Success
[+26.05s] DEBUG: User killer authorized
[+26.13s] DEBUG: Greeter requests session ubuntu
[+26.13s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+26.13s] DEBUG: Session pid=1255: Sending SIGTERM
[+26.14s] DEBUG: Session pid=1255: Exited with return value 0
[+26.14s] DEBUG: Seat seat0: Session stopped
[+26.14s] DEBUG: Seat seat0: Greeter stopped, running session
[+26.14s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+26.15s] DEBUG: Session pid=1338: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+26.15s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+26.15s] DEBUG: Session pid=1338: Logging to .xsession-errors
[+26.33s] DEBUG: Activating VT 7
[+26.33s] DEBUG: Activating login1 session c2
[+26.33s] DEBUG: Seat seat0 changes active session to c2
[+26.33s] DEBUG: Session c2 is already active
[+1892.98s] DEBUG: Session pid=1338: Terminated with signal 1
[+1892.98s] DEBUG: Seat seat0: Session stopped
[+1892.98s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+1892.98s] DEBUG: Sending signal 15 to process 1012
[+1893.04s] DEBUG: Got signal 15 from process 1
[+1893.04s] DEBUG: Caught Terminated signal, shutting down
[+1893.04s] DEBUG: Stopping display manager
[+1893.04s] DEBUG: Seat seat0: Stopping
[+1893.39s] DEBUG: Process 1012 exited with return value 0
[+1893.39s] DEBUG: DisplayServer x-0: X server stopped
[+1893.39s] DEBUG: Releasing VT 7
[+1893.39s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+1893.39s] DEBUG: Seat seat0: Display server stopped
[+1893.39s] DEBUG: Seat seat0: Stopped
[+1893.39s] DEBUG: Display manager stopped
[+1893.39s] DEBUG: Stopping daemon
[+1893.39s] DEBUG: Exiting with return value 0
[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.08s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1021
[+0.08s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.08s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.08s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.08s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.08s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.08s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.08s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.08s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.08s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.08s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.08s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.08s] DEBUG: Registered seat module xlocal
[+0.08s] DEBUG: Registered seat module xremote
[+0.08s] DEBUG: Registered seat module unity
[+0.09s] DEBUG: Monitoring logind for seats
[+0.09s] DEBUG: New seat added from logind: seat0
[+0.09s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.09s] DEBUG: Seat seat0: Starting
[+0.09s] DEBUG: Seat seat0: Creating greeter session
[+0.32s] DEBUG: Seat seat0: Creating display server of type x
[+0.32s] DEBUG: Using VT 7
[+0.32s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.32s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.32s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.32s] DEBUG: DisplayServer x-0: Launching X Server
[+0.32s] DEBUG: Launching process 1048: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.32s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.32s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.32s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.55s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.55s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+9.19s] DEBUG: Got signal 10 from process 1048
[+9.19s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+9.19s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+9.20s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+9.20s] DEBUG: Session pid=1186: Started with service 'lightdm-greeter', username 'lightdm'
[+9.63s] DEBUG: Session pid=1186: Authentication complete with return value 0: Success
[+9.63s] DEBUG: Seat seat0: Session authenticated, running command
[+9.63s] DEBUG: Session pid=1186: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+9.63s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+9.63s] DEBUG: Session pid=1186: Logging to /var/log/lightdm/seat0-greeter.log
[+10.00s] DEBUG: Activating VT 7
[+10.00s] DEBUG: Activating login1 session c1
[+10.00s] DEBUG: Seat seat0 changes active session to c1
[+10.00s] DEBUG: Session c1 is already active
[+12.40s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+14.92s] DEBUG: Greeter start authentication for killer
[+14.92s] DEBUG: Session pid=1358: Started with service 'lightdm', username 'killer'
[+15.09s] DEBUG: Session pid=1358: Got 1 message(s) from PAM
[+15.09s] DEBUG: Prompt greeter with 1 message(s)
[+17.09s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+28.06s] DEBUG: Continue authentication
[+28.07s] DEBUG: Session pid=1358: Authentication complete with return value 0: Success
[+28.07s] DEBUG: Authenticate result for user killer: Success
[+28.07s] DEBUG: User killer authorized
[+28.10s] DEBUG: Greeter requests session ubuntu
[+28.10s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+28.10s] DEBUG: Session pid=1186: Sending SIGTERM
[+28.11s] DEBUG: Session pid=1186: Exited with return value 0
[+28.11s] DEBUG: Seat seat0: Session stopped
[+28.11s] DEBUG: Seat seat0: Greeter stopped, running session
[+28.11s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+28.11s] DEBUG: Session pid=1358: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+28.11s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+28.11s] DEBUG: Session pid=1358: Logging to .xsession-errors
[+28.21s] DEBUG: Activating VT 7
[+28.21s] DEBUG: Activating login1 session c2
[+28.22s] DEBUG: Seat seat0 changes active session to c2
[+28.22s] DEBUG: Session c2 is already active
[+35.10s] DEBUG: Session pid=1358: Exited with return value 0
[+35.10s] DEBUG: Seat seat0: Session stopped
[+35.10s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+35.10s] DEBUG: Sending signal 15 to process 1048
[+35.23s] DEBUG: Process 1048 exited with return value 0
[+35.23s] DEBUG: DisplayServer x-0: X server stopped
[+35.23s] DEBUG: Releasing VT 7
[+35.23s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+35.23s] DEBUG: Seat seat0: Display server stopped
[+35.23s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+35.23s] DEBUG: Seat seat0: Creating greeter session
[+35.23s] DEBUG: Seat seat0: Creating display server of type x
[+35.23s] DEBUG: Using VT 7
[+35.23s] DEBUG: Seat seat0: Starting local X display on VT 7
[+35.23s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+35.23s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+35.23s] DEBUG: DisplayServer x-0: Launching X Server
[+35.23s] DEBUG: Launching process 1882: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+35.23s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+35.37s] DEBUG: Got signal 10 from process 1882
[+35.37s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+35.37s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+35.37s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+35.37s] DEBUG: Session pid=1891: Started with service 'lightdm-greeter', username 'lightdm'
[+35.38s] DEBUG: Session pid=1891: Authentication complete with return value 0: Success
[+35.38s] DEBUG: Seat seat0: Session authenticated, running command
[+35.38s] DEBUG: Session pid=1891: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+35.38s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+35.38s] DEBUG: Session pid=1891: Logging to /var/log/lightdm/seat0-greeter.log
[+35.40s] DEBUG: Activating VT 7
[+35.40s] DEBUG: Activating login1 session c3
[+35.40s] DEBUG: Seat seat0 changes active session to c3
[+35.40s] DEBUG: Session c3 is already active
[+35.55s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+35.68s] DEBUG: Greeter start authentication for killer
[+35.68s] DEBUG: Session pid=1945: Started with service 'lightdm', username 'killer'
[+35.69s] DEBUG: Session pid=1945: Got 1 message(s) from PAM
[+35.69s] DEBUG: Prompt greeter with 1 message(s)
[+35.76s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+39.04s] DEBUG: Continue authentication
[+39.05s] DEBUG: Session pid=1945: Authentication complete with return value 0: Success
[+39.05s] DEBUG: Authenticate result for user killer: Success
[+39.05s] DEBUG: User killer authorized
[+39.06s] DEBUG: Greeter requests session ubuntu
[+39.06s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+39.06s] DEBUG: Session pid=1891: Sending SIGTERM
[+39.07s] DEBUG: Session pid=1891: Exited with return value 0
[+39.07s] DEBUG: Seat seat0: Session stopped
[+39.07s] DEBUG: Seat seat0: Greeter stopped, running session
[+39.07s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+39.07s] DEBUG: Session pid=1945: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+39.07s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+39.07s] DEBUG: Session pid=1945: Logging to .xsession-errors
[+39.10s] DEBUG: Activating VT 7
[+39.10s] DEBUG: Activating login1 session c4
[+39.10s] DEBUG: Seat seat0 changes active session to c4
[+39.10s] DEBUG: Session c4 is already active
[+40.68s] DEBUG: Session pid=1945: Exited with return value 0
[+40.68s] DEBUG: Seat seat0: Session stopped
[+40.68s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+40.68s] DEBUG: Sending signal 15 to process 1882
[+40.69s] DEBUG: Seat seat0 changes active session to 
[+40.69s] CRITICAL: session_get_login1_session_id: assertion 'session != NULL' failed
[+40.78s] DEBUG: Process 1882 exited with return value 0
[+40.78s] DEBUG: DisplayServer x-0: X server stopped
[+40.78s] DEBUG: Releasing VT 7
[+40.78s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+40.78s] DEBUG: Seat seat0: Display server stopped
[+40.78s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+40.78s] DEBUG: Seat seat0: Creating greeter session
[+40.78s] DEBUG: Seat seat0: Creating display server of type x
[+40.78s] DEBUG: Using VT 7
[+40.78s] DEBUG: Seat seat0: Starting local X display on VT 7
[+40.78s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+40.78s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+40.78s] DEBUG: DisplayServer x-0: Launching X Server
[+40.78s] DEBUG: Launching process 2348: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+40.78s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+40.93s] DEBUG: Got signal 10 from process 2348
[+40.93s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+40.93s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+40.93s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+40.93s] DEBUG: Session pid=2357: Started with service 'lightdm-greeter', username 'lightdm'
[+40.94s] DEBUG: Session pid=2357: Authentication complete with return value 0: Success
[+40.94s] DEBUG: Seat seat0: Session authenticated, running command
[+40.94s] DEBUG: Session pid=2357: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+40.94s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+40.94s] DEBUG: Session pid=2357: Logging to /var/log/lightdm/seat0-greeter.log
[+40.96s] DEBUG: Activating VT 7
[+40.96s] DEBUG: Activating login1 session c5
[+40.96s] DEBUG: Seat seat0 changes active session to c5
[+40.96s] DEBUG: Session c5 is already active
[+41.08s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+41.23s] DEBUG: Greeter start authentication for killer
[+41.23s] DEBUG: Session pid=2411: Started with service 'lightdm', username 'killer'
[+41.23s] DEBUG: Session pid=2411: Got 1 message(s) from PAM
[+41.23s] DEBUG: Prompt greeter with 1 message(s)
[+41.32s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+42.96s] DEBUG: Seat seat0 changes active session to 
[+48.89s] DEBUG: Seat seat0 changes active session to 1
[+511.59s] DEBUG: Session pid=2357: Terminated with signal 1
[+511.59s] DEBUG: Seat seat0: Session stopped
[+511.59s] DEBUG: Seat seat0: Stopping; failed to start a greeter
[+511.59s] DEBUG: Seat seat0: Stopping
[+511.59s] DEBUG: Seat seat0: Stopping display server
[+511.59s] DEBUG: Sending signal 15 to process 2348
[+511.59s] DEBUG: Seat seat0: Stopping session
[+511.59s] DEBUG: Session pid=2411: Sending SIGTERM
[+511.59s] DEBUG: Session pid=2411: Terminated with signal 15
[+511.59s] DEBUG: Session: Failed during authentication
[+511.59s] DEBUG: Seat seat0: Session stopped
[+511.60s] DEBUG: Process 2348 exited with return value 0
[+511.60s] DEBUG: DisplayServer x-0: X server stopped
[+511.60s] DEBUG: Releasing VT 7
[+511.60s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+511.60s] DEBUG: Seat seat0: Display server stopped
[+511.60s] DEBUG: Seat seat0: Stopped
[+511.60s] DEBUG: Required seat has stopped
[+511.60s] DEBUG: Stopping display manager
[+511.60s] DEBUG: Display manager stopped
[+511.60s] DEBUG: Stopping daemon
[+511.60s] DEBUG: Exiting with return value 1
[+0.05s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.15s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1038
[+0.15s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.15s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.15s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.15s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.15s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.16s] DEBUG: Registered seat module xlocal
[+0.16s] DEBUG: Registered seat module xremote
[+0.16s] DEBUG: Registered seat module unity
[+0.16s] DEBUG: Monitoring logind for seats
[+0.16s] DEBUG: New seat added from logind: seat0
[+0.16s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.16s] DEBUG: Seat seat0: Starting
[+0.16s] DEBUG: Seat seat0: Creating greeter session
[+0.20s] DEBUG: Seat seat0: Creating display server of type x
[+0.20s] DEBUG: Using VT 7
[+0.28s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.28s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.28s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.28s] DEBUG: DisplayServer x-0: Launching X Server
[+0.28s] DEBUG: Launching process 1050: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.28s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.28s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.28s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.48s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.48s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+9.76s] DEBUG: Got signal 10 from process 1050
[+9.76s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+9.76s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+9.76s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+9.76s] DEBUG: Session pid=1099: Started with service 'lightdm-greeter', username 'lightdm'
[+9.80s] DEBUG: Session pid=1099: Authentication complete with return value 0: Success
[+9.80s] DEBUG: Seat seat0: Session authenticated, running command
[+9.80s] DEBUG: Session pid=1099: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+9.80s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+9.80s] DEBUG: Session pid=1099: Logging to /var/log/lightdm/seat0-greeter.log
[+10.24s] DEBUG: Activating VT 7
[+10.24s] DEBUG: Activating login1 session c1
[+10.24s] DEBUG: Seat seat0 changes active session to c1
[+10.24s] DEBUG: Session c1 is already active
[+12.45s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+13.85s] DEBUG: Greeter start authentication for killer
[+13.85s] DEBUG: Session pid=1362: Started with service 'lightdm', username 'killer'
[+13.86s] DEBUG: Session pid=1362: Got 1 message(s) from PAM
[+13.86s] DEBUG: Prompt greeter with 1 message(s)
[+14.52s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+28.98s] DEBUG: Continue authentication
[+29.00s] DEBUG: Session pid=1362: Authentication complete with return value 0: Success
[+29.00s] DEBUG: Authenticate result for user killer: Success
[+29.00s] DEBUG: User killer authorized
[+29.00s] DEBUG: Greeter requests session ubuntu
[+29.00s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+29.00s] DEBUG: Session pid=1099: Sending SIGTERM
[+29.01s] DEBUG: Greeter closed communication channel
[+29.01s] DEBUG: Session pid=1099: Exited with return value 0
[+29.01s] DEBUG: Seat seat0: Session stopped
[+29.01s] DEBUG: Seat seat0: Greeter stopped, running session
[+29.01s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+29.01s] DEBUG: Session pid=1362: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+29.01s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+29.01s] DEBUG: Session pid=1362: Logging to .xsession-errors
[+29.06s] DEBUG: Activating VT 7
[+29.06s] DEBUG: Activating login1 session c2
[+29.06s] DEBUG: Seat seat0 changes active session to c2
[+29.06s] DEBUG: Session c2 is already active
[+33.19s] DEBUG: Session pid=1362: Exited with return value 0
[+33.19s] DEBUG: Seat seat0: Session stopped
[+33.19s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+33.19s] DEBUG: Sending signal 15 to process 1050
[+33.30s] DEBUG: Process 1050 exited with return value 0
[+33.30s] DEBUG: DisplayServer x-0: X server stopped
[+33.30s] DEBUG: Releasing VT 7
[+33.30s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+33.30s] DEBUG: Seat seat0: Display server stopped
[+33.30s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+33.30s] DEBUG: Seat seat0: Creating greeter session
[+33.30s] DEBUG: Seat seat0: Creating display server of type x
[+33.30s] DEBUG: Using VT 7
[+33.30s] DEBUG: Seat seat0: Starting local X display on VT 7
[+33.30s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+33.30s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+33.30s] DEBUG: DisplayServer x-0: Launching X Server
[+33.30s] DEBUG: Launching process 1843: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+33.30s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+33.43s] DEBUG: Got signal 10 from process 1843
[+33.43s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+33.43s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+33.44s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+33.44s] DEBUG: Session pid=1852: Started with service 'lightdm-greeter', username 'lightdm'
[+33.44s] DEBUG: Session pid=1852: Authentication complete with return value 0: Success
[+33.44s] DEBUG: Seat seat0: Session authenticated, running command
[+33.44s] DEBUG: Session pid=1852: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+33.44s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+33.44s] DEBUG: Session pid=1852: Logging to /var/log/lightdm/seat0-greeter.log
[+33.47s] DEBUG: Activating VT 7
[+33.47s] DEBUG: Activating login1 session c3
[+33.47s] DEBUG: Seat seat0 changes active session to c3
[+33.47s] DEBUG: Session c3 is already active
[+33.59s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+33.72s] DEBUG: Greeter start authentication for killer
[+33.72s] DEBUG: Session pid=1907: Started with service 'lightdm', username 'killer'
[+33.72s] DEBUG: Session pid=1907: Got 1 message(s) from PAM
[+33.72s] DEBUG: Prompt greeter with 1 message(s)
[+33.80s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+41.86s] DEBUG: Seat seat0 changes active session to 
[+46.43s] DEBUG: Seat seat0 changes active session to 1
[+1558.78s] DEBUG: Got signal 15 from process 1
[+1558.78s] DEBUG: Caught Terminated signal, shutting down
[+1558.78s] DEBUG: Stopping display manager
[+1558.78s] DEBUG: Seat seat0: Stopping
[+1558.78s] DEBUG: Seat seat0: Stopping display server
[+1558.78s] DEBUG: Sending signal 15 to process 1843
[+1558.78s] DEBUG: Seat seat0: Stopping session
[+1558.78s] DEBUG: Session pid=1852: Sending SIGTERM
[+1558.78s] DEBUG: Seat seat0: Stopping session
[+1558.78s] DEBUG: Session pid=1907: Sending SIGTERM
[+1558.78s] DEBUG: Session pid=1907: Terminated with signal 15
[+1558.78s] DEBUG: Session: Failed during authentication
[+1558.78s] DEBUG: Seat seat0: Session stopped
[+1558.84s] DEBUG: Greeter closed communication channel
[+1558.84s] DEBUG: Session pid=1852: Terminated with signal 1
[+1558.84s] DEBUG: Seat seat0: Session stopped
[+1558.93s] DEBUG: Seat seat0 changes active session to 
[+1558.93s] CRITICAL: session_get_login1_session_id: assertion 'session != NULL' failed
[+1558.97s] DEBUG: Process 1843 exited with return value 0
[+1558.97s] DEBUG: DisplayServer x-0: X server stopped
[+1558.97s] DEBUG: Releasing VT 7
[+1558.97s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+1558.97s] DEBUG: Seat seat0: Display server stopped
[+1558.97s] DEBUG: Seat seat0: Stopped
[+1558.97s] DEBUG: Display manager stopped
[+1558.97s] DEBUG: Stopping daemon
[+1558.97s] DEBUG: Exiting with return value 0
[+0.03s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.11s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1024
[+0.11s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.11s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.11s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.11s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.11s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.11s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.11s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.11s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.11s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.11s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.11s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.12s] DEBUG: Registered seat module xlocal
[+0.12s] DEBUG: Registered seat module xremote
[+0.12s] DEBUG: Registered seat module unity
[+0.12s] DEBUG: Monitoring logind for seats
[+0.12s] DEBUG: New seat added from logind: seat0
[+0.12s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.12s] DEBUG: Seat seat0: Starting
[+0.12s] DEBUG: Seat seat0: Creating greeter session
[+0.32s] DEBUG: Seat seat0: Creating display server of type x
[+0.32s] DEBUG: Using VT 7
[+0.32s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.32s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.32s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.32s] DEBUG: DisplayServer x-0: Launching X Server
[+0.32s] DEBUG: Launching process 1055: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.32s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.32s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.32s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.41s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.41s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+6.32s] DEBUG: Got signal 10 from process 1055
[+6.32s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+6.32s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+6.32s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+6.32s] DEBUG: Session pid=1147: Started with service 'lightdm-greeter', username 'lightdm'
[+7.04s] DEBUG: Session pid=1147: Authentication complete with return value 0: Success
[+7.04s] DEBUG: Seat seat0: Session authenticated, running command
[+7.04s] DEBUG: Session pid=1147: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+7.04s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+7.04s] DEBUG: Session pid=1147: Logging to /var/log/lightdm/seat0-greeter.log
[+7.76s] DEBUG: Activating VT 7
[+7.76s] DEBUG: Activating login1 session c1
[+7.76s] DEBUG: Seat seat0 changes active session to c1
[+7.76s] DEBUG: Session c1 is already active
[+10.47s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+13.06s] DEBUG: Greeter start authentication for killer
[+13.06s] DEBUG: Session pid=1364: Started with service 'lightdm', username 'killer'
[+13.22s] DEBUG: Session pid=1364: Got 1 message(s) from PAM
[+13.22s] DEBUG: Prompt greeter with 1 message(s)
[+15.41s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+27.02s] DEBUG: Continue authentication
[+27.03s] DEBUG: Session pid=1364: Authentication complete with return value 0: Success
[+27.03s] DEBUG: Authenticate result for user killer: Success
[+27.03s] DEBUG: User killer authorized
[+27.07s] DEBUG: Greeter requests session ubuntu
[+27.07s] DEBUG: Seat seat0: Stopping greeter; display server will be re-used for user session
[+27.07s] DEBUG: Session pid=1147: Sending SIGTERM
[+27.08s] DEBUG: Session pid=1147: Exited with return value 0
[+27.08s] DEBUG: Seat seat0: Session stopped
[+27.08s] DEBUG: Seat seat0: Greeter stopped, running session
[+27.08s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+27.09s] DEBUG: Session pid=1364: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+27.09s] DEBUG: Creating shared data directory /var/lib/lightdm-data/killer
[+27.09s] DEBUG: Session pid=1364: Logging to .xsession-errors
[+27.28s] DEBUG: Activating VT 7
[+27.28s] DEBUG: Activating login1 session c2
[+27.28s] DEBUG: Seat seat0 changes active session to c2
[+27.28s] DEBUG: Session c2 is already active
[+38.73s] DEBUG: Session pid=1364: Exited with return value 0
[+38.73s] DEBUG: Seat seat0: Session stopped
[+38.73s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+38.73s] DEBUG: Sending signal 15 to process 1055
[+38.83s] DEBUG: Process 1055 exited with return value 0
[+38.83s] DEBUG: DisplayServer x-0: X server stopped
[+38.83s] DEBUG: Releasing VT 7
[+38.83s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+38.83s] DEBUG: Seat seat0: Display server stopped
[+38.83s] DEBUG: Seat seat0: Active display server stopped, starting greeter
[+38.83s] DEBUG: Seat seat0: Creating greeter session
[+38.83s] DEBUG: Seat seat0: Creating display server of type x
[+38.83s] DEBUG: Using VT 7
[+38.83s] DEBUG: Seat seat0: Starting local X display on VT 7
[+38.83s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+38.83s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+38.83s] DEBUG: DisplayServer x-0: Launching X Server
[+38.83s] DEBUG: Launching process 1894: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+38.83s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+38.99s] DEBUG: Got signal 10 from process 1894
[+38.99s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+38.99s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+38.99s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+38.99s] DEBUG: Session pid=1905: Started with service 'lightdm-greeter', username 'lightdm'
[+39.00s] DEBUG: Session pid=1905: Authentication complete with return value 0: Success
[+39.00s] DEBUG: Seat seat0: Session authenticated, running command
[+39.00s] DEBUG: Session pid=1905: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+39.00s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+39.00s] DEBUG: Session pid=1905: Logging to /var/log/lightdm/seat0-greeter.log
[+39.02s] DEBUG: Activating VT 7
[+39.02s] DEBUG: Activating login1 session c3
[+39.02s] DEBUG: Seat seat0 changes active session to c3
[+39.02s] DEBUG: Session c3 is already active
[+39.17s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+39.28s] DEBUG: Greeter start authentication for killer
[+39.28s] DEBUG: Session pid=1958: Started with service 'lightdm', username 'killer'
[+39.29s] DEBUG: Session pid=1958: Got 1 message(s) from PAM
[+39.29s] DEBUG: Prompt greeter with 1 message(s)
[+39.39s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+42.61s] DEBUG: Seat seat0 changes active session to 
[+50.82s] DEBUG: Seat seat0 changes active session to 1
[+883.76s] DEBUG: Greeter closed communication channel
[+883.76s] DEBUG: Session pid=1905: Terminated with signal 1
[+883.76s] DEBUG: Seat seat0: Session stopped
[+883.76s] DEBUG: Seat seat0: Stopping; failed to start a greeter
[+883.76s] DEBUG: Seat seat0: Stopping
[+883.76s] DEBUG: Seat seat0: Stopping display server
[+883.76s] DEBUG: Sending signal 15 to process 1894
[+883.76s] DEBUG: Seat seat0: Stopping session
[+883.76s] DEBUG: Session pid=1958: Sending SIGTERM
[+883.76s] DEBUG: Session pid=1958: Terminated with signal 15
[+883.76s] DEBUG: Session: Failed during authentication
[+883.76s] DEBUG: Seat seat0: Session stopped
[+883.77s] DEBUG: Process 1894 exited with return value 0
[+883.77s] DEBUG: DisplayServer x-0: X server stopped
[+883.77s] DEBUG: Releasing VT 7
[+883.77s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+883.77s] DEBUG: Seat seat0: Display server stopped
[+883.77s] DEBUG: Seat seat0: Stopped
[+883.77s] DEBUG: Required seat has stopped
[+883.77s] DEBUG: Stopping display manager
[+883.77s] DEBUG: Display manager stopped
[+883.77s] DEBUG: Stopping daemon
[+883.78s] DEBUG: Exiting with return value 1
[+0.05s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.15s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1043
[+0.15s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.15s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.15s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.15s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.15s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.15s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.15s] DEBUG: Registered seat module xlocal
[+0.15s] DEBUG: Registered seat module xremote
[+0.15s] DEBUG: Registered seat module unity
[+0.68s] DEBUG: Monitoring logind for seats
[+0.68s] DEBUG: New seat added from logind: seat0
[+0.68s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.68s] DEBUG: Seat seat0: Starting
[+0.68s] DEBUG: Seat seat0: Creating greeter session
[+0.93s] DEBUG: Seat seat0: Creating display server of type x
[+0.93s] DEBUG: Using VT 7
[+0.93s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.93s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.93s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.93s] DEBUG: DisplayServer x-0: Launching X Server
[+0.93s] DEBUG: Launching process 1053: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.93s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.93s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.93s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.26s] DEBUG: Loading users from org.freedesktop.Accounts
[+1.26s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+9.11s] DEBUG: Got signal 10 from process 1053
[+9.11s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+9.11s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+9.11s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+9.11s] DEBUG: Session pid=1241: Started with service 'lightdm-greeter', username 'lightdm'
[+9.42s] DEBUG: Session pid=1241: Authentication complete with return value 0: Success
[+9.42s] DEBUG: Seat seat0: Session authenticated, running command
[+9.42s] DEBUG: Session pid=1241: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+9.42s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+9.42s] DEBUG: Session pid=1241: Logging to /var/log/lightdm/seat0-greeter.log
[+9.83s] DEBUG: Activating VT 7
[+9.83s] DEBUG: Activating login1 session c1
[+9.83s] DEBUG: Seat seat0 changes active session to c1
[+9.83s] DEBUG: Session c1 is already active
[+12.85s] DEBUG: Greeter connected version=1.18.3 resettable=false
[+15.45s] DEBUG: Greeter start authentication for killer
[+15.45s] DEBUG: Session pid=1381: Started with service 'lightdm', username 'killer'
[+15.62s] DEBUG: Session pid=1381: Got 1 message(s) from PAM
[+15.62s] DEBUG: Prompt greeter with 1 message(s)
[+17.67s] DEBUG: User /org/freedesktop/Accounts/User108 added
[+90.78s] DEBUG: Seat seat0 changes active session to 
[+101.77s] DEBUG: Seat seat0 changes active session to 1
```

---

### Post by mr.man2 on 2016-12-14
for x-0```

X.Org X Server 1.18.3
Release Date: 2016-04-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-86-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64
Kernel  command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-31-generic  root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset quiet splash  vt.handoff=7
Build Date: 18 May 2016  01:07:07AM
xorg-server 2:1.18.3-1ubuntu2.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 16:31:32 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=/dev/sda1 ro nomodeset quiet splash vt.handoff=7
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 17:10:52 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
modprobe:  ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open  moddep file '/lib/modules/4.4.0-53-generic/modules.dep.bin'
modprobe: FATAL: Module i915 not found in directory /lib/modules/4.4.0-53-generic
modprobe:  ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open  moddep file '/lib/modules/4.4.0-53-generic/modules.dep.bin'
modprobe: FATAL: Module fbcon not found in directory /lib/modules/4.4.0-53-generic
intel: waited 2020 ms for i915.ko driver to load
modprobe:  ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open  moddep file '/lib/modules/4.4.0-53-generic/modules.dep.bin'
modprobe: FATAL: Module i915 not found in directory /lib/modules/4.4.0-53-generic
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=/dev/sda1 ro nomodeset quiet splash vt.handoff=7
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 17:17:13 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
modprobe:  ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open  moddep file '/lib/modules/4.4.0-53-generic/modules.dep.bin'
modprobe: FATAL: Module i915 not found in directory /lib/modules/4.4.0-53-generic
modprobe:  ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open  moddep file '/lib/modules/4.4.0-53-generic/modules.dep.bin'
modprobe: FATAL: Module fbcon not found in directory /lib/modules/4.4.0-53-generic
intel: waited 2020 ms for i915.ko driver to load
modprobe:  ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open  moddep file '/lib/modules/4.4.0-53-generic/modules.dep.bin'
modprobe: FATAL: Module i915 not found in directory /lib/modules/4.4.0-53-generic
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 17:26:24 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 17:58:35 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 17:59:08 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 17:59:13 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 18:07:51 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 18:08:22 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 18:36:01 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro nomodeset text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 18:36:37 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(II) Server terminated successfully (0). Closing log file.

X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-45-generic x86_64 Ubuntu
Current Operating System: Linux szpiid 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-53-generic root=UUID=745bd837-c03e-42d4-bccd-fa9bcea01e04 ro text
Build Date: 02 November 2016  10:06:10PM
xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.33.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 18:52:51 2016
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
```
(i can't cram the results for "greeter" in a reply, what are the relevant tags to narrow it down to what's important?)

i'm  terribly sorry for this datadump, but my senses tell me that the  symptoms appear differently form before, or that i've erred somewhere in  the manipulations }:{T isn't there a way to get nvidia-361 on this here  machine? I swear to all things valuable, it worked spick&span /:/
nevertheless i'm genuinely thankful for the titanesque efforts showcased this far.

all the best, 

Morci

---

### Post by mc4man on 2016-12-15
If your intention is to use bumblebee then you'll need  to configure bumblebee properly, blacklist nvidia properly & prevent gpu-manager from writing a new xorg.conf file. The later can  be done using prime-select intel command.  Not sure you've done any of this..
If you wanted to use Nvidia via nvidia-prime then  you wouldn't want primus and bumblebee installed.

For bumblebee maybe read here
[http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)

---

