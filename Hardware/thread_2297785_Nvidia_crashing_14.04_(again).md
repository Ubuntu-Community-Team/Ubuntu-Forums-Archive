---
title: "Nvidia crashing 14.04 (again)"
date: 2015-10-06
forum: Hardware
---

### Post by mistcloud-misty on 2015-10-06
Graphics card: Nvidia GeForce 940m

The graphics card works fine until I do an update that involves a kernel or anything major, and then it starts crashing the computer. Sometimes instantly, sometimes 5 minutes later, sometimes 30 minutes later, on every kernel, except recovery mode (using the integrated processor's graphics, Intel). 

The first time it happened, all I had to do was purge all the Nvidia drivers using the command, reboot, and everything worked fine. Now I had updates again, and that didn't fix it; reinstalling the desktop didn't fix it; reinstalling unity didn't fix it. 

I can only use my laptop reliably in recovery mode, but the resolution is stuck at 800x600 which doesn't usually work well with many websites. 

What can I do to fix this?

Will upgrading to 15.04 help because it is newer software (newer tends to have more support for newer cards apparently)? Will "Bumblebee" software help? When I crash, I can't go the text only mode, because it 'really' crashed the entire system - only hard reboot brings it back. 

Older kernel crashes too now. Will the graphics card just not work with Ubuntu at all and should I expect to have the same problems every single time I get an update? I only used drivers from additional drivers. I never downloaded from Nvidia or installed any PPAs. 

I would tolerate using Intel-only mode for a short while for normal browsing if I could change the resolution, but obviously that's not a long-term fix.

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Hello;

How are you installing the driver ? 
That is useful information and we do need to know and/or find out.
If from OEM or PPA then yes, the driver is broke in a kernel upgrade . That driver is built against the old kernel and does require re-building the driver with the new kernel. That driver is not ubuntu and it is not ubuntu's fault !
If you want ubuntu to cope with the graphic's driver in a sane manner, install the driver from our software repository.

Show us what we are working with:
Post back the results - Between Code Tags, please - of terminal commands:
```

lspci | grep "VGA\|3D"
dpkg -l | grep -i nvidia
sudo ubuntu-drivers list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

and let us consider purging the current driver(s) and (RE-)installing from the repo.

Sounds reasonable
[INDENT][INDENT][INDENT][INDENT]to me
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2015-10-06
[FONT=arial]I have installed all drivers directly from Additional Drivers in the software packages - right now I am crashing using the open source, Nouveau driver. [/FONT]

This is from recovery mode since I crash far before I can do anything from terminal in regular kernel.

```
 lspci | grep "VGA\|3D"
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
04:00.0 3D controller: NVIDIA Corporation Device 1347 (rev a2)
```

```
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                                304.128-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library
ii  libcuda1-346                                                346.96-0ubuntu0.0.1                                 amd64        NVIDIA CUDA runtime library

```

```
sudo ubuntu-drivers list
[sudo] password for arcane: 
nvidia-346
nvidia-346-updates
```


However, I have found this section in my kernel log and I wonder if it has to do with crashing or if it's entirely unrelated. 

```
Oct  6 15:23:37 arcane-X555LB kernel: [    0.047109] Queued invalidation will be enabled to support x2apic and Intr-remapping.
Oct  6 15:23:37 arcane-X555LB kernel: [    0.047111] Your BIOS is broken and requested that x2apic be disabled.
Oct  6 15:23:37 arcane-X555LB kernel: [    0.047111] This will slightly decrease performance.
```

There is a large amount of invalid characters in the kernel log as well.

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Welp;

Yeah, I do agree with you that there are issues in bios with how ACPI is being handled. Unfortunately for you, I know nothing about that type of a problem. But getting that corrected is the 1st order of business . We will await others here who have the experience to advise.

Now as to the driver issue. We have an in-complete install as the 'nvidi-prime' (hybrid grahics) and driver packages are not installed. While we await advisement on the ACPI issue, let's look at what we need to do for getting the nvidia driver to install.
Perhaps at this time " libcuda1-346 " is in conflict with the nouveau driver .
Post back :
```

sudo lshw -C display
ls -al /etc/X11/Xorg.conf
cat /var/log/Xorg.0.log
cat ~/.Xsession-errors

``` looking to differentiate between system config and driver issues and as well a better understanding of the hardware .

Complicates things that several issues are at play here. 

[INDENT][INDENT]bios is where every thing
[INDENT][INDENT][INDENT][INDENT]starts
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2015-10-06
```
sudo lshw -C display
[sudo] password for arcane: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a1000000-a1ffffff memory:b0000000-bfffffff ioport:5000(size=64)
  *-display UNCLAIMED
       description: 3D controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:a2000000-a2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:a3000000-a307ffff

```

```
ls -al /etc/X11/Xorg.conf
ls: cannot access /etc/X11/Xorg.conf: No such file or directory

``` 

When I check the folder, I have .conf files with dates only: 09292015, 10052015, and 10062015. 
 
```
ls -al /etc/X11/xorg.conf.09292015
-rw-r--r-- 1 root root 593 Sep 29 15:30 /etc/X11/xorg.conf.09292015
arcane@arcane-X555LB:~$ ls -al /etc/X11/xorg.conf.10052015
-rw-r--r-- 1 root root 85 Oct  5 15:48 /etc/X11/xorg.conf.10052015
arcane@arcane-X555LB:~$ ls -al /etc/X11/xorg.conf.10062015
-rw-r--r-- 1 root root 593 Oct  6 15:21 /etc/X11/xorg.conf.10062015
```

```
cat /var/log/Xorg.0.log
[    22.629] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    22.629] X Protocol Version 11, Revision 0
[    22.629] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    22.629] Current Operating System: Linux arcane-X555LB 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64
[    22.629] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic.efi.signed root=UUID=b320ac20-ec61-42ec-8900-f1b181a2d24e ro recovery nomodeset noprompt persistent
[    22.629] Build Date: 11 September 2015  10:33:14AM
[    22.629] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see http://www.ubuntu.com/support) 
[    22.629] Current version of pixman: 0.30.2
[    22.629]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.629] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.629] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  6 15:50:58 2015
[    22.644] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.645] (==) No Layout section.  Using the first Screen section.
[    22.645] (==) No screen section available. Using defaults.
[    22.645] (**) |-->Screen "Default Screen Section" (0)
[    22.645] (**) |   |-->Monitor "<default monitor>"
[    22.645] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    22.645] (==) Automatically adding devices
[    22.645] (==) Automatically enabling devices
[    22.645] (==) Automatically adding GPU devices
[    22.645] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.645]     Entry deleted from font path.
[    22.645] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.645]     Entry deleted from font path.
[    22.645] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.645]     Entry deleted from font path.
[    22.645] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.645]     Entry deleted from font path.
[    22.645] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.645]     Entry deleted from font path.
[    22.645] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    22.645] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.645] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.645] (II) Loader magic: 0x7f92deadec60
[    22.645] (II) Module ABI versions:
[    22.645]     X.Org ANSI C Emulation: 0.4
[    22.645]     X.Org Video Driver: 19.0
[    22.645]     X.Org XInput driver : 21.0
[    22.645]     X.Org Server Extension : 9.0
[    22.646] (--) PCI:*(0:0:2:0) 8086:1616:1043:1a6d rev 9, Mem @ 0xa1000000/16777216, 0xb0000000/268435456, I/O @ 0x00005000/64
[    22.646] (--) PCI: (0:4:0:0) 10de:1347:1043:1a6d rev 162, Mem @ 0xa2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    22.646] (II) LoadModule: "glx"
[    22.737] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.948] (II) Module glx: vendor="X.Org Foundation"
[    22.948]     compiled for 1.17.1, module version = 1.0.0
[    22.948]     ABI class: X.Org Server Extension, version 9.0
[    22.948] (==) AIGLX enabled
[    22.948] (==) Matched intel as autoconfigured driver 0
[    22.948] (==) Matched modesetting as autoconfigured driver 1
[    22.948] (==) Matched fbdev as autoconfigured driver 2
[    22.948] (==) Matched vesa as autoconfigured driver 3
[    22.948] (==) Assigned the driver to the xf86ConfigLayout
[    22.948] (II) LoadModule: "intel"
[    22.949] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.962] (II) Module intel: vendor="X.Org Foundation"
[    22.962]     compiled for 1.17.1, module version = 2.99.917
[    22.962]     Module class: X.Org Video Driver
[    22.962]     ABI class: X.Org Video Driver, version 19.0
[    22.962] (II) LoadModule: "modesetting"
[    22.962] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.962] (II) Module modesetting: vendor="X.Org Foundation"
[    22.962]     compiled for 1.17.1, module version = 1.17.1
[    22.962]     Module class: X.Org Video Driver
[    22.962]     ABI class: X.Org Video Driver, version 19.0
[    22.962] (II) LoadModule: "fbdev"
[    22.962] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.962] (II) Module fbdev: vendor="X.Org Foundation"
[    22.962]     compiled for 1.17.1, module version = 0.4.4
[    22.962]     Module class: X.Org Video Driver
[    22.962]     ABI class: X.Org Video Driver, version 19.0
[    22.962] (II) LoadModule: "vesa"
[    22.962] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.962] (II) Module vesa: vendor="X.Org Foundation"
[    22.962]     compiled for 1.17.1, module version = 2.3.3
[    22.962]     Module class: X.Org Video Driver
[    22.962]     ABI class: X.Org Video Driver, version 19.0
[    22.962] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    22.962] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    22.962] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    22.962] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    22.963] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    22.963] (II) FBDEV: driver for framebuffer: fbdev
[    22.963] (II) VESA: driver for VESA chipsets: vesa
[    22.963] (++) using VT number 7

[    23.014] (EE) open /dev/dri/card0: No such file or directory
[    23.014] (WW) Falling back to old probe method for modesetting
[    23.014] (EE) open /dev/dri/card0: No such file or directory
[    23.014] (II) Loading sub module "fbdevhw"
[    23.014] (II) LoadModule: "fbdevhw"
[    23.014] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.014] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.014]     compiled for 1.17.1, module version = 0.0.2
[    23.014]     ABI class: X.Org Video Driver, version 19.0
[    23.014] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    23.014] (II) FBDEV(1): using default device
[    23.015] (WW) Falling back to old probe method for vesa
[    23.015] (EE) Screen 0 deleted because of no matching config section.
[    23.015] (II) UnloadModule: "modesetting"
[    23.015] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.015] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    23.015] (==) FBDEV(0): RGB weight 888
[    23.015] (==) FBDEV(0): Default visual is TrueColor
[    23.015] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.015] (II) FBDEV(0): hardware: EFI VGA (video memory: 1876kB)
[    23.015] (II) FBDEV(0): checking modes against framebuffer device...
[    23.015] (II) FBDEV(0): checking modes against monitor...
[    23.015] (--) FBDEV(0): Virtual size is 800x600 (pitch 800)
[    23.015] (**) FBDEV(0):  Built-in mode "current": 48.0 MHz, 46.9 kHz, 75.1 Hz
[    23.015] (II) FBDEV(0): Modeline "current"x0.0   48.00  800 832 928 1024  600 604 608 624 -hsync -vsync -csync (46.9 kHz b)
[    23.015] (==) FBDEV(0): DPI set to (96, 96)
[    23.015] (II) Loading sub module "fb"
[    23.015] (II) LoadModule: "fb"
[    23.015] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.015] (II) Module fb: vendor="X.Org Foundation"
[    23.015]     compiled for 1.17.1, module version = 1.0.0
[    23.015]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.015] (**) FBDEV(0): using shadow framebuffer
[    23.015] (II) Loading sub module "shadow"
[    23.015] (II) LoadModule: "shadow"
[    23.015] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    23.015] (II) Module shadow: vendor="X.Org Foundation"
[    23.015]     compiled for 1.17.1, module version = 1.1.0
[    23.015]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.015] (II) UnloadModule: "vesa"
[    23.015] (II) Unloading vesa
[    23.015] (==) Depth 24 pixmap format is 32 bpp
[    23.015] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    23.015] (==) FBDEV(0): Backing store enabled
[    23.015] (==) FBDEV(0): DPMS enabled
[    23.015] (==) RandR enabled
[    23.019] (II) AIGLX: Screen 0 is not DRI2 capable
[    23.019] (EE) AIGLX: reverting to software rendering
[    23.719] (II) AIGLX: Loaded and initialized swrast
[    23.719] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.725] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.727] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.727] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.727] (II) LoadModule: "evdev"
[    23.727] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.752] (II) Module evdev: vendor="X.Org Foundation"
[    23.752]     compiled for 1.17.1, module version = 2.9.0
[    23.752]     Module class: X.Org XInput Driver
[    23.752]     ABI class: X.Org XInput driver, version 21.0
[    23.752] (II) Using input driver 'evdev' for 'Power Button'
[    23.752] (**) Power Button: always reports core events
[    23.752] (**) evdev: Power Button: Device: "/dev/input/event2"
[    23.752] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.752] (--) evdev: Power Button: Found keys
[    23.752] (II) evdev: Power Button: Configuring as keyboard
[    23.752] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    23.752] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.752] (**) Option "xkb_rules" "evdev"
[    23.752] (**) Option "xkb_model" "pc105"
[    23.752] (**) Option "xkb_layout" "us"
[    23.752] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    23.752] (II) No input driver specified, ignoring this device.
[    23.752] (II) This device may have been added with another device file.
[    23.752] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    23.752] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    23.752] (II) Using input driver 'evdev' for 'Sleep Button'
[    23.752] (**) Sleep Button: always reports core events
[    23.752] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    23.752] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    23.752] (--) evdev: Sleep Button: Found keys
[    23.752] (II) evdev: Sleep Button: Configuring as keyboard
[    23.752] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    23.752] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[    23.752] (**) Option "xkb_rules" "evdev"
[    23.752] (**) Option "xkb_model" "pc105"
[    23.753] (**) Option "xkb_layout" "us"
[    23.753] (II) config/udev: Adding input device USB Camera (/dev/input/event7)
[    23.753] (**) USB Camera: Applying InputClass "evdev keyboard catchall"
[    23.753] (II) Using input driver 'evdev' for 'USB Camera'
[    23.753] (**) USB Camera: always reports core events
[    23.753] (**) evdev: USB Camera: Device: "/dev/input/event7"
[    23.753] (--) evdev: USB Camera: Vendor 0xbda Product 0x57b5
[    23.753] (--) evdev: USB Camera: Found keys
[    23.753] (II) evdev: USB Camera: Configuring as keyboard
[    23.753] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input14/event7"
[    23.753] (II) XINPUT: Adding extended input device "USB Camera" (type: KEYBOARD, id 8)
[    23.753] (**) Option "xkb_rules" "evdev"
[    23.753] (**) Option "xkb_model" "pc105"
[    23.753] (**) Option "xkb_layout" "us"
[    23.753] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event6)
[    23.753] (II) No input driver specified, ignoring this device.
[    23.753] (II) This device may have been added with another device file.
[    23.753] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[    23.753] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    23.753] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    23.753] (**) Asus WMI hotkeys: always reports core events
[    23.753] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[    23.753] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    23.753] (--) evdev: Asus WMI hotkeys: Found keys
[    23.753] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    23.753] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input12/event5"
[    23.753] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 9)
[    23.753] (**) Option "xkb_rules" "evdev"
[    23.753] (**) Option "xkb_model" "pc105"
[    23.753] (**) Option "xkb_layout" "us"
[    23.754] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.754] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.754] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.754] (**) AT Translated Set 2 keyboard: always reports core events
[    23.754] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.754] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.754] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.754] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.754] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    23.754] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    23.754] (**) Option "xkb_rules" "evdev"
[    23.754] (**) Option "xkb_model" "pc105"
[    23.754] (**) Option "xkb_layout" "us"
[    23.754] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event4)
[    23.754] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    23.754] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    23.754] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    23.754] (II) LoadModule: "synaptics"
[    23.754] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.754] (II) Module synaptics: vendor="X.Org Foundation"
[    23.754]     compiled for 1.17.1, module version = 1.8.99
[    23.754]     Module class: X.Org XInput Driver
[    23.754]     ABI class: X.Org XInput driver, version 21.0
[    23.754] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    23.754] (**) ETPS/2 Elantech Touchpad: always reports core events
[    23.754] (**) Option "Device" "/dev/input/event4"
[    23.764] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[    23.764] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3097 (res 31)
[    23.764] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 2119 (res 32)
[    23.764] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    23.764] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    23.764] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[    23.764] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    23.764] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    23.764] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    23.764] (**) ETPS/2 Elantech Touchpad: always reports core events
[    23.784] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event4"
[    23.784] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 11)
[    23.784] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    23.784] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    23.784] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.053
[    23.784] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    23.784] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    23.784] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    23.784] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    23.784] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    23.784] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    23.784] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    23.787] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    32.729] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.985] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.999] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    41.927] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm

```

```
cat ~/.xsession-errors
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
```

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Yuk;

All we know from those outputs is all to the bad.
Is the Nvidia card turned off in bios ?
Huh, how come the Intel driver does not load and the system falls back to " 22.963] (II) FBDEV: driver for framebuffer: fbdev " ?

Let me cogitate a bit, consider (RE-)installing the Intel driver 1st prior to the Nvidia driver.
The system is aware of the Intel hardware:
> 
22.948] (==) Matched intel as autoconfigured driver 0


I still yet see what the Nvidia hardware is .. make sure we can match the hardware to a driver.

[INDENT][INDENT]i'll be B A C K
[/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2015-10-06
I have checked my BIOS, and there isn't a single place in the settings that has any information about NVIDIA. I see no entry for it - there is an area that recognizes the processor as Intel i5 5500u, but nothing about the graphics card.

Under graphics configuration, there is only this option: DVMT Pre-alloction 32M

Under 14.04, how would I install/re-install the Intel driver? My search led to this command which does not work:
```
sudo apt-get install xserver-xorg-video-intel
[sudo] password for arcane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-intel : Depends: xorg-video-abi-15
                            Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Hey;

We are making progress. In your case we have to step up with 14.04 having HardWare Enablement . We are dealing with vivid's X stack. - per the xorg file -

I do not have the smarts to know if " libcuda1-346 " can or will conflict with Intel as presently Nvidia's driver and control mechanisms are not installed. But let's remove it for now:
```

sudo apt-get purge libcuda1-346

```
And now for X ->
Let's try this:
```

sudo apt-get install --install-recommends linux-generic-lts-vivid libgl1-mesa-glx-lts-vivid xserver-xorg-lts-vivid linux-image-generic-lts-vivid

```
as we try and take care of :
> 
Depends: xorg-video-abi-15
Depends: xserver-xorg-core (>= 2:1.14.99.902)

I can foresee that the package manager may scream and holler. Post back the commands and the results, and we see what action then to take. Could be that we get X right, will take care of the ACPI situation . Maybe, maybe .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2015-10-06
```
sudo apt-get purge libcuda1-346
[sudo] password for arcane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libvdpau1 linux-headers-3.19.0-28
  linux-headers-3.19.0-28-generic linux-image-3.19.0-28-generic
  linux-image-extra-3.19.0-28-generic linux-signed-image-3.19.0-28-generic
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libcuda1-346*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 26.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 209533 files and directories currently installed.)
Removing libcuda1-346 (346.96-0ubuntu0.0.1) ...
Purging configuration files for libcuda1-346 (346.96-0ubuntu0.0.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
``` 

Seemed to remove just fine. 

```
sudo apt-get install --install-recommends linux-generic-lts-vivid libgl1-mesa-glx-lts-vivid xserver-xorg-lts-vivid linux-image-generic-lts-vivid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-glx-lts-vivid is already the newest version.
libgl1-mesa-glx-lts-vivid set to manually installed.
xserver-xorg-lts-vivid is already the newest version.
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libvdpau1 linux-headers-3.19.0-28
  linux-headers-3.19.0-28-generic linux-image-3.19.0-28-generic
  linux-image-extra-3.19.0-28-generic linux-signed-image-3.19.0-28-generic
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-generic-lts-vivid linux-image-generic-lts-vivid
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/4,068 B of archives.
After this operation, 55.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Selecting previously unselected package linux-image-generic-lts-vivid.
(Reading database ... 209525 files and directories currently installed.)
Preparing to unpack .../linux-image-generic-lts-vivid_3.19.0.30.17_amd64.deb ...
Unpacking linux-image-generic-lts-vivid (3.19.0.30.17) ...
Selecting previously unselected package linux-generic-lts-vivid.
Preparing to unpack .../linux-generic-lts-vivid_3.19.0.30.17_amd64.deb ...
Unpacking linux-generic-lts-vivid (3.19.0.30.17) ...
Setting up linux-image-generic-lts-vivid (3.19.0.30.17) ...
Setting up linux-generic-lts-vivid (3.19.0.30.17) ...


```

No errors with that. I will see what happens when I reboot.

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Yeah !

so far
[INDENT][INDENT]so good
[/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2015-10-06
Well, not only did it boot without instantly crashing, but it was a lot faster than before, and the Intel display is no longer listed as 'unclaimed'. 

No problems so far, and I have been on the regular kernel for quite some time. 

I'm wondering about this command, which I've run afterwards, and it still has 'libcuda' in it:
```
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                                304.128-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library

```

Though that last part in particular no longer seems to be clashing.

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Well !

Just great !

"rc  libcuda1-304" that leading 'rc' is a status indicator .. where r=removed and c= config files remain.
When we get ready to clean things up we will address that .

So as we look'n good, ya want to see what results when the Nvidia driver is installed ?
Are you aware of how nvidia-prime works to switch between graphics sets ?

[INDENT][INDENT]this little light of mine
[/INDENT][/INDENT]

---

### Post by mistcloud-misty on 2015-10-06
Well, this new computer I fresh installed with 14.04 a few weeks ago, and the only thing I did with Nvidia is enable one of the proprietary drivers. I don't think I've seen the extent of Nvidia yet (I was nervous about configuring it because I had issues with Nvidia on an old computer years ago).

I have one question before installing drivers: will updates cause the crashing to recur, or should this be a final fix?

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Welp

Do you feel that the system is stable at this point ?

As to being a final fix. we won't know till we try . Even though this is a fairly fresh install I do suggest we do the house cleaning before we install the Nvidia driver. Now if we install the driver from our repo, henceforth the package manager will take care of it . Should not present a problem in the future once it is fully and properly installed. 'buntu and Nvidia have come a long way from yester-year as Nvidia works close with us now .

The big draw back with using the Nvidia driver however is the battery drain . The big plus is the increase in performance .

[INDENT][INDENT]your call
[/INDENT][/INDENT]

---

### Post by efflandt on 2015-10-06
ii means installed. I think rc just means recommended, not installed (mine shows rc for libcuda1-304, but am currently running nvidia-355, so it shows ii for libcuda1-355).

Does the following show any nvidia package installed (the -l is small L):```
dpkg-query -l nvidia* | grep ii
```If that shows nothing, for 940M nvidia website recommends a 352.41 driver. So you may need to add a ppa per **[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)** and install **nvidia-352** package if you want to use your nvidia graphics. Example (first make sure that any other nvidia packages are purged):```
sudo apt-get purge nvidia*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-352
```Then you should be able to switch graphics Intel/Nvidia graphics using **NVIDIA X Server Settings**. With my laptop I just have to log out of X and back in when switching Nvidia to Intel, but have to reboot after switching from Intel to Nvidia.

---

### Post by mistcloud-misty on 2015-10-06
Well it's been over an hour without crashing, and no errors have popped up. It is as stable as it ever was. I'm fine with trading power usage for performance, since I generally have my charger with me/ready at all times. 

I have no Nvidia packages installed already (the first thing I did was purge them, thinking the crash was the same problem as before). 

So I should install from the PPA repositories, and not from additional drivers, I assume?

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Oh Boy.

While for an experienced user installing from PPA is no big deal .. the burden of maintaning that driver is on you . knowing how to re-install the driver with a kernel upgrade.
Installing from the software repository the package manager will take care of it .
Again the trade-off is the version available, the repo is 346 and it may work just fine good and dandy.
Nvidia recommends the 352 and for your case to install the 352 version then it is a PPA as best choice . 

[INDENT][INDENT]decisions decisions decisions
[/INDENT][/INDENT]

---

### Post by efflandt on 2015-10-06
Using a ppa is NOT like running a .run script from nvidia.com where you may need to rerun the script after kernel updates. A ppa automatically creates graphics modules for a new kernel just like the normal repositories do. So once things are working, they should just keep working when updates are automatically suggested by Software Updater. My GTX 750 Ti with the new Maxwell chip was not supported by nouveau nor nvidia-current in 14.04, so I have been using xorg-edgers ppa for a while for newer drivers. But that was all recently moved over to the **graphics-drivers/ppa** that I suggested above, which is an effort to make more recent graphic drivers more easily available from one place and coordinated with other updates.

---

### Post by mistcloud-misty on 2015-10-06
At this point I've installed the 346 file, which is working fine! I might consider upgrading to the ppa in the future, but for now I'll just keep things simple just in case things go wrong. Thanks for all your help!

---

### Post by Bashing-om on 2015-10-06
mistcloud-misty; Great !

If and only if this matter is concluded to your satisfaction
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

