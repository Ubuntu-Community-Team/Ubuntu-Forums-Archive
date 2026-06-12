---
title: "Laptop doesn't recognize external monitors (Ubuntu 16.04.2)"
date: 2017-08-05
forum: Hardware
---

### Post by insecureboot on 2017-08-05
I installed Ubuntu 16.04.2 on a Dell Precision 5520 laptop that came with Windows 10.  I can't get it to output to my external monitors, or show any sign that they're connected.  The same hardware works when I boot this laptop into Windows 10, and the monitors and cables work when I connect them to a Zareason laptop running Debian.

This laptop top has hybrid graphics, with both an Intel Pro Graphics 630 and an NVidia Quadro M1200.

**Things I've tried**

The default installation didn't recognize the monitors, so I installed NVidia drivers with 'sudo apt-get install nvidia-375'.  That seemed to work but didn't help.

After the original driver installation didn't seem to be working, I did
```

$ sudo apt purge nvidia*
$ sudo rm /etc/X11/xorg.conf
$ sudo ubuntu-drivers autoinstall
```
and rebooted.  That didn't change anything I can find.  Output from the autoinstall is below.

I've checked the BIOS (UEFI) for video-related settings, but the only one I can find is for screen backlight.

```

$ cat ~/data/text/UbuntuDriversAutoinstall.script
Script started on Fri 04 Aug 2017 09:12:39 PM PDT
scorwin@8H2:~$ sudo ubuntu-drivers autoinstall
[sudo] password for scorwin:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcc-5-base:i386 libbsd0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libllvm4.0:i386
  libpciaccess0:i386 libsensors4:i386 libstdc++6:i386 libtxc-dxtn-s2tc0:i386 libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386
  libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxshmfence1:i386 libxxf86vm1:i386 linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.8.0-36 linux-headers-4.8.0-36-generic
  linux-image-4.8.0-36-generic linux-image-extra-4.8.0-36-generic primus-libs primus-libs:i386
  primus-libs-ia32:i386 socat
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libcuda1-375 nvidia-opencl-icd-375 nvidia-prime nvidia-settings
The following NEW packages will be installed:
  libcuda1-375 nvidia-375 nvidia-opencl-icd-375 nvidia-prime nvidia-settings
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/76.1 MB of archives.
After this operation, 337 MB of additional disk space will be used.
Selecting previously unselected package nvidia-375.
(Reading database ... 339537 files and directories currently installed.)
Preparing to unpack .../nvidia-375_375.66-0ubuntu0.16.04.1_amd64.deb ...
Unpacking nvidia-375 (375.66-0ubuntu0.16.04.1) ...
Selecting previously unselected package libcuda1-375.
Preparing to unpack .../libcuda1-375_375.66-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libcuda1-375 (375.66-0ubuntu0.16.04.1) ...
Selecting previously unselected package nvidia-opencl-icd-375.
Preparing to unpack .../nvidia-opencl-icd-375_375.66-0ubuntu0.16.04.1_amd64.deb ...
Unpacking nvidia-opencl-icd-375 (375.66-0ubuntu0.16.04.1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_361.42-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up nvidia-375 (375.66-0ubuntu0.16.04.1) ...
update-alternatives: using /usr/lib/nvidia-375/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-375/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-375/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-375/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-375/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link

update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-375
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 133) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-375-375.66 DKMS files...
First Installation: checking all kernels...
Building only for 4.10.0-28-generic
Building for architecture x86_64
Building initial module for 4.10.0-28-generic
Done.

nvidia_375:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-28-generic/updates/dkms/

nvidia_375_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-28-generic/updates/dkms/

nvidia_375_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-28-generic/updates/dkms/

nvidia_375_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.10.0-28-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up libcuda1-375 (375.66-0ubuntu0.16.04.1) ...
Setting up nvidia-opencl-icd-375 (375.66-0ubuntu0.16.04.1) ...
Setting up nvidia-prime (0.8.2) ...
Setting up nvidia-settings (361.42-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link

Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.10.0-28-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
Processing triggers for shim-signed (1.32~16.04.1+0.9+1474479173.6c180c6-1ubuntu1) ...
Secure Boot not enabled on this system.
Processing triggers for ureadahead (0.100.0-19) ...
[master 13dd7ad] committing changes in /etc after apt run
 42 files changed, 103 insertions(+), 9 deletions(-)
 create mode 100644 OpenCL/vendors/nvidia.icd
 create mode 120000 alternatives/glamor_conf
 create mode 120000 alternatives/i386-linux-gnu_egl_conf
 delete mode 120000 alternatives/i386-linux-gnu_xorg_extra_modules
 create mode 120000 alternatives/x86_64-linux-gnu_libvdpau_nvidia.so
 create mode 120000 alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1
 create mode 120000 alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1_lib32
 create mode 120000 alternatives/x86_64-linux-gnu_libvdpau_nvidia.so_lib32
 create mode 120000 alternatives/x86_64-linux-gnu_man_nvidiaxconfig.gz
 create mode 120000 alternatives/x86_64-linux-gnu_man_persistenced.gz
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia-cuda-mps-control
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia-cuda-mps-control.1.gz
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia-cuda-mps-server
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia-debugdump
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia-smi.1.gz
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_app_profile
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_app_profile_keys
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_bug_report
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_drv
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_modconf
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_persistenced
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_smi
 create mode 120000 alternatives/x86_64-linux-gnu_nvidia_xconfig
 create mode 100644 init/nvidia-prime.conf
 create mode 120000 ld.so.conf.d/i386-linux-gnu_EGL.conf
 create mode 100644 modprobe.d/nvidia-375_hybrid.conf
 create mode 120000 modprobe.d/nvidia-graphics-drivers.conf
 create mode 100644 prime-discrete
 create mode 100644 xdg/autostart/nvidia-settings-autostart.desktop
$ exit
exit

Script done on Fri 04 Aug 2017 09:13:52 PM PDT

```

```

$  dkms status
bbswitch, 0.8, 4.10.0-28-generic, x86_64: installed
nvidia-375, 375.66, 4.10.0-28-generic, x86_64: installed

```

```

$ lsmod | grep nvidia
nvidia_drm             45056  0
nvidia_modeset        790528  1 nvidia_drm
nvidia              12304384  1 nvidia_modeset
drm_kms_helper        151552  2 i915,nvidia_drm
drm                   352256  4 i915,nvidia_drm,drm_kms_helper

```

```

$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
        DeviceName:  Onboard IGD
        Subsystem: Dell Device 07bf
--
01:00.0 3D controller: NVIDIA Corporation Device 13b6 (rev a2)
        Subsystem: Dell Device 07bf
        Kernel driver in use: nvidia

```

```

$ sudo lshw -C display
[sudo] password for scorwin:
  *-display
       description: 3D controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ec000000-ecffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:ed000000-ed07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:eb000000-ebffffff memory:80000000-8fffffff ioport:f000(size=64) memory:c0000-dffff

```

The NVidia X Server Settings app is installed, but when I run it it doesn't have any X Server settings:
[ATTACH=CONFIG]276263[/ATTACH]

Xorg.0.log has some errors that hopefully provide a clue:
```

$ cat /var/log/Xorg.0.log
[     4.206]
X.Org X Server 1.19.3
Release Date: 2017-03-15
[     4.206] X Protocol Version 11, Revision 0
[     4.206] Build Operating System: Linux 4.4.0-87-generic x86_64 Ubuntu
[     4.206] Current Operating System: Linux 8H2 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64
[     4.206] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-28-generic.efi.signed root=UUID=eef38ece-a901-450c-a162-0e3398f2780f ro nomodeset
[     4.206] Build Date: 25 July 2017  01:30:08PM
[     4.206] xorg-server 2:1.19.3-1ubuntu1~16.04.2 (For technical support please see http://www.ubuntu.com/support)
[     4.206] Current version of pixman: 0.33.6
[     4.206]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     4.206] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.206] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  5 08:06:49 2017
[     4.207] (==) Using config file: "/etc/X11/xorg.conf"
[     4.207] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.207] (==) ServerLayout "Layout0"
[     4.207] (**) |-->Screen "Screen 0" (0)
[     4.207] (**) |   |-->Monitor "Monitor0"
[     4.207] (**) |   |-->Device "Device0"
[     4.207] (**) |-->Input Device "Keyboard0"
[     4.207] (**) |-->Input Device "Mouse0"
[     4.207] (==) Automatically adding devices
[     4.207] (==) Automatically enabling devices
[     4.207] (==) Automatically adding GPU devices
[     4.207] (==) Automatically binding GPU devices
[     4.207] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     4.207] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.207]    Entry deleted from font path.
[     4.207] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.207]    Entry deleted from font path.
[     4.207] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.207]    Entry deleted from font path.
[     4.207] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.207]    Entry deleted from font path.
[     4.207] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.207]    Entry deleted from font path.
[     4.207] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     4.207] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.207] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     4.207] (WW) Disabling Keyboard0
[     4.207] (WW) Disabling Mouse0
[     4.207] (II) Loader magic: 0x55b3c429ee00
[     4.207] (II) Module ABI versions:
[     4.207]    X.Org ANSI C Emulation: 0.4
[     4.207]    X.Org Video Driver: 23.0
[     4.207]    X.Org XInput driver : 24.1
[     4.207]    X.Org Server Extension : 10.0
[     4.207] (++) using VT number 7

[     4.207] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     4.208] (II) xfree86: Adding drm device (/dev/dri/card0)
[     4.210] (--) PCI:*(0:0:2:0) 8086:591b:1028:07bf rev 4, Mem @ 0xeb000000/16777216, 0x80000000/268435456, I/O @ 0x0000f000/64, BIOS @ 0x????????/131072
[     4.210] (--) PCI: (0:1:0:0) 10de:13b6:1028:07bf rev 162, Mem @ 0xec000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     4.210] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     4.210] (II) "glx" will be loaded by default.
[     4.210] (II) LoadModule: "glx"
[     4.211] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     4.236] (II) Module glx: vendor="NVIDIA Corporation"
[     4.236]    compiled for 4.0.2, module version = 1.0.0
[     4.236]    Module class: X.Org Server Extension
[     4.237] (II) NVIDIA GLX Module  375.66  Mon May  1 14:28:39 PDT 2017
[     4.237] (II) LoadModule: "nvidia"
[     4.237] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     4.241] (II) Module nvidia: vendor="NVIDIA Corporation"
[     4.241]    compiled for 4.0.2, module version = 1.0.0
[     4.241]    Module class: X.Org Video Driver
[     4.242] (II) NVIDIA dlloader X Driver  375.66  Mon May  1 14:03:26 PDT 2017
[     4.242] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     4.246] (EE) No devices detected.
[     4.246] (==) Matched nvidia as autoconfigured driver 0
[     4.246] (==) Matched nouveau as autoconfigured driver 1
[     4.246] (==) Matched modesetting as autoconfigured driver 2
[     4.246] (==) Matched fbdev as autoconfigured driver 3
[     4.246] (==) Matched vesa as autoconfigured driver 4
[     4.246] (==) Assigned the driver to the xf86ConfigLayout
[     4.246] (II) LoadModule: "nvidia"
[     4.246] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     4.246] (II) Module nvidia: vendor="NVIDIA Corporation"
[     4.246]    compiled for 4.0.2, module version = 1.0.0
[     4.246]    Module class: X.Org Video Driver
[     4.246] (II) UnloadModule: "nvidia"
[     4.246] (II) Unloading nvidia
[     4.246] (II) Failed to load module "nvidia" (already loaded, 21939)
[     4.246] (II) LoadModule: "nouveau"
[     4.246] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     4.247] (II) Module nouveau: vendor="X.Org Foundation"
[     4.247]    compiled for 1.19.3, module version = 1.0.14
[     4.247]    Module class: X.Org Video Driver
[     4.247]    ABI class: X.Org Video Driver, version 23.0
[     4.247] (II) LoadModule: "modesetting"
[     4.247] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.247] (II) Module modesetting: vendor="X.Org Foundation"
[     4.247]    compiled for 1.19.3, module version = 1.19.3
[     4.247]    Module class: X.Org Video Driver
[     4.247]    ABI class: X.Org Video Driver, version 23.0
[     4.247] (II) LoadModule: "fbdev"
[     4.247] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.247] (II) Module fbdev: vendor="X.Org Foundation"
[     4.247]    compiled for 1.19.3, module version = 0.4.4
[     4.247]    Module class: X.Org Video Driver
[     4.247]    ABI class: X.Org Video Driver, version 23.0
[     4.247] (II) LoadModule: "vesa"
[     4.247] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.247] (II) Module vesa: vendor="X.Org Foundation"
[     4.247]    compiled for 1.19.3, module version = 2.3.4
[     4.247]    Module class: X.Org Video Driver
[     4.247]    ABI class: X.Org Video Driver, version 23.0
[     4.247] (II) NVIDIA dlloader X Driver  375.66  Mon May  1 14:03:26 PDT 2017
[     4.247] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     4.247] (II) NOUVEAU driver Date:   Tue Mar 7 18:44:43 2017 -0500
[     4.247] (II) NOUVEAU driver for NVIDIA chipset families :
[     4.247]    RIVA TNT        (NV04)
[     4.247]    RIVA TNT2       (NV05)
[     4.247]    GeForce 256     (NV10)
[     4.247]    GeForce 2       (NV11, NV15)
[     4.247]    GeForce 4MX     (NV17, NV18)
[     4.247]    GeForce 3       (NV20)
[     4.247]    GeForce 4Ti     (NV25, NV28)
[     4.247]    GeForce FX      (NV3x)
[     4.247]    GeForce 6       (NV4x)
[     4.247]    GeForce 7       (G7x)
[     4.247]    GeForce 8       (G8x)
[     4.247]    GeForce GTX 200 (NVA0)
[     4.247]    GeForce GTX 400 (NVC0)
[     4.247] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.247] (II) FBDEV: driver for framebuffer: fbdev
[     4.247] (II) VESA: driver for VESA chipsets: vesa
[     4.247] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[     4.247] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[     4.247] (EE) [drm] Failed to open DRM device for (null): -22
[     4.247] (WW) Falling back to old probe method for modesetting
[     4.247] (II) Loading sub module "fbdevhw"
[     4.247] (II) LoadModule: "fbdevhw"
[     4.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.248]    compiled for 1.19.3, module version = 0.0.2
[     4.248]    ABI class: X.Org Video Driver, version 23.0
[     4.248] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[     4.248] (II) FBDEV(1): using default device
[     4.248] (WW) Falling back to old probe method for vesa
[     4.248] (EE) Screen 0 deleted because of no matching config section.
[     4.248] (II) UnloadModule: "modesetting"
[     4.248] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[     4.248] (==) FBDEV(0): RGB weight 888
[     4.248] (==) FBDEV(0): Default visual is TrueColor
[     4.248] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     4.248] (II) FBDEV(0): hardware: EFI VGA (video memory: 8128kB)
[     4.248] (II) FBDEV(0): checking modes against framebuffer device...
[     4.248] (II) FBDEV(0): checking modes against monitor...
[     4.248] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[     4.248] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[     4.248] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[     4.248] (==) FBDEV(0): DPI set to (96, 96)
[     4.248] (II) Loading sub module "fb"
[     4.248] (II) LoadModule: "fb"
[     4.248] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.248] (II) Module fb: vendor="X.Org Foundation"
[     4.248]    compiled for 1.19.3, module version = 1.0.0
[     4.248]    ABI class: X.Org ANSI C Emulation, version 0.4
[     4.248] (**) FBDEV(0): using shadow framebuffer
[     4.248] (II) Loading sub module "shadow"
[     4.248] (II) LoadModule: "shadow"
[     4.248] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     4.248] (II) Module shadow: vendor="X.Org Foundation"
[     4.248]    compiled for 1.19.3, module version = 1.1.0
[     4.248]    ABI class: X.Org ANSI C Emulation, version 0.4
[     4.248] (II) UnloadModule: "vesa"
[     4.248] (II) Unloading vesa
[     4.248] (==) Depth 24 pixmap format is 32 bpp
[     4.248] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     4.249] (==) FBDEV(0): Backing store enabled
[     4.249] (**) FBDEV(0): DPMS enabled
[     4.249] (==) RandR enabled
[     4.252] (II) SELinux: Disabled on system
[     4.253] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[     4.276] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     4.276] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.276] (II) LoadModule: "evdev"
[     4.276] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.277] (II) Module evdev: vendor="X.Org Foundation"
[     4.277]    compiled for 1.19.3, module version = 2.10.5
[     4.277]    Module class: X.Org XInput Driver
[     4.277]    ABI class: X.Org XInput driver, version 24.1
[     4.277] (II) Using input driver 'evdev' for 'Power Button'
[     4.277] (**) Power Button: always reports core events
[     4.277] (**) evdev: Power Button: Device: "/dev/input/event3"
[     4.277] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.277] (--) evdev: Power Button: Found keys
[     4.277] (II) evdev: Power Button: Configuring as keyboard
[     4.277] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     4.277] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.277] (**) Option "xkb_rules" "evdev"
[     4.277] (**) Option "xkb_model" "pc105"
[     4.277] (**) Option "xkb_layout" "us"
[     4.277] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     4.277] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.277] (II) Using input driver 'evdev' for 'Power Button'
[     4.277] (**) Power Button: always reports core events
[     4.277] (**) evdev: Power Button: Device: "/dev/input/event1"
[     4.277] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.278] (--) evdev: Power Button: Found keys
[     4.278] (II) evdev: Power Button: Configuring as keyboard
[     4.278] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     4.278] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     4.278] (**) Option "xkb_rules" "evdev"
[     4.278] (**) Option "xkb_model" "pc105"
[     4.278] (**) Option "xkb_layout" "us"
[     4.278] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     4.278] (II) No input driver specified, ignoring this device.
[     4.278] (II) This device may have been added with another device file.
[     4.278] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[     4.278] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     4.278] (II) Using input driver 'evdev' for 'Sleep Button'
[     4.278] (**) Sleep Button: always reports core events
[     4.278] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[     4.278] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     4.278] (--) evdev: Sleep Button: Found keys
[     4.278] (II) evdev: Sleep Button: Configuring as keyboard
[     4.278] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[     4.278] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[     4.278] (**) Option "xkb_rules" "evdev"
[     4.278] (**) Option "xkb_model" "pc105"
[     4.278] (**) Option "xkb_layout" "us"
[     4.278] (II) config/udev: Adding input device Integrated_Webcam_HD (/dev/input/event7)
[     4.278] (**) Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[     4.278] (II) Using input driver 'evdev' for 'Integrated_Webcam_HD'
[     4.278] (**) Integrated_Webcam_HD: always reports core events
[     4.278] (**) evdev: Integrated_Webcam_HD: Device: "/dev/input/event7"
[     4.278] (--) evdev: Integrated_Webcam_HD: Vendor 0xc45 Product 0x6713
[     4.278] (--) evdev: Integrated_Webcam_HD: Found keys
[     4.278] (II) evdev: Integrated_Webcam_HD: Configuring as keyboard
[     4.278] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-12/1-12:1.0/input/input8/event7"
[     4.278] (II) XINPUT: Adding extended input device "Integrated_Webcam_HD" (type: KEYBOARD, id 9)
[     4.278] (**) Option "xkb_rules" "evdev"
[     4.278] (**) Option "xkb_model" "pc105"
[     4.278] (**) Option "xkb_layout" "us"
[     4.279] (II) config/udev: Adding input device DLL07BF:01 06CB:7A13 Touchpad (/dev/input/event11)
[     4.279] (**) DLL07BF:01 06CB:7A13 Touchpad: Applying InputClass "evdev touchpad catchall"
[     4.279] (**) DLL07BF:01 06CB:7A13 Touchpad: Applying InputClass "evdev touchscreen catchall"
[     4.279] (**) DLL07BF:01 06CB:7A13 Touchpad: Applying InputClass "touchpad catchall"
[     4.279] (**) DLL07BF:01 06CB:7A13 Touchpad: Applying InputClass "Default clickpad buttons"
[     4.279] (II) LoadModule: "synaptics"
[     4.279] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     4.279] (II) Module synaptics: vendor="X.Org Foundation"
[     4.279]    compiled for 1.19.3, module version = 1.9.0
[     4.279]    Module class: X.Org XInput Driver
[     4.279]    ABI class: X.Org XInput driver, version 24.1
[     4.279] (II) Using input driver 'synaptics' for 'DLL07BF:01 06CB:7A13 Touchpad'
[     4.279] (**) DLL07BF:01 06CB:7A13 Touchpad: always reports core events
[     4.279] (**) Option "Device" "/dev/input/event11"
[     4.324] (II) synaptics: DLL07BF:01 06CB:7A13 Touchpad: found clickpad property
[     4.324] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: x-axis range 0 - 1228 (res 12)
[     4.324] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: y-axis range 0 - 928 (res 12)
[     4.324] (II) synaptics: DLL07BF:01 06CB:7A13 Touchpad: device does not report pressure, will use touch data.
[     4.324] (II) synaptics: DLL07BF:01 06CB:7A13 Touchpad: device does not report finger width.
[     4.324] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: buttons: left double triple
[     4.324] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: Vendor 0x6cb Product 0x7a13
[     4.324] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: invalid pressure range.  defaulting to 0 - 255
[     4.324] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: invalid finger width range.  defaulting to 0 - 15
[     4.324] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     4.324] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: touchpad found
[     4.324] (**) DLL07BF:01 06CB:7A13 Touchpad: always reports core events
[     4.356] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-4/i2c-DLL07BF:01/0018:06CB:7A13.0001/input/input13/event11"
[     4.356] (II) XINPUT: Adding extended input device "DLL07BF:01 06CB:7A13 Touchpad" (type: TOUCHPAD, id 10)
[     4.356] (**) synaptics: DLL07BF:01 06CB:7A13 Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     4.356] (**) synaptics: DLL07BF:01 06CB:7A13 Touchpad: (accel) MaxSpeed is now 1.75
[     4.356] (**) synaptics: DLL07BF:01 06CB:7A13 Touchpad: (accel) AccelFactor is now 0.130
[     4.356] (**) DLL07BF:01 06CB:7A13 Touchpad: (accel) keeping acceleration scheme 1
[     4.356] (**) DLL07BF:01 06CB:7A13 Touchpad: (accel) acceleration profile 1
[     4.356] (**) DLL07BF:01 06CB:7A13 Touchpad: (accel) acceleration factor: 2.000
[     4.356] (**) DLL07BF:01 06CB:7A13 Touchpad: (accel) acceleration threshold: 4
[     4.356] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: touchpad found
[     4.356] (II) config/udev: Adding input device DLL07BF:01 06CB:7A13 Touchpad (/dev/input/mouse1)
[     4.356] (**) DLL07BF:01 06CB:7A13 Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[     4.356] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[     4.356] (II) No input driver specified, ignoring this device.
[     4.356] (II) This device may have been added with another device file.
[     4.357] (II) config/udev: Adding input device HDA Intel PCH Headphone Mic (/dev/input/event8)
[     4.357] (II) No input driver specified, ignoring this device.
[     4.357] (II) This device may have been added with another device file.
[     4.357] (II) config/udev: Adding input device Intel HID events (/dev/input/event5)
[     4.357] (**) Intel HID events: Applying InputClass "evdev keyboard catchall"
[     4.357] (II) Using input driver 'evdev' for 'Intel HID events'
[     4.357] (**) Intel HID events: always reports core events
[     4.357] (**) evdev: Intel HID events: Device: "/dev/input/event5"
[     4.357] (--) evdev: Intel HID events: Vendor 0 Product 0
[     4.357] (--) evdev: Intel HID events: Found keys
[     4.357] (II) evdev: Intel HID events: Configuring as keyboard
[     4.357] (**) Option "config_info" "udev:/sys/devices/platform/INT33D5:00/input/input7/event5"
[     4.357] (II) XINPUT: Adding extended input device "Intel HID events" (type: KEYBOARD, id 11)
[     4.357] (**) Option "xkb_rules" "evdev"
[     4.357] (**) Option "xkb_model" "pc105"
[     4.357] (**) Option "xkb_layout" "us"
[     4.357] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     4.357] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     4.357] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     4.357] (**) AT Translated Set 2 keyboard: always reports core events
[     4.357] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     4.357] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     4.357] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     4.357] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     4.357] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     4.357] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[     4.357] (**) Option "xkb_rules" "evdev"
[     4.357] (**) Option "xkb_model" "pc105"
[     4.357] (**) Option "xkb_layout" "us"
[     4.358] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[     4.358] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     4.358] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[     4.358] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     4.358] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     4.358] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     4.358] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.358] (**) Option "Device" "/dev/input/event6"
[     4.388] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     4.388] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1278 - 5664 (res 0)
[     4.388] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1206 - 4646 (res 0)
[     4.388] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     4.388] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     4.388] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     4.388] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     4.388] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     4.388] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.388] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     4.420] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[     4.420] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[     4.420] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     4.420] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     4.420] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[     4.420] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     4.420] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     4.420] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     4.420] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     4.420] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     4.420] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     4.420] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     4.421] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[     4.421] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     4.421] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[     4.421] (**) Dell WMI hotkeys: always reports core events
[     4.421] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event10"
[     4.421] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[     4.421] (--) evdev: Dell WMI hotkeys: Found keys
[     4.421] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[     4.421] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event10"
[     4.421] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[     4.421] (**) Option "xkb_rules" "evdev"
[     4.421] (**) Option "xkb_model" "pc105"
[     4.421] (**) Option "xkb_layout" "us"
[    74.116] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event12)
[    74.116] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    74.116] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    74.116] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    74.116] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event12"
[    74.116] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[    74.116] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[    74.116] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    74.116] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:045E:00DD.0002/input/input18/event12"
[    74.116] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 15)
[    74.116] (**) Option "xkb_rules" "evdev"
[    74.116] (**) Option "xkb_model" "pc105"
[    74.116] (**) Option "xkb_layout" "us"
[    74.116] (WW) Option "xkb_variant" requires a string value
[    74.116] (WW) Option "xkb_options" requires a string value
[    74.120] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event13)
[    74.120] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    74.120] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    74.120] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    74.120] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event13"
[    74.120] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[    74.120] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[    74.120] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[    74.120] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found relative axes
[    74.120] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing relative x/y axes to exist.
[    74.120] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[    74.120] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing absolute x/y axes to exist.
[    74.120] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[    74.120] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[    74.120] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    74.120] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
[    74.120] (**) evdev: Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[    74.120] (**) evdev: Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    74.120] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.1/0003:045E:00DD.0003/input/input19/event13"
[    74.120] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 16)
[    74.120] (**) Option "xkb_rules" "evdev"
[    74.120] (**) Option "xkb_model" "pc105"
[    74.120] (**) Option "xkb_layout" "us"
[    74.120] (WW) Option "xkb_variant" requires a string value
[    74.120] (WW) Option "xkb_options" requires a string value
[    74.120] (II) evdev: Microsoft Comfort Curve Keyboard 2000: initialized for relative axes.
[    74.120] (WW) evdev: Microsoft Comfort Curve Keyboard 2000: ignoring absolute axes.
[    74.120] (**) Microsoft Comfort Curve Keyboard 2000: (accel) keeping acceleration scheme 1
[    74.120] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration profile 0
[    74.120] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration factor: 2.000
[    74.120] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration threshold: 4
[  1086.344] (--) synaptics: DLL07BF:01 06CB:7A13 Touchpad: touchpad found
[  1086.344] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1092.912] (II) config/udev: removing device SynPS/2 Synaptics TouchPad
[  1092.945] (II) UnloadModule: "synaptics"
[  2283.523] (II) config/udev: Adding input device USB Optical Wheel Mouse (/dev/input/mouse0)
[  2283.523] (II) No input driver specified, ignoring this device.
[  2283.523] (II) This device may have been added with another device file.
[  2283.608] (II) config/udev: Adding input device USB Optical Wheel Mouse (/dev/input/event6)
[  2283.608] (**) USB Optical Wheel Mouse: Applying InputClass "evdev pointer catchall"
[  2283.608] (II) Using input driver 'evdev' for 'USB Optical Wheel Mouse'
[  2283.608] (**) USB Optical Wheel Mouse: always reports core events
[  2283.608] (**) evdev: USB Optical Wheel Mouse: Device: "/dev/input/event6"
[  2283.660] (--) evdev: USB Optical Wheel Mouse: Vendor 0x1bcf Product 0x2
[  2283.660] (--) evdev: USB Optical Wheel Mouse: Found 9 mouse buttons
[  2283.660] (--) evdev: USB Optical Wheel Mouse: Found scroll wheel(s)
[  2283.660] (--) evdev: USB Optical Wheel Mouse: Found relative axes
[  2283.660] (--) evdev: USB Optical Wheel Mouse: Found x and y relative axes
[  2283.660] (II) evdev: USB Optical Wheel Mouse: Configuring as mouse
[  2283.660] (II) evdev: USB Optical Wheel Mouse: Adding scrollwheel support
[  2283.660] (**) evdev: USB Optical Wheel Mouse: YAxisMapping: buttons 4 and 5
[  2283.660] (**) evdev: USB Optical Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2283.660] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/0003:1BCF:0002.0004/input/input22/event6"
[  2283.660] (II) XINPUT: Adding extended input device "USB Optical Wheel Mouse" (type: MOUSE, id 13)
[  2283.660] (II) evdev: USB Optical Wheel Mouse: initialized for relative axes.
[  2283.661] (**) USB Optical Wheel Mouse: (accel) keeping acceleration scheme 1
[  2283.661] (**) USB Optical Wheel Mouse: (accel) acceleration profile 0
[  2283.661] (**) USB Optical Wheel Mouse: (accel) acceleration factor: 2.000
[  2283.661] (**) USB Optical Wheel Mouse: (accel) acceleration threshold: 4

```


Any suggestions would be appreciated.  If there is more information I should post, please let me know.

---

