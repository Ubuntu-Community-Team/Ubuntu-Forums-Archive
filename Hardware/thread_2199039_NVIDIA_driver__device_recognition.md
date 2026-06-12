---
title: "NVIDIA driver / device recognition"
date: 2014-01-11
forum: Hardware
---

### Post by sean.d.matthews on 2014-01-11
My system:
Linux 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 athlon i386 GNU/Linux
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


nvidia-smi
+------------------------------------------------------+                       
| NVIDIA-SMI 5.319.76   Driver Version: 319.76         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 780 Ti  Off  | 0000:01:00.0     N/A |                  N/A |
| 61%   83C  N/A     N/A /  N/A |     1550MB /  3071MB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+


lspci -k
01:00.0 VGA compatible controller: NVIDIA Corporation Device 100a (rev a1)
	Subsystem: eVga.com. Corp. Device 2883
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nvidiafb


lshw -C display
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:d800(size=128) memory:feb80000-febfffff


 nvidia-settings -q all
ERROR: The control display is undefined; please run `nvidia-settings --help` for usage information.


nvidia-settings
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.


xorg.conf
[attached]


Ok, now that that's out of the way... my *primary* problem is that I cannot run nvidia-settings. As you can see above, either the "control display is undefined" or "you do not appear to be using the NVIDIA X driver." I have tried installing the *.run driver from NVIDIA's website. I have also tried installing the nvidia_319_updates driver from synaptic. I have tried purging all nvidia-* programs from synaptic, as well as putting the typical list of other display programs on the blacklist. One important thing is that I have no monitor attached-- I'm running the system through SSH. What else can I try?

Thanks!

---

### Post by steeldriver on 2014-01-11
I'm not sure if it's the same issue, but after upgrading to nvidia-319 via CUDA I was also unable to run nvidia-settings - I *think* the issue turned out to be a stale symlink in the update-alternatives database. Try running

```
sudo update-alternatives --config nvidia_settings_conf
```

and making sure the /usr/lib/nvidia-settings-319/ld.so.conf option is selected

---

### Post by sean.d.matthews on 2014-01-11
No luck. When I do that, I get:
There is only one alternative in link group nvidia_settings_conf: /usr/lib/nvidia-settings-319-updates/ld.so.conf
Nothing to configure.

Also, there's this:
jockey-text --list
kmod:nvidia_319_updates - nvidia_319_updates (Proprietary, Enabled, Not in use)

---

### Post by sean.d.matthews on 2014-01-11
I also installed nvidia-319 and uninstalled the *.run driver (they're incompatible, I've read). New jockey-text -l:

kmod:nvidia_319 - nvidia_319 (Proprietary, Enabled, Not in use)
kmod:nvidia_319_updates - nvidia_319_updates (Proprietary, Enabled, Not in use)

This is very frustrating. I've tried everything I know how to do...

---

### Post by Yellow Pasque on 2014-01-12
Post your /var/log/Xorg.0.log (use code tags)

---

### Post by sean.d.matthews on 2014-01-12
```

/var/log/Xorg.0.log
[    11.910] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    11.910] X Protocol Version 11, Revision 0
[    11.910] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    11.910] Current Operating System: Linux warband-A780LM-M2 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686
[    11.910] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic-pae root=UUID=dfcc3559-db80-440f-9daf-776dd948a5ea ro quiet splash
[    11.910] Build Date: 16 October 2013  04:45:22PM
[    11.910] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    11.910] Current version of pixman: 0.30.2
[    11.910] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.910] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.910] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 11 20:56:45 2014
[    11.911] (==) Using config file: "/etc/X11/xorg.conf"
[    11.911] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.911] (==) ServerLayout "Layout0"
[    11.911] (**) |-->Screen "Screen0" (0)
[    11.911] (**) |   |-->Monitor "Monitor0"
[    11.911] (**) |   |-->Device "Device0"
[    11.911] (**) |-->Input Device "Keyboard0"
[    11.911] (**) |-->Input Device "Mouse0"
[    11.911] (==) Automatically adding devices
[    11.911] (==) Automatically enabling devices
[    11.934] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.934] 	Entry deleted from font path.
[    11.934] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.934] 	Entry deleted from font path.
[    11.934] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.934] 	Entry deleted from font path.
[    11.934] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.934] 	Entry deleted from font path.
[    11.934] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.934] 	Entry deleted from font path.
[    11.934] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    11.934] 	Entry deleted from font path.
[    11.934] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    11.934] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.934] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    11.934] (WW) Disabling Keyboard0
[    11.934] (WW) Disabling Mouse0
[    11.934] (II) Loader magic: 0xb77b75a0
[    11.934] (II) Module ABI versions:
[    11.934] 	X.Org ANSI C Emulation: 0.4
[    11.934] 	X.Org Video Driver: 11.0
[    11.934] 	X.Org XInput driver : 16.0
[    11.934] 	X.Org Server Extension : 6.0
[    11.935] (--) PCI:*(0:1:0:0) 10de:100a:3842:2883 rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x0000d800/128, BIOS @ 0x????????/524288
[    11.935] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.935] (II) LoadModule: "extmod"
[    11.973] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.973] (II) Module extmod: vendor="X.Org Foundation"
[    11.973] 	compiled for 1.11.3, module version = 1.0.0
[    11.973] 	Module class: X.Org Server Extension
[    11.973] 	ABI class: X.Org Server Extension, version 6.0
[    11.973] (II) Loading extension MIT-SCREEN-SAVER
[    11.973] (II) Loading extension XFree86-VidModeExtension
[    11.973] (II) Loading extension XFree86-DGA
[    11.973] (II) Loading extension DPMS
[    11.973] (II) Loading extension XVideo
[    11.973] (II) Loading extension XVideo-MotionCompensation
[    11.973] (II) Loading extension X-Resource
[    11.973] (II) LoadModule: "dbe"
[    11.973] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.973] (II) Module dbe: vendor="X.Org Foundation"
[    11.973] 	compiled for 1.11.3, module version = 1.0.0
[    11.973] 	Module class: X.Org Server Extension
[    11.973] 	ABI class: X.Org Server Extension, version 6.0
[    11.973] (II) Loading extension DOUBLE-BUFFER
[    11.973] (II) LoadModule: "glx"
[    11.973] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    13.255] (II) Module glx: vendor="NVIDIA Corporation"
[    13.255] 	compiled for 4.0.2, module version = 1.0.0
[    13.255] 	Module class: X.Org Server Extension
[    13.255] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:13:45 PDT 2013
[    13.255] (II) Loading extension GLX
[    13.255] (II) LoadModule: "record"
[    13.255] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.255] (II) Module record: vendor="X.Org Foundation"
[    13.255] 	compiled for 1.11.3, module version = 1.13.0
[    13.255] 	Module class: X.Org Server Extension
[    13.255] 	ABI class: X.Org Server Extension, version 6.0
[    13.255] (II) Loading extension RECORD
[    13.255] (II) LoadModule: "dri"
[    13.255] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.256] (II) Module dri: vendor="X.Org Foundation"
[    13.256] 	compiled for 1.11.3, module version = 1.0.0
[    13.256] 	ABI class: X.Org Server Extension, version 6.0
[    13.256] (II) Loading extension XFree86-DRI
[    13.256] (II) LoadModule: "dri2"
[    13.256] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.256] (II) Module dri2: vendor="X.Org Foundation"
[    13.256] 	compiled for 1.11.3, module version = 1.2.0
[    13.256] 	ABI class: X.Org Server Extension, version 6.0
[    13.256] (II) Loading extension DRI2
[    13.256] (II) LoadModule: "nvidia"
[    13.256] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    13.284] (II) Module nvidia: vendor="NVIDIA Corporation"
[    13.284] 	compiled for 4.0.2, module version = 1.0.0
[    13.284] 	Module class: X.Org Video Driver
[    13.286] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 13:52:27 PDT 2013
[    13.286] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    13.286] (++) using VT number 7

[    13.287] (II) Loading sub module "fb"
[    13.287] (II) LoadModule: "fb"
[    13.321] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.321] (II) Module fb: vendor="X.Org Foundation"
[    13.321] 	compiled for 1.11.3, module version = 1.0.0
[    13.321] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.321] (II) Loading sub module "wfb"
[    13.321] (II) LoadModule: "wfb"
[    13.321] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    13.321] (II) Module wfb: vendor="X.Org Foundation"
[    13.321] 	compiled for 1.11.3, module version = 1.0.0
[    13.321] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.321] (II) Loading sub module "shadow"
[    13.321] (II) LoadModule: "shadow"
[    13.321] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    13.321] (II) Module shadow: vendor="X.Org Foundation"
[    13.321] 	compiled for 1.11.3, module version = 1.1.0
[    13.321] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.321] (II) Loading sub module "ramdac"
[    13.321] (II) LoadModule: "ramdac"
[    13.322] (II) Module "ramdac" already built-in
[    13.322] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    13.322] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    13.322] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    13.322] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.322] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    13.322] (==) NVIDIA(0): RGB weight 888
[    13.322] (==) NVIDIA(0): Default visual is TrueColor
[    13.322] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.323] (**) NVIDIA(0): Enabling 2D acceleration
[    13.784] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[    13.784] (EE) NVIDIA(0):     check your system's kernel log for additional error
[    13.784] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[    13.784] (EE) NVIDIA(0):     README for additional information.
[    13.784] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    13.784] (EE) NVIDIA(0): Failing initialization of X screen 0
[    13.784] (II) UnloadModule: "nvidia"
[    13.784] (II) Unloading nvidia
[    13.784] (II) UnloadModule: "shadow"
[    13.784] (II) Unloading shadow
[    13.784] (II) UnloadModule: "wfb"
[    13.784] (II) Unloading wfb
[    13.784] (II) UnloadModule: "fb"
[    13.784] (II) Unloading fb
[    13.784] (EE) Screen(s) found, but none have a usable configuration.
[    13.784] 
Fatal server error:
[    13.784] no screens found
[    13.784] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    13.784] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    13.784] 
[    13.785]  ddxSigGiveUp: Closing log
[    13.785] Server terminated with error (1). Closing log file.
```

---

### Post by Yellow Pasque on 2014-01-12
The problem is that the nvidia and nvidia-updates drivers found in the Ubuntu 12.04.x repo are not new enough to support a GTX780**Ti**
You need to be running 319.82

This should clean up your system:
```
sudo update-pciids
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge nvidia*
```

I don't see any pre-made packages of 319.82 in the usual placse, so you may have to install manually. Just make sure you have dkms installed before you do i.
```
sudo apt-get install dkms
```

[http://www.nvidia.com/download/driverResults.aspx/72229/en-us](http://www.nvidia.com/download/driverResults.aspx/72229/en-us)

---

### Post by sean.d.matthews on 2014-01-12
Had to do 319.76 driver because I'm on 32bit. I had tried this driver before, and then tried the 319.32 to see if I could foster any change. I reinstalled 319.76 and posted xorg.0.log output below.

```

/var/log/Xorg.0.log
[    11.906] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    11.906] X Protocol Version 11, Revision 0
[    11.906] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    11.906] Current Operating System: Linux warband-A780LM-M2 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686
[    11.906] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic-pae root=UUID=dfcc3559-db80-440f-9daf-776dd948a5ea ro quiet splash vt.handoff=7
[    11.906] Build Date: 16 October 2013  04:45:22PM
[    11.906] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    11.906] Current version of pixman: 0.30.2
[    11.906] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.906] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.906] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 12 18:47:52 2014
[    11.906] (==) Using config file: "/etc/X11/xorg.conf"
[    11.906] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.906] (==) ServerLayout "Layout0"
[    11.906] (**) |-->Screen "Screen0" (0)
[    11.906] (**) |   |-->Monitor "Monitor0"
[    11.906] (**) |   |-->Device "Device0"
[    11.906] (**) |-->Input Device "Keyboard0"
[    11.906] (**) |-->Input Device "Mouse0"
[    11.906] (==) Automatically adding devices
[    11.906] (==) Automatically enabling devices
[    11.931] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.931] 	Entry deleted from font path.
[    11.931] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.931] 	Entry deleted from font path.
[    11.931] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.931] 	Entry deleted from font path.
[    11.931] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.931] 	Entry deleted from font path.
[    11.931] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.931] 	Entry deleted from font path.
[    11.931] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    11.931] 	Entry deleted from font path.
[    11.931] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    11.931] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.931] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    11.931] (WW) Disabling Keyboard0
[    11.931] (WW) Disabling Mouse0
[    11.931] (II) Loader magic: 0xb774a5a0
[    11.931] (II) Module ABI versions:
[    11.931] 	X.Org ANSI C Emulation: 0.4
[    11.931] 	X.Org Video Driver: 11.0
[    11.931] 	X.Org XInput driver : 16.0
[    11.931] 	X.Org Server Extension : 6.0
[    11.932] (--) PCI:*(0:1:0:0) 10de:100a:3842:2883 rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x0000d800/128, BIOS @ 0x????????/524288
[    11.932] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.932] (II) LoadModule: "extmod"
[    11.946] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.946] (II) Module extmod: vendor="X.Org Foundation"
[    11.946] 	compiled for 1.11.3, module version = 1.0.0
[    11.946] 	Module class: X.Org Server Extension
[    11.946] 	ABI class: X.Org Server Extension, version 6.0
[    11.946] (II) Loading extension MIT-SCREEN-SAVER
[    11.946] (II) Loading extension XFree86-VidModeExtension
[    11.946] (II) Loading extension XFree86-DGA
[    11.947] (II) Loading extension DPMS
[    11.947] (II) Loading extension XVideo
[    11.947] (II) Loading extension XVideo-MotionCompensation
[    11.947] (II) Loading extension X-Resource
[    11.947] (II) LoadModule: "dbe"
[    11.947] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.947] (II) Module dbe: vendor="X.Org Foundation"
[    11.947] 	compiled for 1.11.3, module version = 1.0.0
[    11.947] 	Module class: X.Org Server Extension
[    11.947] 	ABI class: X.Org Server Extension, version 6.0
[    11.947] (II) Loading extension DOUBLE-BUFFER
[    11.947] (II) LoadModule: "glx"
[    11.947] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.974] (II) Module glx: vendor="NVIDIA Corporation"
[    11.974] 	compiled for 4.0.2, module version = 1.0.0
[    11.974] 	Module class: X.Org Server Extension
[    11.974] (II) NVIDIA GLX Module  319.76  Fri Nov 22 13:30:10 PST 2013
[    11.974] (II) Loading extension GLX
[    11.974] (II) LoadModule: "record"
[    11.974] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.974] (II) Module record: vendor="X.Org Foundation"
[    11.974] 	compiled for 1.11.3, module version = 1.13.0
[    11.974] 	Module class: X.Org Server Extension
[    11.974] 	ABI class: X.Org Server Extension, version 6.0
[    11.974] (II) Loading extension RECORD
[    11.974] (II) LoadModule: "dri"
[    11.975] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.975] (II) Module dri: vendor="X.Org Foundation"
[    11.975] 	compiled for 1.11.3, module version = 1.0.0
[    11.975] 	ABI class: X.Org Server Extension, version 6.0
[    11.975] (II) Loading extension XFree86-DRI
[    11.975] (II) LoadModule: "dri2"
[    11.975] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.975] (II) Module dri2: vendor="X.Org Foundation"
[    11.975] 	compiled for 1.11.3, module version = 1.2.0
[    11.975] 	ABI class: X.Org Server Extension, version 6.0
[    11.975] (II) Loading extension DRI2
[    11.975] (II) LoadModule: "nvidia"
[    11.975] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    11.975] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.975] 	compiled for 4.0.2, module version = 1.0.0
[    11.975] 	Module class: X.Org Video Driver
[    11.975] (II) NVIDIA dlloader X Driver  319.76  Fri Nov 22 13:09:52 PST 2013
[    11.975] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.975] (++) using VT number 7

[    11.976] (II) Loading sub module "fb"
[    11.976] (II) LoadModule: "fb"
[    11.998] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.998] (II) Module fb: vendor="X.Org Foundation"
[    11.998] 	compiled for 1.11.3, module version = 1.0.0
[    11.998] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.998] (II) Loading sub module "wfb"
[    11.998] (II) LoadModule: "wfb"
[    11.999] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.999] (II) Module wfb: vendor="X.Org Foundation"
[    11.999] 	compiled for 1.11.3, module version = 1.0.0
[    11.999] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.999] (II) Loading sub module "shadow"
[    11.999] (II) LoadModule: "shadow"
[    11.999] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    11.999] (II) Module shadow: vendor="X.Org Foundation"
[    11.999] 	compiled for 1.11.3, module version = 1.1.0
[    11.999] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.999] (II) Loading sub module "ramdac"
[    11.999] (II) LoadModule: "ramdac"
[    11.999] (II) Module "ramdac" already built-in
[    11.999] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    11.999] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    11.999] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.999] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.999] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    11.999] (==) NVIDIA(0): RGB weight 888
[    11.999] (==) NVIDIA(0): Default visual is TrueColor
[    11.999] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.999] (**) NVIDIA(0): Enabling 2D acceleration
[    13.005] drmOpenDevice: node name is /dev/dri/card0
[    13.010] drmOpenByBusid: Searching for BusID PCI:1:0:0
[    13.010] drmOpenDevice: node name is /dev/dri/card0
[    13.015] drmOpenByBusid: drmOpenMinor returns -1
[    13.015] drmOpenDevice: node name is /dev/dri/card1
[    13.020] drmOpenByBusid: drmOpenMinor returns -1
[    13.020] drmOpenDevice: node name is /dev/dri/card2
[    13.025] drmOpenByBusid: drmOpenMinor returns -1
[    13.025] drmOpenDevice: node name is /dev/dri/card3
[    13.030] drmOpenByBusid: drmOpenMinor returns -1
[    13.030] drmOpenDevice: node name is /dev/dri/card4
[    13.035] drmOpenByBusid: drmOpenMinor returns -1
[    13.035] drmOpenDevice: node name is /dev/dri/card5
[    13.040] drmOpenByBusid: drmOpenMinor returns -1
[    13.040] drmOpenDevice: node name is /dev/dri/card6
[    13.045] drmOpenByBusid: drmOpenMinor returns -1
[    13.045] drmOpenDevice: node name is /dev/dri/card7
[    13.049] drmOpenByBusid: drmOpenMinor returns -1
[    13.049] drmOpenDevice: node name is /dev/dri/card8
[    13.054] drmOpenByBusid: drmOpenMinor returns -1
[    13.054] drmOpenDevice: node name is /dev/dri/card9
[    13.059] drmOpenByBusid: drmOpenMinor returns -1
[    13.059] drmOpenDevice: node name is /dev/dri/card10
[    13.064] drmOpenByBusid: drmOpenMinor returns -1
[    13.064] drmOpenDevice: node name is /dev/dri/card11
[    13.069] drmOpenByBusid: drmOpenMinor returns -1
[    13.069] drmOpenDevice: node name is /dev/dri/card12
[    13.074] drmOpenByBusid: drmOpenMinor returns -1
[    13.074] drmOpenDevice: node name is /dev/dri/card13
[    13.079] drmOpenByBusid: drmOpenMinor returns -1
[    13.079] drmOpenDevice: node name is /dev/dri/card14
[    13.084] drmOpenByBusid: drmOpenMinor returns -1
[    13.084] drmOpenDevice: node name is /dev/dri/card15
[    13.089] drmOpenByBusid: drmOpenMinor returns -1
[    13.104] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 780 Ti (GK110B) at PCI:1:0:0 (GPU-0)
[    13.104] (--) NVIDIA(0): Memory: 3145728 kBytes
[    13.104] (--) NVIDIA(0): VideoBIOS: 80.80.30.00.80
[    13.104] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    13.106] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 780 Ti at PCI:1:0:0
[    13.106] (--) NVIDIA(0):     CRT-0
[    13.106] (--) NVIDIA(0):     DFP-0 (boot)
[    13.106] (--) NVIDIA(0):     DFP-1
[    13.106] (--) NVIDIA(0):     DFP-2
[    13.106] (--) NVIDIA(0):     DFP-3
[    13.106] (--) NVIDIA(0):     DFP-4
[    13.106] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    13.106] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    13.106] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    13.106] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    13.106] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    13.106] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[    13.106] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[    13.106] (--) NVIDIA(0): DFP-3: 330.0 MHz maximum pixel clock
[    13.106] (--) NVIDIA(0): DFP-3: Internal Single Link TMDS
[    13.106] (--) NVIDIA(0): DFP-4: 960.0 MHz maximum pixel clock
[    13.106] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    13.106] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0
[    13.139] (EE) NVIDIA(0): Failing initialization of X screen 0
[    13.373] (II) UnloadModule: "nvidia"
[    13.373] (II) Unloading nvidia
[    13.373] (II) UnloadModule: "shadow"
[    13.373] (II) Unloading shadow
[    13.373] (II) UnloadModule: "wfb"
[    13.373] (II) Unloading wfb
[    13.373] (II) UnloadModule: "fb"
[    13.373] (II) Unloading fb
[    13.373] (EE) Screen(s) found, but none have a usable configuration.
[    13.373] 
Fatal server error:
[    13.373] no screens found
[    13.373] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    13.373] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    13.373] 
[    13.374]  ddxSigGiveUp: Closing log
[    13.375] Server terminated with error (1). Closing log file.

```

---

### Post by sean.d.matthews on 2014-01-12
Ok. I added a line to my xorg config:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "UseDisplayDevice" "none"
EndSection

```

and that seems to get rid of the log file errors:
```

/var/log/Xorg.0.log
[    11.403] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    11.403] X Protocol Version 11, Revision 0
[    11.403] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    11.403] Current Operating System: Linux warband-A780LM-M2 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686
[    11.403] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic-pae root=UUID=dfcc3559-db80-440f-9daf-776dd948a5ea ro quiet splash vt.handoff=7
[    11.403] Build Date: 16 October 2013  04:45:22PM
[    11.403] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[    11.403] Current version of pixman: 0.30.2
[    11.403] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.403] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.403] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 12 19:46:21 2014
[    11.403] (==) Using config file: "/etc/X11/xorg.conf"
[    11.403] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.403] (==) ServerLayout "Layout0"
[    11.403] (**) |-->Screen "Screen0" (0)
[    11.403] (**) |   |-->Monitor "Monitor0"
[    11.403] (**) |   |-->Device "Device0"
[    11.403] (**) |-->Input Device "Keyboard0"
[    11.403] (**) |-->Input Device "Mouse0"
[    11.403] (==) Automatically adding devices
[    11.403] (==) Automatically enabling devices
[    11.445] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.445] 	Entry deleted from font path.
[    11.445] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.445] 	Entry deleted from font path.
[    11.445] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.445] 	Entry deleted from font path.
[    11.453] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.453] 	Entry deleted from font path.
[    11.453] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.453] 	Entry deleted from font path.
[    11.453] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    11.453] 	Entry deleted from font path.
[    11.453] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    11.453] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.453] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    11.453] (WW) Disabling Keyboard0
[    11.453] (WW) Disabling Mouse0
[    11.453] (II) Loader magic: 0xb779e5a0
[    11.453] (II) Module ABI versions:
[    11.453] 	X.Org ANSI C Emulation: 0.4
[    11.453] 	X.Org Video Driver: 11.0
[    11.453] 	X.Org XInput driver : 16.0
[    11.453] 	X.Org Server Extension : 6.0
[    11.453] (--) PCI:*(0:1:0:0) 10de:100a:3842:2883 rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x0000d800/128, BIOS @ 0x????????/524288
[    11.454] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.454] (II) LoadModule: "extmod"
[    11.489] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.489] (II) Module extmod: vendor="X.Org Foundation"
[    11.489] 	compiled for 1.11.3, module version = 1.0.0
[    11.489] 	Module class: X.Org Server Extension
[    11.489] 	ABI class: X.Org Server Extension, version 6.0
[    11.489] (II) Loading extension MIT-SCREEN-SAVER
[    11.489] (II) Loading extension XFree86-VidModeExtension
[    11.489] (II) Loading extension XFree86-DGA
[    11.489] (II) Loading extension DPMS
[    11.489] (II) Loading extension XVideo
[    11.489] (II) Loading extension XVideo-MotionCompensation
[    11.489] (II) Loading extension X-Resource
[    11.489] (II) LoadModule: "dbe"
[    11.489] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.489] (II) Module dbe: vendor="X.Org Foundation"
[    11.489] 	compiled for 1.11.3, module version = 1.0.0
[    11.489] 	Module class: X.Org Server Extension
[    11.489] 	ABI class: X.Org Server Extension, version 6.0
[    11.489] (II) Loading extension DOUBLE-BUFFER
[    11.489] (II) LoadModule: "glx"
[    11.489] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.509] (II) Module glx: vendor="NVIDIA Corporation"
[    11.509] 	compiled for 4.0.2, module version = 1.0.0
[    11.509] 	Module class: X.Org Server Extension
[    11.509] (II) NVIDIA GLX Module  319.76  Fri Nov 22 13:30:10 PST 2013
[    11.509] (II) Loading extension GLX
[    11.510] (II) LoadModule: "record"
[    11.510] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.510] (II) Module record: vendor="X.Org Foundation"
[    11.510] 	compiled for 1.11.3, module version = 1.13.0
[    11.510] 	Module class: X.Org Server Extension
[    11.510] 	ABI class: X.Org Server Extension, version 6.0
[    11.510] (II) Loading extension RECORD
[    11.510] (II) LoadModule: "dri"
[    11.510] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.510] (II) Module dri: vendor="X.Org Foundation"
[    11.510] 	compiled for 1.11.3, module version = 1.0.0
[    11.510] 	ABI class: X.Org Server Extension, version 6.0
[    11.510] (II) Loading extension XFree86-DRI
[    11.510] (II) LoadModule: "dri2"
[    11.510] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.510] (II) Module dri2: vendor="X.Org Foundation"
[    11.510] 	compiled for 1.11.3, module version = 1.2.0
[    11.510] 	ABI class: X.Org Server Extension, version 6.0
[    11.510] (II) Loading extension DRI2
[    11.510] (II) LoadModule: "nvidia"
[    11.510] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    11.511] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.511] 	compiled for 4.0.2, module version = 1.0.0
[    11.511] 	Module class: X.Org Video Driver
[    11.511] (II) NVIDIA dlloader X Driver  319.76  Fri Nov 22 13:09:52 PST 2013
[    11.511] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.511] (++) using VT number 7

[    11.511] (II) Loading sub module "fb"
[    11.511] (II) LoadModule: "fb"
[    11.532] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.532] (II) Module fb: vendor="X.Org Foundation"
[    11.532] 	compiled for 1.11.3, module version = 1.0.0
[    11.532] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.532] (II) Loading sub module "wfb"
[    11.532] (II) LoadModule: "wfb"
[    11.532] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.532] (II) Module wfb: vendor="X.Org Foundation"
[    11.533] 	compiled for 1.11.3, module version = 1.0.0
[    11.533] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.533] (II) Loading sub module "shadow"
[    11.533] (II) LoadModule: "shadow"
[    11.533] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    11.533] (II) Module shadow: vendor="X.Org Foundation"
[    11.533] 	compiled for 1.11.3, module version = 1.1.0
[    11.533] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    11.533] (II) Loading sub module "ramdac"
[    11.533] (II) LoadModule: "ramdac"
[    11.533] (II) Module "ramdac" already built-in
[    11.533] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    11.533] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    11.533] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    11.533] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.533] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    11.533] (==) NVIDIA(0): RGB weight 888
[    11.533] (==) NVIDIA(0): Default visual is TrueColor
[    11.533] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.533] (**) NVIDIA(0): Option "UseDisplayDevice" "none"
[    11.533] (**) NVIDIA(0): Enabling 2D acceleration
[    11.533] (**) NVIDIA(0): Option "UseDisplayDevice" set to "none"; enabling NoScanout
[    11.533] (**) NVIDIA(0):     mode
[    12.487] drmOpenDevice: node name is /dev/dri/card0
[    12.492] drmOpenByBusid: Searching for BusID PCI:1:0:0
[    12.492] drmOpenDevice: node name is /dev/dri/card0
[    12.497] drmOpenByBusid: drmOpenMinor returns -1
[    12.497] drmOpenDevice: node name is /dev/dri/card1
[    12.502] drmOpenByBusid: drmOpenMinor returns -1
[    12.502] drmOpenDevice: node name is /dev/dri/card2
[    12.507] drmOpenByBusid: drmOpenMinor returns -1
[    12.507] drmOpenDevice: node name is /dev/dri/card3
[    12.511] drmOpenByBusid: drmOpenMinor returns -1
[    12.512] drmOpenDevice: node name is /dev/dri/card4
[    12.516] drmOpenByBusid: drmOpenMinor returns -1
[    12.516] drmOpenDevice: node name is /dev/dri/card5
[    12.521] drmOpenByBusid: drmOpenMinor returns -1
[    12.521] drmOpenDevice: node name is /dev/dri/card6
[    12.526] drmOpenByBusid: drmOpenMinor returns -1
[    12.526] drmOpenDevice: node name is /dev/dri/card7
[    12.531] drmOpenByBusid: drmOpenMinor returns -1
[    12.531] drmOpenDevice: node name is /dev/dri/card8
[    12.536] drmOpenByBusid: drmOpenMinor returns -1
[    12.536] drmOpenDevice: node name is /dev/dri/card9
[    12.541] drmOpenByBusid: drmOpenMinor returns -1
[    12.541] drmOpenDevice: node name is /dev/dri/card10
[    12.546] drmOpenByBusid: drmOpenMinor returns -1
[    12.546] drmOpenDevice: node name is /dev/dri/card11
[    12.551] drmOpenByBusid: drmOpenMinor returns -1
[    12.551] drmOpenDevice: node name is /dev/dri/card12
[    12.556] drmOpenByBusid: drmOpenMinor returns -1
[    12.556] drmOpenDevice: node name is /dev/dri/card13
[    12.560] drmOpenByBusid: drmOpenMinor returns -1
[    12.560] drmOpenDevice: node name is /dev/dri/card14
[    12.565] drmOpenByBusid: drmOpenMinor returns -1
[    12.565] drmOpenDevice: node name is /dev/dri/card15
[    12.570] drmOpenByBusid: drmOpenMinor returns -1
[    12.585] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 780 Ti (GK110B) at PCI:1:0:0 (GPU-0)
[    12.585] (--) NVIDIA(0): Memory: 3145728 kBytes
[    12.585] (--) NVIDIA(0): VideoBIOS: 80.80.30.00.80
[    12.585] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    12.585] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 780 Ti at PCI:1:0:0
[    12.585] (--) NVIDIA(0):     CRT-0
[    12.585] (--) NVIDIA(0):     DFP-0 (boot)
[    12.585] (--) NVIDIA(0):     DFP-1
[    12.585] (--) NVIDIA(0):     DFP-2
[    12.585] (--) NVIDIA(0):     DFP-3
[    12.585] (--) NVIDIA(0):     DFP-4
[    12.585] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    12.585] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    12.585] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    12.585] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    12.585] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    12.585] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[    12.585] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[    12.585] (--) NVIDIA(0): DFP-3: 330.0 MHz maximum pixel clock
[    12.585] (--) NVIDIA(0): DFP-3: Internal Single Link TMDS
[    12.585] (--) NVIDIA(0): DFP-4: 960.0 MHz maximum pixel clock
[    12.585] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[    12.585] (II) NVIDIA(0): Validated MetaModes:
[    12.585] (II) NVIDIA(0):     "nvidia-auto-select"
[    12.585] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    12.585] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    12.585] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    12.604] (--) Depth 24 pixmap format is 32 bpp
[    12.604] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[    12.604] (II) NVIDIA:     access.
[    12.606] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    12.609] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    12.609] (II) Loading extension NV-GLX
[    12.669] (==) NVIDIA(0): Disabling shared memory pixmaps
[    12.669] (==) NVIDIA(0): Backing store disabled
[    12.669] (==) NVIDIA(0): Silken mouse enabled
[    12.669] (**) NVIDIA(0): DPMS enabled
[    12.669] (II) Loading extension NV-CONTROL
[    12.669] (II) Loading sub module "dri2"
[    12.669] (II) LoadModule: "dri2"
[    12.670] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.670] (II) Module dri2: vendor="X.Org Foundation"
[    12.670] 	compiled for 1.11.3, module version = 1.2.0
[    12.670] 	ABI class: X.Org Server Extension, version 6.0
[    12.670] (II) NVIDIA(0): [DRI2] Setup complete
[    12.670] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    12.670] (--) RandR disabled
[    12.670] (II) Initializing built-in extension Generic Event Extension
[    12.670] (II) Initializing built-in extension SHAPE
[    12.670] (II) Initializing built-in extension MIT-SHM
[    12.670] (II) Initializing built-in extension XInputExtension
[    12.670] (II) Initializing built-in extension XTEST
[    12.670] (II) Initializing built-in extension BIG-REQUESTS
[    12.670] (II) Initializing built-in extension SYNC
[    12.670] (II) Initializing built-in extension XKEYBOARD
[    12.670] (II) Initializing built-in extension XC-MISC
[    12.670] (II) Initializing built-in extension SECURITY
[    12.670] (II) Initializing built-in extension XINERAMA
[    12.670] (II) Initializing built-in extension XFIXES
[    12.670] (II) Initializing built-in extension RENDER
[    12.670] (II) Initializing built-in extension RANDR
[    12.670] (II) Initializing built-in extension COMPOSITE
[    12.670] (II) Initializing built-in extension DAMAGE
[    12.671] (II) Initializing extension GLX
[    12.794] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.805] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.805] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.805] (II) LoadModule: "evdev"
[    12.805] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.834] (II) Module evdev: vendor="X.Org Foundation"
[    12.834] 	compiled for 1.11.3, module version = 2.7.0
[    12.834] 	Module class: X.Org XInput Driver
[    12.834] 	ABI class: X.Org XInput driver, version 16.0
[    12.834] (II) Using input driver 'evdev' for 'Power Button'
[    12.834] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.834] (**) Power Button: always reports core events
[    12.834] (**) evdev: Power Button: Device: "/dev/input/event1"
[    12.834] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.834] (--) evdev: Power Button: Found keys
[    12.834] (II) evdev: Power Button: Configuring as keyboard
[    12.834] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    12.834] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    12.834] (**) Option "xkb_rules" "evdev"
[    12.834] (**) Option "xkb_model" "pc105"
[    12.834] (**) Option "xkb_layout" "us"
[    12.834] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    12.834] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.834] (II) Using input driver 'evdev' for 'Power Button'
[    12.834] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.834] (**) Power Button: always reports core events
[    12.834] (**) evdev: Power Button: Device: "/dev/input/event0"
[    12.834] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.834] (--) evdev: Power Button: Found keys
[    12.834] (II) evdev: Power Button: Configuring as keyboard
[    12.834] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    12.834] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    12.834] (**) Option "xkb_rules" "evdev"
[    12.834] (**) Option "xkb_model" "pc105"
[    12.834] (**) Option "xkb_layout" "us"
[    12.835] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event10)
[    12.835] (II) No input driver specified, ignoring this device.
[    12.835] (II) This device may have been added with another device file.
[    12.835] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event7)
[    12.835] (II) No input driver specified, ignoring this device.
[    12.835] (II) This device may have been added with another device file.
[    12.835] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event8)
[    12.835] (II) No input driver specified, ignoring this device.
[    12.835] (II) This device may have been added with another device file.
[    12.835] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event9)
[    12.835] (II) No input driver specified, ignoring this device.
[    12.835] (II) This device may have been added with another device file.
[    12.835] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event2)
[    12.835] (II) No input driver specified, ignoring this device.
[    12.835] (II) This device may have been added with another device file.
[    12.836] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event3)
[    12.836] (II) No input driver specified, ignoring this device.
[    12.836] (II) This device may have been added with another device file.
[    12.836] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event4)
[    12.836] (II) No input driver specified, ignoring this device.
[    12.836] (II) This device may have been added with another device file.
[    12.836] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event5)
[    12.836] (II) No input driver specified, ignoring this device.
[    12.836] (II) This device may have been added with another device file.
[    12.836] (II) config/udev: Adding input device HDA ATI SB Line-Out (/dev/input/event6)
[    12.836] (II) No input driver specified, ignoring this device.
[    12.836] (II) This device may have been added with another device file.
[    37.076] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm

```

However, nvidia-settings still tells me, "You do not appear to be using the NVIDIA X driver." Sigh.

---

