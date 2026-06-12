---
title: "Nvidia-K2100M"
date: 2015-11-05
forum: Hardware
---

### Post by elm3 on 2015-11-05
Hi,
I'm having a lot of hope by asking you, since I always find an answer to my issues on this forum...


As usual, when I install a new laptop with a nvidia graphical card, I have issues.... It is sooo exhausting to try to fix it

Here is my lspci:

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: NVIDIA Corporation GK106GLM [Quadro K2100M] (rev a1) (prog-if 00 [VGA controller])


The nvidia-346 makes my splash screen to freeze, nvidia-340 the same, only nvidia-current makes it ok but doesn't use the graphical card...

Any idea and or feedback on which driver is the best to not make everything frozen is very welcome.

The laptop is Thinkpad lenovo W541, ubuntu 14.04.

Thanks for your precious help,

Best,

e

Hi again,

I'm precising that I don't want to use bumblee or other stuff, just the nvidia-graph card.

Thanks for your reading and help.

---

### Post by Bashing-om on 2015-11-06
elm3; Hello;

What release are you running ? Nvidia recommends the 352 version driver for the Nvidia card; that driver is available in 15.04++ software repository direct.

Presently, what returns from terminal commands:
```

lsb_release -a
uname -r
sudo ubuntu-drivers devices
sudo ubuntu-drivers list
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

To see what we are working with and what our options are.
Let us consider purging the drivers currently installed and install the 352 version, whatever that may take.
In this install will be nvidia-prime. It is this tool that will permit you to switch between the Intel and Nvidia graphic's sets.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by elm3 on 2015-11-06
Hi,
Thanks for your answer,

Presently,

```
lsb_realse-a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

```

```
uname -r 
3.13.0-67-generic
```

```
sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd000011FCsv000017AAsd00002211bc03sc00i00
driver   : nvidia-346 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-346-updates - distro non-free
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-340 - distro non-free
```


```
sudo ubuntu-drivers list
nvidia-346-updates
nvidia-340-updates
nvidia-346
nvidia-340
```

```
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-304                                          304.128-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                          340.93-0ubuntu0.0.1                                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                          346.96-0ubuntu0.0.1                                    amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                            304.128-0ubuntu0.0.1                                   amd64        NVIDIA legacy binary driver - version 304.128
ii  nvidia-current                                        304.128-0ubuntu0.0.1                                   amd64        Transitional package for nvidia-current
rc  nvidia-libopencl1-304                                 304.128-0ubuntu0.0.1                                   amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                                 304.128-0ubuntu0.0.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       331.20-0ubuntu8                                        amd64        Tool for configuring the NVIDIA graphics driver

```


I could not find the 352 version, even if I knew Nvidia recomanded it, I found that 346.16 supports my graph card, that's why I installed it.

Can I access the 15.04++ repository with keeping my ubuntu version ? (LTS)

Cheers

e

---

### Post by Bashing-om on 2015-11-06
elm3; Well ...

Our plot thickens .
You do not show an Intel graphic's set . Is it turned off in bios ?
what returns:
```

lspci | grep "VGA\|3D"

```

And presently maybe you have a conflict in Nvidia drivers:
> 
ii  nvidia-304                                            304.128-0ubuntu0.0.1                                   amd64        NVIDIA legacy binary driver - version 304.128
ii  nvidia-current                                        304.128-0ubuntu0.0.1


How about - once we know the Intel status - we purge all the Nvidia stuff, and (re-)install the 346 version driver ?
Yeah 352 is not offered in the 14.04 repository. If we need to try a different (352/355) we can activate a PPA to obtain the driver.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by elm3 on 2015-11-06
```
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106GLM [Quadro K2100M] (rev a1)

```

Shall I purge and reinstall 346 ?

---

### Post by Bashing-om on 2015-11-06
elm3; Well ..

Still not at all sure of what is not going on. I would be interested to see the log file.
Please post back:
```

cat /var/log/Xorg.0.log

```
and we see what Intel is doing .
Once we have a bit more info we can make a better determination to (RE-)install the driver .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by elm3 on 2015-11-07
Here we go,

346 doesn't want to work..

```
[   515.255] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   515.255] X Protocol Version 11, Revision 0
[   515.255] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[   515.255] Current Operating System: Linux expresso 3.13.0-67-generic #110-Ubuntu SMP Fri Oct 23 13:24:41 UTC 2015 x86_64
[   515.255] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-67-generic root=UUID=a11681d5-607f-4bd5-a17e-0d4933580c26 ro quiet splash
[   515.255] Build Date: 12 February 2015  02:49:29PM
[   515.255] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[   515.255] Current version of pixman: 0.30.2
[   515.255]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   515.255] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   515.255] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  5 16:37:54 2015
[   515.255] (==) Using config file: "/etc/X11/xorg.conf"
[   515.255] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   515.255] (==) No Layout section.  Using the first Screen section.
[   515.255] (==) No screen section available. Using defaults.
[   515.255] (**) |-->Screen "Default Screen Section" (0)
[   515.255] (**) |   |-->Monitor "<default monitor>"
[   515.255] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[   515.255] (**) |   |-->Device "Default Card 0"
[   515.255] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   515.255] (==) Automatically adding devices
[   515.255] (==) Automatically enabling devices
[   515.255] (==) Automatically adding GPU devices
[   515.255] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   515.255]     Entry deleted from font path.
[   515.255] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   515.255]     Entry deleted from font path.
[   515.255] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   515.255]     Entry deleted from font path.
[   515.255] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   515.255]     Entry deleted from font path.
[   515.255] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   515.255]     Entry deleted from font path.
[   515.255] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   515.255] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   515.255] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   515.255] (II) Loader magic: 0x7f203f8c4d40
[   515.255] (II) Module ABI versions:
[   515.255]     X.Org ANSI C Emulation: 0.4
[   515.255]     X.Org Video Driver: 15.0
[   515.255]     X.Org XInput driver : 20.0
[   515.255]     X.Org Server Extension : 8.0
[   515.255] (II) xfree86: Adding drm device (/dev/dri/card1)
[   515.256] (II) xfree86: Adding drm device (/dev/dri/card0)
[   515.258] (--) PCI:*(0:0:2:0) 8086:0416:17aa:2211 rev 6, Mem @ 0xb1400000/4194304, 0xa0000000/268435456, I/O @ 0x00005000/64
[   515.258] (--) PCI: (0:1:0:0) 10de:11fc:17aa:2211 rev 161, Mem @ 0xb0000000/16777216, 0x80000000/268435456, 0x90000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[   515.258] Initializing built-in extension Generic Event Extension
[   515.258] Initializing built-in extension SHAPE
[   515.258] Initializing built-in extension MIT-SHM
[   515.258] Initializing built-in extension XInputExtension
[   515.258] Initializing built-in extension XTEST
[   515.258] Initializing built-in extension BIG-REQUESTS
[   515.258] Initializing built-in extension SYNC
[   515.258] Initializing built-in extension XKEYBOARD
[   515.258] Initializing built-in extension XC-MISC
[   515.258] Initializing built-in extension SECURITY
[   515.258] Initializing built-in extension XINERAMA
[   515.258] Initializing built-in extension XFIXES
[   515.258] Initializing built-in extension RENDER
[   515.258] Initializing built-in extension RANDR
[   515.258] Initializing built-in extension COMPOSITE
[   515.258] Initializing built-in extension DAMAGE
[   515.258] Initializing built-in extension MIT-SCREEN-SAVER
[   515.258] Initializing built-in extension DOUBLE-BUFFER
[   515.258] Initializing built-in extension RECORD
[   515.258] Initializing built-in extension DPMS
[   515.258] Initializing built-in extension Present
[   515.258] Initializing built-in extension DRI3
[   515.258] Initializing built-in extension X-Resource
[   515.258] Initializing built-in extension XVideo
[   515.258] Initializing built-in extension XVideo-MotionCompensation
[   515.258] Initializing built-in extension SELinux
[   515.258] Initializing built-in extension XFree86-VidModeExtension
[   515.258] Initializing built-in extension XFree86-DGA
[   515.258] Initializing built-in extension XFree86-DRI
[   515.258] Initializing built-in extension DRI2
[   515.258] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   515.258] (II) "glx" will be loaded by default.
[   515.258] (WW) "xmir" is not to be loaded by default. Skipping.
[   515.258] (II) LoadModule: "glx"
[   515.258] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   515.259] (II) Module glx: vendor="X.Org Foundation"
[   515.259]     compiled for 1.15.1, module version = 1.0.0
[   515.259]     ABI class: X.Org Server Extension, version 8.0
[   515.259] (==) AIGLX enabled
[   515.259] Loading extension GLX
[   515.259] (==) Matched intel as autoconfigured driver 0
[   515.259] (==) Matched nvidia as autoconfigured driver 1
[   515.259] (==) Matched nouveau as autoconfigured driver 2
[   515.259] (==) Matched intel as autoconfigured driver 3
[   515.259] (==) Matched modesetting as autoconfigured driver 4
[   515.259] (==) Matched fbdev as autoconfigured driver 5
[   515.259] (==) Matched vesa as autoconfigured driver 6
[   515.259] (==) Assigned the driver to the xf86ConfigLayout
[   515.259] (II) LoadModule: "intel"
[   515.259] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   515.259] (II) Module intel: vendor="X.Org Foundation"
[   515.259]     compiled for 1.15.1, module version = 2.99.917
[   515.259]     Module class: X.Org Video Driver
[   515.259]     ABI class: X.Org Video Driver, version 15.0
[   515.259] (II) LoadModule: "nvidia"
[   515.259] (WW) Warning, couldn't open module nvidia
[   515.259] (II) UnloadModule: "nvidia"
[   515.259] (II) Unloading nvidia
[   515.259] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   515.259] (II) LoadModule: "nouveau"
[   515.259] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   515.259] (II) Module nouveau: vendor="X.Org Foundation"
[   515.259]     compiled for 1.15.1, module version = 1.0.11
[   515.259]     Module class: X.Org Video Driver
[   515.259]     ABI class: X.Org Video Driver, version 15.0
[   515.259] (II) LoadModule: "modesetting"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   515.260] (II) Module modesetting: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.0, module version = 0.8.1
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (II) LoadModule: "fbdev"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   515.260] (II) Module fbdev: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.0, module version = 0.4.4
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (II) LoadModule: "vesa"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   515.260] (II) Module vesa: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.0, module version = 2.3.3
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (==) Matched intel as autoconfigured driver 0
[   515.260] (==) Matched nvidia as autoconfigured driver 1
[   515.260] (==) Matched nouveau as autoconfigured driver 2
[   515.260] (==) Matched intel as autoconfigured driver 3
[   515.260] (==) Matched modesetting as autoconfigured driver 4
[   515.260] (==) Matched fbdev as autoconfigured driver 5
[   515.260] (==) Matched vesa as autoconfigured driver 6
[   515.260] (==) Assigned the driver to the xf86ConfigLayout
[   515.260] (II) LoadModule: "intel"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   515.260] (II) Module intel: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.1, module version = 2.99.917
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (II) UnloadModule: "intel"
[   515.260] (II) Unloading intel
[   515.260] (II) Failed to load module "intel" (already loaded, 32544)
[   515.260] (II) LoadModule: "nvidia"
[   515.260] (WW) Warning, couldn't open module nvidia
[   515.260] (II) UnloadModule: "nvidia"
[   515.260] (II) Unloading nvidia
[   515.260] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   515.260] (II) LoadModule: "nouveau"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   515.260] (II) Module nouveau: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.1, module version = 1.0.11
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (II) UnloadModule: "nouveau"
[   515.260] (II) Unloading nouveau
[   515.260] (II) Failed to load module "nouveau" (already loaded, 0)
[   515.260] (II) LoadModule: "modesetting"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   515.260] (II) Module modesetting: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.0, module version = 0.8.1
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (II) UnloadModule: "modesetting"
[   515.260] (II) Unloading modesetting
[   515.260] (II) Failed to load module "modesetting" (already loaded, 0)
[   515.260] (II) LoadModule: "fbdev"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   515.260] (II) Module fbdev: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.0, module version = 0.4.4
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (II) UnloadModule: "fbdev"
[   515.260] (II) Unloading fbdev
[   515.260] (II) Failed to load module "fbdev" (already loaded, 0)
[   515.260] (II) LoadModule: "vesa"
[   515.260] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   515.260] (II) Module vesa: vendor="X.Org Foundation"
[   515.260]     compiled for 1.15.0, module version = 2.3.3
[   515.260]     Module class: X.Org Video Driver
[   515.260]     ABI class: X.Org Video Driver, version 15.0
[   515.260] (II) UnloadModule: "vesa"
[   515.260] (II) Unloading vesa
[   515.260] (II) Failed to load module "vesa" (already loaded, 0)
[   515.260] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   515.261] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   515.261] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   515.261] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   515.261] (II) NOUVEAU driver 
[   515.261] (II) NOUVEAU driver for NVIDIA chipset families :
[   515.261]     RIVA TNT        (NV04)
[   515.261]     RIVA TNT2       (NV05)
[   515.261]     GeForce 256     (NV10)
[   515.261]     GeForce 2       (NV11, NV15)
[   515.261]     GeForce 4MX     (NV17, NV18)
[   515.261]     GeForce 3       (NV20)
[   515.261]     GeForce 4Ti     (NV25, NV28)
[   515.261]     GeForce FX      (NV3x)
[   515.261]     GeForce 6       (NV4x)
[   515.261]     GeForce 7       (G7x)
[   515.261]     GeForce 8       (G8x)
[   515.261]     GeForce GTX 200 (NVA0)
[   515.261]     GeForce GTX 400 (NVC0)
[   515.261] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   515.261] (II) FBDEV: driver for framebuffer: fbdev
[   515.261] (II) VESA: driver for VESA chipsets: vesa
[   515.261] (++) using VT number 7

[   515.261] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[   515.261] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20151015.6861391f-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[   515.261] (II) intel(0): SNA compiled for use with valgrind
[   515.261] (EE) [drm] KMS not enabled
[   515.261] (WW) Falling back to old probe method for modesetting
[   515.261] (WW) Falling back to old probe method for fbdev
[   515.261] (II) Loading sub module "fbdevhw"
[   515.261] (II) LoadModule: "fbdevhw"
[   515.261] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   515.261] (II) Module fbdevhw: vendor="X.Org Foundation"
[   515.261]     compiled for 1.15.1, module version = 0.0.2
[   515.261]     ABI class: X.Org Video Driver, version 15.0
[   515.261] (WW) Falling back to old probe method for vesa
[   515.261] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[   515.261] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[   515.261] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   515.261] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   515.261] (==) intel(0): RGB weight 888
[   515.261] (==) intel(0): Default visual is TrueColor
[   515.262] (II) intel(0): Output eDP1 has no monitor section
[   515.262] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[   515.262] (II) intel(0): Enabled output eDP1
[   515.262] (II) intel(0): Output VGA1 has no monitor section
[   515.262] (II) intel(0): Enabled output VGA1
[   515.262] (II) intel(0): Output DP1 has no monitor section
[   515.262] (II) intel(0): Enabled output DP1
[   515.262] (II) intel(0): Output HDMI1 has no monitor section
[   515.262] (II) intel(0): Enabled output HDMI1
[   515.262] (II) intel(0): Output DP2 has no monitor section
[   515.262] (II) intel(0): Enabled output DP2
[   515.262] (II) intel(0): Output HDMI2 has no monitor section
[   515.262] (II) intel(0): Enabled output HDMI2
[   515.262] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[   515.262] (II) intel(0): Output VIRTUAL1 has no monitor section
[   515.262] (II) intel(0): Enabled output VIRTUAL1
[   515.262] (--) intel(0): Output eDP1 using initial mode 2880x1620 on pipe 0
[   515.262] (==) intel(0): TearFree disabled
[   515.262] (==) intel(0): DPI set to (96, 96)
[   515.262] (II) Loading sub module "dri2"
[   515.262] (II) LoadModule: "dri2"
[   515.262] (II) Module "dri2" already built-in
[   515.262] (II) Loading sub module "present"
[   515.262] (II) LoadModule: "present"
[   515.262] (WW) Warning, couldn't open module present
[   515.262] (II) UnloadModule: "present"
[   515.262] (II) Unloading present
[   515.262] (EE) intel: Failed to load module "present" (module does not exist, 0)
[   515.262] (II) UnloadModule: "fbdev"
[   515.262] (II) Unloading fbdev
[   515.262] (II) UnloadSubModule: "fbdevhw"
[   515.262] (II) Unloading fbdevhw
[   515.262] (II) UnloadModule: "vesa"
[   515.262] (II) Unloading vesa
[   515.262] (==) Depth 24 pixmap format is 32 bpp
[   515.262] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[   515.262] (==) intel(0): Backing store enabled
[   515.262] (==) intel(0): Silken mouse enabled
[   515.262] (II) intel(0): HW Cursor enabled
[   515.262] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   515.262] (==) intel(0): DPMS enabled
[   515.262] (==) intel(0): Display hotplug detection enabled
[   515.262] (II) intel(0): [DRI2] Setup complete
[   515.262] (II) intel(0): [DRI2]   DRI driver: i965
[   515.262] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[   515.262] (II) intel(0): direct rendering: DRI2 enabled
[   515.262] (--) RandR disabled
[   515.265] (II) SELinux: Disabled on system
[   515.269] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   515.269] (II) AIGLX: enabled GLX_ARB_create_context
[   515.269] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   515.269] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   515.269] (II) AIGLX: enabled GLX_INTEL_swap_event
[   515.269] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   515.269] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   515.269] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   515.269] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   515.269] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[   515.270] (II) AIGLX: Loaded and initialized i965
[   515.270] (II) GLX: Initialized DRI2 GL provider for screen 0
[   515.272] (II) intel(0): switch to mode 2880x1620@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[   515.273] (II) intel(0): Setting screen physical size to 762 x 428
[   515.276] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   515.278] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   515.278] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   515.278] (II) LoadModule: "evdev"
[   515.278] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   515.278] (II) Module evdev: vendor="X.Org Foundation"
[   515.278]     compiled for 1.15.0, module version = 2.8.2
[   515.278]     Module class: X.Org XInput Driver
[   515.278]     ABI class: X.Org XInput driver, version 20.0
[   515.278] (II) Using input driver 'evdev' for 'Power Button'
[   515.278] (**) Power Button: always reports core events
[   515.278] (**) evdev: Power Button: Device: "/dev/input/event2"
[   515.278] (--) evdev: Power Button: Vendor 0 Product 0x1
[   515.278] (--) evdev: Power Button: Found keys
[   515.278] (II) evdev: Power Button: Configuring as keyboard
[   515.278] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   515.278] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   515.278] (**) Option "xkb_rules" "evdev"
[   515.278] (**) Option "xkb_model" "pc105"
[   515.278] (**) Option "xkb_layout" "us"
[   515.278] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[   515.278] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   515.278] (II) Using input driver 'evdev' for 'Video Bus'
[   515.278] (**) Video Bus: always reports core events
[   515.278] (**) evdev: Video Bus: Device: "/dev/input/event7"
[   515.278] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   515.278] (--) evdev: Video Bus: Found keys
[   515.278] (II) evdev: Video Bus: Configuring as keyboard
[   515.278] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9/event7"
[   515.278] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   515.278] (**) Option "xkb_rules" "evdev"
[   515.278] (**) Option "xkb_model" "pc105"
[   515.278] (**) Option "xkb_layout" "us"
[   515.278] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[   515.278] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   515.278] (II) Using input driver 'evdev' for 'Video Bus'
[   515.278] (**) Video Bus: always reports core events
[   515.278] (**) evdev: Video Bus: Device: "/dev/input/event8"
[   515.278] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   515.278] (--) evdev: Video Bus: Found keys
[   515.278] (II) evdev: Video Bus: Configuring as keyboard
[   515.278] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input10/event8"
[   515.278] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   515.278] (**) Option "xkb_rules" "evdev"
[   515.278] (**) Option "xkb_model" "pc105"
[   515.278] (**) Option "xkb_layout" "us"
[   515.278] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   515.278] (II) No input driver specified, ignoring this device.
[   515.278] (II) This device may have been added with another device file.
[   515.279] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   515.279] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   515.279] (II) Using input driver 'evdev' for 'Sleep Button'
[   515.279] (**) Sleep Button: always reports core events
[   515.279] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   515.279] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   515.279] (--) evdev: Sleep Button: Found keys
[   515.279] (II) evdev: Sleep Button: Configuring as keyboard
[   515.279] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   515.279] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   515.279] (**) Option "xkb_rules" "evdev"
[   515.279] (**) Option "xkb_model" "pc105"
[   515.279] (**) Option "xkb_layout" "us"
[   515.279] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card1
[   515.279] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[   515.279] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[   515.279] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   515.279] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event13)
[   515.279] (II) No input driver specified, ignoring this device.
[   515.279] (II) This device may have been added with another device file.
[   515.279] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event12)
[   515.279] (II) No input driver specified, ignoring this device.
[   515.279] (II) This device may have been added with another device file.
[   515.279] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event11)
[   515.279] (II) No input driver specified, ignoring this device.
[   515.279] (II) This device may have been added with another device file.
[   515.279] (II) config/udev: Adding input device Integrated Camera (/dev/input/event6)
[   515.279] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[   515.279] (II) Using input driver 'evdev' for 'Integrated Camera'
[   515.279] (**) Integrated Camera: always reports core events
[   515.279] (**) evdev: Integrated Camera: Device: "/dev/input/event6"
[   515.279] (--) evdev: Integrated Camera: Vendor 0x4f2 Product 0xb39a
[   515.279] (--) evdev: Integrated Camera: Found keys
[   515.279] (II) evdev: Integrated Camera: Configuring as keyboard
[   515.279] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12:1.0/input/input8/event6"
[   515.279] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD, id 10)
[   515.279] (**) Option "xkb_rules" "evdev"
[   515.279] (**) Option "xkb_model" "pc105"
[   515.279] (**) Option "xkb_layout" "us"
[   515.279] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[   515.279] (II) No input driver specified, ignoring this device.
[   515.279] (II) This device may have been added with another device file.
[   515.279] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[   515.279] (II) No input driver specified, ignoring this device.
[   515.279] (II) This device may have been added with another device file.
[   515.280] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   515.280] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   515.280] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   515.280] (**) AT Translated Set 2 keyboard: always reports core events
[   515.280] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   515.280] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   515.280] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   515.280] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   515.280] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   515.280] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[   515.280] (**) Option "xkb_rules" "evdev"
[   515.280] (**) Option "xkb_model" "pc105"
[   515.280] (**) Option "xkb_layout" "us"
[   515.280] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   515.280] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   515.280] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   515.280] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   515.280] (II) LoadModule: "synaptics"
[   515.280] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   515.280] (II) Module synaptics: vendor="X.Org Foundation"
[   515.280]     compiled for 1.15.0, module version = 1.7.4
[   515.280]     Module class: X.Org XInput Driver
[   515.280]     ABI class: X.Org XInput driver, version 20.0
[   515.280] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   515.280] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   515.280] (**) Option "Device" "/dev/input/event5"
[   515.312] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[   515.312] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1266 - 5676 (res 45)
[   515.312] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1096 - 4758 (res 68)
[   515.312] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   515.312] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   515.312] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[   515.312] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   515.312] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[   515.312] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   515.312] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   515.324] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[   515.324] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[   515.324] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   515.324] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   515.324] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[   515.324] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   515.324] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   515.324] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   515.324] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   515.324] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   515.324] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   515.324] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   515.324] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event14)
[   515.324] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[   515.324] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[   515.324] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[   515.324] (**) TPPS/2 IBM TrackPoint: always reports core events
[   515.324] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event14"
[   515.324] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[   515.324] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[   515.324] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[   515.324] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[   515.324] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[   515.324] (**) Option "Emulate3Buttons" "true"
[   515.324] (**) Option "EmulateWheel" "true"
[   515.324] (**) Option "EmulateWheelButton" "2"
[   515.324] (**) Option "YAxisMapping" "4 5"
[   515.324] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[   515.324] (**) Option "XAxisMapping" "6 7"
[   515.324] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[   515.324] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   515.324] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input7/event14"
[   515.324] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 13)
[   515.324] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[   515.325] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[   515.325] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[   515.325] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[   515.325] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[   515.325] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[   515.325] (II) No input driver specified, ignoring this device.
[   515.325] (II) This device may have been added with another device file.
[   515.325] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event4)
[   515.325] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[   515.325] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[   515.325] (**) ThinkPad Extra Buttons: always reports core events
[   515.325] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event4"
[   515.325] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[   515.325] (--) evdev: ThinkPad Extra Buttons: Found keys
[   515.325] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[   515.325] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input6/event4"
[   515.325] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 14)
[   515.325] (**) Option "xkb_rules" "evdev"
[   515.325] (**) Option "xkb_model" "pc105"
[   515.325] (**) Option "xkb_layout" "us"
[   515.576] (II) intel(0): EDID vendor "MEI", prod id 38562
[   515.576] (II) intel(0): Using EDID range info for horizontal sync
[   515.576] (II) intel(0): Using EDID range info for vertical refresh
[   515.576] (II) intel(0): Printing DDC gathered Modelines:
[   515.576] (II) intel(0): Modeline "2880x1620"x0.0  302.50  2880 2924 2928 3076  1620 1629 1630 1640 +hsync +vsync (98.3 kHz eP)
[   515.576] (II) intel(0): Modeline "2880x1620"x0.0  302.50  2880 2924 2928 3076  1620 1629 1630 1967 +hsync +vsync (98.3 kHz e)
[   518.788] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   518.872] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   518.882] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   519.211] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
```


Thanks for your help,

Best

e

---

### Post by Bashing-om on 2015-11-07
elm3; OK;

Running on the Intel graphic set and the system is not at all happy with the Nvidia driver.
So yeah, let us purge the present Nvidia driver and (RE-)install:
```

sudo rm /etc/X11/xorg.conf
sudo apt-get remove --purge nvidia*
sudo apt-get install --reinstall ubuntu-desktop
sudo ubuntu-drivers autoinstall
sudo nvidia-xconfig

```
With "autoinstall" we see what driver the system chooses to install .

Reboot the system to see the effect.

Do you now boot to the GUI ?

[INDENT][INDENT][INDENT]maybe now
[INDENT][INDENT][INDENT]yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2015-11-07
Unless a Quadro machine allows using only the discreet gpu in setup (bios) then you have a mobile/optimus card. In that case you need to use nvidia-prime to switch to the nvidia gpu. Note that nvidia-prime does not work with the 304 (nvidia-current) driver at all.
I'd add the ubuntu drivers ppa & install the latest driver for 14.04 -  atm it's 358 (autoinstall should pick that driver
```

sudo apt-get purge nvidia*
```
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install nvidia-358
```
or
```
sudo ubuntu-drivers autoinstall
```
When installing the driver read the terminal output, make sure the _kernel module is successfully built_.
Then reboot & see.
(- note that nvidia mobile gpu's thru nvidia-prime have no vsync & will exhibit tearing in a compositing environment like compiz/mutter

---

### Post by elm3 on 2015-11-09
Good mornin,
Thank you to both of you for your advice and concern,

Bashing-om:
```
sudo ubuntu-drivers autoinstall 
```
The default driver was 346

```
sudo nvidia-xconfig
```
I could not run it.

After reboof, the splash screen disapeared and a black screen stays for ever. Re-reboooted and purge nvidia.

mc4man:
Thanks for putting the proper driver on the repo:
Here is the result of:
```
sudo apt-get install nvidia-358



INFO:Enable nvidia-358
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 117) ...
Adding new group `nvidia-persistenced' (GID 126) ...
Adding new user `nvidia-persistenced' (UID 117) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-358-358.09 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-67-generic
Building for architecture x86_64
Building initial module for 3.13.0-67-generic
Done.

nvidia_358:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-67-generic/updates/dkms/

nvidia_358_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-67-generic/updates/dkms/

nvidia_358_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-67-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-opencl-icd-358 (358.09-0ubuntu0~gpu14.04.1) ...
Setting up nvidia-prime (0.6.2) ...
nvidia-prime start/running, process 6109
Setting up nvidia-settings (358.09-0ubuntu0~gpu14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-67-generic
Processing triggers for ureadahead (0.100.0-16) ...
```

So I'd say it built well. I had the same issue, black screen after the ubuntu spash screen.

I tried to change the bios to use only the discrete card. No results. So I went back on standart.


```
sudo ubuntu-drivers devices
[sudo] password for el: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd000011FCsv000017AAsd00002211bc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-358 - third-party free recommended
driver   : nvidia-340 - distro non-free
driver   : nvidia-346 - distro non-free
driver   : nvidia-346-updates - distro non-free
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-352 - third-party free
driver   : nvidia-355 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin
```

```

nvidia-detector                    
none
```

```
sudo apt-get purge nvidia       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nvidia' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libcuda1-358 libjansson4 libxnvctrl0
  linux-image-generic screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```

Any other idea ? 

Thanks for your precious help

e

---

### Post by Bashing-om on 2015-11-09
elm3; Shucks,

We still do not know why the system is unhappy with a Nvidia proprietary driver.
Is there a graphic's driver loaded at this time ?
```

sudo lshw -C display

```

and we should upgrade the system, per:
> 
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

maybe we have a stumbling block there ?
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

And we consider what options we have, and what we can do.

[INDENT][INDENT]no quitting
[INDENT][INDENT][INDENT][INDENT]quitters don't win
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by elm3 on 2015-11-09
The driver seems to be "nouveau"

```

 *-display               
       description: VGA compatible controller
       product: GK106GLM [Quadro K2100M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:49 memory:b0000000-b0ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:4000(size=128) memory:b1000000-b107ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:b1400000-b17fffff memory:a0000000-afffffff ioport:5000(size=64)

```

In the meantime I'm upgrading

Hi,

No still does the same problem, even after upgrading..

Cheers

e

---

### Post by Bashing-om on 2015-11-09
elm3; Ho Kay ..

Yeah. presently with nouveau .

Let's see what we now have to work with:
```

dpkg -l | grep -i nvidia
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Maybe we can consider (RE-)installing the 358 version from PPA ?
Then look at the log file and see what is taking place in the build .

[INDENT][INDENT]hey, it is a thought
[/INDENT][/INDENT]

---

### Post by elm3 on 2015-11-09
Hey Bashing-om,
```
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                          304.128-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                          340.93-0ubuntu0.0.1                                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                          346.96-0ubuntu0.0.1                                    amd64        NVIDIA CUDA runtime library
ii  libcuda1-358                                          358.09-0ubuntu0~gpu14.04.1                             amd64        NVIDIA CUDA runtime library
rc  nvidia-libopencl1-304                                 304.128-0ubuntu0.0.1                                   amd64        NVIDIA OpenCL Driver and ICD Loader library

```

```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main

```
```
tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/graphics-drivers-ppa-trusty.list <==
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
```

So, I try to resinstall and in debug mod which file you want to see ?

---

### Post by Bashing-om on 2015-11-09
elm3; Well ..

We do have a conflict in sources:
> 
deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) trusty main
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main


let's do away with xorg-edgers:
```

sudo rm /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list
sudo rm /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save

``` and run with graphics-drivers PPA .

clean things up:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get remove --purge nvidia*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
Where The state is rc as shown in dpkg's output, the package is removed, but the config files are not removed . This little number will take care of that .

now (re-)install the 358 (??) proprietary driver :
```

sudo apt update
sudo apt upgrade
sudo apt-get install nvidia-358
sudo nvidia-xconfig

```

Reboot for the change to take effect.
[INDENT][INDENT]up and running now ?[/INDENT][/INDENT]

---

### Post by elm3 on 2015-11-09
No, still not...
Here is the xorg.conf, I didn't have any xorg.conf file before renaming it to the old one.
now I have those:

-rw-r--r-- 1 root root  593 Nov  5 14:59 xorg.conf.11052015
-rw-r--r-- 1 root root  593 Nov  9 08:58 xorg.conf.old
-rw-r--r-- 1 root root    0 Nov  9 13:32 xorg.conf.nvidia-xconfig-original
-rw-r--r-- 1 root root  593 Nov  9 13:32 xorg.conf.11092015


It seems that nvidia cannot has trouble to be configure..
even if nvidia-xconfig returned no error.

---

### Post by Bashing-om on 2015-11-09
elm3; Hummm ..

Yeah, not making much sense ; getting frustrating for sure.
' sudo nvidia-xconfig' should have generated a brand spanking new config file.

Take a read at the directions, see if maybe we can find a fault ?
```

cat /var/log/Xorg.0.log

```

There must be a reason
[INDENT][INDENT]find it
[/INDENT][/INDENT]

---

### Post by elm3 on 2015-11-09
Here is the xorg berfore rebooting and after installing

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 358.09  (buildmeister@swio-display-x64-rhel04-04)  Wed Oct  7 20:38:32 PDT 2015

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
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
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by elm3 on 2015-11-09
Driver is still on nouveau, but it is before rebooting..


```
sudo lshw -C display
[sudo] password for el: 
  *-display               
       description: VGA compatible controller
       product: GK106GLM [Quadro K2100M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:49 memory:b0000000-b0ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:4000(size=128) memory:b1000000-b107ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:b1400000-b17fffff memory:a0000000-afffffff ioport:5000(size=64)

```

---

### Post by Bashing-om on 2015-11-09
elm3; Nope !

I do not have a clue what is not going on .. is the intel chip set turned off ??

a xorg.conf with intel and nvidia should look something like ... and this is but an example !
```

Section "ServerLayout" ##should be as this 
    Identifier "layout" ##should be as this
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:8@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```
But it does go to show in your case Intel is not being picked up.

[INDENT][INDENT]I am going back to the drawing board
[INDENT][INDENT][INDENT]I will be back - hopefully with some idea
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2015-11-09
A couple of points - 
You need to have nvidia-prime installed to run nvidia drivers in an optimus setup, it seems to be missing (at times
With nvidia-prime you do not create an xorg.conf, it's auto created when switching from Intel to nvidia, auto removed when switching from nvidia to intel.

You do not want any 304 nvidia packages installed.

I'd again try this - 
sudo apt-get purge nvidia*
Then reboot & check that you are on Intel (system settings > Details

As far as when you add nvidia-358 from ppa - You say that it goes to a black screen. This shouldn't happen in 14.04 but is/was an issue in 15.10/16.04 due to some problem with recent mesa. If you are getting the same thing the black screen is non-fatal & can be worked around.
It could be that you've gotten a new mesa from xorgers, that's why you are getting the black screen.

To fix the black screen if from mesa - 
Either add back the xorgers ppa, then use ppa-purge on or there are 2 methods to return the display. Do you auto login or go to the unity greeter? 
This bug report lays out the issue, best solution if affected is to set the greeter to go to sleep after 4 sec's, then wake up. After that the login session will be fine.
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1501041](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1501041)

If you want to test if affected before using ppa-purge or either of the 2 workarounds then - 
After purging nvidia* & a reboot to Intel,  install the nvidia-358 driver from ppa, make sure nvidia-prime is installed.
Reboot to black screen, walk away from laptop for at least 300 sec's (6 min should do.
Then hit a key or move mouse, screen should wake up with a display.

---

### Post by elm3 on 2015-11-11
Finally! bloody hell

So the issue is not nvidia, but the black screen.
I waited long enough (600 sec) and I was able to have the ubuntu greeter after..
How to you set the greeter to go to sleep after 4sec ?

Hey, thanks a lot for your help, your patience and all your advice during these days..

I did really appreciated it a lot, sincerely

e

---

### Post by Bashing-om on 2015-11-11
elm3; Yikes ..

In that event of this not being directly attributable to a driver, how about we close this thread and open up a new one .
To get an audience more suitable to this new development.
I would think we would want to see the log files in this new thread:
```

cat /var/log/dmesg
cat /var/log/syslog
cat /var/log/kern.log

```
Maybe the files will provide a hint of what is taking so long.

@ mc4man, with your vested interest, what think you ?

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-11-11
> **elm3 said:**
> Finally! bloody hell

So the issue is not nvidia, but the black screen.
I waited long enough (600 sec) and I was able to have the ubuntu greeter after..
How to you set the greeter to go to sleep after 4sec ?

Hey, thanks a lot for your help, your patience and all your advice during these days..

I did really appreciated it a lot, sincerely

e
I may do a thread on this for 15.10 & 16.04 if not properly fixed as have gotten some emails as how to remove screen tearing on optimus thru nvidia-prime. The so-called 'fix' (actually termed a work-around when dev was pressed) for the black screen in 15.10 prevents any solution to fixing tearing. 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507676](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507676) (the bug itself is erroneous, the workaround is to have the Intel driver be disabled, ie. no sna or uxa, just modesetting.

Anyway for this case of 14.04 with xorgers mesa - 
The reason for 'fixing' the black screen at greeter is then it carries over to the session. If one wanted they could go to autologin & fix via a script at login but then if logging out would get a black screen greeter. If I start a thread then will layout both methods, one could use either or both, ie. fix the session, use autologin so basically just boot up > working session display. Then by also using the greeter method a visible greeter on log outs. Atm in 16.04 I just use the greeter method...

To adjust greeter time to sleep, I find 3-4 sec's a reasonably short wait & enough time to do what one does on the greeter screen. Note that any activity will prevent the greeter from going back to sleep or wake it again...

 In terminal - 
```
sudo -H gedit  /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
scroll down to last section, change 300 to 3 or 4, save file (see screen), close gedit.
Then run this command, it should run/complete without any comment or error, *if there is any error then do not reboot or log out before fixing*
(there should not be any problem if doing what's in screen shot  - 

```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```
Then either reboot or log out to test, in ubuntu the greeter screen is announced with a bell, after hearing wait 3-4 secs, then hit a key, happy days, ect.

---

### Post by mc4man on 2015-11-12
Just as an aside -
Your black screen isn't a 'freeze', actually everything is working fine, you just can't see it.
So you could log in blindly, after bell - type in password, press  enter.
After login you can do anything that doesn't require sight, ex. 
ctrl+alt+t  (open terminal), or alt+F2 (run dialog 
Type in a command, press enter to run

I ran mpv /path/to/file to play vid to ck. Nvidia drivers . Could hear but not  see, the  log file though confirmed Nvidia (vdpau) was being used with no issues

A little exercise in visualizing & muscle memory..

---

### Post by d_j2 on 2016-05-11
There's a lot of this about. I have a Dell M4800 laptop with an NVidia Quatro K2100M in it showing all these issues. None of the configurations I have tried has this working for me yet although it did in a previous setup. The M4800 ships with 12.04 modified by Dell and that works properly. Both this and a second M4800 were upgraded in place from a cloned trusty repo and both worked. However, for historical reasons they had some (unrelated) legacy stuff installed so we decided to try and bring them in line with our other hardware running 14.04 from the same cloned repo. So we now have one M4800 that works but using a strange 12.04 upgraded to 14.04 install and another that used the Dell factory reset to 12.04 and the upgrade which doesn't work. I've been looking/trying at ideas from

[https://devtalk.nvidia.com/default/topic/810964/linux/black-screen-after-prime-select-nvidia-and-log-out-using-v346-35-drivers/3](https://devtalk.nvidia.com/default/topic/810964/linux/black-screen-after-prime-select-nvidia-and-log-out-using-v346-35-drivers/3)

Looks like imanz90 has the same issue (I can't get my registration confirmation through to post there) so I'm posting to this thread

I've also been looking at other sites, e.g.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1362848/comments/46](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1362848/comments/46)
[http://www.bleepingcomputer.com/forums/t/549534/nvidia-drivers-how-to-install-it-in-ubuntu-14041204/](http://www.bleepingcomputer.com/forums/t/549534/nvidia-drivers-how-to-install-it-in-ubuntu-14041204/)
[http://www.dell.com/support/home/uk/en/ukbsdt1/drivers/DriversDetails?productCode=precision-m4800-workstation&driverId=53R21](http://www.dell.com/support/home/uk/en/ukbsdt1/drivers/DriversDetails?productCode=precision-m4800-workstation&driverId=53R21)
[http://xmodulo.com/install-configure-nvidia-optimus-driver-ubuntu.html](http://xmodulo.com/install-configure-nvidia-optimus-driver-ubuntu.html)

Note that I do not have the option of connection to some other repo to try stuff but our Ubuntu repo clone is relatively recent and I also have the latest NVidia linux driver .run file from the NVidia web site i.e. 361.42. Our repo contains a few versions the latest being 352.63 together with 340.96 and 304.131

The first Dell currently is using the latest nVidia driver but cannot detect and second display in it's HDMI port.prime-select query returns unknown and both prime-select intel & nvidia return "Error: alternatives are not set up properly, intel/nvidia mode can't be enabled"
lspci shows an Intel 4th Gen Integrated Graphics Processor and NVIDIA GK106GLM [Quadro K2100M]
lsmod drm shows i915,drm_kms_helper,nvidia

The "working" Dell doesn't appear to use any NVidia driver but claims to be using Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits) which is not something I understand. It also happens to be using it's second monitor via the DisplayPort should that have any effect.
lspci shows only NVIDIA GK106GLM [Quadro K2100M]
lsmod drm lists nouveau and no 1915 or nvidia

I guess that the intel video may be blacklisted on that one.

I do also have a copy of the 12.04 Dell drivers repo but haven't messed with that yet.

Sorry, there's no solution here and I'd really like one. However, the current set-up I have may prompt someone who is far more familiar with anything graphically related than I am to suggest something to try.

---

### Post by deadflowr on 2016-05-11
*Thread moved to **Hardware**.*

---

