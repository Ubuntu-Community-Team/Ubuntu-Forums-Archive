---
title: "Issue to solve problems with drivers - ASUS GeForce GT 710 and 730"
date: 2023-06-13
forum: Hardware
---

### Post by sed_faster on 2023-06-13
Hello,

I have this setup:


[LIST]
[*]**Motherboard**: Asus Prime B360M-K - 2 x DIMM, Max. 32GB, DDR4 2666/2400/2133 MHz Non-ECC, Un-buffered Memory - [https://dlcdnets.asus.com/pub/ASUS/mb/LGA1151/PRIME_B360M-K/E13808_PRIME_B360M-K_UM_WEB.PDF?model=prime](https://dlcdnets.asus.com/pub/ASUS/mb/LGA1151/PRIME_B360M-K/E13808_PRIME_B360M-K_UM_WEB.PDF?model=prime) b360m-k **and** [https://www.asus.com/supportonly/prime%20b360m-k/helpdesk_manual/](https://www.asus.com/supportonly/prime%20b360m-k/helpdesk_manual/) 
[*]**CPU**: Intel i3-9100F CPU 3.6GHz 
[*]**RAM** Kingston Fury Renegade 16GB (1x16GB) DDR4-2666MHz 2R CL13 Black 
[*]**NVMe SSD **- 500GB 
[*]**First Graphic Card**: ASUS GeForce GT 710 [https://www.asus.com/motherboards-components/graphics-cards/asus/gt710-sl-2gd5/](https://www.asus.com/motherboards-components/graphics-cards/asus/gt710-sl-2gd5/) 
[*]**Second Graphic Card**: ASUS GeForce GT 730 [https://www.asus.com/motherboards-components/graphics-cards/asus/gt730-4h-sl-2gd5/techspec/](https://www.asus.com/motherboards-components/graphics-cards/asus/gt730-4h-sl-2gd5/techspec/) 
[*]**PSU**: VS Series VS550 &#8212; 550 Watt 80 PLUS® White Certified PSU (EU) - bought new with 3 years old in use desktop environment- [https://www.corsair.com/eu/en/p/psu/cp-9020171-eu/vs-series-vs550-550-watt-80-plus-white-certified-psu-eu-cp-9020171-eu](https://www.corsair.com/eu/en/p/psu/cp-9020171-eu/vs-series-vs550-550-watt-80-plus-white-certified-psu-eu-cp-9020171-eu) my model has "VS" letters in yellow, link this image: [https://business.shoppable.ph/images/ab__webp/thumbnails/500/500/detailed/16/41qP_8czQZL._AC__jpg.webp](https://business.shoppable.ph/images/ab__webp/thumbnails/500/500/detailed/16/41qP_8czQZL._AC__jpg.webp) 
[/LIST]

The CPU hasn't GPU inboard (see the specs of this piece in this link: [https://ark.intel.com/content/www/us/en/ark/products/190886/intel-core-i39100f-processor-6m-cache-up-to-4-20-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/190886/intel-core-i39100f-processor-6m-cache-up-to-4-20-ghz.html))
Next screen I will share information about my OS:

```

$ lsb_release -a

No LSB modules are available.

Distributor ID: Ubuntu

Description:    Ubuntu 22.04.2 LTS

Release:        22.04

Codename:       jammy

$ uname -a

Linux ssdmain 5.19.0-43-generic #44~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon May 22 13:39:36 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

```

I have an issue because the drivers, I think. The issue is delay between video and sond on youtube videos and see slowness in movements of the pointer mouse and movement in windows.

This is a status before install GT730: [https://ibb.co/4Tfd7yX](https://ibb.co/4Tfd7yX) (this image is old)

After install both graphic card, GT 710 and GT 730 I have this screen: [https://ibb.co/zbWKj3t](https://ibb.co/zbWKj3t)

What can I do to solve this issue beyond test all option available on Software Sources screen?

Thank you

---

### Post by westie457 on 2023-06-13
Have you tried the restart as suggested in your screenshots?

---

### Post by sed_faster on 2023-06-13
Thank you for your reply. But that image is old (i updated the thread with this note)

---

### Post by Bashing-om on 2023-06-13
sed_faster; Hello.

Let's regroup and confirm the hardware and IF a driver is loaded.
Post back the result of terminal command:
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]we see where we go from here
[/INDENT]

---

### Post by Yellow Pasque on 2023-06-13
I'd try the old X11/Xserver session instead of Wayland if Wayland is the default.

---

### Post by sed_faster on 2023-06-14
> **Bashing-om said:**
> sed_faster; Hello.

Let's regroup and confirm the hardware and IF a driver is loaded.
Post back the result of terminal command:
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[INDENT]we see where we go from here
[/INDENT]


My output was:

```

[FONT=monospace][COLOR=#000000]$ sudo lshw -C display[/COLOR] 
  *-display                  
       description: VGA compatible controller 
       product: GK208B [GeForce GT 710] 
       vendor: NVIDIA Corporation 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: a1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom 
       configuration: driver=nvidia latency=0 
       resources: irq:136 memory:ac000000-acffffff memory:a0000000-a7ffffff memory:a8000000-a9ffffff ioport:5000(size=128) memory:ad000000-ad07ffff 
  *-display 
       description: VGA compatible controller 
       product: GK208B [GeForce GT 730] 
       vendor: NVIDIA Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       version: a1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom 
       configuration: driver=nvidia latency=0 
       resources: irq:137 memory:aa000000-aaffffff memory:90000000-97ffffff memory:98000000-99ffffff ioport:4000(size=128) memory:ab000000-ab07ffff 
  *-graphics 
       product: EFI VGA 
       physical id: 2 
       logical name: /dev/fb0 
       capabilities: fb 
       configuration: depth=32 resolution=1920,1080

```
[/FONT]

---

### Post by Bashing-om on 2023-06-15
sed_faster' Well well well ---

The hardware is confirmed ,,, and Nvidia drivers are loaded -
All I know at this point is to look at the logs and see if any errors are reported.
post back the output of:
```

/var/log/gpu-manager.log

```

And ---
Nvida recommends 470 version driver for both cards:
 [https://www.nvidia.com/Download/driverResults.aspx/200634/en-us/](https://www.nvidia.com/Download/driverResults.aspx/200634/en-us/)
what driver version is presently installed ?
```

dpkg -l | grep -i nvidia

```

and does Xorg report any errors ?
```

cat /var/log/Xorg.0.log

```

some desktops recently moved the file >>
.local/share/xorg/Xorg.0.log

the location change of the file may apply in your case - I run xfce and the file remains in the /var/ directory.

[INDENT]sometimes to do wonder
[INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by sed_faster on 2023-06-16
> **Bashing-om said:**
> sed_faster' Well well well ---

The hardware is confirmed ,,, and Nvidia drivers are loaded -
All I know at this point is to look at the logs and see if any errors are reported.
post back the output of:
```

/var/log/gpu-manager.log

```

And ---
Nvida recommends 470 version driver for both cards:
 [https://www.nvidia.com/Download/driverResults.aspx/200634/en-us/](https://www.nvidia.com/Download/driverResults.aspx/200634/en-us/)
what driver version is presently installed ?
```

dpkg -l | grep -i nvidia

```

and does Xorg report any errors ?
```

cat /var/log/Xorg.0.log

```

some desktops recently moved the file >>
.local/share/xorg/Xorg.0.log

the location change of the file may apply in your case - I run xfce and the file remains in the /var/ directory.
[INDENT]sometimes to do wonder[INDENT][INDENT]other times I just do not know
[/INDENT]
[/INDENT]
[/INDENT]



Hello Bashing-om,

Thank you for your support. In next sections I will share the output did you ask.

cat /var/log/gpu-manager.log

```

log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-530
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-525srv
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-525
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-515srv
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-515
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-510
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-470srv
Looking for nvidia modules in /lib/modules/5.19.0-45-generic/kernel/nvidia-470
Found nvidia.ko module in /lib/modules/5.19.0-45-generic/kernel/nvidia-470/nvidia.ko
Looking for amdgpu modules in /lib/modules/5.19.0-45-generic/kernel
Looking for amdgpu modules in /lib/modules/5.19.0-45-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:8562
BusID "PCI:4@0:0:0"
Is boot vga? no
Chassis type: "3"
Laptop not detected
Is nvidia runtime pm supported for "0x8562"? no
Checking power status in /proc/driver/nvidia/gpus/0000:04:00.0/power
Runtime D3 status:          ?
Is nvidia runtime pm enabled for "0x8562"? no
Vendor/Device Id: 17de:158b
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 2
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 2
Has the system changed? No
Takes 0ms to wait for nvidia udev rules completed.
Unsupported discrete card vendor: 10de
Nothing to do

```

dpkg -l | grep -i nvidia

```

ii  libnvidia-cfg1-470:amd64                          470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-470                              470.182.03-0ubuntu0.22.04.1                 all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-450-server:amd64                450.236.01-0ubuntu0.22.04.1                 amd64        NVIDIA libcompute package
ii  libnvidia-compute-470:amd64                       470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA libcompute package
ii  libnvidia-compute-470:i386                        470.182.03-0ubuntu0.22.04.1                 i386         NVIDIA libcompute package
ii  libnvidia-decode-470:amd64                        470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-470:i386                         470.182.03-0ubuntu0.22.04.1                 i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64                      1:1.1.9-1.1                                 amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-470:amd64                        470.182.03-0ubuntu0.22.04.1                 amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-470:i386                         470.182.03-0ubuntu0.22.04.1                 i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-470:amd64                         470.182.03-0ubuntu0.22.04.1                 amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-470:amd64                          470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-470:amd64                            470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-470:i386                             470.182.03-0ubuntu0.22.04.1                 i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-470:amd64                          470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  linux-modules-nvidia-450-server-5.19.0-43-generic 5.19.0-43.44~22.04.1+1                      amd64        Linux kernel nvidia modules for version 5.19.0-43
rc  linux-modules-nvidia-470-5.19.0-32-generic        5.19.0-32.33~22.04.1                        amd64        Linux kernel nvidia modules for version 5.19.0-32
rc  linux-modules-nvidia-470-5.19.0-42-generic        5.19.0-42.43~22.04.1                        amd64        Linux kernel nvidia modules for version 5.19.0-42
ii  linux-modules-nvidia-470-5.19.0-43-generic        5.19.0-43.44~22.04.1+2                      amd64        Linux kernel nvidia modules for version 5.19.0-43
ii  linux-modules-nvidia-470-5.19.0-45-generic        5.19.0-45.46~22.04.1                        amd64        Linux kernel nvidia modules for version 5.19.0-45
ii  linux-modules-nvidia-470-generic-hwe-22.04        5.19.0-45.46~22.04.1                        amd64        Extra drivers for nvidia-470 for the generic-hwe-22.04 flavour
ii  linux-objects-nvidia-450-server-5.19.0-43-generic 5.19.0-43.44~22.04.1+2                      amd64        Linux kernel nvidia modules for version 5.19.0-43 (objects)
rc  linux-objects-nvidia-470-5.19.0-42-generic        5.19.0-42.43~22.04.1                        amd64        Linux kernel nvidia modules for version 5.19.0-42 (objects)
ii  linux-objects-nvidia-470-5.19.0-43-generic        5.19.0-43.44~22.04.1+2                      amd64        Linux kernel nvidia modules for version 5.19.0-43 (objects)
ii  linux-objects-nvidia-470-5.19.0-45-generic        5.19.0-45.46~22.04.1                        amd64        Linux kernel nvidia modules for version 5.19.0-45 (objects)
ii  linux-signatures-nvidia-5.19.0-43-generic         5.19.0-43.44~22.04.1+2                      amd64        Linux kernel signatures for nvidia modules for version 5.19.0-43-generic
ii  linux-signatures-nvidia-5.19.0-45-generic         5.19.0-45.46~22.04.1                        amd64        Linux kernel signatures for nvidia modules for version 5.19.0-45-generic
rc  nvidia-compute-utils-450-server                   450.236.01-0ubuntu0.22.04.1                 amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-470                          470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA compute utilities
ii  nvidia-driver-470                                 470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-450-server                   450.236.01-0ubuntu0.22.04.1                 amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-470                          470.182.03-0ubuntu0.22.04.1                 amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-470                          470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA kernel source package
ii  nvidia-prime                                      0.8.17.1                                    all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                   510.47.03-0ubuntu1                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-470                                  470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                           0.18.2                                      all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-470                     470.182.03-0ubuntu0.22.04.1                 amd64        NVIDIA binary Xorg driver

```

/var/log/Xorg.0.log

```

[     7.613] (--) Log file renamed from "/var/log/Xorg.pid-1336.log" to "/var/log/Xorg.0.log"
[     7.613]
X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[     7.613] Current Operating System: Linux fgtd 5.19.0-45-generic #46~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Jun 7 15:06:04 UTC 20 x86_64
[     7.613] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.19.0-45-generic root=UUID=avvwxkea-5147-48c4-97c2-307lsce0b972 ro
[     7.613] xorg-server 2:21.1.4-2ubuntu1.7~22.04.1 (For technical support please see http://www.ubuntu.com/support)
[     7.613] Current version of pixman: 0.40.0
[     7.613]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     7.613] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.613] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 16 14:49:01 2023
[     7.614] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.617] (==) No Layout section.  Using the first Screen section.
[     7.617] (==) No screen section available. Using defaults.
[     7.617] (**) |-->Screen "Default Screen Section" (0)
[     7.617] (**) |   |-->Monitor "<default monitor>"
[     7.618] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     7.618] (==) Automatically adding devices
[     7.618] (==) Automatically enabling devices
[     7.618] (==) Automatically adding GPU devices
[     7.618] (==) Automatically binding GPU devices
[     7.618] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     7.622] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.622]     Entry deleted from font path.
[     7.622] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     7.622]     Entry deleted from font path.
[     7.622] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     7.622]     Entry deleted from font path.
[     7.622] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     7.622]     Entry deleted from font path.
[     7.622] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     7.622]     Entry deleted from font path.
[     7.622] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     7.622] (==) ModulePath set to "/usr/lib/xorg/modules"
[     7.622] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     7.622] (II) Loader magic: 0x563548ed8020
[     7.622] (II) Module ABI versions:
[     7.622]     X.Org ANSI C Emulation: 0.4
[     7.622]     X.Org Video Driver: 25.2
[     7.622]     X.Org XInput driver : 24.4
[     7.622]     X.Org Server Extension : 10.0
[     7.622] (++) using VT number 1

[     7.622] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     7.623] (II) xfree86: Adding drm device (/dev/dri/card0)
[     7.623] (II) Platform probe for /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     7.623] (II) xfree86: Adding drm device (/dev/dri/card1)
[     7.623] (II) Platform probe for /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/drm/card1
[     7.648] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[     7.648] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[     7.649] (--) PCI:*(1@0:0:0) 17de:158b:1043:8572 rev 161, Mem @ 0xac000000/16777216, 0xa0000000/134217728, 0xa8000000/33554432, I/O @ 0x00005000/128, BIOS @ 0x????????/524288
[     7.649] (--) PCI: (4@0:0:0) 10de:8562:1043:884a rev 161, Mem @ 0xaa000000/16777216, 0x90000000/134217728, 0x98000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[     7.649] (II) LoadModule: "glx"
[     7.650] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     7.656] (II) Module glx: vendor="X.Org Foundation"
[     7.656]     compiled for 1.21.1.4, module version = 1.0.0
[     7.656]     ABI class: X.Org Server Extension, version 10.0
[     7.656] (II) Applying OutputClass "nvidia" to /dev/dri/card0
[     7.656]     loading driver: nvidia
[     7.782] (II) Applying OutputClass "nvidia" to /dev/dri/card1
[     7.782]     loading driver: nvidia
[     7.993] (==) Matched nvidia as autoconfigured driver 0
[     7.993] (==) Matched nouveau as autoconfigured driver 1
[     7.993] (==) Matched modesetting as autoconfigured driver 2
[     7.993] (==) Matched fbdev as autoconfigured driver 3
[     7.993] (==) Matched vesa as autoconfigured driver 4
[     7.993] (==) Assigned the driver to the xf86ConfigLayout
[     7.993] (II) LoadModule: "nvidia"
[     7.993] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[     7.996] (II) Module nvidia: vendor="NVIDIA Corporation"
[     7.996]     compiled for 1.6.99.901, module version = 1.0.0
[     7.996]     Module class: X.Org Video Driver
[     7.996] (II) LoadModule: "nouveau"
[     7.997] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     7.997] (II) Module nouveau: vendor="X.Org Foundation"
[     7.997]     compiled for 1.21.1.3, module version = 1.0.17
[     7.997]     Module class: X.Org Video Driver
[     7.997]     ABI class: X.Org Video Driver, version 25.2
[     7.998] (II) LoadModule: "modesetting"
[     7.998] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     7.998] (II) Module modesetting: vendor="X.Org Foundation"
[     7.998]     compiled for 1.21.1.4, module version = 1.21.1
[     7.998]     Module class: X.Org Video Driver
[     7.998]     ABI class: X.Org Video Driver, version 25.2
[     7.998] (II) LoadModule: "fbdev"
[     7.998] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     7.998] (II) Module fbdev: vendor="X.Org Foundation"
[     7.998]     compiled for 1.21.1.3, module version = 0.5.0
[     7.998]     Module class: X.Org Video Driver
[     7.998]     ABI class: X.Org Video Driver, version 25.2
[     7.998] (II) LoadModule: "vesa"
[     7.999] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.999] (II) Module vesa: vendor="X.Org Foundation"
[     7.999]     compiled for 1.21.1.3, module version = 2.5.0
[     7.999]     Module class: X.Org Video Driver
[     7.999]     ABI class: X.Org Video Driver, version 25.2
[     7.999] (II) NVIDIA dlloader X Driver  470.182.03  Fri Feb 24 03:24:48 UTC 2023
[     7.999] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     7.999] (II) NOUVEAU driver Date:   Sat Jan 23 12:24:42 2021 -0500
[     7.999] (II) NOUVEAU driver for NVIDIA chipset families :
[     7.999]     RIVA TNT            (NV04)
[     7.999]     RIVA TNT2           (NV05)
[     7.999]     GeForce 256         (NV10)
[     7.999]     GeForce 2           (NV11, NV15)
[     7.999]     GeForce 4MX         (NV17, NV18)
[     7.999]     GeForce 3           (NV20)
[     7.999]     GeForce 4Ti         (NV25, NV28)
[     7.999]     GeForce FX          (NV3x)
[     7.999]     GeForce 6           (NV4x)
[     7.999]     GeForce 7           (G7x)
[     7.999]     GeForce 8           (G8x)
[     7.999]     GeForce 9           (G9x)
[     7.999]     GeForce GTX 2xx/3xx (GT2xx)
[     7.999]     GeForce GTX 4xx/5xx (GFxxx)
[     7.999]     GeForce GTX 6xx/7xx (GKxxx)
[     7.999]     GeForce GTX 9xx     (GMxxx)
[     7.999]     GeForce GTX 10xx    (GPxxx)
[     7.999] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     7.999] (II) FBDEV: driver for framebuffer: fbdev
[     7.999] (II) VESA: driver for VESA chipsets: vesa
[     8.000] (II) Loading sub module "fb"
[     8.000] (II) LoadModule: "fb"
[     8.000] (II) Module "fb" already built-in
[     8.000] (II) Loading sub module "wfb"
[     8.000] (II) LoadModule: "wfb"
[     8.000] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     8.001] (II) Module wfb: vendor="X.Org Foundation"
[     8.001]     compiled for 1.21.1.4, module version = 1.0.0
[     8.001]     ABI class: X.Org ANSI C Emulation, version 0.4
[     8.001] (II) Loading sub module "ramdac"
[     8.001] (II) LoadModule: "ramdac"
[     8.001] (II) Module "ramdac" already built-in
[     8.002] (WW) Falling back to old probe method for modesetting
[     8.002] (WW) Falling back to old probe method for fbdev
[     8.002] (II) Loading sub module "fbdevhw"
[     8.002] (II) LoadModule: "fbdevhw"
[     8.002] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     8.002] (II) Module fbdevhw: vendor="X.Org Foundation"
[     8.002]     compiled for 1.21.1.4, module version = 0.0.2
[     8.002]     ABI class: X.Org Video Driver, version 25.2
[     8.002] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     8.002] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     8.002] (==) NVIDIA(0): RGB weight 888
[     8.002] (==) NVIDIA(0): Default visual is TrueColor
[     8.002] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     8.002] (II) Applying OutputClass "nvidia" options to /dev/dri/card0
[     8.002] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[     8.002] (**) NVIDIA(0): Enabling 2D acceleration
[     8.002] (II) Loading sub module "glxserver_nvidia"
[     8.002] (II) LoadModule: "glxserver_nvidia"
[     8.002] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglxserver_nvidia.so
[     8.024] (II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
[     8.024]     compiled for 1.6.99.901, module version = 1.0.0
[     8.024]     Module class: X.Org Server Extension
[     8.024] (II) NVIDIA GLX Module  470.182.03  Fri Feb 24 03:21:43 UTC 2023
[     8.025] (II) NVIDIA: The X server supports PRIME Render Offload.
[     8.027] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     8.027] (--) NVIDIA(0):     CRT-0
[     8.027] (--) NVIDIA(0):     DFP-0 (boot)
[     8.027] (--) NVIDIA(0):     DFP-1
[     8.028] (II) NVIDIA(0): NVIDIA GPU NVIDIA GeForce GT 710 (GK208) at PCI:1:0:0 (GPU-0)
[     8.028] (--) NVIDIA(0): Memory: 2097152 kBytes
[     8.028] (--) NVIDIA(0): VideoBIOS: 80.28.b0.00.05
[     8.028] (II) NVIDIA(0): Detected PCI Express Link width: 8X
[     8.057] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[     8.057] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[     8.057] (--) NVIDIA(GPU-0):
[     8.071] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[     8.071] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[     8.071] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[     8.071] (--) NVIDIA(GPU-0):
[     8.071] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     8.071] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     8.071] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     8.071] (--) NVIDIA(GPU-0):
[     8.076] (==) NVIDIA(0):
[     8.076] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     8.076] (==) NVIDIA(0):     will be used as the requested mode.
[     8.076] (==) NVIDIA(0):
[     8.076] (II) NVIDIA(0): Validated MetaModes:
[     8.076] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select,CRT-0:nvidia-auto-select"
[     8.076] (II) NVIDIA(0): Virtual screen size determined to be 3360 x 1080
[     8.078] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[     8.078] (--) NVIDIA(0):     option
[     8.079] (==) NVIDIA(G0): Depth 24, (==) framebuffer bpp 32
[     8.079] (==) NVIDIA(G0): RGB weight 888
[     8.079] (==) NVIDIA(G0): Default visual is TrueColor
[     8.079] (==) NVIDIA(G0): Using gamma correction (1.0, 1.0, 1.0)
[     8.079] (II) Applying OutputClass "nvidia" options to /dev/dri/card1
[     8.079] (**) NVIDIA(G0): Option "AllowEmptyInitialConfiguration"
[     8.079] (**) NVIDIA(G0): Enabling 2D acceleration
[     8.079] (II) NVIDIA: The X server supports PRIME Render Offload.
[     8.080] (--) NVIDIA(0): Valid display device(s) on GPU-1 at PCI:4:0:0
[     8.080] (--) NVIDIA(0):     DFP-0
[     8.080] (--) NVIDIA(0):     DFP-1 (boot)
[     8.080] (--) NVIDIA(0):     DFP-2
[     8.080] (--) NVIDIA(0):     DFP-3
[     8.081] (II) NVIDIA(G0): NVIDIA GPU NVIDIA GeForce GT 730 (GK208) at PCI:4:0:0 (GPU-1)
[     8.081] (--) NVIDIA(G0): Memory: 2097152 kBytes
[     8.081] (--) NVIDIA(G0): VideoBIOS: 80.28.b8.00.13
[     8.081] (II) NVIDIA(G0): Detected PCI Express Link width: 8X
[     8.081] (--) NVIDIA(GPU-1): DFP-0: disconnected
[     8.081] (--) NVIDIA(GPU-1): DFP-0: Internal TMDS
[     8.081] (--) NVIDIA(GPU-1): DFP-0: 165.0 MHz maximum pixel clock
[     8.081] (--) NVIDIA(GPU-1):
[     8.124] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[     8.124] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[     8.124] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[     8.124] (--) NVIDIA(GPU-1):
[     8.168] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): connected
[     8.168] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): Internal TMDS
[     8.168] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): 340.0 MHz maximum pixel clock
[     8.168] (--) NVIDIA(GPU-1):
[     8.168] (--) NVIDIA(GPU-1): DFP-3: disconnected
[     8.168] (--) NVIDIA(GPU-1): DFP-3: Internal TMDS
[     8.168] (--) NVIDIA(GPU-1): DFP-3: 165.0 MHz maximum pixel clock
[     8.168] (--) NVIDIA(GPU-1):
[     8.173] (II) NVIDIA(G0): Validated MetaModes:
[     8.173] (II) NVIDIA(G0):     "NULL"
[     8.173] (II) NVIDIA(G0): Virtual screen size determined to be 640 x 480
[     8.177] (WW) NVIDIA(G0): Cannot find size of first mode for HPN HP Model3 (DFP-1); cannot
[     8.177] (WW) NVIDIA(G0):     compute DPI from HPN HP Model3 (DFP-1)'s EDID.
[     8.177] (==) NVIDIA(G0): DPI set to (75, 75); computed from built-in default
[     8.177] (II) UnloadModule: "nouveau"
[     8.177] (II) Unloading nouveau
[     8.177] (II) UnloadModule: "modesetting"
[     8.177] (II) Unloading modesetting
[     8.177] (II) UnloadModule: "fbdev"
[     8.177] (II) Unloading fbdev
[     8.177] (II) UnloadSubModule: "fbdevhw"
[     8.177] (II) Unloading fbdevhw
[     8.177] (II) UnloadModule: "vesa"
[     8.177] (II) Unloading vesa
[     8.177] (II) NVIDIA: Reserving 6144.00 MB of virtual memory for indirect memory
[     8.177] (II) NVIDIA:     access.
[     8.196] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,CRT-0:nvidia-auto-select"
[     8.251] (==) NVIDIA(0): Disabling shared memory pixmaps
[     8.251] (==) NVIDIA(0): Backing store enabled
[     8.251] (==) NVIDIA(0): Silken mouse enabled
[     8.251] (==) NVIDIA(0): DPMS enabled
[     8.251] (II) Loading sub module "dri2"
[     8.251] (II) LoadModule: "dri2"
[     8.251] (II) Module "dri2" already built-in
[     8.252] (II) NVIDIA(0): [DRI2] Setup complete
[     8.252] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     8.272] (II) NVIDIA(G0): Setting mode "NULL"
[     8.278] (==) NVIDIA(G0): Disabling shared memory pixmaps
[     8.278] (==) NVIDIA(G0): Backing store enabled
[     8.278] (==) NVIDIA(G0): Silken mouse enabled
[     8.278] (==) NVIDIA(G0): DPMS enabled
[     8.278] (II) Loading sub module "dri2"
[     8.278] (II) LoadModule: "dri2"
[     8.278] (II) Module "dri2" already built-in
[     8.278] (II) NVIDIA(G0): [DRI2] Setup complete
[     8.278] (II) NVIDIA(G0): [DRI2]   VDPAU driver: nvidia
[     8.278] (II) Initializing extension Generic Event Extension
[     8.278] (II) Initializing extension SHAPE
[     8.278] (II) Initializing extension MIT-SHM
[     8.278] (II) Initializing extension XInputExtension
[     8.278] (II) Initializing extension XTEST
[     8.278] (II) Initializing extension BIG-REQUESTS
[     8.278] (II) Initializing extension SYNC
[     8.278] (II) Initializing extension XKEYBOARD
[     8.278] (II) Initializing extension XC-MISC
[     8.279] (II) Initializing extension SECURITY
[     8.279] (II) Initializing extension XFIXES
[     8.279] (II) Initializing extension RENDER
[     8.279] (II) Initializing extension RANDR
[     8.279] (II) Initializing extension COMPOSITE
[     8.279] (II) Initializing extension DAMAGE
[     8.279] (II) Initializing extension MIT-SCREEN-SAVER
[     8.279] (II) Initializing extension DOUBLE-BUFFER
[     8.279] (II) Initializing extension RECORD
[     8.279] (II) Initializing extension DPMS
[     8.279] (II) Initializing extension Present
[     8.279] (II) Initializing extension DRI3
[     8.279] (II) Initializing extension X-Resource
[     8.279] (II) Initializing extension XVideo
[     8.279] (II) Initializing extension XVideo-MotionCompensation
[     8.279] (II) Initializing extension SELinux
[     8.279] (II) SELinux: Disabled on system
[     8.279] (II) Initializing extension GLX
[     8.280] (II) Initializing extension GLX
[     8.280] (II) Indirect GLX disabled.
[     8.280] (II) GLX: Another vendor is already registered for screen 0
[     8.280] (II) Initializing extension XFree86-VidModeExtension
[     8.280] (II) Initializing extension XFree86-DGA
[     8.280] (II) Initializing extension XFree86-DRI
[     8.280] (II) Initializing extension DRI2
[     8.280] (II) Initializing extension NV-GLX
[     8.280] (II) Initializing extension NV-CONTROL
[     8.280] (II) Initializing extension XINERAMA
[     8.328] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     8.328] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     8.328] (II) LoadModule: "libinput"
[     8.328] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[     8.330] (II) Module libinput: vendor="X.Org Foundation"
[     8.330]     compiled for 1.20.14, module version = 1.2.1
[     8.330]     Module class: X.Org XInput Driver
[     8.330]     ABI class: X.Org XInput driver, version 24.1
[     8.330] (II) Using input driver 'libinput' for 'Power Button'
[     8.330] (**) Power Button: always reports core events
[     8.330] (**) Option "Device" "/dev/input/event2"
[     8.334] (II) event2  - Power Button: is tagged by udev as: Keyboard
[     8.334] (II) event2  - Power Button: device is a keyboard
[     8.334] (II) event2  - Power Button: device removed
[     8.348] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     8.348] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     8.348] (**) Option "xkb_model" "pc105"
[     8.348] (**) Option "xkb_layout" "eng"
[     8.360] (II) event2  - Power Button: is tagged by udev as: Keyboard
[     8.360] (II) event2  - Power Button: device is a keyboard
[     8.360] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.360] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     8.360] (II) Using input driver 'libinput' for 'Power Button'
[     8.360] (**) Power Button: always reports core events
[     8.360] (**) Option "Device" "/dev/input/event1"
[     8.361] (II) event1  - Power Button: is tagged by udev as: Keyboard
[     8.361] (II) event1  - Power Button: device is a keyboard
[     8.361] (II) event1  - Power Button: device removed
[     8.380] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     8.380] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     8.380] (**) Option "xkb_model" "pc105"
[     8.380] (**) Option "xkb_layout" "eng"
[     8.381] (II) event1  - Power Button: is tagged by udev as: Keyboard
[     8.381] (II) event1  - Power Button: device is a keyboard
[     8.381] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[     8.381] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[     8.381] (II) Using input driver 'libinput' for 'Sleep Button'
[     8.381] (**) Sleep Button: always reports core events
[     8.381] (**) Option "Device" "/dev/input/event0"
[     8.382] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[     8.382] (II) event0  - Sleep Button: device is a keyboard
[     8.382] (II) event0  - Sleep Button: device removed
[     8.396] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[     8.396] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[     8.396] (**) Option "xkb_model" "pc105"
[     8.396] (**) Option "xkb_layout" "eng"
[     8.397] (II) event0  - Sleep Button: is tagged by udev as: Keyboard
[     8.397] (II) event0  - Sleep Button: device is a keyboard
[     8.398] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     8.398] (II) No input driver specified, ignoring this device.
[     8.398] (II) This device may have been added with another device file.
[     8.398] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     8.398] (II) No input driver specified, ignoring this device.
[     8.398] (II) This device may have been added with another device file.
[     8.398] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     8.398] (II) No input driver specified, ignoring this device.
[     8.398] (II) This device may have been added with another device file.
[     8.398] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event17)
[     8.398] (II) No input driver specified, ignoring this device.
[     8.398] (II) This device may have been added with another device file.
[     8.399] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=10 (/dev/input/event18)
[     8.399] (II) No input driver specified, ignoring this device.
[     8.399] (II) This device may have been added with another device file.
[     8.399] (II) config/udev: Adding input device Logitech Model5 (/dev/input/event6)
[     8.399] (**) Logitech Model5: Applying InputClass "libinput pointer catchall"
[     8.399] (II) Using input driver 'libinput' for 'Logitech Model5'
[     8.399] (**) Logitech Model5: always reports core events
[     8.399] (**) Option "Device" "/dev/input/event6"
[     8.401] (II) event6  - Logitech Model5: is tagged by udev as: Mouse
[     8.401] (II) event6  - Logitech Model5: device set to 1000 DPI
[     8.401] (II) event6  - Logitech Model5: device is a pointer
[     8.401] (II) event6  - Logitech Model5: device removed
[     8.436] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.2/0003:046D:C52B.0003/0003:046D:101B.0009/input/input31/event6"
[     8.436] (II) XINPUT: Adding extended input device "Logitech Model5" (type: MOUSE, id 9)
[     8.436] (**) Option "AccelerationScheme" "none"
[     8.436] (**) Logitech Model5: (accel) selected scheme none/0
[     8.436] (**) Logitech Model5: (accel) acceleration factor: 2.000
[     8.436] (**) Logitech Model5: (accel) acceleration threshold: 4
[     8.437] (II) event6  - Logitech Model5: is tagged by udev as: Mouse
[     8.437] (II) event6  - Logitech Model5: device set to 1000 DPI
[     8.437] (II) event6  - Logitech Model5: device is a pointer
[     8.438] (II) config/udev: Adding input device Logitech Model5 (/dev/input/mouse2)
[     8.438] (II) No input driver specified, ignoring this device.
[     8.438] (II) This device may have been added with another device file.
[     8.439] (II) config/udev: Adding input device Logitech Model6 (/dev/input/event3)
[     8.439] (**) Logitech Model6: Applying InputClass "libinput keyboard catchall"
[     8.439] (II) Using input driver 'libinput' for 'Logitech Model6'
[     8.439] (**) Logitech Model6: always reports core events
[     8.439] (**) Option "Device" "/dev/input/event3"
[     8.440] (II) event3  - Logitech Model6: is tagged by udev as: Keyboard
[     8.440] (II) event3  - Logitech Model6: device is a keyboard
[     8.440] (II) event3  - Logitech Model6: device removed
[     8.460] (II) libinput: Logitech Model6: needs a virtual subdevice
[     8.460] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.2/0003:046D:C52B.0003/0003:046D:4004.0006/input/input28/event3"
[     8.460] (II) XINPUT: Adding extended input device "Logitech Model6" (type: MOUSE, id 10)
[     8.460] (**) Option "AccelerationScheme" "none"
[     8.460] (**) Logitech Model6: (accel) selected scheme none/0
[     8.460] (**) Logitech Model6: (accel) acceleration factor: 2.000
[     8.460] (**) Logitech Model6: (accel) acceleration threshold: 4
[     8.461] (II) event3  - Logitech Model6: is tagged by udev as: Keyboard
[     8.461] (II) event3  - Logitech Model6: device is a keyboard
[     8.462] (II) config/udev: Adding input device Logitech Model6 (/dev/input/event5)
[     8.462] (**) Logitech Model6: Applying InputClass "libinput keyboard catchall"
[     8.462] (II) Using input driver 'libinput' for 'Logitech Model6'
[     8.462] (**) Logitech Model6: always reports core events
[     8.462] (**) Option "Device" "/dev/input/event5"
[     8.463] (II) event5  - Logitech Model6: is tagged by udev as: Keyboard
[     8.463] (II) event5  - Logitech Model6: device is a keyboard
[     8.464] (II) event5  - Logitech Model6: device removed
[     8.476] (II) libinput: Logitech Model6: needs a virtual subdevice
[     8.476] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.2/0003:046D:C52B.0003/0003:046D:4004.0008/input/input30/event5"
[     8.476] (II) XINPUT: Adding extended input device "Logitech Model6" (type: MOUSE, id 11)
[     8.476] (**) Option "AccelerationScheme" "none"
[     8.476] (**) Logitech Model6: (accel) selected scheme none/0
[     8.476] (**) Logitech Model6: (accel) acceleration factor: 2.000
[     8.476] (**) Logitech Model6: (accel) acceleration threshold: 4
[     8.477] (II) event5  - Logitech Model6: is tagged by udev as: Keyboard
[     8.477] (II) event5  - Logitech Model6: device is a keyboard
[     8.478] (II) config/udev: Adding input device Logitech Model7 (/dev/input/event4)
[     8.478] (**) Logitech Model7: Applying InputClass "libinput pointer catchall"
[     8.478] (II) Using input driver 'libinput' for 'Logitech Model7'
[     8.478] (**) Logitech Model7: always reports core events
[     8.478] (**) Option "Device" "/dev/input/event4"
[     8.479] (II) event4  - Logitech Model7: is tagged by udev as: Mouse
[     8.479] (II) event4  - Logitech Model7: device is a pointer
[     8.480] (II) event4  - Logitech Model7: device removed
[     8.508] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.2/0003:046D:C52B.0003/0003:046D:4009.0007/input/input29/event4"
[     8.508] (II) XINPUT: Adding extended input device "Logitech Model7" (type: MOUSE, id 12)
[     8.508] (**) Option "AccelerationScheme" "none"
[     8.508] (**) Logitech Model7: (accel) selected scheme none/0
[     8.508] (**) Logitech Model7: (accel) acceleration factor: 2.000
[     8.508] (**) Logitech Model7: (accel) acceleration threshold: 4
[     8.509] (II) event4  - Logitech Model7: is tagged by udev as: Mouse
[     8.509] (II) event4  - Logitech Model7: device is a pointer
[     8.510] (II) config/udev: Adding input device Logitech Model7 (/dev/input/mouse0)
[     8.510] (II) No input driver specified, ignoring this device.
[     8.510] (II) This device may have been added with another device file.
[     8.511] (II) config/udev: Adding input device Logitech Gaming Mouse Model8 (/dev/input/event7)
[     8.511] (**) Logitech Gaming Mouse Model8: Applying InputClass "libinput pointer catchall"
[     8.511] (II) Using input driver 'libinput' for 'Logitech Gaming Mouse Model8'
[     8.511] (**) Logitech Gaming Mouse Model8: always reports core events
[     8.511] (**) Option "Device" "/dev/input/event7"
[     8.569] (II) event7  - Logitech Gaming Mouse Model8: is tagged by udev as: Mouse
[     8.569] (II) event7  - Logitech Gaming Mouse Model8: device set to 2400 DPI
[     8.569] (II) event7  - Logitech Gaming Mouse Model8: device is a pointer
[     8.569] (II) event7  - Logitech Gaming Mouse Model8: device removed
[     8.604] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:046D:C332.0004/input/input8/event7"
[     8.604] (II) XINPUT: Adding extended input device "Logitech Gaming Mouse Model8" (type: MOUSE, id 13)
[     8.604] (**) Option "AccelerationScheme" "none"
[     8.604] (**) Logitech Gaming Mouse Model8: (accel) selected scheme none/0
[     8.604] (**) Logitech Gaming Mouse Model8: (accel) acceleration factor: 2.000
[     8.604] (**) Logitech Gaming Mouse Model8: (accel) acceleration threshold: 4
[     8.665] (II) event7  - Logitech Gaming Mouse Model8: is tagged by udev as: Mouse
[     8.665] (II) event7  - Logitech Gaming Mouse Model8: device set to 2400 DPI
[     8.665] (II) event7  - Logitech Gaming Mouse Model8: device is a pointer
[     8.666] (II) config/udev: Adding input device Logitech Gaming Mouse Model8 (/dev/input/mouse1)
[     8.666] (II) No input driver specified, ignoring this device.
[     8.666] (II) This device may have been added with another device file.
[     8.666] (II) config/udev: Adding input device Logitech Gaming Mouse Model8 Keyboard (/dev/input/event8)
[     8.666] (**) Logitech Gaming Mouse Model8 Keyboard: Applying InputClass "libinput keyboard catchall"
[     8.666] (II) Using input driver 'libinput' for 'Logitech Gaming Mouse Model8 Keyboard'
[     8.666] (**) Logitech Gaming Mouse Model8 Keyboard: always reports core events
[     8.666] (**) Option "Device" "/dev/input/event8"
[     8.667] (II) event8  - Logitech Gaming Mouse Model8 Keyboard: is tagged by udev as: Keyboard
[     8.667] (II) event8  - Logitech Gaming Mouse Model8 Keyboard: device is a keyboard
[     8.668] (II) event8  - Logitech Gaming Mouse Model8 Keyboard: device removed
[     8.680] (II) libinput: Logitech Gaming Mouse Model8 Keyboard: needs a virtual subdevice
[     8.680] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:046D:C332.0005/input/input9/event8"
[     8.680] (II) XINPUT: Adding extended input device "Logitech Gaming Mouse Model8 Keyboard" (type: MOUSE, id 14)
[     8.680] (**) Option "AccelerationScheme" "none"
[     8.680] (**) Logitech Gaming Mouse Model8 Keyboard: (accel) selected scheme none/0
[     8.680] (**) Logitech Gaming Mouse Model8 Keyboard: (accel) acceleration factor: 2.000
[     8.680] (**) Logitech Gaming Mouse Model8 Keyboard: (accel) acceleration threshold: 4
[     8.681] (II) event8  - Logitech Gaming Mouse Model8 Keyboard: is tagged by udev as: Keyboard
[     8.681] (II) event8  - Logitech Gaming Mouse Model8 Keyboard: device is a keyboard
[     8.682] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event20)
[     8.682] (II) No input driver specified, ignoring this device.
[     8.682] (II) This device may have been added with another device file.
[     8.682] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event21)
[     8.682] (II) No input driver specified, ignoring this device.
[     8.682] (II) This device may have been added with another device file.
[     8.683] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event22)
[     8.683] (II) No input driver specified, ignoring this device.
[     8.683] (II) This device may have been added with another device file.
[     8.683] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event23)
[     8.683] (II) No input driver specified, ignoring this device.
[     8.683] (II) This device may have been added with another device file.
[     8.683] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=10 (/dev/input/event24)
[     8.683] (II) No input driver specified, ignoring this device.
[     8.683] (II) This device may have been added with another device file.
[     8.684] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=11 (/dev/input/event25)
[     8.684] (II) No input driver specified, ignoring this device.
[     8.684] (II) This device may have been added with another device file.
[     8.684] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=12 (/dev/input/event26)
[     8.684] (II) No input driver specified, ignoring this device.
[     8.684] (II) This device may have been added with another device file.
[     8.684] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[     8.684] (II) No input driver specified, ignoring this device.
[     8.684] (II) This device may have been added with another device file.
[     8.685] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event11)
[     8.685] (II) No input driver specified, ignoring this device.
[     8.685] (II) This device may have been added with another device file.
[     8.685] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event12)
[     8.685] (II) No input driver specified, ignoring this device.
[     8.685] (II) This device may have been added with another device file.
[     8.685] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event16)
[     8.685] (II) No input driver specified, ignoring this device.
[     8.685] (II) This device may have been added with another device file.
[     8.685] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event19)
[     8.686] (II) No input driver specified, ignoring this device.
[     8.686] (II) This device may have been added with another device file.
[     8.686] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event9)
[     8.686] (**) Eee PC WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[     8.686] (II) Using input driver 'libinput' for 'Eee PC WMI hotkeys'
[     8.686] (**) Eee PC WMI hotkeys: always reports core events
[     8.686] (**) Option "Device" "/dev/input/event9"
[     8.686] (II) event9  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[     8.686] (II) event9  - Eee PC WMI hotkeys: device is a keyboard
[     8.686] (II) event9  - Eee PC WMI hotkeys: device removed
[     8.704] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input32/event9"
[     8.704] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 15)
[     8.704] (**) Option "xkb_model" "pc105"
[     8.704] (**) Option "xkb_layout" "eng"
[     8.705] (II) event9  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[     8.705] (II) event9  - Eee PC WMI hotkeys: device is a keyboard
[     8.713] (**) Logitech Model6: Applying InputClass "libinput keyboard catchall"
[     8.713] (II) Using input driver 'libinput' for 'Logitech Model6'
[     8.713] (**) Logitech Model6: always reports core events
[     8.713] (**) Option "Device" "/dev/input/event3"
[     8.713] (II) libinput: Logitech Model6: is a virtual subdevice
[     8.713] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.2/0003:046D:C52B.0003/0003:046D:4004.0006/input/input28/event3"
[     8.713] (II) XINPUT: Adding extended input device "Logitech Model6" (type: KEYBOARD, id 16)
[     8.713] (**) Option "xkb_model" "pc105"
[     8.713] (**) Option "xkb_layout" "eng"
[     8.713] (**) Logitech Model6: Applying InputClass "libinput keyboard catchall"
[     8.713] (II) Using input driver 'libinput' for 'Logitech Model6'
[     8.713] (**) Logitech Model6: always reports core events
[     8.713] (**) Option "Device" "/dev/input/event5"
[     8.713] (II) libinput: Logitech Model6: is a virtual subdevice
[     8.713] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.2/0003:046D:C52B.0003/0003:046D:4004.0008/input/input30/event5"
[     8.713] (II) XINPUT: Adding extended input device "Logitech Model6" (type: KEYBOARD, id 17)
[     8.713] (**) Option "xkb_model" "pc105"
[     8.713] (**) Option "xkb_layout" "eng"
[     8.713] (**) Logitech Gaming Mouse Model8 Keyboard: Applying InputClass "libinput keyboard catchall"
[     8.713] (II) Using input driver 'libinput' for 'Logitech Gaming Mouse Model8 Keyboard'
[     8.713] (**) Logitech Gaming Mouse Model8 Keyboard: always reports core events
[     8.713] (**) Option "Device" "/dev/input/event8"
[     8.713] (II) libinput: Logitech Gaming Mouse Model8 Keyboard: is a virtual subdevice
[     8.713] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.1/0003:046D:C332.0005/input/input9/event8"
[     8.713] (II) XINPUT: Adding extended input device "Logitech Gaming Mouse Model8 Keyboard" (type: KEYBOARD, id 18)
[     8.713] (**) Option "xkb_model" "pc105"
[     8.713] (**) Option "xkb_layout" "eng"
[     8.759] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[     8.759] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[     8.759] (--) NVIDIA(GPU-0):
[     8.774] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[     8.774] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[     8.774] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[     8.774] (--) NVIDIA(GPU-0):
[     8.774] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     8.774] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     8.774] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     8.774] (--) NVIDIA(GPU-0):
[     8.804] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[     8.804] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[     8.804] (--) NVIDIA(GPU-0):
[     8.818] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[     8.818] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[     8.818] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[     8.818] (--) NVIDIA(GPU-0):
[     8.818] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     8.818] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     8.818] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     8.818] (--) NVIDIA(GPU-0):
[     8.818] (--) NVIDIA(GPU-1): DFP-0: disconnected
[     8.818] (--) NVIDIA(GPU-1): DFP-0: Internal TMDS
[     8.818] (--) NVIDIA(GPU-1): DFP-0: 165.0 MHz maximum pixel clock
[     8.818] (--) NVIDIA(GPU-1):
[     8.862] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[     8.862] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[     8.862] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[     8.862] (--) NVIDIA(GPU-1):
[     8.909] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): connected
[     8.909] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): Internal TMDS
[     8.909] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): 340.0 MHz maximum pixel clock
[     8.909] (--) NVIDIA(GPU-1):
[     8.909] (--) NVIDIA(GPU-1): DFP-3: disconnected
[     8.910] (--) NVIDIA(GPU-1): DFP-3: Internal TMDS
[     8.910] (--) NVIDIA(GPU-1): DFP-3: 165.0 MHz maximum pixel clock
[     8.910] (--) NVIDIA(GPU-1):
[     8.940] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[     8.940] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[     8.940] (--) NVIDIA(GPU-0):
[     8.955] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[     8.955] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[     8.955] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[     8.955] (--) NVIDIA(GPU-0):
[     8.955] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     8.955] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     8.955] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     8.955] (--) NVIDIA(GPU-0):
[     8.962] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[     9.080] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, VGA-0: nvidia-auto-select @1440x900 +0+0 {ViewPortIn=1440x900, ViewPortOut=1440x900+0+0}"
[     9.181] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +1440+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, VGA-0: nvidia-auto-select @1440x900 +0+0 {ViewPortIn=1440x900, ViewPortOut=1440x900+0+0}"
[     9.262] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[     9.262] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[     9.262] (--) NVIDIA(GPU-0):
[     9.277] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[     9.277] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[     9.277] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[     9.277] (--) NVIDIA(GPU-0):
[     9.277] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.277] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.277] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.277] (--) NVIDIA(GPU-0):
[     9.306] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[     9.306] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[     9.306] (--) NVIDIA(GPU-0):
[     9.321] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[     9.321] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[     9.321] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[     9.321] (--) NVIDIA(GPU-0):
[     9.321] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.321] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.321] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.321] (--) NVIDIA(GPU-0):
[     9.321] (--) NVIDIA(GPU-1): DFP-0: disconnected
[     9.321] (--) NVIDIA(GPU-1): DFP-0: Internal TMDS
[     9.321] (--) NVIDIA(GPU-1): DFP-0: 165.0 MHz maximum pixel clock
[     9.321] (--) NVIDIA(GPU-1):
[     9.364] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[     9.364] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[     9.364] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[     9.364] (--) NVIDIA(GPU-1):
[     9.408] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): connected
[     9.408] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): Internal TMDS
[     9.408] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): 340.0 MHz maximum pixel clock
[     9.408] (--) NVIDIA(GPU-1):
[     9.408] (--) NVIDIA(GPU-1): DFP-3: disconnected
[     9.408] (--) NVIDIA(GPU-1): DFP-3: Internal TMDS
[     9.408] (--) NVIDIA(GPU-1): DFP-3: 165.0 MHz maximum pixel clock
[     9.408] (--) NVIDIA(GPU-1):
[     9.438] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[     9.438] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[     9.438] (--) NVIDIA(GPU-0):
[     9.452] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[     9.452] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[     9.452] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[     9.452] (--) NVIDIA(GPU-0):
[     9.452] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.452] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[     9.452] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     9.452] (--) NVIDIA(GPU-0):
[    26.594] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[    26.594] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[    26.594] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[    26.594] (--) NVIDIA(GPU-1):
[    26.639] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[    26.639] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[    26.639] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[    26.639] (--) NVIDIA(GPU-1):
[    32.328] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[    32.328] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[    32.328] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[    32.328] (--) NVIDIA(GPU-1):
[    32.373] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[    32.373] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[    32.373] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[    32.373] (--) NVIDIA(GPU-1):
[   432.099] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[   432.099] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[   432.099] (--) NVIDIA(GPU-0):
[   432.114] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[   432.114] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[   432.114] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[   432.114] (--) NVIDIA(GPU-0):
[   432.114] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   432.114] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[   432.114] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[   432.114] (--) NVIDIA(GPU-0):
[   432.143] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[   432.143] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[   432.143] (--) NVIDIA(GPU-0):
[   432.158] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[   432.158] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[   432.158] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[   432.158] (--) NVIDIA(GPU-0):
[   432.158] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   432.158] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[   432.158] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[   432.158] (--) NVIDIA(GPU-0):
[   432.158] (--) NVIDIA(GPU-1): DFP-0: disconnected
[   432.158] (--) NVIDIA(GPU-1): DFP-0: Internal TMDS
[   432.158] (--) NVIDIA(GPU-1): DFP-0: 165.0 MHz maximum pixel clock
[   432.158] (--) NVIDIA(GPU-1):
[   432.202] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[   432.202] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[   432.202] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[   432.202] (--) NVIDIA(GPU-1):
[   432.247] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): connected
[   432.247] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): Internal TMDS
[   432.247] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): 340.0 MHz maximum pixel clock
[   432.247] (--) NVIDIA(GPU-1):
[   432.247] (--) NVIDIA(GPU-1): DFP-3: disconnected
[   432.247] (--) NVIDIA(GPU-1): DFP-3: Internal TMDS
[   432.247] (--) NVIDIA(GPU-1): DFP-3: 165.0 MHz maximum pixel clock
[   432.247] (--) NVIDIA(GPU-1):
[   432.776] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[   432.776] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[   432.776] (--) NVIDIA(GPU-0):
[   432.791] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[   432.791] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[   432.791] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[   432.791] (--) NVIDIA(GPU-0):
[   432.791] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   432.791] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[   432.791] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[   432.791] (--) NVIDIA(GPU-0):
[   432.820] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): connected
[   432.820] (--) NVIDIA(GPU-0): HP Model1 (CRT-0): 400.0 MHz maximum pixel clock
[   432.820] (--) NVIDIA(GPU-0):
[   432.834] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): connected
[   432.834] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): Internal TMDS
[   432.834] (--) NVIDIA(GPU-0): DELL Model2 (DFP-0): 330.0 MHz maximum pixel clock
[   432.834] (--) NVIDIA(GPU-0):
[   432.834] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   432.834] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[   432.834] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[   432.834] (--) NVIDIA(GPU-0):
[   432.835] (--) NVIDIA(GPU-1): DFP-0: disconnected
[   432.835] (--) NVIDIA(GPU-1): DFP-0: Internal TMDS
[   432.835] (--) NVIDIA(GPU-1): DFP-0: 165.0 MHz maximum pixel clock
[   432.835] (--) NVIDIA(GPU-1):
[   432.879] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): connected
[   432.879] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): Internal TMDS
[   432.879] (--) NVIDIA(GPU-1): HPN HP Model3 (DFP-1): 340.0 MHz maximum pixel clock
[   432.879] (--) NVIDIA(GPU-1):
[   432.924] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): connected
[   432.924] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): Internal TMDS
[   432.924] (--) NVIDIA(GPU-1): HPN HP Model4 (DFP-2): 340.0 MHz maximum pixel clock
[   432.924] (--) NVIDIA(GPU-1):
[   432.924] (--) NVIDIA(GPU-1): DFP-3: disconnected
[   432.924] (--) NVIDIA(GPU-1): DFP-3: Internal TMDS
[   432.924] (--) NVIDIA(GPU-1): DFP-3: 165.0 MHz maximum pixel clock
[   432.924] (--) NVIDIA(GPU-1):
[   433.177] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +1440+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, VGA-0: nvidia-auto-select @1440x900 +5760+0 {ViewPortIn=1440x900, ViewPortOut=1440x900+0+0}"
[   433.225] (II) NVIDIA(0): Setting mode "DVI-D-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, VGA-0: nvidia-auto-select @1440x900 +5760+0 {ViewPortIn=1440x900, ViewPortOut=1440x900+0+0}"
[   433.296] (II) NVIDIA(G0): Setting mode "HDMI-1-1: nvidia-auto-select @1920x1080 +1920+0 {AllowGSYNC=Off, ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[   433.465] (II) NVIDIA(G0): Setting mode "HDMI-1-1: nvidia-auto-select @1920x1080 +1920+0 {AllowGSYNC=Off, ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, HDMI-1-2: nvidia-auto-select @1920x1080 +3840+0 {AllowGSYNC=Off, ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[   570.895] (EE) event7  - Logitech Gaming Mouse Model8: client bug: event processing lagging behind by 22ms, your system is too slow
[   581.510] (EE) event7  - Logitech Gaming Mouse Model8: client bug: event processing lagging behind by 21ms, your system is too slow
[   586.735] (EE) event7  - Logitech Gaming Mouse Model8: client bug: event processing lagging behind by 22ms, your system is too slow
[   606.342] (EE) event7  - Logitech Gaming Mouse Model8: client bug: event processing lagging behind by 21ms, your system is too slow
[   770.255] (EE) event7  - Logitech Gaming Mouse Model8: client bug: event processing lagging behind by 21ms, your system is too slow
[   770.255] (EE) event7  - Logitech Gaming Mouse Model8: WARNING: log rate limit exceeded (5 msgs per 60min). Discarding future messages.
[   883.097] (EE) event3  - Logitech Model6: client bug: event processing lagging behind by 21ms, your system is too slow
[  1170.884] (EE) event3  - Logitech Model6: client bug: event processing lagging behind by 28ms, your system is too slow
[  1229.537] (EE) event3  - Logitech Model6: client bug: event processing lagging behind by 21ms, your system is too slow
[  1482.202] (EE) event3  - Logitech Model6: client bug: event processing lagging behind by 33ms, your system is too slow
[  1583.558] (EE) event3  - Logitech Model6: client bug: event processing lagging behind by 22ms, your system is too slow
[  1583.558] (EE) event3  - Logitech Model6: WARNING: log rate limit exceeded (5 msgs per 60min). Discarding future messages.

```

---

### Post by Bashing-om on 2023-06-16
sed_faster; Hummm ...

All seemingly looks good to me - except -
in the Xorg file:
> 
client bug: event processing lagging behind by 22ms, your system is too slow

I have no clue as to what this may mean.

I am out of ideas as to where the problem with lagging in the GUI may reside - I hope others with greater  skills will offer opinions.

[INDENT]A know-it-all I am not :D
[/INDENT]

---

### Post by TheFu on 2023-06-17
> **Bashing-om said:**
>  and does Xorg report any errors ?
```

cat /var/log/Xorg.0.log

```

some desktops recently moved the file >>
.local/share/xorg/Xorg.0.log

the location change of the file may apply in your case - I run xfce and the file remains in the /var/ directory.

[INDENT]sometimes to do wonder
[INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT]

Xorg (i.e. X11) can be run as root **or** as the user logged in on the console.  Running as root has been a problem, rightly so, for *security conscious* people for 25+ yrs.  This could easily be a move to run X11 as the userid.  Provided it doesn't break anything, this would be nice.  I know a number of distros have supported it for years.  

I don't know how a guest mode and fast-user-switch would work for a non-root X/server.  Would suspect they'd have to restart X between the login manager and login session startup. When the display server is restarted, that kills all X apps connected to it, so it wouldn't be good. While I'd happily do without guest or fast-user-switching, I bet there are places where that gets used 20x a day on every workstation.

Not really related to this issue at hand. Sorry to drop in with nothing to help the real issue.

---

### Post by Yellow Pasque on 2023-06-17
So if we've ruled out a graphics issue, I'd be looking through dmesg for anything related to clock sources. It sounds like it might be a timer/interrupt issue. Can you give output of:
```
dmesg | grep -i -E hpet|tsc|clocksource
```

On my motherboard, I use this boot parameter to force HPET (high precision event timers) to be used as the clock source because the tsc method was giving warnings/errors:
```
tsc=unstable
```

---

### Post by sed_faster on 2023-06-18
I needed install this:

```

[FONT=monospace][COLOR=#000000]sudo apt install node-typescript[/COLOR] -y[/FONT]

```

The output is this:

```

[FONT=monospace][COLOR=#000000]sudo dmesg | grep -i -E hpet|tsc|clocksource [/COLOR]
clocksource: command not found 
events.js:291 
      throw er; // Unhandled 'error' event 
      ^ 

Error: write EPIPE 
[COLOR=#686868]    at afterWriteDispatched (internal/stream_base_commons.js:156:25)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at writeGeneric (internal/stream_base_commons.js:147:3)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at Socket._writeGeneric (net.js:788:11)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at Socket._write (net.js:800:8)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at doWrite (_stream_writable.js:403:12)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at writeOrBuffer (_stream_writable.js:387:5)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at Socket.Writable.write (_stream_writable.js:318:11)[/COLOR][COLOR=#000000] [/COLOR]
    at Object.write (/usr/share/nodejs/typescript/lib/tsc.js:4600:36) 
    at printVersion (/usr/share/nodejs/typescript/lib/tsc.js:101464:13) 
    at executeCommandLineWorker (/usr/share/nodejs/typescript/lib/tsc.js:101819:17) 
Emitted 'error' event on Socket instance at: 
[COLOR=#686868]    at errorOrDestroy (internal/streams/destroy.js:108:12)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at onwriteError (_stream_writable.js:418:5)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at onwrite (_stream_writable.js:445:5)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at internal/streams/destroy.js:50:7[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at Socket.dummyDestroy [as _destroy] (internal/bootstrap/switches/is_main_thread.js:97:3)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at Socket.destroy (internal/streams/destroy.js:38:8)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at afterWriteDispatched (internal/stream_base_commons.js:156:17)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at writeGeneric (internal/stream_base_commons.js:147:3)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at Socket._writeGeneric (net.js:788:11)[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#686868]    at Socket._write (net.js:800:8)[/COLOR][COLOR=#000000] { [/COLOR]
  errno: [COLOR=#18b218]'EPIPE'[/COLOR][COLOR=#000000], [/COLOR]
  code: [COLOR=#18b218]'EPIPE'[/COLOR][COLOR=#000000], [/COLOR]
  syscall: [COLOR=#18b218]'write'[/COLOR][COLOR=#000000] [/COLOR]
}


```

I have no clue what could be!
Thank you
[/FONT]

---

