---
title: "Radeon HD 4350/4550 not recognized"
date: 2014-09-12
forum: Hardware
---

### Post by marino3 on 2014-09-12
Hello from France,

First, I shall state that it's not an hardware compatibility issue, for I'm posting this message using the Ubuntu 14.04 Live CD, which runs fine. I've been using Ubuntu on this computer with no hardware change since Lucid. Everything worked fine till I upgraded from 12.xx to 14.04.1.

ubuntu@ubuntu:~$ sudo lsb_release -a; uname -a

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
Linux ubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

In GRUB2, the option "nomodeset" is not present:```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

I use the open source driver. A "dpkg" shows:

```
xserver-xorg-video-ati     1:7.3.0-1ubuntu3    amd64     X.Org X server -- AMD/ATI display driver wrapper
xserver-xorg-video-radeon   1:7.3.0-1ubuntu3  amd64 X.Org X server -- AMD/ATI Radeon display driver
```

When I try to boot my original system, black screen. Here is the xorg.conf.failsafe (if still useful) and the corresponding xorg.failsafe.log which shows a "[COLOR=#ff0000]**GLX error: Can not get required symbols.**[/COLOR]" :

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```


```
[   566.125] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   566.125] X Protocol Version 11, Revision 0
[   566.125] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[   566.126] Current Operating System: Linux MC 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686
[   566.126] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=516de79f-8347-47ad-acaf-6e44b3fec267 ro recovery nomodeset
[   566.126] Build Date: 30 July 2014  12:19:53AM
[   566.126] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[   566.126] Current version of pixman: 0.30.2
[   566.127]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   566.127] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   566.129] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri Sep 12 09:41:51 2014
[   566.154] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[   566.154] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   566.189] (==) No Layout section.  Using the first Screen section.
[   566.189] (**) |-->Screen "Default Screen" (0)
[   566.189] (**) |   |-->Monitor "Configured Monitor"
[   566.205] (**) |   |-->Device "Configured Video Device"
[   566.205] (==) Automatically adding devices
[   566.205] (==) Automatically enabling devices
[   566.205] (==) Automatically adding GPU devices
[   566.254] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   566.254]     Entry deleted from font path.
[   566.267] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[   566.267] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   566.267] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   566.267] (II) Loader magic: 0xb775a6c0
[   566.267] (II) Module ABI versions:
[   566.267]     X.Org ANSI C Emulation: 0.4
[   566.267]     X.Org Video Driver: 15.0
[   566.267]     X.Org XInput driver : 20.0
[   566.267]     X.Org Server Extension : 8.0
[   566.269] (--) PCI:*(0:2:0:0) 1002:954f:1462:1612 rev 0, Mem @ 0xc0000000/268435456, 0xdfee0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[   566.282] Initializing built-in extension Generic Event Extension
[   566.282] Initializing built-in extension SHAPE
[   566.282] Initializing built-in extension MIT-SHM
[   566.282] Initializing built-in extension XInputExtension
[   566.282] Initializing built-in extension XTEST
[   566.282] Initializing built-in extension BIG-REQUESTS
[   566.282] Initializing built-in extension SYNC
[   566.283] Initializing built-in extension XKEYBOARD
[   566.283] Initializing built-in extension XC-MISC
[   566.283] Initializing built-in extension SECURITY
[   566.283] Initializing built-in extension XINERAMA
[   566.283] Initializing built-in extension XFIXES
[   566.283] Initializing built-in extension RENDER
[   566.283] Initializing built-in extension RANDR
[   566.283] Initializing built-in extension COMPOSITE
[   566.284] Initializing built-in extension DAMAGE
[   566.284] Initializing built-in extension MIT-SCREEN-SAVER
[   566.284] Initializing built-in extension DOUBLE-BUFFER
[   566.284] Initializing built-in extension RECORD
[   566.284] Initializing built-in extension DPMS
[   566.284] Initializing built-in extension Present
[   566.284] Initializing built-in extension DRI3
[   566.284] Initializing built-in extension X-Resource
[   566.285] Initializing built-in extension XVideo
[   566.285] Initializing built-in extension XVideo-MotionCompensation
[   566.285] Initializing built-in extension SELinux
[   566.285] Initializing built-in extension XFree86-VidModeExtension
[   566.285] Initializing built-in extension XFree86-DGA
[   566.285] Initializing built-in extension XFree86-DRI
[   566.285] Initializing built-in extension DRI2
[   566.285] (II) LoadModule: "glx"
[   566.286] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[   566.286] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[   566.286]     compiled for 6.9.0, module version = 1.0.0
[   566.287] Loading extension GLX
[   566.287] (II) LoadModule: "vesa"
[   566.341] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   566.365] (II) Module vesa: vendor="X.Org Foundation"
[   566.365]     compiled for 1.15.0, module version = 2.3.3
[   566.365]     Module class: X.Org Video Driver
[   566.365]     ABI class: X.Org Video Driver, version 15.0
[   566.365] (II) VESA: driver for VESA chipsets: vesa
[   566.365] (--) using VT number 2

[   566.367] (II) Loading sub module "vbe"
[   566.367] (II) LoadModule: "vbe"
[   566.367] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   566.384] (II) Module vbe: vendor="X.Org Foundation"
[   566.384]     compiled for 1.15.1, module version = 1.1.0
[   566.384]     ABI class: X.Org Video Driver, version 15.0
[   566.384] (II) Loading sub module "int10"
[   566.384] (II) LoadModule: "int10"
[   566.401] (II) Loading /usr/lib/xorg/modules/libint10.so
[   566.423] (II) Module int10: vendor="X.Org Foundation"
[   566.424]     compiled for 1.15.1, module version = 1.0.0
[   566.424]     ABI class: X.Org Video Driver, version 15.0
[   566.424] (II) VESA(0): initializing int10
[   566.429] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   566.429] (II) VESA(0): VESA BIOS detected
[   566.429] (II) VESA(0): VESA VBE Version 3.0
[   566.429] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   566.429] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   566.429] (II) VESA(0): VESA VBE OEM Software Rev: 11.15
[   566.429] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   566.429] (II) VESA(0): VESA VBE OEM Product: RV710
[   566.430] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   566.470] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[   566.470] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[   566.470] (==) VESA(0): RGB weight 888
[   566.470] (==) VESA(0): Default visual is TrueColor
[   566.470] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   566.470] (II) Loading sub module "ddc"
[   566.470] (II) LoadModule: "ddc"
[   566.470] (II) Module "ddc" already built-in
[   566.471] (II) VESA(0): VESA VBE DDC supported
[   566.471] (II) VESA(0): VESA VBE DDC Level 2
[   566.471] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[   575.551] (II) VESA(0): VESA VBE DDC unkown failure 768
[   575.551] (II) VESA(0): Searching for matching VESA mode(s):
[   575.551] Mode: 100 (640x400)
[   575.551]     ModeAttributes: 0xbb
[   575.551]     WinAAttributes: 0x7
[   575.551]     WinBAttributes: 0x0
[   575.551]     WinGranularity: 64
[   575.551]     WinSize: 64
[   575.551]     WinASegment: 0xa000
[   575.551]     WinBSegment: 0x0
[   575.551]     WinFuncPtr: 0xc0005101
[   575.551]     BytesPerScanline: 640
[   575.551]     XResolution: 640
[   575.555]     YResolution: 400
[   575.555]     XCharSize: 8
[   575.555]     YCharSize: 16
[   575.555]     NumberOfPlanes: 1
[   575.555]     BitsPerPixel: 8
[   575.555]     NumberOfBanks: 1
[   575.555]     MemoryModel: 4
[   575.555]     BankSize: 0
[   575.555]     NumberOfImages: 63
[   575.555]     RedMaskSize: 0
[   575.555]     RedFieldPosition: 0
[   575.555]     GreenMaskSize: 0

.......................................
... Big bunch of mode related lines ...
.......................................

[   575.642]     LinRsvdFieldPosition: 0
[   575.642]     MaxPixelClock: 400000000
[   575.642] 
[   575.642] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[   575.642] (II) VESA(0): Configured Monitor: Using default hsync range of 31.50-48.00 kHz
[   575.642] (II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[   575.642] (II) VESA(0): Configured Monitor: Using default maximum pixel clock of 65.00 MHz
[   575.642] (WW) VESA(0): Unable to estimate virtual size
[   575.642] (II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
[   575.642] (II) VESA(0): Not using built-in mode "1856x1392" (no mode of this name)
[   575.642] (II) VESA(0): Not using built-in mode "1792x1344" (no mode of this name)
[   575.642] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[   575.642] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[   575.642] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[   575.642] (II) VESA(0): Not using built-in mode "1280x960" (no mode of this name)
[   575.642] (II) VESA(0): Not using built-in mode "1152x864" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[   575.643] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[   575.643] (WW) VESA(0): No valid modes left. Trying less strict filter...
[   575.643] (II) VESA(0): Configured Monitor: Using hsync range of 31.50-48.00 kHz
[   575.643] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
[   575.643] (II) VESA(0): Configured Monitor: Using maximum pixel clock of 65.00 MHz
[   575.643] (WW) VESA(0): Unable to estimate virtual size
[   575.643] (II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "1856x1392" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "1792x1344" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "1400x1050" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "1280x960" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "1152x864" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[   575.643] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[   575.643] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[   575.643] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[   575.643] (**) VESA(0): *Built-in mode "1024x768"
[   575.643] (**) VESA(0): *Built-in mode "800x600"
[   575.643] (**) VESA(0): *Built-in mode "640x480"
[   575.643] (==) VESA(0): DPI set to (96, 96)
[   575.643] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (123)
[   575.649] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (122)
[   575.649] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (121)
[   575.649] (**) VESA(0): Using "Shadow Framebuffer"
[   575.649] (II) Loading sub module "shadow"
[   575.649] (II) LoadModule: "shadow"
[   575.650] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   575.660] (II) Module shadow: vendor="X.Org Foundation"
[   575.660]     compiled for 1.15.1, module version = 1.1.0
[   575.660]     ABI class: X.Org ANSI C Emulation, version 0.4
[   575.660] (II) Loading sub module "fb"
[   575.660] (II) LoadModule: "fb"
[   575.660] (II) Loading /usr/lib/xorg/modules/libfb.so
[   575.676] (II) Module fb: vendor="X.Org Foundation"
[   575.676]     compiled for 1.15.1, module version = 1.0.0
[   575.676]     ABI class: X.Org ANSI C Emulation, version 0.4
[   575.676] (==) Depth 24 pixmap format is 32 bpp
[   575.676] (II) Loading sub module "int10"
[   575.676] (II) LoadModule: "int10"
[   575.677] (II) Loading /usr/lib/xorg/modules/libint10.so
[   575.677] (II) Module int10: vendor="X.Org Foundation"
[   575.677]     compiled for 1.15.1, module version = 1.0.0
[   575.677]     ABI class: X.Org Video Driver, version 15.0
[   575.677] (II) VESA(0): initializing int10
[   575.679] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   575.681] (II) VESA(0): VESA BIOS detected
[   575.682] (II) VESA(0): VESA VBE Version 3.0
[   575.682] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   575.682] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   575.682] (II) VESA(0): VESA VBE OEM Software Rev: 11.15
[   575.682] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   575.682] (II) VESA(0): VESA VBE OEM Product: RV710
[   575.682] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   575.682] (II) VESA(0): virtual address = 0xb5c68000,
    physical address = 0xc0000000, size = 16777216
[   575.719] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[   575.719] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[   584.956] (==) VESA(0): Default visual is TrueColor
[   584.972] (==) VESA(0): Backing store enabled
[   584.983] (==) VESA(0): DPMS enabled
[   584.984] (==) RandR enabled
[   585.005] (II) SELinux: Disabled on system
**[COLOR=#ff0000][   585.012] (EE) GLX error: Can not get required symbols.[/COLOR]**
[   585.309] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   585.317] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   585.317] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   585.317] (II) LoadModule: "evdev"
[   585.318] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   585.339] (II) Module evdev: vendor="X.Org Foundation"
[   585.340]     compiled for 1.15.0, module version = 2.8.2
[   585.340]     Module class: X.Org XInput Driver
[   585.340]     ABI class: X.Org XInput driver, version 20.0
[   585.340] (II) Using input driver 'evdev' for 'Power Button'
[   585.340] (**) Power Button: always reports core events
[   585.340] (**) evdev: Power Button: Device: "/dev/input/event1"
[   585.340] (--) evdev: Power Button: Vendor 0 Product 0x1
[   585.340] (--) evdev: Power Button: Found keys
[   585.340] (II) evdev: Power Button: Configuring as keyboard
[   585.340] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   585.340] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   585.340] (**) Option "xkb_rules" "evdev"
[   585.340] (**) Option "xkb_model" "pc105"
[   585.340] (**) Option "xkb_layout" "fr"
[   585.340] (**) Option "xkb_variant" "oss"
[   585.343] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[   585.356] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   585.356] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   585.356] (II) Using input driver 'evdev' for 'Power Button'
[   585.356] (**) Power Button: always reports core events
[   585.356] (**) evdev: Power Button: Device: "/dev/input/event0"
[   585.356] (--) evdev: Power Button: Vendor 0 Product 0x1
[   585.356] (--) evdev: Power Button: Found keys
[   585.356] (II) evdev: Power Button: Configuring as keyboard
[   585.356] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   585.356] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   585.356] (**) Option "xkb_rules" "evdev"
[   585.356] (**) Option "xkb_model" "pc105"
[   585.356] (**) Option "xkb_layout" "fr"
[   585.356] (**) Option "xkb_variant" "oss"
[   585.357] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[   585.357] (II) No input driver specified, ignoring this device.
[   585.357] (II) This device may have been added with another device file.
[   585.358] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/event3)
[   585.358] (**) Logitech USB Mouse: Applying InputClass "evdev pointer catchall"
[   585.358] (II) Using input driver 'evdev' for 'Logitech USB Mouse'
[   585.358] (**) Logitech USB Mouse: always reports core events
[   585.358] (**) evdev: Logitech USB Mouse: Device: "/dev/input/event3"
[   585.358] (--) evdev: Logitech USB Mouse: Vendor 0x46d Product 0xc001
[   585.358] (--) evdev: Logitech USB Mouse: Found 3 mouse buttons
[   585.358] (--) evdev: Logitech USB Mouse: Found scroll wheel(s)
[   585.358] (--) evdev: Logitech USB Mouse: Found relative axes
[   585.358] (--) evdev: Logitech USB Mouse: Found x and y relative axes
[   585.358] (II) evdev: Logitech USB Mouse: Configuring as mouse
[   585.358] (II) evdev: Logitech USB Mouse: Adding scrollwheel support
[   585.358] (**) evdev: Logitech USB Mouse: YAxisMapping: buttons 4 and 5
[   585.358] (**) evdev: Logitech USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   585.358] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input3/event3"
[   585.358] (II) XINPUT: Adding extended input device "Logitech USB Mouse" (type: MOUSE, id 8)
[   585.358] (II) evdev: Logitech USB Mouse: initialized for relative axes.
[   585.358] (**) Logitech USB Mouse: (accel) keeping acceleration scheme 1
[   585.358] (**) Logitech USB Mouse: (accel) acceleration profile 0
[   585.358] (**) Logitech USB Mouse: (accel) acceleration factor: 2.000
[   585.358] (**) Logitech USB Mouse: (accel) acceleration threshold: 4
[   585.359] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/mouse0)
[   585.359] (II) No input driver specified, ignoring this device.
[   585.359] (II) This device may have been added with another device file.
[   585.359] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   585.359] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   585.359] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   585.359] (**) AT Translated Set 2 keyboard: always reports core events
[   585.359] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   585.359] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   585.359] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   585.359] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   585.359] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   585.359] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[   585.359] (**) Option "xkb_rules" "evdev"
[   585.359] (**) Option "xkb_model" "pc105"
[   585.359] (**) Option "xkb_layout" "fr"
[   585.359] (**) Option "xkb_variant" "oss"
```

The graphic card seems to be not recognized. While a "**lspci**" shows:
```
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550]
```

... a "**lshw**" will show:
```

           *-[COLOR=#ff0000]**display UNCLAIMED**[/COLOR]
                description: VGA compatible controller
                product: RV710 [Radeon HD 4350/4550]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff memory:dfee0000-dfeeffff ioport:de00(size=256) memory:dfe00000-dfe1ffff
```

Using the Live DVD, the same gives:

```
  *-[COLOR=#ff0000]**display               **[/COLOR]
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:24 memory:c0000000-cfffffff memory:dfee0000-dfeeffff ioport:de00(size=256) memory:dfe00000-dfe1ffff
```

So, it's a software configuration issue. Currently investigating... I can't see why it does not work properly. A "glxinfo" will return:

```
Error: Unable to open display
```

Using the Live DVD, a "xrandr" gives:

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
```

Any hint appreciated.

---

### Post by Yellow Pasque on 2014-09-12
```
[   566.286] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[   566.286] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[   566.286]     compiled for 6.9.0, module version = 1.0.0
```

You still have cruft left over from the proprietary fglrx/Catalyst driver.
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by marino3 on 2014-09-12
Uh oh... Catalyst slime? Thank you Temüjin. 

Checked but no /usr/share/ati/fglrx-uninstall.sh script not even a /usr/share/ati/ directory. No /etc/ati neither...

I used ```
sudo sh /[...]/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run --uninstall
``` ...to uninstall catalyst. I guest it had done the job.

I'm gonna try the rest:

```
sudo apt-get remove --purge fglrx*

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

---

### Post by marino3 on 2014-09-12
Things are moving... Still getting an error, BUT another one:

```
[    28.367] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    28.367] X Protocol Version 11, Revision 0
[    28.367] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    28.367] Current Operating System: Linux MC 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686
[    28.368] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=516de79f-8347-47ad-acaf-6e44b3fec267 ro recovery nomodeset
[    28.368] Build Date: 30 July 2014  12:19:53AM
[    28.368] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    28.368] Current version of pixman: 0.30.2
[    28.369]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.369] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.370] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri Sep 12 14:42:26 2014
[    28.412] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[    28.413] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.453] (==) No Layout section.  Using the first Screen section.
[    28.453] (**) |-->Screen "Default Screen" (0)
[    28.453] (**) |   |-->Monitor "Configured Monitor"
[    28.465] (**) |   |-->Device "Configured Video Device"
[    28.465] (==) Automatically adding devices
[    28.465] (==) Automatically enabling devices
[    28.465] (==) Automatically adding GPU devices
[    28.537] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.537]     Entry deleted from font path.
[    28.560] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    28.560] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.560] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.560] (II) Loader magic: 0xb77976c0
[    28.560] (II) Module ABI versions:
[    28.560]     X.Org ANSI C Emulation: 0.4
[    28.560]     X.Org Video Driver: 15.0
[    28.560]     X.Org XInput driver : 20.0
[    28.560]     X.Org Server Extension : 8.0
[    28.560] (II) xfree86: Adding drm device (/dev/dri/card0)
[    28.562] (--) PCI:*(0:2:0:0) 1002:954f:1462:1612 rev 0, Mem @ 0xc0000000/268435456, 0xdfee0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[    28.591] Initializing built-in extension Generic Event Extension
[    28.591] Initializing built-in extension SHAPE
[    28.592] Initializing built-in extension MIT-SHM
[    28.592] Initializing built-in extension XInputExtension
[    28.592] Initializing built-in extension XTEST
[    28.592] Initializing built-in extension BIG-REQUESTS
[    28.592] Initializing built-in extension SYNC
[    28.592] Initializing built-in extension XKEYBOARD
[    28.592] Initializing built-in extension XC-MISC
[    28.592] Initializing built-in extension SECURITY
[    28.593] Initializing built-in extension XINERAMA
[    28.593] Initializing built-in extension XFIXES
[    28.593] Initializing built-in extension RENDER
[    28.593] Initializing built-in extension RANDR
[    28.593] Initializing built-in extension COMPOSITE
[    28.593] Initializing built-in extension DAMAGE
[    28.593] Initializing built-in extension MIT-SCREEN-SAVER
[    28.593] Initializing built-in extension DOUBLE-BUFFER
[    28.594] Initializing built-in extension RECORD
[    28.594] Initializing built-in extension DPMS
[    28.594] Initializing built-in extension Present
[    28.594] Initializing built-in extension DRI3
[    28.594] Initializing built-in extension X-Resource
[    28.594] Initializing built-in extension XVideo
[    28.594] Initializing built-in extension XVideo-MotionCompensation
[    28.594] Initializing built-in extension SELinux
[    28.595] Initializing built-in extension XFree86-VidModeExtension
[    28.595] Initializing built-in extension XFree86-DGA
[    28.595] Initializing built-in extension XFree86-DRI
[    28.595] Initializing built-in extension DRI2
[    28.595] (II) LoadModule: "glx"
[    28.676] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.998] (II) Module glx: vendor="X.Org Foundation"
[    28.998]     compiled for 1.15.1, module version = 1.0.0
[    28.998]     ABI class: X.Org Server Extension, version 8.0
[    28.998] (==) AIGLX enabled
[    28.998] Loading extension GLX
[    28.998] (II) LoadModule: "vesa"
[    28.999] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.011] (II) Module vesa: vendor="X.Org Foundation"
[    29.011]     compiled for 1.15.0, module version = 2.3.3
[    29.011]     Module class: X.Org Video Driver
[    29.011]     ABI class: X.Org Video Driver, version 15.0
[    29.011] (II) VESA: driver for VESA chipsets: vesa
[    29.011] (--) using VT number 2

[    29.013] (II) Loading sub module "vbe"
[    29.013] (II) LoadModule: "vbe"
[    29.013] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    29.036] (II) Module vbe: vendor="X.Org Foundation"
[    29.036]     compiled for 1.15.1, module version = 1.1.0
[    29.036]     ABI class: X.Org Video Driver, version 15.0
[    29.036] (II) Loading sub module "int10"
[    29.036] (II) LoadModule: "int10"
[    29.059] (II) Loading /usr/lib/xorg/modules/libint10.so
[    29.085] (II) Module int10: vendor="X.Org Foundation"
[    29.085]     compiled for 1.15.1, module version = 1.0.0
[    29.085]     ABI class: X.Org Video Driver, version 15.0
[    29.085] (II) VESA(0): initializing int10
[    29.091] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    29.091] (II) VESA(0): VESA BIOS detected
[    29.091] (II) VESA(0): VESA VBE Version 3.0
[    29.091] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    29.091] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    29.091] (II) VESA(0): VESA VBE OEM Software Rev: 11.15
[    29.091] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    29.091] (II) VESA(0): VESA VBE OEM Product: RV710
[    29.091] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    29.109] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    29.109] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    29.109] (==) VESA(0): RGB weight 888
[    29.109] (==) VESA(0): Default visual is TrueColor
[    29.109] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.109] (II) Loading sub module "ddc"
[    29.109] (II) LoadModule: "ddc"
[    29.109] (II) Module "ddc" already built-in
[    29.110] (II) VESA(0): VESA VBE DDC supported
[    29.110] (II) VESA(0): VESA VBE DDC Level 2
[    29.110] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    33.570] (II) VESA(0): VESA VBE DDC unkown failure 768
[    33.571] (II) VESA(0): Searching for matching VESA mode(s):
[    33.571] Mode: 100 (640x400)
[    33.571]     ModeAttributes: 0xbb
[    33.571]     WinAAttributes: 0x7
[    33.571]     WinBAttributes: 0x0
[    33.571]     WinGranularity: 64
[    33.571]     WinSize: 64
[    33.571]     WinASegment: 0xa000

... Blah blah ... 

[    33.610]     LinRedMaskSize: 8
[    33.610]     LinRedFieldPosition: 16
[    33.610]     LinGreenMaskSize: 8
[    33.610]     LinGreenFieldPosition: 8
[    33.610]     LinBlueMaskSize: 8
[    33.610]     LinBlueFieldPosition: 0
[    33.610]     LinRsvdMaskSize: 0
[    33.610]     LinRsvdFieldPosition: 0
[    33.610]     MaxPixelClock: 400000000
[    33.610] 
[    33.610] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    33.610] (II) VESA(0): Configured Monitor: Using default hsync range of 31.50-48.00 kHz
[    33.610] (II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[    33.610] (II) VESA(0): Configured Monitor: Using default maximum pixel clock of 65.00 MHz
[    33.610] (WW) VESA(0): Unable to estimate virtual size
[    33.610] (II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1856x1392" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1792x1344" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1280x960" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1152x864" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    33.610] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    33.610] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    33.610] (II) VESA(0): Configured Monitor: Using hsync range of 31.50-48.00 kHz
[    33.610] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
[    33.610] (II) VESA(0): Configured Monitor: Using maximum pixel clock of 65.00 MHz
[    33.610] (WW) VESA(0): Unable to estimate virtual size
[    33.610] (II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "1856x1392" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "1792x1344" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "1400x1050" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "1280x960" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "1152x864" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[    33.611] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    33.611] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    33.611] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    33.611] (**) VESA(0): *Built-in mode "1024x768"
[    33.611] (**) VESA(0): *Built-in mode "800x600"
[    33.611] (**) VESA(0): *Built-in mode "640x480"
[    33.611] (==) VESA(0): DPI set to (96, 96)
[    33.611] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (123)
[    33.611] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (122)
[    33.611] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (121)
[    33.612] (**) VESA(0): Using "Shadow Framebuffer"
[    33.612] (II) Loading sub module "shadow"
[    33.612] (II) LoadModule: "shadow"
[    33.612] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    33.631] (II) Module shadow: vendor="X.Org Foundation"
[    33.631]     compiled for 1.15.1, module version = 1.1.0
[    33.631]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.631] (II) Loading sub module "fb"
[    33.631] (II) LoadModule: "fb"
[    33.631] (II) Loading /usr/lib/xorg/modules/libfb.so
[    33.651] (II) Module fb: vendor="X.Org Foundation"
[    33.651]     compiled for 1.15.1, module version = 1.0.0
[    33.651]     ABI class: X.Org ANSI C Emulation, version 0.4
[    33.651] (==) Depth 24 pixmap format is 32 bpp
[    33.651] (II) Loading sub module "int10"
[    33.651] (II) LoadModule: "int10"
[    33.652] (II) Loading /usr/lib/xorg/modules/libint10.so
[    33.652] (II) Module int10: vendor="X.Org Foundation"
[    33.652]     compiled for 1.15.1, module version = 1.0.0
[    33.652]     ABI class: X.Org Video Driver, version 15.0
[    33.652] (II) VESA(0): initializing int10
[    33.654] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    33.655] (II) VESA(0): VESA BIOS detected
[    33.655] (II) VESA(0): VESA VBE Version 3.0
[    33.655] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    33.655] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    33.655] (II) VESA(0): VESA VBE OEM Software Rev: 11.15
[    33.655] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    33.655] (II) VESA(0): VESA VBE OEM Product: RV710
[    33.655] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    33.655] (II) VESA(0): virtual address = 0xb5aec000,
    physical address = 0xc0000000, size = 16777216
[    33.672] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[    33.672] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[    38.229] (==) VESA(0): Default visual is TrueColor
[    38.251] (==) VESA(0): Backing store enabled
[    38.261] (==) VESA(0): DPMS enabled
[    38.262] (==) RandR enabled
[    38.274] (II) SELinux: Disabled on system
[B][COLOR=#ff0000][    38.283] (II) AIGLX: Screen 0 is not DRI2 capable
[    38.283] (EE) AIGLX: reverting to software rendering[/COLOR][/B]
[    39.533] (II) AIGLX: Loaded and initialized swrast
[    39.533] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    39.834] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.843] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    39.843] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.843] (II) LoadModule: "evdev"
[    39.843] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.873] (II) Module evdev: vendor="X.Org Foundation"
[    39.873]     compiled for 1.15.0, module version = 2.8.2
[    39.873]     Module class: X.Org XInput Driver
[    39.873]     ABI class: X.Org XInput driver, version 20.0
[    39.873] (II) Using input driver 'evdev' for 'Power Button'
[    39.873] (**) Power Button: always reports core events
[    39.873] (**) evdev: Power Button: Device: "/dev/input/event1"
[    39.873] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.873] (--) evdev: Power Button: Found keys
[    39.873] (II) evdev: Power Button: Configuring as keyboard
[    39.873] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    39.873] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    39.873] (**) Option "xkb_rules" "evdev"
[    39.873] (**) Option "xkb_model" "pc105"
[    39.873] (**) Option "xkb_layout" "fr"
[    39.873] (**) Option "xkb_variant" "oss"
[    39.911] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[    39.923] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    39.923] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.923] (II) Using input driver 'evdev' for 'Power Button'
[    39.923] (**) Power Button: always reports core events
[    39.923] (**) evdev: Power Button: Device: "/dev/input/event0"
[    39.923] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.923] (--) evdev: Power Button: Found keys
[    39.923] (II) evdev: Power Button: Configuring as keyboard
[    39.923] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    39.923] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    39.923] (**) Option "xkb_rules" "evdev"
[    39.923] (**) Option "xkb_model" "pc105"
[    39.923] (**) Option "xkb_layout" "fr"
[    39.923] (**) Option "xkb_variant" "oss"
[    39.924] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/drm/card0
[    39.924] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    39.924] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[    39.924] (II) No input driver specified, ignoring this device.
[    39.924] (II) This device may have been added with another device file.
[    39.924] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/event3)
[    39.925] (**) Logitech USB Mouse: Applying InputClass "evdev pointer catchall"
[    39.925] (II) Using input driver 'evdev' for 'Logitech USB Mouse'
[    39.925] (**) Logitech USB Mouse: always reports core events
[    39.925] (**) evdev: Logitech USB Mouse: Device: "/dev/input/event3"
[    39.925] (--) evdev: Logitech USB Mouse: Vendor 0x46d Product 0xc001
[    39.925] (--) evdev: Logitech USB Mouse: Found 3 mouse buttons
[    39.925] (--) evdev: Logitech USB Mouse: Found scroll wheel(s)
[    39.925] (--) evdev: Logitech USB Mouse: Found relative axes
[    39.925] (--) evdev: Logitech USB Mouse: Found x and y relative axes
[    39.925] (II) evdev: Logitech USB Mouse: Configuring as mouse
[    39.925] (II) evdev: Logitech USB Mouse: Adding scrollwheel support
[    39.925] (**) evdev: Logitech USB Mouse: YAxisMapping: buttons 4 and 5
[    39.925] (**) evdev: Logitech USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    39.925] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    39.925] (II) XINPUT: Adding extended input device "Logitech USB Mouse" (type: MOUSE, id 8)
[    39.925] (II) evdev: Logitech USB Mouse: initialized for relative axes.
[    39.925] (**) Logitech USB Mouse: (accel) keeping acceleration scheme 1
[    39.925] (**) Logitech USB Mouse: (accel) acceleration profile 0
[    39.925] (**) Logitech USB Mouse: (accel) acceleration factor: 2.000
[    39.925] (**) Logitech USB Mouse: (accel) acceleration threshold: 4
[    39.926] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/mouse0)
[    39.926] (II) No input driver specified, ignoring this device.
[    39.926] (II) This device may have been added with another device file.
[    39.926] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    39.926] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    39.926] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    39.926] (**) AT Translated Set 2 keyboard: always reports core events
[    39.926] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    39.926] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    39.926] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    39.926] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    39.926] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    39.926] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    39.926] (**) Option "xkb_rules" "evdev"
[    39.926] (**) Option "xkb_model" "pc105"
[    39.926] (**) Option "xkb_layout" "fr"
[    39.926] (**) Option "xkb_variant" "oss"
[    56.832] (II) evdev: AT Translated Set 2 keyboard: Close
[    56.832] (II) UnloadModule: "evdev"
[    56.832] (II) evdev: Logitech USB Mouse: Close
[    56.832] (II) UnloadModule: "evdev"
[    56.832] (II) evdev: Power Button: Close
[    56.832] (II) UnloadModule: "evdev"
[    56.832] (II) evdev: Power Button: Close
[    56.832] (II) UnloadModule: "evdev"
[    66.025] (EE) Server terminated successfully (0). Closing log file.
```

Investigating...

Would it be a xorg.conf.failsafe screen section issue? On my previous configuration with Catalyst, my xorg.conf was like this:

```
Section "Files"
    ModulePath "/usr/lib/xorg/modules"
EndSection

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option        "Clone" "off"
    Option        "Xinerama" "off"
EndSection

Section "Module"
    Load  "glx"
    Load  "record"
    Load  "extmod"
    Load  "dbe"
    Load  "dri2"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "ACER"
    ModelName    "1440X900@60HZ"
    HorizSync    30-80
    VertRefresh  55-75
    Option        "DPMS"
    Option        "PreferredMode" "1440x900"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "fglrx"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV710 [Radeon HD 4350]"
    BusID       "PCI:2:0:0"
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "ACER X193W LCD MONITOR"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes    "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes    "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

What would be the changes for the open source driver "fglrx" -> "aiglx" ?

---

### Post by marino3 on 2014-09-12
Crap. Still a "display UNCLAIMED" for my radeon through lshw... Crap, crap crap.
Is it a X server issue or a open source driver issue?
Can't even get a failsafe in recovery. Three days lost. Feeling a little weary.

Through lshw, I can see there is another "UNCLAIMED":

        ```
        *-generic UNCLAIMED
             description: PIC
             product: K8M890CE I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
```

Not related? Related?

             What "UNCLAIMED" means that there's no driver claiming it and thus it's not going to work until one does.

On this page [http://manpages.ubuntu.com/manpages/trusty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/trusty/man4/radeon.4.html) , it's stated my graphic card is still supported.

---

### Post by marino3 on 2014-09-12
Here come the point where one feel... damn stupid.

I humbly bow my head, Temüjin.

```
dpkg -l|grep fglrx
``` ... showed that, yes, despite my certitude, there were still **fglrx** and **fglrx-updates** around.

I uninstalled them, re-checked there were gone, uninstalled and purged the whole xorg thing, reinstalled, reconfigure and yadah!

Still an error, but not the same. Investigating...

---

### Post by marino3 on 2014-09-12
Argh! fglrx entries in Xorg.failsafe.log...

```
[    91.767] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    91.767] X Protocol Version 11, Revision 0
[    91.767] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    91.767] Current Operating System: Linux MC 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686
[    91.767] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=516de79f-8347-47ad-acaf-6e44b3fec267 ro recovery nomodeset
[    91.768] Build Date: 30 July 2014  12:19:53AM
[    91.768] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    91.768] Current version of pixman: 0.30.2
[    91.768]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    91.768] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    91.770] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Fri Sep 12 21:49:03 2014
[    91.854] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[    91.854] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    91.878] (==) No Layout section.  Using the first Screen section.
[    91.879] (**) |-->Screen "Default Screen" (0)
[    91.879] (**) |   |-->Monitor "Configured Monitor"
[    91.904] (**) |   |-->Device "Configured Video Device"
[    91.904] (==) Automatically adding devices
[    91.904] (==) Automatically enabling devices
[    91.904] (==) Automatically adding GPU devices
[    91.979] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    91.979]     Entry deleted from font path.
[    92.001] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    92.001] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    92.001] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    92.001] (II) Loader magic: 0xb77176c0
[    92.001] (II) Module ABI versions:
[    92.001]     X.Org ANSI C Emulation: 0.4
[    92.001]     X.Org Video Driver: 15.0
[    92.001]     X.Org XInput driver : 20.0
[    92.001]     X.Org Server Extension : 8.0
[    92.002] (II) xfree86: Adding drm device (/dev/dri/card0)
[    92.003] (--) PCI:*(0:2:0:0) 1002:954f:1462:1612 rev 0, Mem @ 0xc0000000/268435456, 0xdfee0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[    92.013] Initializing built-in extension Generic Event Extension
[    92.014] Initializing built-in extension SHAPE
[    92.014] Initializing built-in extension MIT-SHM
[    92.014] Initializing built-in extension XInputExtension
[    92.014] Initializing built-in extension XTEST
[    92.014] Initializing built-in extension BIG-REQUESTS
[    92.014] Initializing built-in extension SYNC
[    92.014] Initializing built-in extension XKEYBOARD
[    92.014] Initializing built-in extension XC-MISC
[    92.015] Initializing built-in extension SECURITY
[    92.015] Initializing built-in extension XINERAMA
[    92.015] Initializing built-in extension XFIXES
[    92.015] Initializing built-in extension RENDER
[    92.015] Initializing built-in extension RANDR
[    92.015] Initializing built-in extension COMPOSITE
[    92.015] Initializing built-in extension DAMAGE
[    92.015] Initializing built-in extension MIT-SCREEN-SAVER
[    92.016] Initializing built-in extension DOUBLE-BUFFER
[    92.016] Initializing built-in extension RECORD
[    92.016] Initializing built-in extension DPMS
[    92.016] Initializing built-in extension Present
[    92.016] Initializing built-in extension DRI3
[    92.016] Initializing built-in extension X-Resource
[    92.016] Initializing built-in extension XVideo
[    92.016] Initializing built-in extension XVideo-MotionCompensation
[    92.017] Initializing built-in extension SELinux
[    92.017] Initializing built-in extension XFree86-VidModeExtension
[    92.017] Initializing built-in extension XFree86-DGA
[    92.017] Initializing built-in extension XFree86-DRI
[    92.017] Initializing built-in extension DRI2
[    92.017] (II) LoadModule: "glx"
[    92.192] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    92.228] (II) Module glx: vendor="X.Org Foundation"
[    92.228]     compiled for 1.15.1, module version = 1.0.0
[    92.228]     ABI class: X.Org Server Extension, version 8.0
[    92.228] (==) AIGLX enabled
[    92.228] Loading extension GLX
[    92.228] (II) LoadModule: "vesa"
[    92.259] (WW) Warning, couldn't open module vesa
[    92.259] (II) UnloadModule: "vesa"
[    92.259] (II) Unloading vesa
[    92.259] (EE) Failed to load module "vesa" (module does not exist, 0)
[    92.259] (==) Matched fglrx as autoconfigured driver 0
[    92.259] (==) Matched ati as autoconfigured driver 1
[    92.259] (==) Matched fglrx as autoconfigured driver 2
[    92.259] (==) Matched ati as autoconfigured driver 3
[    92.259] (==) Matched modesetting as autoconfigured driver 4
[    92.259] (==) Matched fbdev as autoconfigured driver 5
[    92.259] (==) Matched vesa as autoconfigured driver 6
[    92.259] (==) Assigned the driver to the xf86ConfigLayout
[    92.259] (II) LoadModule: "**[COLOR=#ff0000]fglrx[/COLOR]**"
[    92.260] (WW) Warning, couldn't open module **[COLOR=#ff0000]fglrx[/COLOR]**
[    92.260] (II) UnloadModule: "**[COLOR=#ff0000]fglrx[/COLOR]**"
[    92.260] (II) Unloading **[COLOR=#ff0000]fglrx[/COLOR]**
[    92.260] (EE) Failed to load module "**[COLOR=#ff0000]fglrx[/COLOR]**" (module does not exist, 0)
```


Using config file: "/etc/X11/xorg.conf.failsafe" (is very basic and does not invoke fglrx).
Using system config directory "/usr/share/X11/xorg.conf.d" -> No invokation of fglrx whatsoever.

---

### Post by marino3 on 2014-09-12
Waaaaah Could log during normal boot... Sluggish 1024X768 but far better than an idle black screen.

glxinfo gives now a very big output:

```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
[...]
```


sudo lshw -C display shows now:

  ```
*-display               
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:24 memory:c0000000-cfffffff memory:dfee0000-dfeeffff ioport:de00(size=256) memory:dfe00000-dfe1ffff
```

Nearly working.

---

### Post by Yellow Pasque on 2014-09-12
Can I get an Xorg log of what happens when you boot without xorg.conf?

---

### Post by marino3 on 2014-09-12
Hmmm... Graphic is reported as "Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)".

```
sudo glxinfo | grep -i gall
OpenGL renderer string: Gallium 0.4 on AMD RV710
```




I wonder how the graphic system could start, as the xorg.0.log file shows error**[COLOR=#ff0000]S[/COLOR]**. Yes, plural:

```
[    50.438] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    50.438] X Protocol Version 11, Revision 0
[    50.438] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    50.438] Current Operating System: Linux MC 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686
[    50.438] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=516de79f-8347-47ad-acaf-6e44b3fec267 ro
[    50.438] Build Date: 30 July 2014  12:19:53AM
[    50.438] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    50.438] Current version of pixman: 0.30.2
[    50.438]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    50.438] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    50.438] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 12 23:49:41 2014
[    50.492] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    50.492] (==) No Layout section.  Using the first Screen section.

...

[    53.017] (==) Assigned the driver to the xf86ConfigLayout
[    53.017] (II) LoadModule: "[COLOR=#ff0000]fglrx[/COLOR]"
[    53.190] (WW) Warning, couldn't open module fglrx
[    53.190] (II) UnloadModule: "fglrx"
[    53.190] (II) Unloading fglrx
[    53.190] **[COLOR=#ff0000](EE) Failed to load module "fglrx" (module does not exist, 0)[/COLOR]**
[    53.190] (II) LoadModule: "ati"
[    53.190] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    53.190] (II) Module ati: vendor="X.Org Foundation"
[    53.190]     compiled for 1.15.1, module version = 7.3.0
[    53.190]     Module class: X.Org Video Driver
[    53.190]     ABI class: X.Org Video Driver, version 15.0
[    53.190] (II) LoadModule: "radeon"
[    53.240] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    53.442] (II) Module radeon: vendor="X.Org Foundation"
[    53.442]     compiled for 1.15.1, module version = 7.3.0
[    53.442]     Module class: X.Org Video Driver
[    53.442]     ABI class: X.Org Video Driver, version 15.0
[    53.442] (II) LoadModule: "modesetting"
[    53.442] (WW) Warning, couldn't open module modesetting
[    53.442] (II) UnloadModule: "modesetting"
[    53.442] (II) Unloading modesetting
[    53.442] **[COLOR=#ff0000](EE) Failed to load module "modesetting" (module does not exist, 0)[/COLOR]**
[    53.442] (II) LoadModule: "fbdev"
[    53.443] (WW) Warning, couldn't open module fbdev
[    53.443] (II) UnloadModule: "fbdev"
[    53.443] (II) Unloading fbdev
[    53.443] [COLOR=#ff0000]**(EE) Failed to load module "fbdev" (module does not exist, 0)**[/COLOR]
[    53.443] (II) LoadModule: "vesa"
[    53.443] (WW) Warning, couldn't open module vesa
[    53.443] (II) UnloadModule: "vesa"
[    53.443] (II) Unloading vesa
[    53.443] **[COLOR=#ff0000](EE) Failed to load module "vesa" (module does not exist, 0)[/COLOR]**
[    53.443] (==) Matched fglrx as autoconfigured driver 0
[    53.443] (==) Matched ati as autoconfigured driver 1
[    53.443] (==) Matched fglrx as autoconfigured driver 2
[    53.443] (==) Matched ati as autoconfigured driver 3
[    53.443] (==) Matched modesetting as autoconfigured driver 4
[    53.443] (==) Matched fbdev as autoconfigured driver 5
[    53.443] (==) Matched vesa as autoconfigured driver 6
[    53.443] (==) Assigned the driver to the xf86ConfigLayout
[    53.443] (II) LoadModule: "fglrx"
[    53.444] (WW) Warning, couldn't open module fglrx
[    53.444] (II) UnloadModule: "fglrx"
[    53.444] (II) Unloading fglrx
[    53.444] **[COLOR=#ff0000](EE) Failed to load module "fglrx" (module does not exist, 0)[/COLOR]**
[    53.444] (II) LoadModule: "ati"
[    53.444] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    53.445] (II) Module ati: vendor="X.Org Foundation"
[    53.445]     compiled for 1.15.1, module version = 7.3.0
[    53.445]     Module class: X.Org Video Driver
[    53.445]     ABI class: X.Org Video Driver, version 15.0
[    53.445] (II) LoadModule: "modesetting"
[    53.445] (WW) Warning, couldn't open module modesetting
[    53.445] (II) UnloadModule: "modesetting"
[    53.445] (II) Unloading modesetting
[    53.445] **[COLOR=#ff0000](EE) Failed to load module "modesetting" (module does not exist, 0)[/COLOR]**
[    53.445] (II) LoadModule: "fbdev"
[    53.445] (WW) Warning, couldn't open module fbdev
[    53.445] (II) UnloadModule: "fbdev"
[    53.445] (II) Unloading fbdev
[    53.445] **[COLOR=#ff0000](EE) Failed to load module "fbdev" (module does not exist, 0)[/COLOR]**
[    53.445] (II) LoadModule: "vesa"
[    53.446] (WW) Warning, couldn't open module vesa
[    53.446] (II) UnloadModule: "vesa"
[    53.446] (II) Unloading vesa
[    53.446] **[COLOR=#ff0000](EE) Failed to load module "vesa" (module does not exist, 0)[/COLOR]**
[    53.446] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),

...

    HAWAII, HAWAII, HAWAII, HAWAII
[    53.468] (--) using VT number 1

[    53.479] (II) [KMS] Kernel modesetting enabled.
[    53.479] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    53.479] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    53.479] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    53.479] (==) RADEON(0): Default visual is TrueColor
[    53.479] (==) RADEON(0): RGB weight 888
[    53.480] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    53.480] (--) RADEON(0): Chipset: "ATI Radeon HD 4350" (ChipID = 0x954f)
[    53.480] (II) Loading sub module "dri2"
[    53.480] (II) LoadModule: "dri2"
[    53.480] (II) Module "dri2" already built-in
[    53.480] (II) Loading sub module "exa"
[    53.480] (II) LoadModule: "exa"
[    53.480] (II) Loading /usr/lib/xorg/modules/libexa.so
[    53.489] (II) Module exa: vendor="X.Org Foundation"
[    53.489]     compiled for 1.15.1, module version = 2.6.0
[    53.489]     ABI class: X.Org Video Driver, version 15.0
[    53.489] (II) RADEON(0): KMS Color Tiling: enabled
[    53.489] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    53.489] (II) RADEON(0): KMS Pageflipping: enabled
[    53.489] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    53.644] (II) RADEON(0): Output VGA-0 has no monitor section
[    53.668] (II) RADEON(0): Output DVI-0 has no monitor section
[    53.816] (II) RADEON(0): EDID for output VGA-0
[    53.816] (II) RADEON(0): Printing probed modes for output VGA-0
[    53.816] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    53.816] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    53.816] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    53.816] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    53.816] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    53.840] (II) RADEON(0): EDID for output DVI-0
[    53.840] (II) RADEON(0): Output VGA-0 connected
[    53.840] (II) RADEON(0): Output DVI-0 disconnected
[    53.840] (II) RADEON(0): Using exact sizes for initial modes
[    53.840] (II) RADEON(0): Output VGA-0 using initial mode 1024x768
[    53.840] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    53.840] (II) RADEON(0): mem size init: gart size :3fdee000 vram size: s:20000000 visible:1fcc0000
[    53.840] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    53.840] (==) RADEON(0): DPI set to (96, 96)
[    53.840] (II) Loading sub module "fb"
[    53.840] (II) LoadModule: "fb"
[    53.840] (II) Loading /usr/lib/xorg/modules/libfb.so
[    53.905] (II) Module fb: vendor="X.Org Foundation"
[    53.905]     compiled for 1.15.1, module version = 1.0.0
[    53.905]     ABI class: X.Org ANSI C Emulation, version 0.4
[    53.905] (II) Loading sub module "ramdac"
[    53.905] (II) LoadModule: "ramdac"
[    53.905] (II) Module "ramdac" already built-in
[    53.905] (--) Depth 24 pixmap format is 32 bpp
[    53.919] (II) RADEON(0): [DRI2] Setup complete
[    53.919] (II) RADEON(0): [DRI2]   DRI driver: r600
[    53.919] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    53.919] (II) RADEON(0): Front buffer size: 3072K
[    53.919] (II) RADEON(0): VRAM usage limit set to 466070K
[    54.001] (==) RADEON(0): Backing store enabled
[    54.001] (II) RADEON(0): Direct rendering enabled
[    54.001] (II) EXA(0): Driver allocated offscreen pixmaps
[    54.001] (II) EXA(0): Driver registered support for the following operations:
[    54.001] (II)         Solid
[    54.001] (II)         Copy
[    54.001] (II)         Composite (RENDER acceleration)
[    54.001] (II)         UploadToScreen
[    54.001] (II)         DownloadFromScreen
[    54.001] (II) RADEON(0): Acceleration enabled
[    54.001] (==) RADEON(0): DPMS enabled
[    54.001] (==) RADEON(0): Silken mouse enabled
[    54.014] (II) RADEON(0): Set up textured video
[    54.014] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    54.014] (II) RADEON(0): [XvMC] Extension initialized.
[    54.014] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    54.039] (--) RandR disabled
[    54.103] (II) SELinux: Disabled on system
[    57.140] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    57.140] (II) AIGLX: enabled GLX_ARB_create_context
[    57.140] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    57.140] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    57.140] (II) AIGLX: enabled GLX_INTEL_swap_event
[    57.140] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    57.140] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    57.140] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    57.140] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    57.141] (II) AIGLX: Loaded and initialized r600
[    57.141] (II) GLX: Initialized DRI2 GL provider for screen 0
[    57.142] (II) RADEON(0): Setting screen physical size to 270 x 203
[    58.173] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    58.207] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    58.212] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    58.212] (II) LoadModule: "evdev"
[    58.212] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    58.319] (II) Module evdev: vendor="X.Org Foundation"
[    58.319]     compiled for 1.15.0, module version = 2.8.2
[    58.319]     Module class: X.Org XInput Driver
[    58.319]     ABI class: X.Org XInput driver, version 20.0
[    58.319] (II) Using input driver 'evdev' for 'Power Button'
[    58.319] (**) Power Button: always reports core events
[    58.320] (**) evdev: Power Button: Device: "/dev/input/event1"
[    58.320] (--) evdev: Power Button: Vendor 0 Product 0x1
[    58.320] (--) evdev: Power Button: Found keys
[    58.320] (II) evdev: Power Button: Configuring as keyboard
[    58.320] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    58.320] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    58.320] (**) Option "xkb_rules" "evdev"
[    58.320] (**) Option "xkb_model" "pc105"
[    58.320] (**) Option "xkb_layout" "fr"
[    58.320] (**) Option "xkb_variant" "oss"
[    58.342] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[    58.354] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    58.354] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    58.354] (II) Using input driver 'evdev' for 'Power Button'
[    58.354] (**) Power Button: always reports core events
[    58.354] (**) evdev: Power Button: Device: "/dev/input/event0"
[    58.354] (--) evdev: Power Button: Vendor 0 Product 0x1
[    58.354] (--) evdev: Power Button: Found keys
[    58.354] (II) evdev: Power Button: Configuring as keyboard
[    58.354] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    58.354] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    58.354] (**) Option "xkb_rules" "evdev"
[    58.355] (**) Option "xkb_model" "pc105"
[    58.355] (**) Option "xkb_layout" "fr"
[    58.355] (**) Option "xkb_variant" "oss"
[    58.355] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/drm/card0
[    58.355] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    58.356] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[    58.356] (II) No input driver specified, ignoring this device.
[    58.356] (II) This device may have been added with another device file.
[    58.360] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/event3)
[    58.360] (**) Logitech USB Mouse: Applying InputClass "evdev pointer catchall"
[    58.360] (II) Using input driver 'evdev' for 'Logitech USB Mouse'
[    58.360] (**) Logitech USB Mouse: always reports core events
[    58.360] (**) evdev: Logitech USB Mouse: Device: "/dev/input/event3"
[    58.360] (--) evdev: Logitech USB Mouse: Vendor 0x46d Product 0xc001
[    58.360] (--) evdev: Logitech USB Mouse: Found 3 mouse buttons
[    58.360] (--) evdev: Logitech USB Mouse: Found scroll wheel(s)
[    58.360] (--) evdev: Logitech USB Mouse: Found relative axes
[    58.360] (--) evdev: Logitech USB Mouse: Found x and y relative axes
[    58.360] (II) evdev: Logitech USB Mouse: Configuring as mouse
[    58.360] (II) evdev: Logitech USB Mouse: Adding scrollwheel support
[    58.360] (**) evdev: Logitech USB Mouse: YAxisMapping: buttons 4 and 5
[    58.360] (**) evdev: Logitech USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    58.360] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    58.360] (II) XINPUT: Adding extended input device "Logitech USB Mouse" (type: MOUSE, id 8)
[    58.360] (II) evdev: Logitech USB Mouse: initialized for relative axes.
[    58.360] (**) Logitech USB Mouse: (accel) keeping acceleration scheme 1
[    58.360] (**) Logitech USB Mouse: (accel) acceleration profile 0
[    58.360] (**) Logitech USB Mouse: (accel) acceleration factor: 2.000
[    58.360] (**) Logitech USB Mouse: (accel) acceleration threshold: 4
[    58.361] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/mouse0)
[    58.361] (II) No input driver specified, ignoring this device.
[    58.361] (II) This device may have been added with another device file.
[    58.361] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    58.361] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    58.361] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    58.361] (**) AT Translated Set 2 keyboard: always reports core events
[    58.361] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    58.361] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    58.361] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    58.362] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    58.362] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    58.362] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    58.362] (**) Option "xkb_rules" "evdev"
[    58.362] (**) Option "xkb_model" "pc105"
[    58.362] (**) Option "xkb_layout" "fr"
[    58.362] (**) Option "xkb_variant" "oss"
[    75.340] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[    75.970] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[    76.007] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[    76.014] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[    77.181] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[    78.385] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[    80.561] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[    80.571] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[    80.582] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[    80.591] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[    80.604] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[   108.251] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[   124.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   124.990] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   125.295] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm

```

Amazing... Did radeon and AIGLX save my system's butt?

---

### Post by Yellow Pasque on 2014-09-12
Mmhmmm.....

---

### Post by marino3 on 2014-09-13
The Gallium thing seems normal.

I got rid of most of the error by installing missing packages:
```

ii  xserver-xorg-video-fbdev                    1:0.4.4-1build1  i386         X.Org X server -- fbdev display driver
ii  xserver-xorg-video-modesetting           0.8.1-1build1  i386            X.Org X server -- Generic modesetting driver
ii  xserver-xorg-video-vesa                     1:2.3.3-1build1  i386         X.Org X server -- VESA display driver
```

So, fglrx cruft again...

dpkg -l '*fglrx*' shows nothing.

```
**dpkg -l '*fglrx*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture     Description
+++-======================-================-================-=================================================
un  fglrx-driver           <none>           <none>           (no description available)
un  fglrx-glx              <none>           <none>           (no description available)

```

I got rid of this last error through a xorg.conf file, but it's still puzzling me.

The desktop is stuck in 1024X768 (instead of 1440X900), and flickers to black whenever I use the mouse wheel or scroll a window.

I'm following tips given on [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) to go forth:

```
**dmesg | egrep 'drm|radeon'**
[    6.251516] [drm] Initialized drm 1.1.0 20060810
[    6.951187] [drm] radeon kernel modesetting enabled.
[    7.220178] [COLOR=#ff0000]fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver[/COLOR]
[    7.674328] [drm] initializing kernel modesetting (RV710 0x1002:0x954F 0x1462:0x1612).
[    7.674345] radeon 0000:02:00.0: PCI: Disallowing DAC for device
[    7.674350] [COLOR=#ff0000]radeon: No suitable DMA available.[/COLOR]
[    7.674369] [drm] register mmio base: 0xDFEE0000
[    7.674372] [drm] register mmio size: 65536
[    7.675064] radeon 0000:02:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    7.675073] radeon 0000:02:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    7.675080] [drm] Detected VRAM RAM=512M, BAR=256M
[    7.675084] [drm] RAM width 64bits DDR
[    7.677773] [drm] radeon: 512M of VRAM memory ready
[    7.677777] [drm] radeon: 1024M of GTT memory ready.
[    7.677795] [drm] Loading RV710 Microcode
[    7.678198] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    7.699426] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[    7.701672] radeon 0000:02:00.0: WB enabled
[    7.701686] radeon 0000:02:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xf6289c00
[    7.701695] radeon 0000:02:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xf6289c0c
[    7.708495] radeon 0000:02:00.0: fence driver on ring 5 use gpu addr 0x000000000005c598 and cpu addr 0xf8a1c598
[    7.708514] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    7.708518] [drm] Driver supports precise vblank timestamp query.
[    7.708567] [drm] radeon: irq initialized.
[    7.756077] [drm] ring test on 0 succeeded in 1 usecs
[    7.756142] [drm] ring test on 3 succeeded in 1 usecs
[    7.941429] [drm] ring test on 5 succeeded in 1 usecs
[    7.941438] [drm] UVD initialized successfully.
[    7.941598] [drm] Enabling audio 0 support
[    7.941631] [drm] ib test on ring 0 succeeded in 0 usecs
[    7.941659] [drm] ib test on ring 3 succeeded in 0 usecs
[    8.091018] [drm] ib test on ring 5 succeeded
[    8.091790] [drm] Radeon Display Connectors
[    8.091799] [drm] Connector 0:
[    8.091803] [drm]   VGA-1
[    8.091808] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    8.091813] [drm]   Encoders:
[    8.091816] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    8.091820] [drm] Connector 1:
[    8.091823] [drm]   DVI-I-1
[    8.091826] [drm]   HPD4
[    8.091831] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[    8.091836] [drm]   Encoders:
[    8.091839] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.091843] [drm]     DFP1: INTERNAL_UNIPHY2
[    8.091872] [drm] Internal thermal controller with fan control
[    8.102157] [drm] radeon: dpm initialized
[    8.262297] [drm] fb mappable at 0xC045E000
[    8.262308] [drm] vram apper at 0xC0000000
[    8.262312] [drm] size 3145728
[    8.262315] [drm] fb depth is 24
[    8.262319] [drm]    pitch is 4096
[    8.262506] fbcon: radeondrmfb (fb0) is primary device
[    8.286435] radeon 0000:02:00.0: fb0: radeondrmfb frame buffer device
[    8.286561] [COLOR=#ff0000]**radeon**[/COLOR] 0000:02:00.0: [COLOR=#ff0000]**registered panic notifier**[/COLOR]
[    8.286700] [drm] Initialized radeon 2.36.0 20080528 for 0000:02:00.0 on minor 0
```

Well, well, well...

---

### Post by marino3 on 2014-09-13
Following tips from [https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI)
The is no "20-radeon.conf" in my /usr/share/X11/xorg.conf.d/
Should I add this file:
```
Section "Device"
    Identifier "Radeon"
    Driver "radeon"
EndSection
```

...  and remove the xorg.conf file? Let's try that.
Ok, nothing changed. Guess it's cleaner though.

---

### Post by marino3 on 2014-09-13
Got rid of this conflict. Cool.

Still stuck in 1024X768. Let's see to it.

I'll try to add a 30-screen.conf salvaged from my old xorg.conf in /usr/share/X11/xorg.conf.d/ :

```
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "ACER"
    ModelName    "1440X900@60HZ"
    HorizSync    30-80
    VertRefresh  55-75
    Option        "DPMS"
    Option        "PreferredMode" "1440x900"
EndSection
```

---

### Post by marino3 on 2014-09-13
Seem to be ignored... Following tips on [http://forums.gentoo.org/viewtopic-t-970048-start-0.html](http://forums.gentoo.org/viewtopic-t-970048-start-0.html)

**xrandr** gives :

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
```

In xorg.0.log:

[    53.408] (II) RADEON(0): EDID for output VGA-0
[    53.409] (II) RADEON(0): Printing probed modes for output VGA-0
[    53.410] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    53.410] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    53.410] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    53.410] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    53.410] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)

So, it seems the screen doesn't gives its correct EDID, which should go up to 1440X900.

Adding a **14-device.conf**:
```
Section "Device"
    Identifier    "Radeon"
    Driver    "radeon"
    Option    "monitor-VGA-0" "Screen0"
EndSection
```

... a **15-monitor.conf**:
```
Section "Monitor"
    Identifier        "Screen0"
    VendorName     "ACER"
    Modelname    "X193W LCD MONITOR"
    HorizSync        30-82
    VertRefresh      50-75
    Option            "DPMS"
    Option            "PreferredMode" "1440x900"
    ModeLine           "1440x900_60.00" 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync
    Gamma         1.0
EndSection
```

... and a **16-screen.conf**:
```
Section "Screen"
    Identifier        "Screen0"
    Device            "Radeon"
    Monitor           "ACER X193W LCD MONITOR"
    DefaultDepth     24
    SubSection        "Display"
        Viewport   0 0
        Depth     8
        Modes           "1280x1024"        "1024x768"        "800x600"        "640x480"
    EndSubSection
    SubSection        "Display"
        Viewport   0 0
        Depth     16
        Modes           "1280x1024"        "1024x768"        "800x600"        "640x480"
    EndSubSection
    SubSection        "Display"
        Viewport   0 0
        Depth     24
        Modes           "1440x900"        "1280x1024"        "1024x768"        "800x600"        "640x480"
    EndSubSection
EndSection
```

sudo reboot now...

---

### Post by marino3 on 2014-09-13
AND IT WORKED! YES!

In **xorg.0.log** :
```
[    51.676] (II) RADEON(0): Printing probed modes for output VGA-0
[    51.676] (II) RADEON(0): Modeline "1440x900_60.00"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    51.676] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    51.676] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    51.676] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    51.676] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    51.676] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
```

**xrandr**
```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
VGA-0 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1440x900_60.00   59.9* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
```

The flickering is painful when scrolling. May be some fine-tuning. It's peculiar, for the flickering doesn't always occur. In firefox open office writer and jedit, none. In Scite, dreadful... ([http://ubuntuforums.org/showthread.php?t=2203954](http://ubuntuforums.org/showthread.php?t=2203954) and [http://ubuntuforums.org/showthread.php?t=2220468](http://ubuntuforums.org/showthread.php?t=2220468) tell me it's a Scite version issue...)

I still can see "[    8.254627] radeon 0000:02:00.0: registered panic notifier" in **xorg.0.log**....

Is it a serious issue? My Gnome 3 seems working fine.

---

### Post by Yellow Pasque on 2014-09-13
> **marino3 said:**
> I still can see "[    8.254627] radeon 0000:02:00.0: registered panic notifier" in **xorg.0.log**.... Is it a serious issue?

No, it's not an issue. It's just a standard informative message.

As for the flickering, I'm not sure what you can do. I don't use Unity/Compiz, so maybe there is a vsync setting there that is not enabled by default?

---

### Post by marino3 on 2014-09-14
I use Gnome. Never get used to Unity.
About Scite, I'll wait for the next version.
Wow. Everything is working fine so far.
Recollecting, I've spent nearly 3 days for something that needed, what? Half an hour... Damn me.
Thank for your help, Temüjin.

---

