---
title: "nVidia and Bumblebee"
date: 2014-06-06
forum: Hardware
---

### Post by zrussellneely on 2014-06-06
Hi everyone,

So up until earlier today, everything was going well. My laptop (with an Intel integrated graphics card AND an nVidia 5200 M) was running smoothly. My battery life was great since I had finally gotten Bumblebee to work, and I could even optirun most programs (execpt a few in WINE, but meh).

Then. Despite my careful package installing and nVidia-configuring, everything went wrong. My battery died and when I rebooted my computer, the resolution was bad. Not "this computer is running in low graphics mode" bad, but pretty ungood. I looked in "System Settings > Displays", but there was nothing except one even lower resolution to select from. Ok, I thought, I've fixed things like this before, I can do it again. But. I could not. So now I've got a pretty low resolution, my nice Unity 3D is now plain Unity (instead of my carefully configured 6-workspace layout, I have the default 4), and strangely enough my backgrounds look the same as ever.

Here's the output of every relevant command I could think of and find online. If anyone has any ideas, please help! It looks to me like the integrated card isn't being found, but I'm not sure what I can do about that.

sudo dpkg -l | grep nouveau
```
ii  libdrm-nouveau1a                                            2.4.46-1ubuntu0.0.0.1                               Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a:i386                                       2.4.46-1ubuntu0.0.0.1                               Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2                                             2.4.46-1ubuntu0.0.0.1                               Userspace interface to nouveau-specific kernel DRM services -- runtime
rc  libdrm-nouveau2:i386                                        2.4.46-1ubuntu0.0.0.1                               Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  xserver-xorg-video-nouveau                                  1:0.0.16+git20111201+b5534a1-1build3  

```
sudo dpkg -l | grep nvidia
```
ii  bumblebee-nvidia                                            3.2.1-90~preciseppa1                                NVIDIA Optimus support using the proprietary NVIDIA driver
ii  nvidia-304                                                  304.121-0ubuntu1~xedgers12.04.2                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current                                              304.121-0ubuntu1~xedgers12.04.2                     Transitional package for nvidia-current
ii  nvidia-settings                                             331.38-0ubuntu0.0.1~xedgers~precise1                Tool for configuring the NVIDIA graphics driver
```

sudo dpkg -l | grep bumblebee
```
ii  bumblebee                                                   3.2.1-90~preciseppa1                                NVIDIA Optimus support
ii  bumblebee-nvidia                                            3.2.1-90~preciseppa1                                NVIDIA Optimus support using the proprietary NVIDIA driver
```

sudo jockey-text -l
```
kmod:nvidia_304 - nvidia_304 (Proprietary, Disabled, Not in use)
kmod:nvidia_304_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_331 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
kmod:nvidia_331_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)
```

sudo service bumblebeed status
```
bumblebeed stop/waiting
```

dmesg | tail -n15
  ```
269.769903] init: bumblebeed main process ended, respawning
[  269.784725] init: bumblebeed main process (21801) terminated with status 1
[  269.784767] init: bumblebeed main process ended, respawning
[  269.799355] init: bumblebeed main process (21809) terminated with status 1
[  269.799401] init: bumblebeed main process ended, respawning
[  269.814726] init: bumblebeed main process (21817) terminated with status 1
[  269.814767] init: bumblebeed main process ended, respawning
[  269.829612] init: bumblebeed main process (21825) terminated with status 1
[  269.829660] init: bumblebeed main process ended, respawning
[  269.844355] init: bumblebeed main process (21833) terminated with status 1
[  269.844395] init: bumblebeed main process ended, respawning
[  269.859188] init: bumblebeed main process (21841) terminated with status 1
[  269.859227] init: bumblebeed respawning too fast, stopped
[  924.544482] audit_printk_skb: 66 callbacks suppressed
[  924.544488] type=1400 audit(1402091078.261:34): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1290 comm="cupsd" pid=1290 comm="cupsd" capability=36  capname="block_suspend"
```

cat /var/log/syslog | grep bumblebeed | tail -n5
```
Jun  6 17:33:42 [hostname]-latitude-pc bumblebeed[21809]: No integrated video card found, quitting.
Jun  6 17:33:42 [hostname]-latitude-pc bumblebeed[21817]: No integrated video card found, quitting.
Jun  6 17:33:42 [hostname]-latitude-pc bumblebeed[21825]: No integrated video card found, quitting.
Jun  6 17:33:42 [hostname]-latitude-pc bumblebeed[21833]: No integrated video card found, quitting.
Jun  6 17:33:42 [hostname]-latitude-pc bumblebeed[21841]: No integrated video card found, quitting.
```

lspci -nn | grep '\[030[02]\]'
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108GLM [NVS 5200M] [10de:0dfc] (rev a1)
```

---

### Post by Yellow Pasque on 2014-06-07
> Jun 6 17:33:42 [hostname]-latitude-pc bumblebeed[21809]: No integrated video card found, quitting.

Is it possible that BIOS settings got reset/changed from the dead battery? Can you give /var/log/Xorg.0.log? (use code tags)

---

### Post by zrussellneely on 2014-06-07
I looked in the bios settings and didn't find anything that said Integrated Graphics was disabled - but optimus is turned off. Here's the Xorg Log:

```
[    33.911]     NumberOfBanks: 1[    33.911]     MemoryModel: 6
[    33.911]     BankSize: 0
[    33.911]     NumberOfImages: 6
[    33.911]     RedMaskSize: 5
[    33.911]     RedFieldPosition: 11
[    33.911]     GreenMaskSize: 6
[    33.911]     GreenFieldPosition: 5
[    33.911]     BlueMaskSize: 5
[    33.911]     BlueFieldPosition: 0
[    33.911]     RsvdMaskSize: 0
[    33.911]     RsvdFieldPosition: 0
[    33.911]     DirectColorModeInfo: 0
[    33.911]     PhysBasePtr: 0xf1000000
[    33.911]     LinBytesPerScanLine: 1280
[    33.911]     BnkNumberOfImagePages: 6
[    33.911]     LinNumberOfImagePages: 6
[    33.911]     LinRedMaskSize: 5
[    33.911]     LinRedFieldPosition: 11
[    33.911]     LinGreenMaskSize: 6
[    33.911]     LinGreenFieldPosition: 5
[    33.911]     LinBlueMaskSize: 5
[    33.911]     LinBlueFieldPosition: 0
[    33.911]     LinRsvdMaskSize: 0
[    33.911]     LinRsvdFieldPosition: 0
[    33.911]     MaxPixelClock: 229500000
[    33.912] *Mode: 13e (640x400)
[    33.912]     ModeAttributes: 0x3bf
[    33.912]     WinAAttributes: 0x7
[    33.912]     WinBAttributes: 0x0
[    33.912]     WinGranularity: 64
[    33.912]     WinSize: 64
[    33.912]     WinASegment: 0xa000
[    33.912]     WinBSegment: 0x0
[    33.912]     WinFuncPtr: 0xc0008130
[    33.912]     BytesPerScanline: 2560
[    33.912]     XResolution: 640
[    33.912]     YResolution: 400
[    33.912]     XCharSize: 8
[    33.912]     YCharSize: 16
[    33.912]     NumberOfPlanes: 1
[    33.912]     BitsPerPixel: 32
[    33.912]     NumberOfBanks: 1
[    33.912]     MemoryModel: 6
[    33.912]     BankSize: 0
[    33.912]     NumberOfImages: 2
[    33.912]     RedMaskSize: 8
[    33.912]     RedFieldPosition: 16
[    33.912]     GreenMaskSize: 8
[    33.912]     GreenFieldPosition: 8
[    33.912]     BlueMaskSize: 8
[    33.912]     BlueFieldPosition: 0
[    33.912]     RsvdMaskSize: 8
[    33.912]     RsvdFieldPosition: 24
[    33.912]     DirectColorModeInfo: 0
[    33.912]     PhysBasePtr: 0xf1000000
[    33.912]     LinBytesPerScanLine: 2560
[    33.912]     BnkNumberOfImagePages: 2
[    33.912]     LinNumberOfImagePages: 2
[    33.912]     LinRedMaskSize: 8
[    33.912]     LinRedFieldPosition: 16
[    33.912]     LinGreenMaskSize: 8
[    33.912]     LinGreenFieldPosition: 8
[    33.913]     LinBlueMaskSize: 8
[    33.913]     LinBlueFieldPosition: 0
[    33.913]     LinRsvdMaskSize: 8
[    33.913]     LinRsvdFieldPosition: 24
[    33.913]     MaxPixelClock: 229500000
[    33.914] Mode: 14b (1366x768)
[    33.914]     ModeAttributes: 0x3bf
[    33.914]     WinAAttributes: 0x7
[    33.914]     WinBAttributes: 0x0
[    33.914]     WinGranularity: 64
[    33.914]     WinSize: 64
[    33.914]     WinASegment: 0xa000
[    33.914]     WinBSegment: 0x0
[    33.914]     WinFuncPtr: 0xc0008130
[    33.914]     BytesPerScanline: 1368
[    33.914]     XResolution: 1366
[    33.914]     YResolution: 768
[    33.914]     XCharSize: 8
[    33.914]     YCharSize: 16
[    33.914]     NumberOfPlanes: 1
[    33.914]     BitsPerPixel: 8
[    33.914]     NumberOfBanks: 1
[    33.914]     MemoryModel: 4
[    33.914]     BankSize: 0
[    33.914]     NumberOfImages: 0
[    33.914]     RedMaskSize: 0
[    33.914]     RedFieldPosition: 0
[    33.914]     GreenMaskSize: 0
[    33.914]     GreenFieldPosition: 0
[    33.914]     BlueMaskSize: 0
[    33.914]     BlueFieldPosition: 0
[    33.914]     RsvdMaskSize: 0
[    33.914]     RsvdFieldPosition: 0
[    33.914]     DirectColorModeInfo: 0
[    33.914]     PhysBasePtr: 0xf1000000
[    33.914]     LinBytesPerScanLine: 1368
[    33.914]     BnkNumberOfImagePages: 0
[    33.914]     LinNumberOfImagePages: 0
[    33.914]     LinRedMaskSize: 0
[    33.914]     LinRedFieldPosition: 0
[    33.914]     LinGreenMaskSize: 0
[    33.914]     LinGreenFieldPosition: 0
[    33.914]     LinBlueMaskSize: 0
[    33.914]     LinBlueFieldPosition: 0
[    33.914]     LinRsvdMaskSize: 0
[    33.914]     LinRsvdFieldPosition: 0
[    33.914]     MaxPixelClock: 229500000
[    33.915] Mode: 14c (1366x768)
[    33.915]     ModeAttributes: 0x3bf
[    33.915]     WinAAttributes: 0x7
[    33.915]     WinBAttributes: 0x0
[    33.915]     WinGranularity: 64
[    33.915]     WinSize: 64
[    33.915]     WinASegment: 0xa000
[    33.915]     WinBSegment: 0x0
[    33.915]     WinFuncPtr: 0xc0008130
[    33.915]     BytesPerScanline: 2736
[    33.915]     XResolution: 1366
[    33.915]     YResolution: 768
[    33.915]     XCharSize: 8
[    33.915]     YCharSize: 16
[    33.915]     NumberOfPlanes: 1
[    33.915]     BitsPerPixel: 16
[    33.915]     NumberOfBanks: 1
[    33.915]     MemoryModel: 6
[    33.915]     BankSize: 0
[    33.915]     NumberOfImages: 1
[    33.915]     RedMaskSize: 5
[    33.915]     RedFieldPosition: 11
[    33.915]     GreenMaskSize: 6
[    33.915]     GreenFieldPosition: 5
[    33.915]     BlueMaskSize: 5
[    33.915]     BlueFieldPosition: 0
[    33.915]     RsvdMaskSize: 0
[    33.915]     RsvdFieldPosition: 0
[    33.915]     DirectColorModeInfo: 0
[    33.915]     PhysBasePtr: 0xf1000000
[    33.915]     LinBytesPerScanLine: 2736
[    33.915]     BnkNumberOfImagePages: 1
[    33.915]     LinNumberOfImagePages: 1
[    33.915]     LinRedMaskSize: 5
[    33.915]     LinRedFieldPosition: 11
[    33.915]     LinGreenMaskSize: 6
[    33.915]     LinGreenFieldPosition: 5
[    33.915]     LinBlueMaskSize: 5
[    33.915]     LinBlueFieldPosition: 0
[    33.915]     LinRsvdMaskSize: 0
[    33.915]     LinRsvdFieldPosition: 0
[    33.915]     MaxPixelClock: 229500000
[    33.917] *Mode: 14d (1366x768)
[    33.917]     ModeAttributes: 0x3bf
[    33.917]     WinAAttributes: 0x7
[    33.917]     WinBAttributes: 0x0
[    33.917]     WinGranularity: 64
[    33.917]     WinSize: 64
[    33.917]     WinASegment: 0xa000
[    33.917]     WinBSegment: 0x0
[    33.917]     WinFuncPtr: 0xc0008130
[    33.917]     BytesPerScanline: 5472
[    33.917]     XResolution: 1366
[    33.917]     YResolution: 768
[    33.917]     XCharSize: 8
[    33.917]     YCharSize: 16
[    33.917]     NumberOfPlanes: 1
[    33.917]     BitsPerPixel: 32
[    33.917]     NumberOfBanks: 1
[    33.917]     MemoryModel: 6
[    33.917]     BankSize: 0
[    33.917]     NumberOfImages: 0
[    33.917]     RedMaskSize: 8
[    33.917]     RedFieldPosition: 16
[    33.917]     GreenMaskSize: 8
[    33.917]     GreenFieldPosition: 8
[    33.917]     BlueMaskSize: 8
[    33.917]     BlueFieldPosition: 0
[    33.917]     RsvdMaskSize: 8
[    33.917]     RsvdFieldPosition: 24
[    33.917]     DirectColorModeInfo: 0
[    33.917]     PhysBasePtr: 0xf1000000
[    33.917]     LinBytesPerScanLine: 5472
[    33.917]     BnkNumberOfImagePages: 0
[    33.917]     LinNumberOfImagePages: 0
[    33.917]     LinRedMaskSize: 8
[    33.917]     LinRedFieldPosition: 16
[    33.917]     LinGreenMaskSize: 8
[    33.917]     LinGreenFieldPosition: 8
[    33.917]     LinBlueMaskSize: 8
[    33.917]     LinBlueFieldPosition: 0
[    33.917]     LinRsvdMaskSize: 8
[    33.917]     LinRsvdFieldPosition: 24
[    33.917]     MaxPixelClock: 229500000
[    33.917] 
[    33.917] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    33.917] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    33.917] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    33.917] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    33.917] (WW) VESA(0): Unable to estimate virtual size
[    33.917] (II) VESA(0): Not using built-in mode "1366x768" (no mode of this name)
[    33.917] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    33.917] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    33.917] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    33.917] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    33.917] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    33.917] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    33.917] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    33.917] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    33.917] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    33.917] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    33.917] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    33.917] (WW) VESA(0): Unable to estimate virtual size
[    33.917] (II) VESA(0): Not using built-in mode "1366x768" (hsync out of range)
[    33.917] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    33.917] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    33.917] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    33.917] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    33.917] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    33.917] (**) VESA(0): *Built-in mode "1024x768"
[    33.917] (**) VESA(0): *Built-in mode "800x600"
[    33.917] (**) VESA(0): *Built-in mode "640x480"
[    33.917] (==) VESA(0): DPI set to (96, 96)
[    33.917] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    33.918] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    33.918] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    33.918] (**) VESA(0): Using "Shadow Framebuffer"
[    33.918] (II) Loading sub module "shadow"
[    33.918] (II) LoadModule: "shadow"
[    33.919] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    34.042] (II) Module shadow: vendor="X.Org Foundation"
[    34.042]     compiled for 1.11.3, module version = 1.1.0
[    34.042]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.042] (II) Loading sub module "fb"
[    34.042] (II) LoadModule: "fb"
[    34.042] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.149] (II) Module fb: vendor="X.Org Foundation"
[    34.149]     compiled for 1.11.3, module version = 1.0.0
[    34.149]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.149] (II) UnloadModule: "fbdev"
[    34.149] (II) Unloading fbdev
[    34.149] (II) UnloadModule: "fbdevhw"
[    34.149] (II) Unloading fbdevhw
[    34.149] (==) Depth 24 pixmap format is 32 bpp
[    34.149] (II) Loading sub module "int10"
[    34.149] (II) LoadModule: "int10"
[    34.149] (II) Loading /usr/lib/xorg/modules/libint10.so
[    34.149] (II) Module int10: vendor="X.Org Foundation"
[    34.149]     compiled for 1.11.3, module version = 1.0.0
[    34.149]     ABI class: X.Org Video Driver, version 11.0
[    34.149] (II) VESA(0): initializing int10
[    34.149] (II) VESA(0): Bad V_BIOS checksum
[    34.149] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    34.200] (II) VESA(0): VESA BIOS detected
[    34.200] (II) VESA(0): VESA VBE Version 3.0
[    34.200] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    34.200] (II) VESA(0): VESA VBE OEM: NVIDIA
[    34.200] (II) VESA(0): VESA VBE OEM Software Rev: 112.8
[    34.200] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    34.200] (II) VESA(0): VESA VBE OEM Product: nVIDIA N12M-NS1  - dalmore1
[    34.200] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    34.200] (II) VESA(0): virtual address = 0x7f507c2bd000,
    physical address = 0xf1000000, size = 14680064
[    34.204] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    34.346] (==) VESA(0): Default visual is TrueColor
[    34.375] (==) VESA(0): Backing store disabled
[    34.376] (==) VESA(0): DPMS enabled
[    34.376] (==) RandR enabled
[    34.376] (II) Initializing built-in extension Generic Event Extension
[    34.376] (II) Initializing built-in extension SHAPE
[    34.376] (II) Initializing built-in extension MIT-SHM
[    34.376] (II) Initializing built-in extension XInputExtension
[    34.376] (II) Initializing built-in extension XTEST
[    34.376] (II) Initializing built-in extension BIG-REQUESTS
[    34.376] (II) Initializing built-in extension SYNC
[    34.376] (II) Initializing built-in extension XKEYBOARD
[    34.376] (II) Initializing built-in extension XC-MISC
[    34.376] (II) Initializing built-in extension SECURITY
[    34.376] (II) Initializing built-in extension XINERAMA
[    34.376] (II) Initializing built-in extension XFIXES
[    34.376] (II) Initializing built-in extension RENDER
[    34.376] (II) Initializing built-in extension RANDR
[    34.376] (II) Initializing built-in extension COMPOSITE
[    34.376] (II) Initializing built-in extension DAMAGE
[    34.457] (II) AIGLX: Screen 0 is not DRI2 capable
[    34.457] (II) AIGLX: Screen 0 is not DRI capable
[    38.640] (II) AIGLX: Loaded and initialized swrast
[    38.640] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    39.758] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.781] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    39.782] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.782] (II) LoadModule: "evdev"
[    39.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.126] (II) Module evdev: vendor="X.Org Foundation"
[    40.126]     compiled for 1.11.3, module version = 2.7.0
[    40.126]     Module class: X.Org XInput Driver
[    40.126]     ABI class: X.Org XInput driver, version 16.0
[    40.126] (II) Using input driver 'evdev' for 'Power Button'
[    40.126] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.126] (**) Power Button: always reports core events
[    40.126] (**) evdev: Power Button: Device: "/dev/input/event3"
[    40.126] (--) evdev: Power Button: Vendor 0 Product 0x1
[    40.126] (--) evdev: Power Button: Found keys
[    40.126] (II) evdev: Power Button: Configuring as keyboard
[    40.126] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    40.126] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    40.126] (**) Option "xkb_rules" "evdev"
[    40.126] (**) Option "xkb_model" "pc105"
[    40.126] (**) Option "xkb_layout" "us"
[    40.126] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    40.126] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    40.126] (II) Using input driver 'evdev' for 'Video Bus'
[    40.126] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.126] (**) Video Bus: always reports core events
[    40.126] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    40.126] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    40.126] (--) evdev: Video Bus: Found keys
[    40.126] (II) evdev: Video Bus: Configuring as keyboard
[    40.126] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14/LNXVIDEO:00/input/input5/event5"
[    40.126] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    40.126] (**) Option "xkb_rules" "evdev"
[    40.126] (**) Option "xkb_model" "pc105"
[    40.126] (**) Option "xkb_layout" "us"
[    40.126] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    40.126] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    40.126] (II) Using input driver 'evdev' for 'Power Button'
[    40.126] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.126] (**) Power Button: always reports core events
[    40.126] (**) evdev: Power Button: Device: "/dev/input/event1"
[    40.126] (--) evdev: Power Button: Vendor 0 Product 0x1
[    40.126] (--) evdev: Power Button: Found keys
[    40.126] (II) evdev: Power Button: Configuring as keyboard
[    40.126] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    40.126] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    40.126] (**) Option "xkb_rules" "evdev"
[    40.126] (**) Option "xkb_model" "pc105"
[    40.126] (**) Option "xkb_layout" "us"
[    40.127] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    40.127] (II) No input driver specified, ignoring this device.
[    40.127] (II) This device may have been added with another device file.
[    40.127] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    40.127] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    40.127] (II) Using input driver 'evdev' for 'Sleep Button'
[    40.127] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.127] (**) Sleep Button: always reports core events
[    40.127] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    40.127] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    40.127] (--) evdev: Sleep Button: Found keys
[    40.127] (II) evdev: Sleep Button: Configuring as keyboard
[    40.127] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    40.127] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    40.127] (**) Option "xkb_rules" "evdev"
[    40.127] (**) Option "xkb_model" "pc105"
[    40.127] (**) Option "xkb_layout" "us"
[    40.127] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event12)
[    40.127] (II) No input driver specified, ignoring this device.
[    40.127] (II) This device may have been added with another device file.
[    40.127] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event13)
[    40.127] (II) No input driver specified, ignoring this device.
[    40.127] (II) This device may have been added with another device file.
[    40.127] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[    40.127] (II) No input driver specified, ignoring this device.
[    40.127] (II) This device may have been added with another device file.
[    40.128] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event15)
[    40.128] (II) No input driver specified, ignoring this device.
[    40.128] (II) This device may have been added with another device file.
[    40.128] (II) config/udev: Adding input device Laptop_Integrated_Webcam_E4HD (/dev/input/event16)
[    40.128] (**) Laptop_Integrated_Webcam_E4HD: Applying InputClass "evdev keyboard catchall"
[    40.128] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_E4HD'
[    40.128] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.128] (**) Laptop_Integrated_Webcam_E4HD: always reports core events
[    40.128] (**) evdev: Laptop_Integrated_Webcam_E4HD: Device: "/dev/input/event16"
[    40.128] (--) evdev: Laptop_Integrated_Webcam_E4HD: Vendor 0xc45 Product 0x648b
[    40.128] (--) evdev: Laptop_Integrated_Webcam_E4HD: Found keys
[    40.128] (II) evdev: Laptop_Integrated_Webcam_E4HD: Configuring as keyboard
[    40.128] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input16/event16"
[    40.128] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_E4HD" (type: KEYBOARD, id 10)
[    40.128] (**) Option "xkb_rules" "evdev"
[    40.128] (**) Option "xkb_model" "pc105"
[    40.128] (**) Option "xkb_layout" "us"
[    40.128] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    40.128] (II) No input driver specified, ignoring this device.
[    40.128] (II) This device may have been added with another device file.
[    40.128] (II) config/udev: Adding input device HDA Intel PCH Dock Line Out (/dev/input/event11)
[    40.128] (II) No input driver specified, ignoring this device.
[    40.128] (II) This device may have been added with another device file.
[    40.128] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    40.128] (II) No input driver specified, ignoring this device.
[    40.128] (II) This device may have been added with another device file.
[    40.128] (II) config/udev: Adding input device HDA Intel PCH Dock Mic (/dev/input/event9)
[    40.128] (II) No input driver specified, ignoring this device.
[    40.128] (II) This device may have been added with another device file.
[    40.129] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    40.129] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    40.129] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    40.129] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.129] (**) AT Translated Set 2 keyboard: always reports core events
[    40.129] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    40.129] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    40.129] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    40.129] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    40.129] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    40.129] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    40.129] (**) Option "xkb_rules" "evdev"
[    40.129] (**) Option "xkb_model" "pc105"
[    40.129] (**) Option "xkb_layout" "us"
[    40.129] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    40.129] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    40.129] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[    40.129] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.129] (**) PS/2 Generic Mouse: always reports core events
[    40.129] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event7"
[    40.129] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[    40.129] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[    40.129] (--) evdev: PS/2 Generic Mouse: Found relative axes
[    40.129] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[    40.129] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[    40.129] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    40.129] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.129] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    40.129] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 12)
[    40.129] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[    40.129] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[    40.129] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[    40.129] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[    40.129] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[    40.129] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[    40.129] (II) No input driver specified, ignoring this device.
[    40.129] (II) This device may have been added with another device file.
[    40.130] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event6)
[    40.130] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    40.130] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    40.130] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.130] (**) Dell WMI hotkeys: always reports core events
[    40.130] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event6"
[    40.130] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    40.130] (--) evdev: Dell WMI hotkeys: Found keys
[    40.130] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    40.130] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    40.130] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[    40.130] (**) Option "xkb_rules" "evdev"
[    40.130] (**) Option "xkb_model" "pc105"
[    40.130] (**) Option "xkb_layout" "us"
[    75.768] (II) XKB: reuse xkmfile /var/lib/xkb/server-4D75FCE2617879BDD3AB3013B11AFEEBB1EBF28F.xkm

```

---

### Post by Yellow Pasque on 2014-06-07
Have you tried turning Optimus on in the BIOS?

---

