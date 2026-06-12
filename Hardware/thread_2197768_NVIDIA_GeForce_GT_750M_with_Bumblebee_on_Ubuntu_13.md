---
title: "NVIDIA GeForce GT 750M with Bumblebee on Ubuntu 13.10 giving error"
date: 2014-01-05
forum: Hardware
---

### Post by db579 on 2014-01-05
[COLOR=#333333][FONT=UbuntuRegular]I have an Acer Aspire V7 running Ubuntu 13.10 with an NVIDIA GeForce GT 750M graphics card. Currently though I'm not using this at all I'm just using the standard Integrated Haswell Graphics. I've tried installing the Bumblebee package by following the instructions [/FONT][/COLOR][here]("https://wiki.ubuntu.com/Bumblebee#Installation")[COLOR=#333333][FONT=UbuntuRegular] but whenever I try to run an application using the NVIDIA card I get the following error message:

[/FONT][/COLOR]```
[FONT=Ubuntu Mono][ 1641.382331] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please[/FONT]
 [FONT=Ubuntu Mono][ 1641.382365] [ERROR]Aborting because fallback start is disabled.[/FONT]
```[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2014-01-05
> Failed to initialize the NVIDIA GPU at PCI:1:0:0

Check lspci. It's possible that your Nvidia card is not actually at that address and you need to manually specify it:
```
sudo update-pciids
lspci
```

---

### Post by db579 on 2014-01-05
Thanks for the response - so I think the relevant line of the lspci output is this:

 ```
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
```

Assuming the first 3 numbers are the pci address that seems correct? Does that mean that I need to manually specify the address and how would I do so?

---

### Post by Yellow Pasque on 2014-01-05
Yes, address is correct. Attempt to use optirun and look at last 10 or so lines of:
```
sudo cat /var/log/messages
```

What version of nvidia driver are you using? As long as you are using 319.17 or later, it should be okay in that regard.

---

### Post by db579 on 2014-01-06
I don't have a messages file at that location. I have a syslog file which contains the following:

```
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (WW) "xmir" is not to be loaded by default. Skipping.Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) NVIDIA(0):     system's kernel log for additional error messages and
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) NVIDIA(0):     consult the NVIDIA README for details.
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) NVIDIA(0):  *** Aborting ***
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) NVIDIA(0): Failing initialization of X screen 0
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) Screen(s) found, but none have a usable configuration.
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) 
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) no screens found(EE) 
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) 
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) Please also check the log file at "/var/log/Xorg.8.log" for additional information.
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) 
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: [XORG] (EE) Server terminated with error (1). Closing log file.
Jan  6 20:12:15 dan-Aspire-V7-482PG bumblebeed[1171]: X did not start properly
```

The Xorg.8.log file it asks me to check contains this:

```
[ 20636.656] (II) Open ACPI successful (/var/run/acpid.socket)
[ 20636.656] Initializing built-in extension Generic Event Extension
[ 20636.656] Initializing built-in extension SHAPE
[ 20636.656] Initializing built-in extension MIT-SHM
[ 20636.656] Initializing built-in extension XInputExtension
[ 20636.656] Initializing built-in extension XTEST
[ 20636.656] Initializing built-in extension BIG-REQUESTS
[ 20636.656] Initializing built-in extension SYNC
[ 20636.656] Initializing built-in extension XKEYBOARD
[ 20636.656] Initializing built-in extension XC-MISC
[ 20636.656] Initializing built-in extension SECURITY
[ 20636.656] Initializing built-in extension XINERAMA
[ 20636.656] Initializing built-in extension XFIXES
[ 20636.656] Initializing built-in extension RENDER
[ 20636.656] Initializing built-in extension RANDR
[ 20636.656] Initializing built-in extension COMPOSITE
[ 20636.656] Initializing built-in extension DAMAGE
[ 20636.656] Initializing built-in extension MIT-SCREEN-SAVER
[ 20636.656] Initializing built-in extension DOUBLE-BUFFER
[ 20636.656] Initializing built-in extension RECORD
[ 20636.656] Initializing built-in extension DPMS
[ 20636.656] Initializing built-in extension X-Resource
[ 20636.656] Initializing built-in extension XVideo
[ 20636.656] Initializing built-in extension XVideo-MotionCompensation
[ 20636.656] Initializing built-in extension SELinux
[ 20636.656] Initializing built-in extension XFree86-VidModeExtension
[ 20636.656] Initializing built-in extension XFree86-DGA
[ 20636.656] Initializing built-in extension XFree86-DRI
[ 20636.656] Initializing built-in extension DRI2
[ 20636.656] (II) "glx" will be loaded by default.
[ 20636.656] (WW) "xmir" is not to be loaded by default. Skipping.
[ 20636.656] (II) LoadModule: "dri2"
[ 20636.656] (II) Module "dri2" already built-in
[ 20636.656] (II) LoadModule: "glamoregl"
[ 20636.656] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[ 20636.665] (II) Module glamoregl: vendor="X.Org Foundation"
[ 20636.665] 	compiled for 1.14.3, module version = 0.5.1
[ 20636.665] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 20636.665] (II) LoadModule: "glx"
[ 20636.665] (II) Loading /usr/lib/nvidia-304/xorg/libglx.so
[ 20636.687] (II) Module glx: vendor="NVIDIA Corporation"
[ 20636.687] 	compiled for 4.0.2, module version = 1.0.0
[ 20636.687] 	Module class: X.Org Server Extension
[ 20636.687] (II) NVIDIA GLX Module  304.116  Mon Oct 28 20:59:08 PDT 2013
[ 20636.687] Loading extension GLX
[ 20636.687] (II) LoadModule: "nvidia"
[ 20636.687] (II) Loading /usr/lib/nvidia-304/xorg/nvidia_drv.so
[ 20636.689] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 20636.689] 	compiled for 4.0.2, module version = 1.0.0
[ 20636.689] 	Module class: X.Org Video Driver
[ 20636.689] (II) LoadModule: "mouse"
[ 20636.690] (II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
[ 20636.690] (II) Module mouse: vendor="X.Org Foundation"
[ 20636.690] 	compiled for 1.14.1, module version = 1.7.2
[ 20636.690] 	Module class: X.Org XInput Driver
[ 20636.690] 	ABI class: X.Org XInput driver, version 19.1
[ 20636.690] (II) LoadModule: "kbd"
[ 20636.690] (WW) Warning, couldn't open module kbd
[ 20636.690] (II) UnloadModule: "kbd"
[ 20636.690] (II) Unloading kbd
[ 20636.690] (EE) Failed to load module "kbd" (module does not exist, 0)
[ 20636.690] (II) NVIDIA dlloader X Driver  304.116  Mon Oct 28 20:40:38 PDT 2013
[ 20636.690] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 20636.690] (--) using VT number 7


[ 20636.690] (II) Loading sub module "fb"
[ 20636.690] (II) LoadModule: "fb"
[ 20636.690] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 20636.691] (II) Module fb: vendor="X.Org Foundation"
[ 20636.691] 	compiled for 1.14.3, module version = 1.0.0
[ 20636.691] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 20636.691] (II) Loading sub module "wfb"
[ 20636.691] (II) LoadModule: "wfb"
[ 20636.691] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 20636.691] (II) Module wfb: vendor="X.Org Foundation"
[ 20636.691] 	compiled for 1.14.3, module version = 1.0.0
[ 20636.691] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 20636.691] (II) Loading sub module "ramdac"
[ 20636.691] (II) LoadModule: "ramdac"
[ 20636.691] (II) Module "ramdac" already built-in
[ 20636.691] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[ 20636.691] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[ 20636.691] (==) NVIDIA(0): RGB weight 888
[ 20636.691] (==) NVIDIA(0): Default visual is TrueColor
[ 20636.691] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 20636.691] (**) NVIDIA(0): Option "NoLogo" "true"
[ 20636.692] (**) NVIDIA(0): Option "ProbeAllGpus" "false"
[ 20636.692] (**) NVIDIA(0): Option "UseEDID" "false"
[ 20636.692] (**) NVIDIA(0): Option "UseDisplayDevice" "none"
[ 20636.692] (**) NVIDIA(0): Enabling 2D acceleration
[ 20636.692] (**) NVIDIA(0): Ignoring EDIDs
[ 20636.692] (**) NVIDIA(0): Option "UseDisplayDevice" set to "none"; enabling NoScanout
[ 20636.692] (**) NVIDIA(0):     mode
[ 20636.692] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[ 20636.692] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[ 20636.692] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[ 20636.692] (EE) NVIDIA(0):  *** Aborting ***
[ 20636.692] (EE) NVIDIA(0): Failing initialization of X screen 0
[ 20636.692] (II) UnloadModule: "nvidia"
[ 20636.692] (II) UnloadSubModule: "wfb"
[ 20636.692] (II) UnloadSubModule: "fb"
[ 20636.692] (EE) Screen(s) found, but none have a usable configuration.
[ 20636.692] (EE) 
Fatal server error:
[ 20636.692] (EE) no screens found(EE) 
[ 20636.692] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[ 20636.692] (EE) Please also check the log file at "/var/log/Xorg.8.log" for additional information.
[ 20636.692] (EE) 
[ 20636.692] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by Yellow Pasque on 2014-01-06
```
[ 20636.687] (II) LoadModule: "nvidia"
[ 20636.687] (II) Loading /usr/lib/nvidia-304/xorg/nvidia_drv.so
[ 20636.689] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 20636.689] 	compiled for 4.0.2, module version = 1.0.0
[ 20636.689] 	Module class: X.Org Video Driver
```

You have an old 304.xx nvidia driver installed (or some remnants thereof) and that is borking things (because 304.xx is not new enough to support your 750m GPU).

---

### Post by lokz2 on 2014-01-25
I have Asus N550JV With Nvidia GT 750M (4GB) and after installing, when I try to run firefox with optirun I get this in terminal:


~$ optirun firefox


(process:2861): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


What is wrong?

---

### Post by Yellow Pasque on 2014-01-26
lokz2, although you have the same GPU/driver, your issue seems much different, especially if it's only firefox giving you issue. I'd recommend starting your own thread.

---

