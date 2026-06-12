---
title: "NVIDIA GT320 driver issues"
date: 2013-04-01
forum: Hardware
---

### Post by NorthAntrim on 2013-04-01
Hey,

For a long time with Linux (in general, not just Ubuntu) I've had an annoying issue with my video card and drivers.

My card is a NVIDIA GT320. Here's the output from *lspci | grep VGA*:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GT215 [GeForce GT 320] (rev a2)
```

Currently, I'm using the Nouveau driver (from xserver-xorg-video-nouveau). It appears to work fine and I get a full resolution display, however I experience random crashes. The screen freezes (often the mouse jitters slowly for a couple of seconds before) to a complete halt and I'm unable to do practically anything, including switching to tty screens. The only thing I *can* do is reboot the system with ALT + SYSREQ + R, E, I, S, U, B. The crashes seem more frequent in Unity and Cinnamon 3D than in Cinnamon 2D or Xfce (in fact, Xfce doesn't crash randomly, other than when I try to play Minecraft, which causes a crash after a seemingly random amount of gameplay), so I think it has something to do with 3D.

Whenever I try to use the proprietary NVIDIA driver, I get a low resolution display (should be 1920x1080). Then when I go to Display settings, the display is called "Laptop" and no other resolution is available, and when I open NVIDIA settings, it says I'm not using the NVIDIA driver, even after running nvidia-xconfig as root and rebooting.

The NVIDIA driver used to work for me a few months ago (the only problem being low res tty screens), but I changed to Arch for a while, experienced crashes and came back to Ubuntu only to find the NVIDIA driver no longer works).

I'd really love to get this issue sorted once and for all, as it is persistent in other distros like Arch and Mint.

---

### Post by NorthAntrim on 2013-04-02
**Update: **

I installed the NVIDIA driver again and took these screenshots:

Monitor settings (before running nvidia-xconfig);
[IMG]http://i.imgur.com/dcKjf49.png[/IMG]

nvidia-settings (after running nvidia-xconfig);
[IMG]http://i.imgur.com/ajRUWtU.png[/IMG]


Monitor settings (after running nvidia-xconfig);
[IMG]http://i.imgur.com/ABpv7p6.png[/IMG]

---

### Post by Joseph Wraith on 2013-04-02
I just used the Nvidia-current driver. For my GT 630. Follow this Tutorial or chose the Nvidia current through Jockey. (It's just above the Dev release on ubuntu 12.4.2.)




[LIST]
[*][COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/COLOR]
[*][COLOR=red]sudo apt-get update[/COLOR]
[*][COLOR=red]sudo apt-get install nvidia-current[/COLOR]
[/LIST]

---

### Post by Perfect Storm on 2013-04-03
If you're using Ubuntu 12.10, it's possible you need to install the headers to build the driver. Somehow (at least for me), it doesn't install them automatically with the nvidia driver.

Uninstall the driver, then:
```
sudo apt-get install linux-headers-$(uname -r)
```

Then install the driver.

---

### Post by NorthAntrim on 2013-04-03
> **Joseph Wraith said:**
> I just used the Nvidia-current driver. For my GT 630. Follow this Tutorial or chose the Nvidia current through Jockey. (It's just above the Dev release on ubuntu 12.4.2.)




[LIST]
[*][COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/COLOR]
[*][COLOR=red]sudo apt-get update[/COLOR]
[*][COLOR=red]sudo apt-get install nvidia-current[/COLOR]
[/LIST]

That's what I was doing before, getting the results above unfortunately :(

> **Artificial Intelligence said:**
> If you're using Ubuntu 12.10, it's possible you need to install the headers to build the driver. Somehow (at least for me), it doesn't install them automatically with the nvidia driver.

Uninstall the driver, then:
```
sudo apt-get install linux-headers-$(uname -r)
```

Then install the driver.

Thanks, I think that gets me *somewhere*. After installing the nvidia driver and rebooting, I get a black screen. I can't switch to tty screens, but I can reboot with REISUB.

That's the exact same issue I had with Arch. I was able to SSH into my computer and get the Xorg log and dmesg:

Xorg.0.log:
```
[    21.766] X.Org X Server 1.13.2.902 (1.13.3 RC 2)
Release Date: 2013-02-28
[    21.766] X Protocol Version 11, Revision 0
[    21.766] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[    21.766] Current Operating System: Linux Matthew-PC 3.7.0-7-generic #15-Ubuntu SMP Sat Dec 15 16:34:25 UTC 2012 x86_64
[    21.766] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-7-generic root=UUID=fda5426a-198c-44a3-9c0e-021f9472529b ro 3
[    21.766] Build Date: 02 March 2013  10:08:57AM
[    21.766] xorg-server 2:1.13.2.902+git20130301+server-1.13-branch.4d98c7da-0ubuntu0ricotz~quantal (For technical support please see http://www.ubuntu.com/support) 
[    21.766] Current version of pixman: 0.28.2
[    21.766]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.766] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.766] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr  3 10:49:30 2013
[    21.780] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.780] (==) No Layout section.  Using the first Screen section.
[    21.780] (==) No screen section available. Using defaults.
[    21.780] (**) |-->Screen "Default Screen Section" (0)
[    21.780] (**) |   |-->Monitor "<default monitor>"
[    21.780] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.780] (==) Automatically adding devices
[    21.780] (==) Automatically enabling devices
[    21.780] (==) Automatically adding GPU devices
[    21.780] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.780]     Entry deleted from font path.
[    21.780] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    21.780]     Entry deleted from font path.
[    21.780] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    21.780] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.780] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.780] (II) Loader magic: 0x7f0072f1fd00
[    21.780] (II) Module ABI versions:
[    21.780]     X.Org ANSI C Emulation: 0.4
[    21.780]     X.Org Video Driver: 13.1
[    21.780]     X.Org XInput driver : 18.0
[    21.780]     X.Org Server Extension : 7.0
[    21.781] (--) PCI:*(0:1:0:0) 10de:0ca2:174b:2150 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    21.781] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.781] Initializing built-in extension Generic Event Extension
[    21.781] Initializing built-in extension SHAPE
[    21.781] Initializing built-in extension MIT-SHM
[    21.781] Initializing built-in extension XInputExtension
[    21.781] Initializing built-in extension XTEST
[    21.781] Initializing built-in extension BIG-REQUESTS
[    21.782] Initializing built-in extension SYNC
[    21.782] Initializing built-in extension XKEYBOARD
[    21.782] Initializing built-in extension XC-MISC
[    21.782] Initializing built-in extension SECURITY
[    21.782] Initializing built-in extension XINERAMA
[    21.782] Initializing built-in extension XFIXES
[    21.782] Initializing built-in extension RENDER
[    21.782] Initializing built-in extension RANDR
[    21.782] Initializing built-in extension COMPOSITE
[    21.782] Initializing built-in extension DAMAGE
[    21.782] Initializing built-in extension MIT-SCREEN-SAVER
[    21.782] Initializing built-in extension DOUBLE-BUFFER
[    21.782] Initializing built-in extension RECORD
[    21.782] Initializing built-in extension DPMS
[    21.782] Initializing built-in extension X-Resource
[    21.782] Initializing built-in extension XVideo
[    21.782] Initializing built-in extension XVideo-MotionCompensation
[    21.782] Initializing built-in extension SELinux
[    21.782] Initializing built-in extension XFree86-VidModeExtension
[    21.782] Initializing built-in extension XFree86-DGA
[    21.782] Initializing built-in extension XFree86-DRI
[    21.782] Initializing built-in extension DRI2
[    21.782] (II) LoadModule: "glx"
[    21.835] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    22.512] (II) Module glx: vendor="NVIDIA Corporation"
[    22.512]     compiled for 4.0.2, module version = 1.0.0
[    22.512]     Module class: X.Org Server Extension
[    22.512] (II) NVIDIA GLX Module  310.32  Mon Jan 14 15:02:04 PST 2013
[    22.512] Loading extension GLX
[    22.512] (==) Matched nvidia as autoconfigured driver 0
[    22.512] (==) Matched nouveau as autoconfigured driver 1
[    22.512] (==) Matched nv as autoconfigured driver 2
[    22.512] (==) Matched vesa as autoconfigured driver 3
[    22.512] (==) Matched modesetting as autoconfigured driver 4
[    22.512] (==) Matched fbdev as autoconfigured driver 5
[    22.512] (==) Assigned the driver to the xf86ConfigLayout
[    22.512] (II) LoadModule: "nvidia"
[    22.512] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.591] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.591]     compiled for 4.0.2, module version = 1.0.0
[    22.591]     Module class: X.Org Video Driver
[    22.611] (II) LoadModule: "nouveau"
[    22.622] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.622] (II) Module nouveau: vendor="X.Org Foundation"
[    22.622]     compiled for 1.13.2.902, module version = 1.0.6
[    22.622]     Module class: X.Org Video Driver
[    22.622]     ABI class: X.Org Video Driver, version 13.1
[    22.622] (II) LoadModule: "nv"
[    22.623] (WW) Warning, couldn't open module nv
[    22.623] (II) UnloadModule: "nv"
[    22.623] (II) Unloading nv
[    22.623] (EE) Failed to load module "nv" (module does not exist, 0)
[    22.623] (II) LoadModule: "vesa"
[    22.623] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.623] (II) Module vesa: vendor="X.Org Foundation"
[    22.623]     compiled for 1.13.0, module version = 2.3.2
[    22.623]     Module class: X.Org Video Driver
[    22.623]     ABI class: X.Org Video Driver, version 13.0
[    22.623] (II) LoadModule: "modesetting"
[    22.623] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.623] (II) Module modesetting: vendor="X.Org Foundation"
[    22.623]     compiled for 1.13.0, module version = 0.5.0
[    22.623]     Module class: X.Org Video Driver
[    22.623]     ABI class: X.Org Video Driver, version 13.0
[    22.623] (II) LoadModule: "fbdev"
[    22.623] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.623] (II) Module fbdev: vendor="X.Org Foundation"
[    22.623]     compiled for 1.12.99.903, module version = 0.4.3
[    22.623]     Module class: X.Org Video Driver
[    22.624]     ABI class: X.Org Video Driver, version 13.0
[    22.624] (==) Matched nvidia as autoconfigured driver 0
[    22.624] (==) Matched nouveau as autoconfigured driver 1
[    22.624] (==) Matched nv as autoconfigured driver 2
[    22.624] (==) Matched vesa as autoconfigured driver 3
[    22.624] (==) Matched modesetting as autoconfigured driver 4
[    22.624] (==) Matched fbdev as autoconfigured driver 5
[    22.624] (==) Assigned the driver to the xf86ConfigLayout
[    22.624] (II) LoadModule: "nvidia"
[    22.624] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.624] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.624]     compiled for 4.0.2, module version = 1.0.0
[    22.624]     Module class: X.Org Video Driver
[    22.624] (II) UnloadModule: "nvidia"
[    22.624] (II) Unloading nvidia
[    22.624] (II) Failed to load module "nvidia" (already loaded, 32512)
[    22.624] (II) LoadModule: "nouveau"
[    22.624] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.624] (II) Module nouveau: vendor="X.Org Foundation"
[    22.624]     compiled for 1.13.2.902, module version = 1.0.6
[    22.624]     Module class: X.Org Video Driver
[    22.624]     ABI class: X.Org Video Driver, version 13.1
[    22.624] (II) UnloadModule: "nouveau"
[    22.624] (II) Unloading nouveau
[    22.624] (II) Failed to load module "nouveau" (already loaded, 32512)
[    22.624] (II) LoadModule: "nv"
[    22.624] (WW) Warning, couldn't open module nv
[    22.624] (II) UnloadModule: "nv"
[    22.624] (II) Unloading nv
[    22.624] (EE) Failed to load module "nv" (module does not exist, 0)
[    22.624] (II) LoadModule: "vesa"
[    22.625] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.625] (II) Module vesa: vendor="X.Org Foundation"
[    22.625]     compiled for 1.13.0, module version = 2.3.2
[    22.625]     Module class: X.Org Video Driver
[    22.625]     ABI class: X.Org Video Driver, version 13.0
[    22.625] (II) UnloadModule: "vesa"
[    22.625] (II) Unloading vesa
[    22.625] (II) Failed to load module "vesa" (already loaded, 0)
[    22.625] (II) LoadModule: "modesetting"
[    22.625] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.625] (II) Module modesetting: vendor="X.Org Foundation"
[    22.625]     compiled for 1.13.0, module version = 0.5.0
[    22.625]     Module class: X.Org Video Driver
[    22.625]     ABI class: X.Org Video Driver, version 13.0
[    22.625] (II) UnloadModule: "modesetting"
[    22.625] (II) Unloading modesetting
[    22.625] (II) Failed to load module "modesetting" (already loaded, 0)
[    22.625] (II) LoadModule: "fbdev"
[    22.625] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.625] (II) Module fbdev: vendor="X.Org Foundation"
[    22.625]     compiled for 1.12.99.903, module version = 0.4.3
[    22.625]     Module class: X.Org Video Driver
[    22.625]     ABI class: X.Org Video Driver, version 13.0
[    22.625] (II) UnloadModule: "fbdev"
[    22.625] (II) Unloading fbdev
[    22.625] (II) Failed to load module "fbdev" (already loaded, 0)
[    22.625] (II) NVIDIA dlloader X Driver  310.32  Mon Jan 14 14:42:46 PST 2013
[    22.625] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.626] (II) NOUVEAU driver 
[    22.626] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.626]     RIVA TNT        (NV04)
[    22.626]     RIVA TNT2       (NV05)
[    22.626]     GeForce 256     (NV10)
[    22.626]     GeForce 2       (NV11, NV15)
[    22.626]     GeForce 4MX     (NV17, NV18)
[    22.626]     GeForce 3       (NV20)
[    22.626]     GeForce 4Ti     (NV25, NV28)
[    22.626]     GeForce FX      (NV3x)
[    22.626]     GeForce 6       (NV4x)
[    22.626]     GeForce 7       (G7x)
[    22.626]     GeForce 8       (G8x)
[    22.626]     GeForce GTX 200 (NVA0)
[    22.626]     GeForce GTX 400 (NVC0)
[    22.626] (II) VESA: driver for VESA chipsets: vesa
[    22.626] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    22.626] (II) FBDEV: driver for framebuffer: fbdev
[    22.626] (++) using VT number 7


[    22.628] (II) Loading sub module "wfb"
[    22.628] (II) LoadModule: "wfb"
[    22.628] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.639] (II) Module wfb: vendor="X.Org Foundation"
[    22.639]     compiled for 1.13.2.902, module version = 1.0.0
[    22.639]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.639] (II) Loading sub module "ramdac"
[    22.639] (II) LoadModule: "ramdac"
[    22.639] (II) Module "ramdac" already built-in
[    22.652] (WW) Falling back to old probe method for vesa
[    22.652] (WW) Falling back to old probe method for modesetting
[    22.652] (EE) open /dev/dri/card0: No such file or directory
[    22.652] (EE) open /dev/dri/card0: No such file or directory
[    22.652] (WW) Falling back to old probe method for fbdev
[    22.652] (II) Loading sub module "fbdevhw"
[    22.652] (II) LoadModule: "fbdevhw"
[    22.653] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.653] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.653]     compiled for 1.13.2.902, module version = 0.0.2
[    22.653]     ABI class: X.Org Video Driver, version 13.1
[    22.653] (EE) open /dev/fb0: No such file or directory
[    22.653] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.653] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    22.653] (==) NVIDIA(0): RGB weight 888
[    22.653] (==) NVIDIA(0): Default visual is TrueColor
[    22.653] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.662] (**) NVIDIA(0): Enabling 2D acceleration

```

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.7.0-7-generic (buildd@meitnerium) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #15-Ubuntu SMP Sat Dec 15 16:34:25 UTC 2012 (Ubuntu 3.7.0-7.15-generic 3.7.0)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-7-generic root=UUID=fda5426a-198c-44a3-9c0e-021f9472529b ro 3
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e5000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bff8ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bff90000-0x00000000bff9dfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bff9e000-0x00000000bffdffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bffe0000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001bfffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Packard Bell ixtreme M5722/EG43M, BIOS P01-A1 08/31/2009
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x1c0000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask E00000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 7GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 8GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6144M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 2GB, type WB
[    0.000000] reg 3, base: 6GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbff90 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xbff8ffff]
[    0.000000]  [mem 0x00000000-0xbfdfffff] page 2M
[    0.000000]  [mem 0xbfe00000-0xbff8ffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xbff8ffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1bfffffff]
[    0.000000]  [mem 0x100000000-0x1bfffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x1bfffffff @ [mem 0xbff8c000-0xbff8ffff]
[    0.000000] RAMDISK: [mem 0x361b2000-0x370d0fff]
[    0.000000] ACPI: RSDP 00000000000fa8b0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bff90000 00048 (v01 ACRSYS ACRPRDCT 20090831 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bff90200 00084 (v01 083109 FACP2014 20090831 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bff905c0 06BDB (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bff9e000 00040
[    0.000000] ACPI: APIC 00000000bff90390 0006C (v01 083109 APIC2014 20090831 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bff90400 0003C (v01 083109 OEMMCFG  20090831 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000bff90440 00176 (v01 ACRSYS ACRPRDCT 20090831 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bff9e040 00072 (v01 083109 OEMB2014 20090831 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bff985c0 00038 (v01 083109 OEMHPET  20090831 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000bff9e0c0 02024 (v01 083109 GMCHSCI  20090831 MSFT 00000097)
[    0.000000] ACPI: AWMI 00000000bffa00f0 0004E (v01 083109 OEMB2014 20090831 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bffa0fb0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001bfffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x1bfffffff]
[    0.000000]   NODE_DATA [mem 0x1bfffc000-0x1bfffffff]
[    0.000000]  [ffffea0000000000-ffffea0006ffffff] PMD -> [ffff8801b9600000-ffff8801bf5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x1bfffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xbff8ffff]
[    0.000000]   node   0: [mem 0x100000000-0x1bfffffff]
[    0.000000] On node 0 totalpages: 1572639
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 765904 pages, LIFO batch:31
[    0.000000]   Normal zone: 12288 pages used for memmap
[    0.000000]   Normal zone: 774144 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e5000
[    0.000000] PM: Registered nosave memory: 00000000000e5000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bff90000 - 00000000bff9e000
[    0.000000] PM: Registered nosave memory: 00000000bff9e000 - 00000000bffe0000
[    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
[    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
[    0.000000] e820: [mem 0xc0000000-0xfedfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8801bfc00000 s84736 r8192 d21760 u524288
[    0.000000] pcpu-alloc: s84736 r8192 d21760 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1543961
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-7-generic root=UUID=fda5426a-198c-44a3-9c0e-021f9472529b ro 3
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 6094312k/7340032k available (6900k kernel code, 1049476k absent, 196244k reserved, 6312k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 25165824 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2500.071 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5000.14 BogoMIPS (lpj=10000284)
[    0.004087] pid_max: default: 32768 minimum: 301
[    0.004156] Security Framework initialized
[    0.004210] AppArmor: AppArmor initialized
[    0.004250] Yama: becoming mindful.
[    0.008391] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012716] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014748] Mount-cache hash table entries: 256
[    0.015027] Initializing cgroup subsys cpuacct
[    0.015072] Initializing cgroup subsys memory
[    0.015121] Initializing cgroup subsys devices
[    0.015162] Initializing cgroup subsys freezer
[    0.015202] Initializing cgroup subsys blkio
[    0.015243] Initializing cgroup subsys perf_event
[    0.015284] Initializing cgroup subsys hugetlb
[    0.015353] CPU: Physical Processor ID: 0
[    0.015393] CPU: Processor Core ID: 0
[    0.015433] mce: CPU supports 6 MCE banks
[    0.015479] CPU0: Thermal monitoring enabled (TM2)
[    0.015522] process: using mwait in idle threads
[    0.015566] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.015566] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.015566] tlb_flushall_shift: -1
[    0.015742] Freeing SMP alternatives: 24k freed
[    0.018309] ACPI: Core revision 20120913
[    0.024009] ftrace: allocating 25955 entries in 102 pages
[    0.032429] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.077863] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q8300  @ 2.50GHz (fam: 06, model: 17, stepping: 0a)
[    0.080000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.080000] ... version:                2
[    0.080000] ... bit width:              40
[    0.080000] ... generic registers:      2
[    0.080000] ... value mask:             000000ffffffffff
[    0.080000] ... max period:             000000007fffffff
[    0.080000] ... fixed-purpose events:   3
[    0.080000] ... event mask:             0000000700000003
[    0.090675] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080000] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.116007] Brought up 4 CPUs
[    0.116052] smpboot: Total of 4 processors activated (20000.56 BogoMIPS)
[    0.120085] devtmpfs: initialized
[    0.121420] EVM: security.selinux
[    0.121460] EVM: security.SMACK64
[    0.121499] EVM: security.capability
[    0.121549] PM: Registering ACPI NVS region [mem 0xbff9e000-0xbffdffff] (270336 bytes)
[    0.121549] regulator-dummy: no parameters
[    0.121549] NET: Registered protocol family 16
[    0.121549] ACPI: bus type pci registered
[    0.121549] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.121549] PCI: not using MMCONFIG
[    0.121549] PCI: Using configuration type 1 for base access
[    0.124140] bio: create slab <bio-0> at 0
[    0.124140] ACPI: Added _OSI(Module Device)
[    0.124140] ACPI: Added _OSI(Processor Device)
[    0.124158] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.124199] ACPI: Added _OSI(Processor Aggregator Device)
[    0.125422] ACPI: EC: Look up EC in DSDT
[    0.127186] ACPI: Executed 1 blocks of module-level executable AML code
[    0.129721] ACPI: SSDT 00000000bffa0140 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.130107] ACPI: Dynamic OEM Table Load:
[    0.130200] ACPI: SSDT           (null) 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.130408] ACPI: SSDT 00000000bffa0940 004B2 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    0.130783] ACPI: Dynamic OEM Table Load:
[    0.130877] ACPI: SSDT           (null) 004B2 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    0.131156] ACPI: SSDT 00000000bffa0340 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.131544] ACPI: Dynamic OEM Table Load:
[    0.131638] ACPI: SSDT           (null) 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.132112] ACPI: SSDT 00000000bffa0e00 00085 (v01  PmRef  P002Cst 00003000 INTL 20051117)
[    0.132490] ACPI: Dynamic OEM Table Load:
[    0.132583] ACPI: SSDT           (null) 00085 (v01  PmRef  P002Cst 00003000 INTL 20051117)
[    0.132863] ACPI: SSDT 00000000bffa0540 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.133257] ACPI: Dynamic OEM Table Load:
[    0.133351] ACPI: SSDT           (null) 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.133531] ACPI: SSDT 00000000bffa0e90 00085 (v01  PmRef  P003Cst 00003000 INTL 20051117)
[    0.133909] ACPI: Dynamic OEM Table Load:
[    0.134003] ACPI: SSDT           (null) 00085 (v01  PmRef  P003Cst 00003000 INTL 20051117)
[    0.134285] ACPI: SSDT 00000000bffa0740 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.134675] ACPI: Dynamic OEM Table Load:
[    0.134768] ACPI: SSDT           (null) 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.134948] ACPI: SSDT 00000000bffa0f20 00085 (v01  PmRef  P004Cst 00003000 INTL 20051117)
[    0.136131] ACPI: Dynamic OEM Table Load:
[    0.136224] ACPI: SSDT           (null) 00085 (v01  PmRef  P004Cst 00003000 INTL 20051117)
[    0.136973] ACPI: Interpreter enabled
[    0.137015] ACPI: (supports S0 S3 S4 S5)
[    0.137180] ACPI: Using IOAPIC for interrupt routing
[    0.137237] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.139286] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.165432] ACPI: No dock devices found.
[    0.165477] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.165666] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.165848] PCI host bridge to bus 0000:00
[    0.165890] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.165932] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.165975] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.166018] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.166061] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.166105] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xdfffffff]
[    0.166148] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfed8ffff]
[    0.166198] pci 0000:00:00.0: [8086:2e20] type 00 class 0x060000
[    0.166235] pci 0000:00:01.0: [8086:2e21] type 01 class 0x060400
[    0.166267] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.166303] pci 0000:00:19.0: [8086:10ce] type 00 class 0x020000
[    0.166319] pci 0000:00:19.0: reg 10: [mem 0xfcfe0000-0xfcffffff]
[    0.166327] pci 0000:00:19.0: reg 14: [mem 0xfcfdf000-0xfcfdffff]
[    0.166334] pci 0000:00:19.0: reg 18: [io  0xcc00-0xcc1f]
[    0.166388] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.166406] pci 0000:00:1a.0: [8086:3a37] type 00 class 0x0c0300
[    0.166442] pci 0000:00:1a.0: reg 20: [io  0xc880-0xc89f]
[    0.166487] pci 0000:00:1a.1: [8086:3a38] type 00 class 0x0c0300
[    0.166524] pci 0000:00:1a.1: reg 20: [io  0xc800-0xc81f]
[    0.166570] pci 0000:00:1a.2: [8086:3a39] type 00 class 0x0c0300
[    0.166606] pci 0000:00:1a.2: reg 20: [io  0xc480-0xc49f]
[    0.166659] pci 0000:00:1a.7: [8086:3a3c] type 00 class 0x0c0320
[    0.166678] pci 0000:00:1a.7: reg 10: [mem 0xfcfdec00-0xfcfdefff]
[    0.166756] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.166779] pci 0000:00:1b.0: [8086:3a3e] type 00 class 0x040300
[    0.166792] pci 0000:00:1b.0: reg 10: [mem 0xfcfd8000-0xfcfdbfff 64bit]
[    0.166850] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.166869] pci 0000:00:1c.0: [8086:3a40] type 01 class 0x060400
[    0.166927] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.166948] pci 0000:00:1c.1: [8086:3a42] type 01 class 0x060400
[    0.167006] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.167031] pci 0000:00:1d.0: [8086:3a34] type 00 class 0x0c0300
[    0.167068] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.167112] pci 0000:00:1d.1: [8086:3a35] type 00 class 0x0c0300
[    0.167149] pci 0000:00:1d.1: reg 20: [io  0xc080-0xc09f]
[    0.167194] pci 0000:00:1d.2: [8086:3a36] type 00 class 0x0c0300
[    0.167230] pci 0000:00:1d.2: reg 20: [io  0xc000-0xc01f]
[    0.167285] pci 0000:00:1d.7: [8086:3a3a] type 00 class 0x0c0320
[    0.167303] pci 0000:00:1d.7: reg 10: [mem 0xfcfde800-0xfcfdebff]
[    0.167382] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.167402] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.167456] pci 0000:00:1f.0: [8086:3a18] type 00 class 0x060100
[    0.167558] pci 0000:00:1f.2: [8086:3a20] type 00 class 0x01018f
[    0.167571] pci 0000:00:1f.2: reg 10: [io  0xbc00-0xbc07]
[    0.167578] pci 0000:00:1f.2: reg 14: [io  0xb880-0xb883]
[    0.167585] pci 0000:00:1f.2: reg 18: [io  0xb800-0xb807]
[    0.167592] pci 0000:00:1f.2: reg 1c: [io  0xb480-0xb483]
[    0.167599] pci 0000:00:1f.2: reg 20: [io  0xb400-0xb40f]
[    0.167606] pci 0000:00:1f.2: reg 24: [io  0xb080-0xb08f]
[    0.167646] pci 0000:00:1f.3: [8086:3a30] type 00 class 0x0c0500
[    0.167659] pci 0000:00:1f.3: reg 10: [mem 0xfcfde400-0xfcfde4ff 64bit]
[    0.167677] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.167706] pci 0000:00:1f.5: [8086:3a26] type 00 class 0x010185
[    0.167719] pci 0000:00:1f.5: reg 10: [io  0xac00-0xac07]
[    0.167726] pci 0000:00:1f.5: reg 14: [io  0xa880-0xa883]
[    0.167733] pci 0000:00:1f.5: reg 18: [io  0xa800-0xa807]
[    0.167740] pci 0000:00:1f.5: reg 1c: [io  0xa480-0xa483]
[    0.167747] pci 0000:00:1f.5: reg 20: [io  0xa400-0xa40f]
[    0.167754] pci 0000:00:1f.5: reg 24: [io  0xa080-0xa08f]
[    0.167819] pci 0000:01:00.0: [10de:0ca2] type 00 class 0x030000
[    0.167828] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.167838] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.167847] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.167854] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.167860] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
[    0.167909] pci 0000:01:00.1: [10de:0be4] type 00 class 0x040300
[    0.167918] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
[    0.168017] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.168060] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.168063] pci 0000:00:01.0:   bridge window [mem 0xfd000000-0xfe9fffff]
[    0.168066] pci 0000:00:01.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.168100] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.168199] pci 0000:03:00.0: [1106:3403] type 00 class 0x0c0010
[    0.168220] pci 0000:03:00.0: reg 10: [mem 0xfeaff800-0xfeafffff 64bit]
[    0.168231] pci 0000:03:00.0: reg 18: [io  0xe800-0xe8ff]
[    0.168319] pci 0000:03:00.0: supports D2
[    0.168321] pci 0000:03:00.0: PME# supported from D2 D3hot D3cold
[    0.176017] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.176063] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.176067] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.176104] pci 0000:04:02.0: [168c:001b] type 00 class 0x020000
[    0.176121] pci 0000:04:02.0: reg 10: [mem 0xfebf0000-0xfebfffff]
[    0.176241] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.176288] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.176294] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.176296] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.176298] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.176300] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.176302] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.176304] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.176318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.176397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.176455] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.176477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.176589]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.176751]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.176804] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.183332] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.183699] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.183852] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.184229] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.184594] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.184958] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.185334] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.185702] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.186113] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.186113] vgaarb: loaded
[    0.186113] vgaarb: bridge control possible 0000:01:00.0
[    0.186113] SCSI subsystem initialized
[    0.186113] ACPI: bus type scsi registered
[    0.186113] libata version 3.00 loaded.
[    0.186113] ACPI: bus type usb registered
[    0.186113] usbcore: registered new interface driver usbfs
[    0.186113] usbcore: registered new interface driver hub
[    0.186113] usbcore: registered new device driver usb
[    0.186113] PCI: Using ACPI for IRQ routing
[    0.192140] PCI: pci_cache_line_size set to 64 bytes
[    0.192200] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.192202] e820: reserve RAM buffer [mem 0xbff90000-0xbfffffff]
[    0.192289] NetLabel: Initializing
[    0.192328] NetLabel:  domain hash size = 128
[    0.192368] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.192418] NetLabel:  unlabeled traffic allowed by default
[    0.192476] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.192476] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.192476] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.194317] Switching to clocksource hpet
[    0.198295] AppArmor: AppArmor Filesystem Enabled
[    0.198369] pnp: PnP ACPI init
[    0.198422] ACPI: bus type pnp registered
[    0.198569] pnp 00:00: [bus 00-ff]
[    0.198571] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.198577] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.198579] pnp 00:00: [io  0x0d00-0xffff window]
[    0.198581] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.198583] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.198585] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.198586] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    0.198632] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.198641] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.198642] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.198689] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.198734] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.198779] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.198810] pnp 00:02: [dma 4]
[    0.198812] pnp 00:02: [io  0x0000-0x000f]
[    0.198814] pnp 00:02: [io  0x0081-0x0083]
[    0.198815] pnp 00:02: [io  0x0087]
[    0.198817] pnp 00:02: [io  0x0089-0x008b]
[    0.198819] pnp 00:02: [io  0x008f]
[    0.198821] pnp 00:02: [io  0x00c0-0x00df]
[    0.198836] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.198845] pnp 00:03: [io  0x0070-0x0071]
[    0.198856] pnp 00:03: [irq 8]
[    0.198874] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.198881] pnp 00:04: [io  0x0061]
[    0.198896] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.198903] pnp 00:05: [io  0x00f0-0x00ff]
[    0.198908] pnp 00:05: [irq 13]
[    0.198923] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.199693] pnp 00:06: [io  0x0060]
[    0.199696] pnp 00:06: [io  0x0064]
[    0.199700] pnp 00:06: [irq 12]
[    0.199724] pnp 00:06: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.199831] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.199833] pnp 00:07: [io  0x0a00-0x0a0f]
[    0.199835] pnp 00:07: [io  0x0a10-0x0a1f]
[    0.199837] pnp 00:07: [io  0x0a20-0x0a2f]
[    0.199839] pnp 00:07: [io  0x0a30-0x0a3f]
[    0.199871] system 00:07: [io  0x0a00-0x0a0f] has been reserved
[    0.199914] system 00:07: [io  0x0a10-0x0a1f] has been reserved
[    0.199957] system 00:07: [io  0x0a20-0x0a2f] has been reserved
[    0.200024] system 00:07: [io  0x0a30-0x0a3f] has been reserved
[    0.200068] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200157] pnp 00:08: [io  0x0010-0x001f]
[    0.200159] pnp 00:08: [io  0x0022-0x003f]
[    0.200161] pnp 00:08: [io  0x0044-0x005f]
[    0.200163] pnp 00:08: [io  0x0062-0x0063]
[    0.200164] pnp 00:08: [io  0x0065-0x006f]
[    0.200166] pnp 00:08: [io  0x0072-0x007f]
[    0.200168] pnp 00:08: [io  0x0080]
[    0.200170] pnp 00:08: [io  0x0084-0x0086]
[    0.200171] pnp 00:08: [io  0x0088]
[    0.200173] pnp 00:08: [io  0x008c-0x008e]
[    0.200175] pnp 00:08: [io  0x0090-0x009f]
[    0.200177] pnp 00:08: [io  0x00a2-0x00bf]
[    0.200178] pnp 00:08: [io  0x00e0-0x00ef]
[    0.200180] pnp 00:08: [io  0x04d0-0x04d1]
[    0.200185] pnp 00:08: [io  0x04c0-0x04cf]
[    0.200187] pnp 00:08: [io  0x04d2-0x04ff]
[    0.200188] pnp 00:08: [io  0x0800-0x087f]
[    0.200190] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.200192] pnp 00:08: [io  0x0480-0x04bf]
[    0.200194] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.200196] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.200198] pnp 00:08: [mem 0xfed40000-0xfed8ffff]
[    0.200242] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.200285] system 00:08: [io  0x04c0-0x04cf] has been reserved
[    0.200330] system 00:08: [io  0x04d2-0x04ff] has been reserved
[    0.200373] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.200416] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.200459] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.200503] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.200546] system 00:08: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.200591] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200635] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.200651] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.200690] pnp 00:0a: [mem 0xffb00000-0xffbfffff]
[    0.200692] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    0.200713] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.200745] pnp 00:0b: [mem 0xffc00000-0xffefffff]
[    0.200769] system 00:0b: [mem 0xffc00000-0xffefffff] has been reserved
[    0.200814] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200874] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.200876] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.200906] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.200951] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.200996] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.201209] pnp 00:0d: [mem 0xe0000000-0xefffffff]
[    0.201235] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.201280] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.201449] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.201451] pnp 00:0e: [mem 0x000c0000-0x000cffff]
[    0.201453] pnp 00:0e: [mem 0x000e0000-0x000fffff]
[    0.201455] pnp 00:0e: [mem 0x00100000-0xbfffffff]
[    0.201457] pnp 00:0e: [mem 0xfed90000-0xffffffff]
[    0.201492] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.201537] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.201581] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.201625] system 00:0e: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.201669] system 00:0e: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.201714] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.201817] pnp: PnP ACPI: found 15 devices
[    0.201858] ACPI: ACPI bus type pnp unregistered
[    0.210116] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.210120] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.210123] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.210130] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.210141] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.210144] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.210146] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.210148] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.210153] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.210198] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.210252] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.210306] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.210350] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.210392] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.210436] pci 0000:00:01.0:   bridge window [mem 0xfd000000-0xfe9fffff]
[    0.210480] pci 0000:00:01.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.210535] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.210577] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.210622] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.210667] pci 0000:00:1c.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.210723] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.210765] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.210810] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.210855] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.210911] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.210954] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.211015] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.211070] pci 0000:00:1e.0: setting latency timer to 64
[    0.211074] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.211076] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.211078] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.211080] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.211081] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.211083] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.211086] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.211088] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfe9fffff]
[    0.211090] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.211092] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.211094] pci_bus 0000:02: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.211096] pci_bus 0000:02: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.211097] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.211099] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.211101] pci_bus 0000:03: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.211104] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.211105] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.211107] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.211109] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.211111] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.211113] pci_bus 0000:04: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.211115] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.211155] NET: Registered protocol family 2
[    0.211893] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.215718] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.216292] TCP: Hash tables configured (established 524288 bind 65536)
[    0.216394] TCP: reno registered
[    0.216446] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.216561] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.216753] NET: Registered protocol family 1
[    0.217034] pci 0000:01:00.0: Boot video device
[    0.217049] PCI: CLS 32 bytes, default 64
[    0.217099] Trying to unpack rootfs image as initramfs...
[    0.479532] Freeing initrd memory: 15484k freed
[    0.484787] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.484840] software IO TLB [mem 0xbbf8c000-0xbff8bfff] (64MB) mapped at [ffff8800bbf8c000-ffff8800bff8bfff]
[    0.485285] Initialise module verification
[    0.485370] audit: initializing netlink socket (disabled)
[    0.485427] type=2000 audit(1364982548.484:1): initialized
[    0.511192] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.512991] VFS: Disk quotas dquot_6.5.2
[    0.513074] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.513609] fuse init (API version 7.20)
[    0.513751] msgmni has been set to 11933
[    0.514622] Key type asymmetric registered
[    0.514669] Asymmetric key parser 'x509' registered
[    0.514740] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.514846] io scheduler noop registered
[    0.514892] io scheduler deadline registered (default)
[    0.514936] io scheduler cfq registered
[    0.515092] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.515158] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.515231] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.515293] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.515351] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.515436] intel_idle: does not run on family 6 model 23
[    0.515520] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.515577] ACPI: Power Button [PWRB]
[    0.515651] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.515705] ACPI: Power Button [PWRF]
[    0.515828] ACPI: Requesting acpi_cpufreq
[    0.517073] Monitor-Mwait will be used to enter C-1 state
[    0.517094] Monitor-Mwait will be used to enter C-2 state
[    0.517110] tsc: Marking TSC unstable due to TSC halts in idle
[    0.517160] ACPI: acpi_idle registered with cpuidle
[    0.522948] GHES: HEST is not enabled!
[    0.523080] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.524580] Linux agpgart interface v0.103
[    0.525897] brd: module loaded
[    0.526540] loop: module loaded
[    0.526692] ata_piix 0000:00:1f.2: version 2.13
[    0.526704] ata_piix 0000:00:1f.2: MAP [
[    0.526744]  P0 P2 P1 P3 ]
[    0.526921] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.527157] scsi0 : ata_piix
[    0.527743] scsi1 : ata_piix
[    0.529237] ata1: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
[    0.529283] ata2: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
[    0.529348] ata_piix 0000:00:1f.5: MAP [
[    0.529408]  P0 -- P1 -- ]
[    0.529577] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.529727] scsi2 : ata_piix
[    0.530163] scsi3 : ata_piix
[    0.530543] ata3: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 19
[    0.530589] ata4: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 19
[    0.530890] libphy: Fixed MDIO Bus: probed
[    0.530984] tun: Universal TUN/TAP device driver, 1.6
[    0.531026] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.531103] PPP generic driver version 2.4.2
[    0.531179] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.531278] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.531282] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.531328] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.535288] ehci_hcd 0000:00:1a.7: debug port 1
[    0.535334] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.535348] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfcfdec00
[    0.544016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.544080] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.544126] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.544180] usb usb1: Product: EHCI Host Controller
[    0.544221] usb usb1: Manufacturer: Linux 3.7.0-7-generic ehci_hcd
[    0.544264] usb usb1: SerialNumber: 0000:00:1a.7
[    0.544396] hub 1-0:1.0: USB hub found
[    0.544439] hub 1-0:1.0: 6 ports detected
[    0.544816] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.544819] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.544864] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.548811] ehci_hcd 0000:00:1d.7: debug port 1
[    0.548857] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.548868] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfcfde800
[    0.560016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.560078] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.560127] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.560181] usb usb2: Product: EHCI Host Controller
[    0.560232] usb usb2: Manufacturer: Linux 3.7.0-7-generic ehci_hcd
[    0.560274] usb usb2: SerialNumber: 0000:00:1d.7
[    0.560403] hub 2-0:1.0: USB hub found
[    0.560446] hub 2-0:1.0: 6 ports detected
[    0.560807] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.560866] uhci_hcd: USB Universal Host Controller Interface driver
[    0.560924] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.560927] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.560971] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.561050] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.561117] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.561161] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.561214] usb usb3: Product: UHCI Host Controller
[    0.561255] usb usb3: Manufacturer: Linux 3.7.0-7-generic uhci_hcd
[    0.561298] usb usb3: SerialNumber: 0000:00:1a.0
[    0.561414] hub 3-0:1.0: USB hub found
[    0.561456] hub 3-0:1.0: 2 ports detected
[    0.561595] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.561598] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.561644] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.561723] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.561791] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.561835] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.561888] usb usb4: Product: UHCI Host Controller
[    0.561929] usb usb4: Manufacturer: Linux 3.7.0-7-generic uhci_hcd
[    0.561972] usb usb4: SerialNumber: 0000:00:1a.1
[    0.562086] hub 4-0:1.0: USB hub found
[    0.562128] hub 4-0:1.0: 2 ports detected
[    0.562266] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.562269] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.562313] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.562384] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.562451] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.562495] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.562547] usb usb5: Product: UHCI Host Controller
[    0.562588] usb usb5: Manufacturer: Linux 3.7.0-7-generic uhci_hcd
[    0.562631] usb usb5: SerialNumber: 0000:00:1a.2
[    0.562749] hub 5-0:1.0: USB hub found
[    0.562791] hub 5-0:1.0: 2 ports detected
[    0.562929] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.562932] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.562977] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.563049] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.563115] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.563159] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.563212] usb usb6: Product: UHCI Host Controller
[    0.563253] usb usb6: Manufacturer: Linux 3.7.0-7-generic uhci_hcd
[    0.563296] usb usb6: SerialNumber: 0000:00:1d.0
[    0.563410] hub 6-0:1.0: USB hub found
[    0.563453] hub 6-0:1.0: 2 ports detected
[    0.563587] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.563590] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.563635] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.563705] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.563773] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.563817] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.563869] usb usb7: Product: UHCI Host Controller
[    0.563911] usb usb7: Manufacturer: Linux 3.7.0-7-generic uhci_hcd
[    0.563953] usb usb7: SerialNumber: 0000:00:1d.1
[    0.564081] hub 7-0:1.0: USB hub found
[    0.564123] hub 7-0:1.0: 2 ports detected
[    0.564255] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.564258] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.564303] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.564373] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.564443] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.564487] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.564539] usb usb8: Product: UHCI Host Controller
[    0.564581] usb usb8: Manufacturer: Linux 3.7.0-7-generic uhci_hcd
[    0.564623] usb usb8: SerialNumber: 0000:00:1d.2
[    0.564741] hub 8-0:1.0: USB hub found
[    0.564785] hub 8-0:1.0: 2 ports detected
[    0.564974] i8042: PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    0.565017] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.565406] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.565459] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.565643] mousedev: PS/2 mouse device common for all mice
[    0.565864] rtc_cmos 00:03: RTC can wake from S4
[    0.566027] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.566089] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.566223] device-mapper: uevent: version 1.0.3
[    0.566343] device-mapper: ioctl: 4.23.0-ioctl (2012-07-25) initialised: dm-devel@redhat.com
[    0.566443] cpuidle: using governor ladder
[    0.566553] cpuidle: using governor menu
[    0.566595] ledtrig-cpu: registered to indicate activity on CPUs
[    0.566637] EFI Variables Facility v0.08 2004-May-17
[    0.566939] ashmem: initialized
[    0.567114] TCP: cubic registered
[    0.567241] NET: Registered protocol family 10
[    0.567435] NET: Registered protocol family 17
[    0.567488] Key type dns_resolver registered
[    0.567854] Loading module verification certificates
[    0.568888] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: a37e8d8f17247a12bca04fac461c3b30422126d5'
[    0.568954] registered taskstats version 1
[    0.571522] Key type trusted registered
[    0.573632] Key type encrypted registered
[    0.575856] rtc_cmos 00:03: setting system clock to 2013-04-03 09:49:09 UTC (1364982549)
[    0.576586] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.576629] EDD information not available.
[    0.858577] ata3: SATA link down (SStatus 0 SControl 300)
[    0.858580] usb 1-3: new high-speed USB device number 2 using ehci_hcd
[    0.869254] ata4: SATA link down (SStatus 0 SControl 300)
[    0.989820] usb 1-3: New USB device found, idVendor=0bc2, idProduct=3320
[    0.989869] usb 1-3: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    0.989915] usb 1-3: Product: Expansion Desk
[    0.989957] usb 1-3: Manufacturer: Seagate
[    0.989998] usb 1-3: SerialNumber: NA4L6VXW
[    1.100038] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.178598] ata2.00: SATA link down (SStatus 0 SControl 300)
[    1.178650] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.233944] usb 1-4: New USB device found, idVendor=04a9, idProduct=172b
[    1.233990] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.234035] usb 1-4: Product: MP140 series
[    1.234077] usb 1-4: Manufacturer: Canon
[    1.234119] usb 1-4: SerialNumber: 82CB91
[    1.332080] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.332135] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.348173] ata1.00: ATAPI: ATAPI   DVD A  DH16AASH, SA15, max UDMA/100
[    1.348409] ata1.01: ATA-8: WDC WD10EADS-22M2B0, 01.00A01, max UDMA/133
[    1.348455] ata1.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.348696] ata1.01: failed to get Identify Device Data, Emask 0x1
[    1.364171] ata1.00: configured for UDMA/100
[    1.372518] ata1.01: failed to get Identify Device Data, Emask 0x1
[    1.372523] ata1.01: configured for UDMA/133
[    1.375814] scsi 0:0:0:0: CD-ROM            ATAPI    DVD A  DH16AASH  SA15 PQ: 0 ANSI: 5
[    1.379139] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.379194] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.379350] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.379426] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.379606] ACPI: Invalid Power Resource to register!
[    1.380019] scsi 0:0:1:0: Direct-Access     ATA      WDC WD10EADS-22M 01.0 PQ: 0 ANSI: 5
[    1.380258] sd 0:0:1:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.380267] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.380442] sd 0:0:1:0: [sda] Write Protect is off
[    1.381553] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.381584] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.400031] usb 2-4: new high-speed USB device number 3 using ehci_hcd
[    1.406887]  sda: sda1 sda2
[    1.407190] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.408560] Freeing unused kernel memory: 984k freed
[    1.408813] Write protecting the kernel read-only data: 12288k
[    1.412171] Freeing unused kernel memory: 1280k freed
[    1.415233] Freeing unused kernel memory: 1148k freed
[    1.431722] udevd[117]: starting version 175
[    1.475620] Disabling lock debugging due to kernel taint
[    1.476266] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    1.476317] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.476411] e1000e 0000:00:19.0: setting latency timer to 64
[    1.476476] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.476568] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.480991] usbcore: registered new interface driver uas
[    1.481706] Initializing USB Mass Storage driver...
[    1.483396] scsi4 : usb-storage 1-3:1.0
[    1.483533] usbcore: registered new interface driver usb-storage
[    1.483581] USB Mass Storage support registered.
[    1.548092] firewire_ohci 0000:03:00.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.610401] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.668043] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 44:87:fc:4f:c1:ef
[    1.668102] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.668166] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    1.800090] usb 2-4: New USB device found, idVendor=0bda, idProduct=0182
[    1.800138] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.800183] usb 2-4: Product: USB2.0-CRW
[    1.800225] usb 2-4: Manufacturer: Generic
[    1.800282] usb 2-4: SerialNumber: 20060413092100000
[    1.806222] scsi5 : usb-storage 2-4:1.0
[    2.044033] usb 7-1: new low-speed USB device number 2 using uhci_hcd
[    2.048121] firewire_core 0000:03:00.0: created device fw0: GUID 0000002511954a44, S400
[    2.224799] usb 7-1: New USB device found, idVendor=046d, idProduct=c52a
[    2.224849] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.224894] usb 7-1: Product: 2.4GHz Cordless Desktop
[    2.224937] usb 7-1: Manufacturer: Logitech
[    2.480857] scsi 4:0:0:0: Direct-Access     Seagate  Expansion Desk   070B PQ: 0 ANSI: 6
[    2.481548] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.482100] sd 4:0:0:0: [sdb] 3907029167 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.482950] sd 4:0:0:0: [sdb] Write Protect is off
[    2.482995] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    2.483828] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.807484] scsi 5:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    2.810481] scsi 5:0:0:1: Direct-Access     Generic- xD-Picture       1.00 PQ: 0 ANSI: 0 CCS
[    2.813486] scsi 5:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    2.816727] scsi 5:0:0:3: Direct-Access     Generic- MS/MS-Pro/HG     1.00 PQ: 0 ANSI: 0 CCS
[    2.819731] scsi 5:0:0:4: Direct-Access     Generic- MicroSD          1.00 PQ: 0 ANSI: 0 CCS
[    2.820377] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    2.820659] sd 5:0:0:1: Attached scsi generic sg4 type 0
[    2.820823] sd 5:0:0:2: Attached scsi generic sg5 type 0
[    2.821019] sd 5:0:0:3: Attached scsi generic sg6 type 0
[    2.821175] sd 5:0:0:4: Attached scsi generic sg7 type 0
[    2.848226] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    2.850726] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[    2.853102] sd 5:0:0:2: [sde] Attached SCSI removable disk
[    2.855848] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[    2.858351] sd 5:0:0:4: [sdg] Attached SCSI removable disk
[    6.279975]  sdb: sdb1
[    6.282836] sd 4:0:0:0: [sdb] Attached SCSI disk
[   13.716152] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.823064] udevd[384]: starting version 175
[   13.931799] type=1400 audit(1364982562.851:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
[   13.932204] type=1400 audit(1364982562.855:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor_parser"
[   13.932423] type=1400 audit(1364982562.855:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=463 comm="apparmor_parser"
[    1.380349] ACPI: Invalid Power Resource to register!
[   14.141927] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \PMRG 1 (20120913/utaddress-251)
[   14.141936] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.141960] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.155020] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x172B
[   14.155054] usbcore: registered new interface driver usblp
[   14.177179] wmi: Mapper loaded
[   14.197856] microcode: CPU0 sig=0x1067a, pf=0x10, revision=0xa07
[   14.199190] lp: driver loaded but no devices found
[   14.293873] usbcore: registered new interface driver usbhid
[   14.293879] usbhid: USB HID core driver
[   14.303770] gpio_ich: GPIO from 195 to 255 on gpio_ich
[   14.353475] microcode: CPU1 sig=0x1067a, pf=0x10, revision=0xa07
[   14.355224] microcode: CPU2 sig=0x1067a, pf=0x10, revision=0xa07
[   14.357075] microcode: CPU3 sig=0x1067a, pf=0x10, revision=0xa07
[   14.358702] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.434504] cfg80211: Calling CRDA to update world regulatory domain
[   14.439695] cfg80211: World regulatory domain updated:
[   14.439700] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.439702] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.439704] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.439705] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.439707] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.439709] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.698704] ath5k 0000:04:02.0: registered as 'phy0'
[   14.738705] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   14.801118] nvidia: module license 'NVIDIA' taints kernel.
[   14.820144] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.820435] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.32  Mon Jan 14 14:41:13 PST 2013
[   15.131143] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.308571] ath: EEPROM regdomain: 0x65
[   15.308575] ath: EEPROM indicates we should expect a direct regpair map
[   15.308578] ath: Country alpha2 being used: 00
[   15.308580] ath: Regpair used: 0x65
[   15.404241] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.404475] ath5k: phy0: Atheros AR5414 chip found (MAC: 0xa2, PHY: 0x61)
[   15.547826] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   17.390113] init: failsafe main process (925) killed by TERM signal
[   17.788034] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   18.071106] type=1400 audit(1364982566.991:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=993 comm="apparmor_parser"
[   18.071395] type=1400 audit(1364982566.991:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=993 comm="apparmor_parser"
[   18.076675] type=1400 audit(1364982566.999:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=995 comm="apparmor_parser"
[   18.077120] type=1400 audit(1364982566.999:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=995 comm="apparmor_parser"
[   18.077219] type=1400 audit(1364982566.999:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=992 comm="apparmor_parser"
[   18.077508] type=1400 audit(1364982566.999:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=992 comm="apparmor_parser"
[   18.077671] type=1400 audit(1364982566.999:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=995 comm="apparmor_parser"
[   18.150185] ppdev: user-space parallel port driver
[   18.157893] Bluetooth: Core ver 2.16
[   18.158186] NET: Registered protocol family 31
[   18.158188] Bluetooth: HCI device and connection manager initialized
[   18.158198] Bluetooth: HCI socket layer initialized
[   18.158200] Bluetooth: L2CAP socket layer initialized
[   18.158206] Bluetooth: SCO socket layer initialized
[   18.186316] Bluetooth: RFCOMM TTY layer initialized
[   18.186332] Bluetooth: RFCOMM socket layer initialized
[   18.186334] Bluetooth: RFCOMM ver 1.11
[   18.197009] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.197017] Bluetooth: BNEP filters: protocol multicast
[   18.197028] Bluetooth: BNEP socket layer initialized
[   18.251901] init: alsa-restore main process (1100) terminated with status 19
[   18.280248] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   18.384085] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   18.384180] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.384541] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.386591] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.792027] hda-intel: No response from codec, disabling MSI: last cmd=0x300f0000
[   19.754875] usblp0: removed
[   19.758277] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x172B
[   19.796041] hda-intel: Codec #3 probe error; disabling it...
[   19.861057] hda_codec: ALC888: SKU not ready 0x411111f0
[   19.870858] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input2
[   19.870968] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
[   19.871045] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   19.871114] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   19.871181] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.871248] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.871315] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.871380] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.871707] hda_intel: Disabling MSI
[   19.871716] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   20.188891] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   20.188898] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   20.188928] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.836119] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   20.836254] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   20.836336] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   20.836412] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   21.556416] hid-generic 0003:0BDA:0182.0001: hiddev0,hidraw0: USB HID v1.11 Device [Generic USB2.0-CRW] on usb-0000:00:1d.7-4/input1
[   21.556714] input: Logitech 2.4GHz Cordless Desktop as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input14
[   21.556839] hid-generic 0003:046D:C52A.0002: input,hidraw1: USB HID v1.11 Keyboard [Logitech 2.4GHz Cordless Desktop] on usb-0000:00:1d.1-1/input0
[   21.557470] input: Logitech 2.4GHz Cordless Desktop as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input15
[   21.559003] hid-generic 0003:046D:C52A.0003: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Logitech 2.4GHz Cordless Desktop] on usb-0000:00:1d.1-1/input1
[   21.611783] init: udev-fallback-graphics main process (1277) terminated with status 1
[   21.668049] usb 2-4: reset high-speed USB device number 3 using ehci_hcd
[   23.115673] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
[   52.087993] BUG: soft lockup - CPU#0 stuck for 22s! [Xorg:1303]
[   52.087997] Modules linked in: joydev(F) snd_hda_codec_hdmi snd_hda_codec_realtek bnep rfcomm parport_pc(F) bluetooth ppdev(F) binfmt_misc(F) arc4(F) nvidia(POF) snd_hda_intel snd_hda_codec ath5k coretemp snd_hwdep(F) snd_pcm(F) ath snd_seq_midi(F) kvm_intel snd_rawmidi(F) snd_seq_midi_event(F) mac80211 kvm snd_seq(F) snd_timer(F) snd_seq_device(F) cfg80211 snd(F) hid_generic gpio_ich soundcore(F) psmouse(F) usbhid snd_page_alloc(F) microcode(F) mac_hid hid wmi serio_raw(F) usblp lpc_ich lp(F) parport(F) firewire_ohci usb_storage(F) uas firewire_core crc_itu_t(F) e1000e(F)
[   52.088002] CPU 0 
[   52.088002] Pid: 1303, comm: Xorg Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[   52.088002] RIP: 0010:[<ffffffffa04ad681>]  [<ffffffffa04ad681>] _nv011875rm+0x1be/0x1c1 [nvidia]
[   52.088002] RSP: 0018:ffff8801955a58c8  EFLAGS: 00000286
[   52.088002] RAX: ffff880198aac008 RBX: 0000000000000001 RCX: 0000000000000000
[   52.088002] RDX: 0000000000000000 RSI: 0000000000000003 RDI: ffff880198aac018
[   52.088002] RBP: ffff8801914c5e78 R08: 0000000000000001 R09: ffff8801914c5e98
[   52.088002] R10: ffffea00066249c0 R11: ffffffffa0978e7b R12: ffffea00066249c0
[   52.088002] R13: ffffffffa0978e7b R14: ffffea00066249c0 R15: ffff8801914c5e70
[   52.088002] FS:  00007f0072aca940(0000) GS:ffff8801bfc00000(0000) knlGS:0000000000000000
[   52.088002] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   52.088002] CR2: 00007f2007eb7138 CR3: 0000000195724000 CR4: 00000000000407f0
[   52.088002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   52.088002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   52.088002] Process Xorg (pid: 1303, threadinfo ffff8801955a4000, task ffff880199805c00)
[   52.088002] Stack:
[   52.088002]  ffffffffa04ad68d ffffffffa04aab90 0000000000000000 ffff880192018008
[   52.088002]  ffff880198a28008 ffff8801914c5e98 0000000000000000 ffffffffa047c4e4
[   52.088002]  ffff880192018008 ffffffffa04802b4 ffff880192018008 ffff880192018008
[   52.088002] Call Trace:
[   52.088002]  [<ffffffffa04ad68d>] ? _nv011869rm+0x9/0x21 [nvidia]
[   52.088002]  [<ffffffffa04aab90>] ? _nv000758rm+0x91f/0x2e1e [nvidia]
[   52.088002]  [<ffffffffa047c4e4>] ? _nv008087rm+0x1f/0x50 [nvidia]
[   52.088002]  [<ffffffffa04802b4>] ? _nv008136rm+0x39/0x77 [nvidia]
[   52.088002]  [<ffffffffa0797d7b>] ? _nv003221rm+0x4d2a/0xaef3 [nvidia]
[   52.088002]  [<ffffffffa048226a>] ? _nv008145rm+0x39/0x185 [nvidia]
[   52.088002]  [<ffffffffa08c485d>] ? _nv012877rm+0x5f/0xb9 [nvidia]
[   52.088002]  [<ffffffffa08ca3da>] ? _nv012878rm+0xa66/0x293c [nvidia]
[   52.088002]  [<ffffffffa08ca752>] ? _nv012878rm+0xdde/0x293c [nvidia]
[   52.088002]  [<ffffffffa08ca275>] ? _nv012878rm+0x901/0x293c [nvidia]
[   52.088002]  [<ffffffffa079c7d7>] ? _nv003221rm+0x9786/0xaef3 [nvidia]
[   52.088002]  [<ffffffffa079ae06>] ? _nv003221rm+0x7db5/0xaef3 [nvidia]
[   52.088002]  [<ffffffffa0957ba3>] ? _nv000879rm+0x135/0x1e3 [nvidia]
[   52.088002]  [<ffffffffa0957a3b>] ? _nv000794rm+0x728/0x75b [nvidia]
[   52.088002]  [<ffffffffa0951a1b>] ? rm_init_adapter+0x73/0xf6 [nvidia]
[   52.088002]  [<ffffffffa0970114>] ? nv_kern_open+0x4b4/0x800 [nvidia]
[   52.088002]  [<ffffffff8119250f>] ? chrdev_open+0xaf/0x1a0
[   52.088002]  [<ffffffff8118c313>] ? do_dentry_open+0x203/0x290
[   52.088002]  [<ffffffff81192460>] ? cdev_put+0x30/0x30
[   52.088002]  [<ffffffff8118c3e9>] ? vfs_open+0x49/0x50
[   52.088002]  [<ffffffff8119ad68>] ? do_last+0x298/0xea0
[   52.088002]  [<ffffffff8119a1bc>] ? link_path_walk+0x7c/0x8a0
[   52.088002]  [<ffffffff811794bf>] ? kmem_cache_alloc_trace+0x11f/0x130
[   52.088002]  [<ffffffff8119c893>] ? path_openat+0xb3/0x4b0
[   52.088002]  [<ffffffff811b2439>] ? simple_xattr_get+0x79/0xd0
[   52.088002]  [<ffffffff8119d581>] ? do_filp_open+0x41/0xa0
[   52.088002]  [<ffffffff811aab49>] ? __alloc_fd+0xd9/0x130
[   52.088002]  [<ffffffff8118d493>] ? do_sys_open+0xf3/0x230
[   52.088002]  [<ffffffff81197872>] ? path_put+0x22/0x30
[   52.088002]  [<ffffffff8118d5f1>] ? sys_open+0x21/0x30
[   52.088002]  [<ffffffff816b911d>] ? system_call_fastpath+0x1a/0x1f
[   52.088002] Code: ff ff 48 89 c7 89 d9 ba 01 00 00 00 44 89 e6 e8 01 09 00 00 41 ff c5 44 3b 6d 04 72 8e 48 83 c5 08 5b 41 5c 41 5d 41 5e 41 5f c3 <8b> 07 c3 48 83 c7 10 e8 f4 ff ff ff f3 c3 48 8b 47 08 c3 48 89 
[   80.087999] BUG: soft lockup - CPU#0 stuck for 22s! [Xorg:1303]
[   80.088002] Modules linked in: joydev(F) snd_hda_codec_hdmi snd_hda_codec_realtek bnep rfcomm parport_pc(F) bluetooth ppdev(F) binfmt_misc(F) arc4(F) nvidia(POF) snd_hda_intel snd_hda_codec ath5k coretemp snd_hwdep(F) snd_pcm(F) ath snd_seq_midi(F) kvm_intel snd_rawmidi(F) snd_seq_midi_event(F) mac80211 kvm snd_seq(F) snd_timer(F) snd_seq_device(F) cfg80211 snd(F) hid_generic gpio_ich soundcore(F) psmouse(F) usbhid snd_page_alloc(F) microcode(F) mac_hid hid wmi serio_raw(F) usblp lpc_ich lp(F) parport(F) firewire_ohci usb_storage(F) uas firewire_core crc_itu_t(F) e1000e(F)
[   80.088002] CPU 0 
[   80.088002] Pid: 1303, comm: Xorg Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[   80.088002] RIP: 0010:[<ffffffffa04aab7b>]  [<ffffffffa04aab7b>] _nv000758rm+0x90a/0x2e1e [nvidia]
[   80.088002] RSP: 0018:ffff8801955a58e8  EFLAGS: 00000282
[   80.088002] RAX: ffff880198aac008 RBX: 0000000000000003 RCX: 0000000000000000
[   80.088002] RDX: 0000000000000000 RSI: 0000000000000003 RDI: ffff880198aac008
[   80.088002] RBP: ffff8801914c5e78 R08: 0000000000000001 R09: ffff8801914c5e98
[   80.088002] R10: ffffea00066249c0 R11: ffffffffa0978e7b R12: 0000000000000000
[   80.088002] R13: ffff880198aac008 R14: 0000000000000001 R15: ffff8801914c5e98
[   80.088002] FS:  00007f0072aca940(0000) GS:ffff8801bfc00000(0000) knlGS:0000000000000000
[   80.088002] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   80.088002] CR2: 00007f2007eb7138 CR3: 0000000195724000 CR4: 00000000000407f0
[   80.088002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   80.088002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   80.088002] Process Xorg (pid: 1303, threadinfo ffff8801955a4000, task ffff880199805c00)
[   80.088002] Stack:
[   80.088002]  0000000000000000 ffff880192018008 ffff880198a28008 0000000000000000
[   80.088002]  0000000000000000 ffffffffa047c4e4 ffff880192018008 ffffffffa04802b4
[   80.088002]  ffff880192018008 0000000000000045 0000000000000002 ffffffffa0797e03
[   80.088002] Call Trace:
[   80.088002]  [<ffffffffa047c4e4>] ? _nv008087rm+0x1f/0x50 [nvidia]
[   80.088002]  [<ffffffffa04802b4>] ? _nv008136rm+0x39/0x77 [nvidia]
[   80.088002]  [<ffffffffa0797e03>] ? _nv003221rm+0x4db2/0xaef3 [nvidia]
[   80.088002]  [<ffffffffa0482333>] ? _nv008145rm+0x102/0x185 [nvidia]
[   80.088002]  [<ffffffffa08c485d>] ? _nv012877rm+0x5f/0xb9 [nvidia]
[   80.088002]  [<ffffffffa08ca3da>] ? _nv012878rm+0xa66/0x293c [nvidia]
[   80.088002]  [<ffffffffa08ca752>] ? _nv012878rm+0xdde/0x293c [nvidia]
[   80.088002]  [<ffffffffa08ca275>] ? _nv012878rm+0x901/0x293c [nvidia]
[   80.088002]  [<ffffffffa079c7d7>] ? _nv003221rm+0x9786/0xaef3 [nvidia]
[   80.088002]  [<ffffffffa079ae06>] ? _nv003221rm+0x7db5/0xaef3 [nvidia]
[   80.088002]  [<ffffffffa0957ba3>] ? _nv000879rm+0x135/0x1e3 [nvidia]
[   80.088002]  [<ffffffffa0957a3b>] ? _nv000794rm+0x728/0x75b [nvidia]
[   80.088002]  [<ffffffffa0951a1b>] ? rm_init_adapter+0x73/0xf6 [nvidia]
[   80.088002]  [<ffffffffa0970114>] ? nv_kern_open+0x4b4/0x800 [nvidia]
[   80.088002]  [<ffffffff8119250f>] ? chrdev_open+0xaf/0x1a0
[   80.088002]  [<ffffffff8118c313>] ? do_dentry_open+0x203/0x290
[   80.088002]  [<ffffffff81192460>] ? cdev_put+0x30/0x30
[   80.088002]  [<ffffffff8118c3e9>] ? vfs_open+0x49/0x50
[   80.088002]  [<ffffffff8119ad68>] ? do_last+0x298/0xea0
[   80.088002]  [<ffffffff8119a1bc>] ? link_path_walk+0x7c/0x8a0
[   80.088002]  [<ffffffff811794bf>] ? kmem_cache_alloc_trace+0x11f/0x130
[   80.088002]  [<ffffffff8119c893>] ? path_openat+0xb3/0x4b0
[   80.088002]  [<ffffffff811b2439>] ? simple_xattr_get+0x79/0xd0
[   80.088002]  [<ffffffff8119d581>] ? do_filp_open+0x41/0xa0
[   80.088002]  [<ffffffff811aab49>] ? __alloc_fd+0xd9/0x130
[   80.088002]  [<ffffffff8118d493>] ? do_sys_open+0xf3/0x230
[   80.088002]  [<ffffffff81197872>] ? path_put+0x22/0x30
[   80.088002]  [<ffffffff8118d5f1>] ? sys_open+0x21/0x30
[   80.088002]  [<ffffffff816b911d>] ? system_call_fastpath+0x1a/0x1f
[   80.088002] Code: 00 eb 11 48 89 83 a8 26 00 00 48 89 c7 e8 f7 0e 01 00 89 c2 89 d0 48 83 c5 10 5b c3 b8 2f 00 00 00 c3 41 57 41 56 41 55 41 54 53 <48> 89 fb 41 89 f5 41 89 d6 41 89 cf 49 89 fc ff 93 80 00 00 00 
[   88.000000] INFO: rcu_sched self-detected stall on CPU { 0}  (t=15000 jiffies)
[   88.000002] sending NMI to all CPUs:
[   88.000002] NMI backtrace for cpu 0
[   88.000002] CPU 0 
[   88.000002] Pid: 1303, comm: Xorg Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[   88.000002] RIP: 0010:[<ffffffff813488e5>]  [<ffffffff813488e5>] delay_tsc+0x5/0x80
[   88.000002] RSP: 0018:ffff8801bfc03db0  EFLAGS: 00000813
[   88.000002] RAX: 000000005104d300 RBX: 0000000000002710 RCX: 0000000001312f38
[   88.000002] RDX: 000000000025d7d9 RSI: 0000000000000100 RDI: 000000000025d7da
[   88.000002] RBP: ffff8801bfc03db8 R08: 000000000000000a R09: 0000000000000005
[   88.000002] R10: 0000000000000406 R11: 0000000000000002 R12: ffff8801955a4000
[   88.000002] R13: 0000000000000000 R14: ffffffff81c3cd80 R15: ffffffff81c3cd80
[   88.000002] FS:  00007f0072aca940(0000) GS:ffff8801bfc00000(0000) knlGS:0000000000000000
[   88.000002] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   88.000002] CR2: 00007f2007eb7138 CR3: 0000000195724000 CR4: 00000000000407f0
[   88.000002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   88.000002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   88.000002] Process Xorg (pid: 1303, threadinfo ffff8801955a4000, task ffff880199805c00)
[   88.000002] Stack:
[   88.000002]  ffffffff8134885c ffff8801bfc03dd8 ffffffff81039d8a 0000000000000000
[   88.000002]  ffff8801bfc0ee40 ffff8801bfc03e38 ffffffff810ef160 ffff880199805c00
[   88.000002]  ffff8801b648bb80 ffff8801bfc03e38 ffffffff81090ce8 0000000000000000
[   88.000002] Call Trace:
[   88.000002]  <IRQ> 
[   88.000002]  [<ffffffff8134885c>] ? __const_udelay+0x2c/0x30
[   88.000002]  [<ffffffff81039d8a>] arch_trigger_all_cpu_backtrace+0x6a/0xa0
[   88.000002]  [<ffffffff810ef160>] rcu_pending+0x230/0x540
[   88.000002]  [<ffffffff81090ce8>] ? account_system_time+0x118/0x1d0
[   88.000002]  [<ffffffff810f1273>] rcu_check_callbacks+0xa3/0x140
[   88.000002]  [<ffffffff81069a58>] update_process_times+0x48/0x90
[   88.000002]  [<ffffffff810b01fe>] tick_sched_timer+0x6e/0xe0
[   88.000002]  [<ffffffff810807e9>] __run_hrtimer+0x79/0x1d0
[   88.000002]  [<ffffffff810b0190>] ? tick_nohz_handler+0x110/0x110
[   88.000002]  [<ffffffff81081107>] hrtimer_interrupt+0xf7/0x230
[   88.000002]  [<ffffffff816ba49c>] ? call_softirq+0x1c/0x30
[   88.000002]  [<ffffffff816bae09>] smp_apic_timer_interrupt+0x69/0x99
[   88.000002]  [<ffffffff816b9d5d>] apic_timer_interrupt+0x6d/0x80
[   88.000002]  <EOI> 
[   88.000002]  [<ffffffffa0978e7b>] ? os_free_mem+0x1b/0x30 [nvidia]
[   88.000002]  [<ffffffffa04aad97>] ? _nv000758rm+0xb26/0x2e1e [nvidia]
[   88.000002]  [<ffffffffa047bcf5>] ? _nv008086rm+0x1f/0x5d [nvidia]
[   88.000002]  [<ffffffffa047c545>] ? _nv008098rm+0x30/0x32 [nvidia]
[   88.000002]  [<ffffffffa047c56d>] ? _nv008122rm+0x11/0x3e [nvidia]
[   88.000002]  [<ffffffffa048228e>] ? _nv008145rm+0x5d/0x185 [nvidia]
[   88.000002]  [<ffffffffa08c485d>] ? _nv012877rm+0x5f/0xb9 [nvidia]
[   88.000002]  [<ffffffffa08ca3da>] ? _nv012878rm+0xa66/0x293c [nvidia]
[   88.000002]  [<ffffffffa08ca752>] ? _nv012878rm+0xdde/0x293c [nvidia]
[   88.000002]  [<ffffffffa08ca275>] ? _nv012878rm+0x901/0x293c [nvidia]
[   88.000002]  [<ffffffffa079c7d7>] ? _nv003221rm+0x9786/0xaef3 [nvidia]
[   88.000002]  [<ffffffffa079ae06>] ? _nv003221rm+0x7db5/0xaef3 [nvidia]
[   88.000002]  [<ffffffffa0957ba3>] ? _nv000879rm+0x135/0x1e3 [nvidia]
[   88.000002]  [<ffffffffa0957a3b>] ? _nv000794rm+0x728/0x75b [nvidia]
[   88.000002]  [<ffffffffa0951a1b>] ? rm_init_adapter+0x73/0xf6 [nvidia]
[   88.000002]  [<ffffffffa0970114>] ? nv_kern_open+0x4b4/0x800 [nvidia]
[   88.000002]  [<ffffffff8119250f>] ? chrdev_open+0xaf/0x1a0
[   88.000002]  [<ffffffff8118c313>] ? do_dentry_open+0x203/0x290
[   88.000002]  [<ffffffff81192460>] ? cdev_put+0x30/0x30
[   88.000002]  [<ffffffff8118c3e9>] ? vfs_open+0x49/0x50
[   88.000002]  [<ffffffff8119ad68>] ? do_last+0x298/0xea0
[   88.000002]  [<ffffffff8119a1bc>] ? link_path_walk+0x7c/0x8a0
[   88.000002]  [<ffffffff811794bf>] ? kmem_cache_alloc_trace+0x11f/0x130
[   88.000002]  [<ffffffff8119c893>] ? path_openat+0xb3/0x4b0
[   88.000002]  [<ffffffff811b2439>] ? simple_xattr_get+0x79/0xd0
[   88.000002]  [<ffffffff8119d581>] ? do_filp_open+0x41/0xa0
[   88.000002]  [<ffffffff811aab49>] ? __alloc_fd+0xd9/0x130
[   88.000002]  [<ffffffff8118d493>] ? do_sys_open+0xf3/0x230
[   88.000002]  [<ffffffff81197872>] ? path_put+0x22/0x30
[   88.000002]  [<ffffffff8118d5f1>] ? sys_open+0x21/0x30
[   88.000002]  [<ffffffff816b911d>] ? system_call_fastpath+0x1a/0x1f
[   88.000002] Code: 06 48 89 e5 48 c1 e0 02 48 29 ca f7 e2 48 8d 7a 01 ff 15 c7 b1 92 00 5d c3 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 66 66 66 66 90 <55> 48 89 e5 41 56 65 44 8b 34 25 64 b0 00 00 41 55 41 89 fd 41 
[   88.000039] NMI backtrace for cpu 1
[   88.000039] CPU 1 
[   88.000039] Pid: 0, comm: swapper/1 Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[   88.000039] RIP: 0010:[<ffffffff810374df>]  [<ffffffff810374df>] mwait_idle_with_hints+0x5f/0x80
[   88.000039] RSP: 0018:ffff8801b693be28  EFLAGS: 00000046
[   88.000039] RAX: 0000000000000010 RBX: ffff8801b2ce84a0 RCX: 0000000000000001
[   88.000039] RDX: 0000000000000000 RSI: 0000000000000001 RDI: 0000000000000010
[   88.000039] RBP: ffff8801b693be28 R08: ffff8801b693bfd8 R09: 0000000000000000
[   88.000039] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000002
[   88.000039] R13: ffff8801b2ce8400 R14: ffff8801b5e92200 R15: 12f16479caccd6d8
[   88.000039] FS:  0000000000000000(0000) GS:ffff8801bfc80000(0000) knlGS:0000000000000000
[   88.000039] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   88.000039] CR2: 00007f80f6a93000 CR3: 00000001b247d000 CR4: 00000000000407e0
[   88.000039] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   88.000039] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   88.000039] Process swapper/1 (pid: 0, threadinfo ffff8801b693a000, task ffff8801b6931700)
[   88.000039] Stack:
[   88.000039]  ffff8801b693be38 ffffffff81037532 ffff8801b693be48 ffffffff813ce268
[   88.000039]  ffff8801b693be88 ffffffff813ce3dd ffffffff81c7b140 0000000000000001
[   88.000039]  ffff8801b5e92200 0000000000000002 0000000000000001 ffffffff81c7b140
[   88.000039] Call Trace:
[   88.000039]  [<ffffffff81037532>] acpi_processor_ffh_cstate_enter+0x32/0x40
[   88.000039]  [<ffffffff813ce268>] acpi_idle_do_entry+0x10/0x2b
[   88.000039]  [<ffffffff813ce3dd>] acpi_idle_enter_simple+0xa6/0x106
[   88.000039]  [<ffffffff8154bbf9>] cpuidle_enter+0x19/0x20
[   88.000039]  [<ffffffff8154c2c7>] cpuidle_idle_call+0xa7/0x260
[   88.000039]  [<ffffffff810efa05>] ? rcu_eqs_enter+0x65/0xa0
[   88.000039]  [<ffffffff8101d8cf>] cpu_idle+0xaf/0x120
[   88.000039]  [<ffffffff8169957f>] start_secondary+0x1d4/0x1db
[   88.000039] Code: 8b 04 25 30 c7 00 00 48 89 d1 49 8d 80 38 e0 ff ff 0f 01 c8 0f ae f0 49 8b 80 38 e0 ff ff a8 08 75 09 48 89 f8 48 89 f1 0f 01 c9 <5d> c3 0f 1f 80 00 00 00 00 41 0f ae b8 38 e0 ff ff eb be 66 66 
[   88.001235] NMI backtrace for cpu 2
[   88.001240] CPU 2 
[   88.001244] Pid: 0, comm: swapper/2 Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[   88.001246] RIP: 0010:[<ffffffff8108e128>]  [<ffffffff8108e128>] try_to_wake_up+0x38/0x2a0
[   88.001254] RSP: 0018:ffff8801bfd03d10  EFLAGS: 00000046
[   88.001256] RAX: 0000000000000001 RBX: ffff8801b69b2e00 RCX: 000000000000022b
[   88.001258] RDX: 000000000000022b RSI: 0000000000000086 RDI: ffff8801b69b33f4
[   88.001259] RBP: ffff8801bfd03d60 R08: ffff8801bfd0e590 R09: dead000000200200
[   88.001261] R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
[   88.001263] R13: ffff8801b69b33f4 R14: 0000000000000000 R15: 000000000000000f
[   88.001265] FS:  0000000000000000(0000) GS:ffff8801bfd00000(0000) knlGS:0000000000000000
[   88.001267] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   88.001269] CR2: 00007fdd5c774839 CR3: 00000001b249a000 CR4: 00000000000407e0
[   88.001271] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   88.001273] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   88.001275] Process swapper/2 (pid: 0, threadinfo ffff8801b693c000, task ffff8801b6932e00)
[   88.001276] Stack:
[   88.001277]  0000000000000002 ffff8801bfd0e800 000000147d3593d8 0000000000000086
[   88.001282]  ffffffff81344fc4 ffff8801bfd11068 ffff8801bfd0e380 0000000000000002
[   88.001285]  0000000000000000 ffff8801bfd17700 ffff8801bfd03d70 ffffffff8108e3e5
[   88.001288] Call Trace:
[   88.001290]  <IRQ> 
[   88.001292]  [<ffffffff81344fc4>] ? timerqueue_add+0x64/0xb0
[   88.001299]  [<ffffffff8108e3e5>] wake_up_process+0x15/0x20
[   88.001303]  [<ffffffff81073bb4>] wake_up_worker+0x24/0x30
[   88.001306]  [<ffffffff81073c54>] insert_work+0x94/0xb0
[   88.001309]  [<ffffffff81076202>] __queue_work+0xe2/0x3a0
[   88.001313]  [<ffffffff810ae7b6>] ? clockevents_program_event+0x76/0x120
[   88.001316]  [<ffffffff810764c0>] ? __queue_work+0x3a0/0x3a0
[   88.001319]  [<ffffffff810764eb>] delayed_work_timer_fn+0x2b/0x30
[   88.001323]  [<ffffffff8106737a>] call_timer_fn+0x3a/0x120
[   88.001326]  [<ffffffff810ae7b6>] ? clockevents_program_event+0x76/0x120
[   88.001329]  [<ffffffff810764c0>] ? __queue_work+0x3a0/0x3a0
[   88.001332]  [<ffffffff81068f3b>] run_timer_softirq+0x15b/0x2a0
[   88.001335]  [<ffffffff8106024f>] __do_softirq+0xcf/0x210
[   88.001339]  [<ffffffff816b06ae>] ? _raw_spin_lock+0xe/0x20
[   88.001343]  [<ffffffff816ba49c>] call_softirq+0x1c/0x30
[   88.001347]  [<ffffffff810167a5>] do_softirq+0x75/0xb0
[   88.001350]  [<ffffffff81060505>] irq_exit+0xa5/0xb0
[   88.001353]  [<ffffffff816bad23>] do_IRQ+0x63/0xe0
[   88.001357]  [<ffffffff816b0cad>] common_interrupt+0x6d/0x6d
[   88.001358]  <EOI> 
[   88.001360]  [<ffffffff8101bd13>] ? native_sched_clock+0x13/0x80
[   88.001366]  [<ffffffff813cdb2b>] ? arch_local_irq_enable+0x8/0xd
[   88.001370]  [<ffffffff81090ade>] ? sched_clock_idle_wakeup_event+0x1e/0x20
[   88.001373]  [<ffffffff813ce403>] acpi_idle_enter_simple+0xcc/0x106
[   88.001377]  [<ffffffff8154bbf9>] cpuidle_enter+0x19/0x20
[   88.001379]  [<ffffffff8154c2c7>] cpuidle_idle_call+0xa7/0x260
[   88.001383]  [<ffffffff810efa05>] ? rcu_eqs_enter+0x65/0xa0
[   88.001386]  [<ffffffff8101d8cf>] cpu_idle+0xaf/0x120
[   88.001390]  [<ffffffff8169957f>] start_secondary+0x1d4/0x1db
[   88.001391] Code: f7 41 56 41 89 d6 41 55 41 54 53 48 89 fb 48 83 ec 28 4c 8d af f4 05 00 00 45 31 e4 4c 89 ef e8 6f 28 62 00 48 89 45 c8 48 8b 03 <41> 85 c7 0f 84 9d 01 00 00 48 8b 43 08 44 8b 5b 2c 49 c7 c7 40 
[   88.000053] NMI backtrace for cpu 3
[   88.000053] CPU 3 
[   88.000053] Pid: 0, comm: swapper/3 Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[   88.000053] RIP: 0010:[<ffffffff810374df>]  [<ffffffff810374df>] mwait_idle_with_hints+0x5f/0x80
[   88.000053] RSP: 0018:ffff8801b693fe28  EFLAGS: 00000046
[   88.000053] RAX: 0000000000000010 RBX: ffff8801b5e86ca0 RCX: 0000000000000001
[   88.000053] RDX: 0000000000000000 RSI: 0000000000000001 RDI: 0000000000000010
[   88.000053] RBP: ffff8801b693fe28 R08: ffff8801b693ffd8 R09: 0000000000000000
[   88.000053] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000000002
[   88.000053] R13: ffff8801b5e86c00 R14: ffff8801b5e92600 R15: 12f16479cacd05c5
[   88.000053] FS:  0000000000000000(0000) GS:ffff8801bfd80000(0000) knlGS:0000000000000000
[   88.000053] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   88.000053] CR2: 000000000104da90 CR3: 00000001b247d000 CR4: 00000000000407e0
[   88.000053] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   88.000053] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   88.000053] Process swapper/3 (pid: 0, threadinfo ffff8801b693e000, task ffff8801b6934500)
[   88.000053] Stack:
[   88.000053]  ffff8801b693fe38 ffffffff81037532 ffff8801b693fe48 ffffffff813ce268
[   88.000053]  ffff8801b693fe88 ffffffff813ce3dd ffffffff81c7b140 0000000000000001
[   88.000053]  ffff8801b5e92600 0000000000000002 0000000000000003 ffffffff81c7b140
[   88.000053] Call Trace:
[   88.000053]  [<ffffffff81037532>] acpi_processor_ffh_cstate_enter+0x32/0x40
[   88.000053]  [<ffffffff813ce268>] acpi_idle_do_entry+0x10/0x2b
[   88.000053]  [<ffffffff813ce3dd>] acpi_idle_enter_simple+0xa6/0x106
[   88.000053]  [<ffffffff8154bbf9>] cpuidle_enter+0x19/0x20
[   88.000053]  [<ffffffff8154c2c7>] cpuidle_idle_call+0xa7/0x260
[   88.000053]  [<ffffffff810efa05>] ? rcu_eqs_enter+0x65/0xa0
[   88.000053]  [<ffffffff8101d8cf>] cpu_idle+0xaf/0x120
[   88.000053]  [<ffffffff8169957f>] start_secondary+0x1d4/0x1db
[   88.000053] Code: 8b 04 25 30 c7 00 00 48 89 d1 49 8d 80 38 e0 ff ff 0f 01 c8 0f ae f0 49 8b 80 38 e0 ff ff a8 08 75 09 48 89 f8 48 89 f1 0f 01 c9 <5d> c3 0f 1f 80 00 00 00 00 41 0f ae b8 38 e0 ff ff eb be 66 66 
[  112.087997] BUG: soft lockup - CPU#0 stuck for 22s! [Xorg:1303]
[  112.088001] Modules linked in: joydev(F) snd_hda_codec_hdmi snd_hda_codec_realtek bnep rfcomm parport_pc(F) bluetooth ppdev(F) binfmt_misc(F) arc4(F) nvidia(POF) snd_hda_intel snd_hda_codec ath5k coretemp snd_hwdep(F) snd_pcm(F) ath snd_seq_midi(F) kvm_intel snd_rawmidi(F) snd_seq_midi_event(F) mac80211 kvm snd_seq(F) snd_timer(F) snd_seq_device(F) cfg80211 snd(F) hid_generic gpio_ich soundcore(F) psmouse(F) usbhid snd_page_alloc(F) microcode(F) mac_hid hid wmi serio_raw(F) usblp lpc_ich lp(F) parport(F) firewire_ohci usb_storage(F) uas firewire_core crc_itu_t(F) e1000e(F)
[  112.088003] CPU 0 
[  112.088003] Pid: 1303, comm: Xorg Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[  112.088003] RIP: 0010:[<ffffffffa04ae03a>]  [<ffffffffa04ae03a>] _nv012166rm+0x46/0x51 [nvidia]
[  112.088003] RSP: 0018:ffff8801955a5908  EFLAGS: 00000246
[  112.088003] RAX: 0000000000000000 RBX: 0000000000000001 RCX: 0000000000000014
[  112.088003] RDX: 0000000000100000 RSI: 0000000000005414 RDI: ffff880192018034
[  112.088003] RBP: ffff8801914c5e78 R08: 0000000000000001 R09: ffff8801914c5e98
[  112.088003] R10: ffffea00066249c0 R11: ffffffffa0978e7b R12: 0000000000000001
[  112.088003] R13: ffff8801914c5e98 R14: ffffea00066249c0 R15: ffffffffa0978e7b
[  112.088003] FS:  00007f0072aca940(0000) GS:ffff8801bfc00000(0000) knlGS:0000000000000000
[  112.088003] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  112.088003] CR2: 00007f2007eb7138 CR3: 0000000195724000 CR4: 00000000000407f0
[  112.088003] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  112.088003] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  112.088003] Process Xorg (pid: 1303, threadinfo ffff8801955a4000, task ffff880199805c00)
[  112.088003] Stack:
[  112.088003]  0000000000000001 ffffffffa04ad57d 0000000000000000 ffff880192018008
[  112.088003]  0000000000000001 ffffffffa079d09d ffff880192018008 ffff880192018008
[  112.088003]  0000000000000045 ffffffffa04822dc ffff880192018008 0000000000000045
[  112.088003] Call Trace:
[  112.088003]  [<ffffffffa04ad57d>] ? _nv011875rm+0xba/0x1c1 [nvidia]
[  112.088003]  [<ffffffffa079d09d>] ? _nv003221rm+0xa04c/0xaef3 [nvidia]
[  112.088003]  [<ffffffffa04822dc>] ? _nv008145rm+0xab/0x185 [nvidia]
[  112.088003]  [<ffffffffa08c485d>] ? _nv012877rm+0x5f/0xb9 [nvidia]
[  112.088003]  [<ffffffffa08ca3da>] ? _nv012878rm+0xa66/0x293c [nvidia]
[  112.088003]  [<ffffffffa08ca752>] ? _nv012878rm+0xdde/0x293c [nvidia]
[  112.088003]  [<ffffffffa08ca275>] ? _nv012878rm+0x901/0x293c [nvidia]
[  112.088003]  [<ffffffffa079c7d7>] ? _nv003221rm+0x9786/0xaef3 [nvidia]
[  112.088003]  [<ffffffffa079ae06>] ? _nv003221rm+0x7db5/0xaef3 [nvidia]
[  112.088003]  [<ffffffffa0957ba3>] ? _nv000879rm+0x135/0x1e3 [nvidia]
[  112.088003]  [<ffffffffa0957a3b>] ? _nv000794rm+0x728/0x75b [nvidia]
[  112.088003]  [<ffffffffa0951a1b>] ? rm_init_adapter+0x73/0xf6 [nvidia]
[  112.088003]  [<ffffffffa0970114>] ? nv_kern_open+0x4b4/0x800 [nvidia]
[  112.088003]  [<ffffffff8119250f>] ? chrdev_open+0xaf/0x1a0
[  112.088003]  [<ffffffff8118c313>] ? do_dentry_open+0x203/0x290
[  112.088003]  [<ffffffff81192460>] ? cdev_put+0x30/0x30
[  112.088003]  [<ffffffff8118c3e9>] ? vfs_open+0x49/0x50
[  112.088003]  [<ffffffff8119ad68>] ? do_last+0x298/0xea0
[  112.088003]  [<ffffffff8119a1bc>] ? link_path_walk+0x7c/0x8a0
[  112.088003]  [<ffffffff811794bf>] ? kmem_cache_alloc_trace+0x11f/0x130
[  112.088003]  [<ffffffff8119c893>] ? path_openat+0xb3/0x4b0
[  112.088003]  [<ffffffff811b2439>] ? simple_xattr_get+0x79/0xd0
[  112.088003]  [<ffffffff8119d581>] ? do_filp_open+0x41/0xa0
[  112.088003]  [<ffffffff811aab49>] ? __alloc_fd+0xd9/0x130
[  112.088003]  [<ffffffff8118d493>] ? do_sys_open+0xf3/0x230
[  112.088003]  [<ffffffff81197872>] ? path_put+0x22/0x30
[  112.088003]  [<ffffffff8118d5f1>] ? sys_open+0x21/0x30
[  112.088003]  [<ffffffff816b911d>] ? system_call_fastpath+0x1a/0x1f
[  112.088003] Code: 00 e8 be f8 49 00 48 89 c2 be 01 00 00 00 bf 00 00 00 00 e8 a4 f1 00 00 b8 00 00 00 00 eb 12 89 c0 ba 01 00 00 00 d3 e2 85 14 87 <0f> 95 c0 0f b6 c0 48 83 c4 08 c3 41 55 41 54 53 48 89 fb 49 89 
[  140.087998] BUG: soft lockup - CPU#0 stuck for 22s! [Xorg:1303]
[  140.088002] Modules linked in: joydev(F) snd_hda_codec_hdmi snd_hda_codec_realtek bnep rfcomm parport_pc(F) bluetooth ppdev(F) binfmt_misc(F) arc4(F) nvidia(POF) snd_hda_intel snd_hda_codec ath5k coretemp snd_hwdep(F) snd_pcm(F) ath snd_seq_midi(F) kvm_intel snd_rawmidi(F) snd_seq_midi_event(F) mac80211 kvm snd_seq(F) snd_timer(F) snd_seq_device(F) cfg80211 snd(F) hid_generic gpio_ich soundcore(F) psmouse(F) usbhid snd_page_alloc(F) microcode(F) mac_hid hid wmi serio_raw(F) usblp lpc_ich lp(F) parport(F) firewire_ohci usb_storage(F) uas firewire_core crc_itu_t(F) e1000e(F)
[  140.088002] CPU 0 
[  140.088002] Pid: 1303, comm: Xorg Tainted: PF          O 3.7.0-7-generic #15-Ubuntu Packard Bell ixtreme M5722/EG43M
[  140.088002] RIP: 0010:[<ffffffffa047c515>]  [<ffffffffa047c515>] _nv008087rm+0x50/0x50 [nvidia]
[  140.088002] RSP: 0018:ffff8801955a5940  EFLAGS: 00000202
[  140.088002] RAX: 0000000000000000 RBX: ffff880198a28008 RCX: 0000000000000002
[  140.088002] RDX: 0000000000000004 RSI: 0000000000005402 RDI: 0000000000000000
[  140.088002] RBP: ffff8801914c5e78 R08: 0000000000000001 R09: ffff8801914c5e98
[  140.088002] R10: ffffea00066249c0 R11: ffffffffa0978e7b R12: 0000000000000000
[  140.088002] R13: 0000000000000000 R14: ffffffffa04aab90 R15: ffffffffa04ad68d
[  140.088002] FS:  00007f0072aca940(0000) GS:ffff8801bfc00000(0000) knlGS:0000000000000000
[  140.088002] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  140.088002] CR2: 00007f2007eb7138 CR3: 0000000195724000 CR4: 00000000000407f0
[  140.088002] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  140.088002] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  140.088002] Process Xorg (pid: 1303, threadinfo ffff8801955a4000, task ffff880199805c00)
[  140.088002] Stack:
[  140.088002]  ffffffffa047c56d ffff880192018008 ffffffffa0482365 ffff880192018008
[  140.088002]  0000000000000045 0000000000000001 ffff8801914c5e98 0000000000000000
[  140.088002]  ffffffffa08c485d 0000000000000038 ffff88019226e008 ffff880192018008
[  140.088002] Call Trace:
[  140.088002]  [<ffffffffa047c56d>] ? _nv008122rm+0x11/0x3e [nvidia]
[  140.088002]  [<ffffffffa0482365>] ? _nv008145rm+0x134/0x185 [nvidia]
[  140.088002]  [<ffffffffa08c485d>] ? _nv012877rm+0x5f/0xb9 [nvidia]
[  140.088002]  [<ffffffffa08ca3da>] ? _nv012878rm+0xa66/0x293c [nvidia]
[  140.088002]  [<ffffffffa08ca752>] ? _nv012878rm+0xdde/0x293c [nvidia]
[  140.088002]  [<ffffffffa08ca275>] ? _nv012878rm+0x901/0x293c [nvidia]
[  140.088002]  [<ffffffffa079c7d7>] ? _nv003221rm+0x9786/0xaef3 [nvidia]
[  140.088002]  [<ffffffffa079ae06>] ? _nv003221rm+0x7db5/0xaef3 [nvidia]
[  140.088002]  [<ffffffffa0957ba3>] ? _nv000879rm+0x135/0x1e3 [nvidia]
[  140.088002]  [<ffffffffa0957a3b>] ? _nv000794rm+0x728/0x75b [nvidia]
[  140.088002]  [<ffffffffa0951a1b>] ? rm_init_adapter+0x73/0xf6 [nvidia]
[  140.088002]  [<ffffffffa0970114>] ? nv_kern_open+0x4b4/0x800 [nvidia]
[  140.088002]  [<ffffffff8119250f>] ? chrdev_open+0xaf/0x1a0
[  140.088002]  [<ffffffff8118c313>] ? do_dentry_open+0x203/0x290
[  140.088002]  [<ffffffff81192460>] ? cdev_put+0x30/0x30
[  140.088002]  [<ffffffff8118c3e9>] ? vfs_open+0x49/0x50
[  140.088002]  [<ffffffff8119ad68>] ? do_last+0x298/0xea0
[  140.088002]  [<ffffffff8119a1bc>] ? link_path_walk+0x7c/0x8a0
[  140.088002]  [<ffffffff811794bf>] ? kmem_cache_alloc_trace+0x11f/0x130
[  140.088002]  [<ffffffff8119c893>] ? path_openat+0xb3/0x4b0
[  140.088002]  [<ffffffff811b2439>] ? simple_xattr_get+0x79/0xd0
[  140.088002]  [<ffffffff8119d581>] ? do_filp_open+0x41/0xa0
[  140.088002]  [<ffffffff811aab49>] ? __alloc_fd+0xd9/0x130
[  140.088002]  [<ffffffff8118d493>] ? do_sys_open+0xf3/0x230
[  140.088002]  [<ffffffff81197872>] ? path_put+0x22/0x30
[  140.088002]  [<ffffffff8118d5f1>] ? sys_open+0x21/0x30
[  140.088002]  [<ffffffff816b911d>] ? system_call_fastpath+0x1a/0x1f
[  140.088002] Code: 00 00 b8 01 00 00 00 89 c7 89 d9 d3 e7 89 d0 48 8d 04 c0 48 c1 e0 04 85 bc 30 78 3d 00 00 75 07 ff c2 83 fa 1f 76 e6 89 d0 5b c3 <53> e8 aa ff ff ff 89 c3 83 f8 1f 76 1c bf 00 00 00 00 e8 a7 13 

```

I think ```
[   23.115673] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
``` may be of some importance.

---

### Post by pme 72 on 2013-04-03
[    21.766] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu

That looks like a Lucid, 10.04 kernel.

---

### Post by NorthAntrim on 2013-04-03
> **pme 72 said:**
> [    21.766] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu

That looks like a Lucid, 10.04 kernel.
What does that mean? :?, or how can I update to a different kernel which the drivers will work with?

---

### Post by Perfect Storm on 2013-04-03
Try purge the current ppa:ubuntu-x-swat/x-updates (downgrade), then try bleeding edge xorg. Just note it's bleeding edge.

```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```


> [    22.624] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.624]     compiled for 4.0.2, module version = 1.0.0
[    22.624]     Module class: X.Org Video Driver
[    22.624] (II) UnloadModule: "nvidia"
[    22.624] (II) Unloading nvidia
[    22.624] (II) Failed to load module "nvidia" (already loaded, 32512)

---

### Post by gordintoronto on 2013-04-04
> **NorthAntrim said:**
> What does that mean? :?, or how can I update to a different kernel which the drivers will work with?

It means you are running Ubuntu 10.04, which will end support on May 9. It also means your OS is older than your video card, which is a common source of problems.

The obvious solution is to install 12.04. Make sure you have excellent backup before you begin thinking about it! (Two sets of backup!)

Download 12.04, install unetbootin, use unetbootin to create a bootable flash drive, try 12.04.

---

### Post by pme 72 on 2013-04-04
Not sure but it may mean he upgraded from 10.04. It appears he has Quantal running. I am wondering if he neglected to disable the proprietary Nvidia driver when he upgraded. I have read that it is a good idea with any proprietary driver to avoid potential conflicts. 

Sorry for the confusing post...

---

### Post by NorthAntrim on 2013-04-04
According to "[FONT=monospace][COLOR=#333333]*lsb_release -a*" I am running 12.10, and when I installed Ubuntu I formatted the root partition but not the home partition which I'm still using.[/COLOR][/FONT]
> **Artificial Intelligence said:**
> Try purge the current ppa:ubuntu-x-swat/x-updates (downgrade), then try bleeding edge xorg. Just note it's bleeding edge.

```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```
I ran those commands and rebooted, but I got the same low resolution display.

---

