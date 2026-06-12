---
title: "Can't run Intel drivers"
date: 2014-04-04
forum: Hardware
---

### Post by etc9053 on 2014-04-04
I'm using nvidia cards in my system previously, but now I want to try xen, which is incompatible with nvidia drivers so I decided to use my internal HD 2000.
But... I can't run intel drivers, here is a xlog:

```
[   931.892] X.Org X Server 1.14.5
Release Date: 2013-12-12
[   931.892] X Protocol Version 11, Revision 0
[   931.892] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[   931.892] Current Operating System: Linux Gordon01 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64
[   931.892] Kernel command line: BOOT_IMAGE=/vmlinuz-3.11.0-15-generic root=UUID=cc4e6e5b-6113-4949-9ba5-769b7a73e948 ro max_loop=64 iommu=pt iommu=1 amd_iommu=fullflush xen-pciback.hide=(02:00.0)(02:00.1) nomodeset
[   931.892] Build Date: 17 December 2013  10:06:15AM
[   931.892] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[   931.892] Current version of pixman: 0.30.2
[   931.892] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   931.892] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   931.892] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  5 01:41:52 2014
[   931.892] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   931.893] (==) No Layout section.  Using the first Screen section.
[   931.893] (==) No screen section available. Using defaults.
[   931.893] (**) |-->Screen "Default Screen Section" (0)
[   931.893] (**) |   |-->Monitor "<default monitor>"
[   931.893] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   931.893] (==) Automatically adding devices
[   931.893] (==) Automatically enabling devices
[   931.893] (==) Automatically adding GPU devices
[   931.893] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   931.893] 	Entry deleted from font path.
[   931.893] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   931.893] 	Entry deleted from font path.
[   931.893] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   931.893] 	Entry deleted from font path.
[   931.893] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   931.893] 	Entry deleted from font path.
[   931.893] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   931.893] 	Entry deleted from font path.
[   931.893] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   931.893] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   931.893] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   931.893] (II) Loader magic: 0x7f809a19ad20
[   931.893] (II) Module ABI versions:
[   931.893] 	X.Org ANSI C Emulation: 0.4
[   931.893] 	X.Org Video Driver: 14.1
[   931.893] 	X.Org XInput driver : 19.1
[   931.893] 	X.Org Server Extension : 7.0
[   931.894] (--) PCI:*(0:0:2:0) 8086:0102:1849:0102 rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[   931.894] (II) Open ACPI successful (/var/run/acpid.socket)
[   931.894] Initializing built-in extension Generic Event Extension
[   931.894] Initializing built-in extension SHAPE
[   931.894] Initializing built-in extension MIT-SHM
[   931.894] Initializing built-in extension XInputExtension
[   931.894] Initializing built-in extension XTEST
[   931.894] Initializing built-in extension BIG-REQUESTS
[   931.894] Initializing built-in extension SYNC
[   931.894] Initializing built-in extension XKEYBOARD
[   931.894] Initializing built-in extension XC-MISC
[   931.894] Initializing built-in extension SECURITY
[   931.894] Initializing built-in extension XINERAMA
[   931.894] Initializing built-in extension XFIXES
[   931.894] Initializing built-in extension RENDER
[   931.894] Initializing built-in extension RANDR
[   931.894] Initializing built-in extension COMPOSITE
[   931.895] Initializing built-in extension DAMAGE
[   931.895] Initializing built-in extension MIT-SCREEN-SAVER
[   931.895] Initializing built-in extension DOUBLE-BUFFER
[   931.895] Initializing built-in extension RECORD
[   931.895] Initializing built-in extension DPMS
[   931.895] Initializing built-in extension X-Resource
[   931.895] Initializing built-in extension XVideo
[   931.895] Initializing built-in extension XVideo-MotionCompensation
[   931.895] Initializing built-in extension SELinux
[   931.895] Initializing built-in extension XFree86-VidModeExtension
[   931.895] Initializing built-in extension XFree86-DGA
[   931.895] Initializing built-in extension XFree86-DRI
[   931.895] Initializing built-in extension DRI2
[   931.895] (II) LoadModule: "glx"
[   931.895] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   931.895] (II) Module glx: vendor="X.Org Foundation"
[   931.895] 	compiled for 1.14.5, module version = 1.0.0
[   931.895] 	ABI class: X.Org Server Extension, version 7.0
[   931.895] (==) AIGLX enabled
[   931.895] Loading extension GLX
[   931.895] (==) Matched intel as autoconfigured driver 0
[   931.895] (==) Matched vesa as autoconfigured driver 1
[   931.895] (==) Matched modesetting as autoconfigured driver 2
[   931.895] (==) Matched fbdev as autoconfigured driver 3
[   931.895] (==) Assigned the driver to the xf86ConfigLayout
[   931.895] (II) LoadModule: "intel"
[   931.896] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   931.896] (II) Module intel: vendor="X.Org Foundation"
[   931.896] 	compiled for 1.14.3, module version = 2.99.907
[   931.896] 	Module class: X.Org Video Driver
[   931.896] 	ABI class: X.Org Video Driver, version 14.1
[   931.896] (II) LoadModule: "vesa"
[   931.896] (WW) Warning, couldn't open module vesa
[   931.896] (II) UnloadModule: "vesa"
[   931.896] (II) Unloading vesa
[   931.896] (EE) Failed to load module "vesa" (module does not exist, 0)
[   931.896] (II) LoadModule: "modesetting"
[   931.897] (WW) Warning, couldn't open module modesetting
[   931.897] (II) UnloadModule: "modesetting"
[   931.897] (II) Unloading modesetting
[   931.897] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   931.897] (II) LoadModule: "fbdev"
[   931.897] (WW) Warning, couldn't open module fbdev
[   931.897] (II) UnloadModule: "fbdev"
[   931.897] (II) Unloading fbdev
[   931.897] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   931.897] (==) Matched intel as autoconfigured driver 0
[   931.897] (==) Matched vesa as autoconfigured driver 1
[   931.897] (==) Matched modesetting as autoconfigured driver 2
[   931.897] (==) Matched fbdev as autoconfigured driver 3
[   931.897] (==) Assigned the driver to the xf86ConfigLayout
[   931.897] (II) LoadModule: "intel"
[   931.897] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   931.897] (II) Module intel: vendor="X.Org Foundation"
[   931.897] 	compiled for 1.14.3, module version = 2.99.907
[   931.897] 	Module class: X.Org Video Driver
[   931.897] 	ABI class: X.Org Video Driver, version 14.1
[   931.897] (II) UnloadModule: "intel"
[   931.897] (II) Unloading intel
[   931.897] (II) Failed to load module "intel" (already loaded, 32640)
[   931.897] (II) LoadModule: "vesa"
[   931.898] (WW) Warning, couldn't open module vesa
[   931.898] (II) UnloadModule: "vesa"
[   931.898] (II) Unloading vesa
[   931.898] (EE) Failed to load module "vesa" (module does not exist, 0)
[   931.898] (II) LoadModule: "modesetting"
[   931.898] (WW) Warning, couldn't open module modesetting
[   931.898] (II) UnloadModule: "modesetting"
[   931.898] (II) Unloading modesetting
[   931.898] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   931.898] (II) LoadModule: "fbdev"
[   931.898] (WW) Warning, couldn't open module fbdev
[   931.898] (II) UnloadModule: "fbdev"
[   931.898] (II) Unloading fbdev
[   931.898] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   931.898] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   931.899] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[   931.899] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[   931.899] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[   931.899] (++) using VT number 7


[   931.901] (EE) No devices detected.
[   931.901] (EE) 
Fatal server error:
[   931.901] (EE) no screens found(EE) 
[   931.901] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   931.901] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   931.901] (EE) 

```

I really need some help because I'm stuck!
Of cource, I have no xorg.conf file, I've also tried to reinstall xorg completely, but again no luck :(

---

### Post by tgalati4 on 2014-04-04
xorg is telling you that it could not load the VESA or framebuffer driver (vesa and fbdev).  These are fallback graphics devices.  Because you are having problems loading these fallback devices, you end up with no display whatsoever.  Are there settings in BIOS to allow the HD2000 to support VESA or framebuffer or "Legacy Video"?

Why do you want to run xen?  Normally that would run on a server (text console) or headless, serving multiple virtual machines.  That is why there is limited graphics support.

KVM is the supported virtual environment on Ubuntu:

qemu-kvm - Full virtualization on supported hardware
qemu-utils - qemu utilities

---

### Post by etc9053 on 2014-04-04
Hello, thank you for reply!

I've intentionally deleted VESA and fbdev driver, bacause, as you say, xorg falling back to this drivers that have limited resolution (up to 1280x1024) and performance. Intel drivers don't start if I have VESA driver installed. Of course, under XEN VESA driver do not work.
In BIOS for HD2000 I only have enable/disable oprion and shared memory setting.

The reason I want to run XEN is VGA passthrough. The setup I originally want is geforce gtx780 in dom0 and some radeon card in domU to run windows 7. This is for ability to play games on same PC with my wife :)
But I discovered that I can't run nvidia card in dom0 bacause of incompatibility in nvidia proprietary drivers. Then I just want to see how it works even with HD2000 card in dom0.

Does kvm support vga passthrough?

Alexander.

---

### Post by Yellow Pasque on 2014-04-05
Does your CPU support Vt-d?

As for qemu support for vga passthrough, I'd consider it experimental right now. There's an interesting guide here: [https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)
Personally, I have trouble getting the emulated q35 chipset to work properly at all (it could just be me though).

---

### Post by etc9053 on 2014-04-05
> [COLOR=#000000]Does your CPU support Vt-d?[/COLOR]

Yes, I have i5 2500 and ASRock H77 Pro4-M that proved to work

---

### Post by etc9053 on 2014-04-08
BUMP!
I still can't run Intel even not under XEN

---

### Post by Yellow Pasque on 2014-04-09
So the Xorg log you gave was from the host system?

---

### Post by heiko_s on 2014-04-14
I would try again installing the Nvidia proprietary driver under Xen, but you have to set the environment variable
IGNORE_XEN_PRESENCE=1 to get it to build.

As for VGA passthrough, you may want to try Ubuntu 14.04 with Xen 4.4 if you pass through an AMD graphics card. More on that [here]("http://ubuntuforums.org/showthread.php?t=2216910").



Good luck!

EDIT: About the Intel driver not running and the "no screen found", I had the same issue with the AMD driver. My workaround was to remove the second VGA card and install Ubuntu and Xen, then install the proprietary driver (I had to install the AMD driver, in your case Intel). Then install the second VGA card and boot into Xen. Hope that works for you as well.

---

