---
title: "black screen on logout after upgrade to ibex"
date: 2008-11-03
forum: General Help
---

### Post by tich on 2008-11-03
i recently updated my thinkpad t61 (with nvidia) to ibex and everything has gone pretty smoothly except for a couple things...

for some reason when i log out to the GDM login i get dropped into a black screen with no options except to reboot.
switching users (either to the new Guest user or to any other user on the computer) works fine and i don't have any problems switching back.

before everything freezes and the screen goes black i get a message on the screen... i will attempt to logout again and post the message shortly!

the last things that pop up on the screen are: 
starting system tools backend
starting anac(h)ronistic cron anacron
starting defered execution scheduler atd
starting periodic command scheduler crond
checking battery state
starting timidity ++ alsa midi emulation

then, after i alt+ctrl+bksp'ed about 4 times to get out of the black screen a window popped up with this:
ubuntu is running in low graphics mode
your screen, graphics card, and input device settings could not be detected correctly.
you will need to configure them yourself.

it gave me the option to view a few logs so i attached the info here:
0.log:

16356 11711
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux bradley-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Mon Nov  3 14:52:16 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xd1000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) No input driver/identifier specified (ignoring)
(EE) config/hal: NewInputDeviceRequest failed
16356 11711


and Xorg.0.log:


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux bradley-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  3 14:51:39 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation Quadro NVS 140M rev 161, Mem @ 0xd2000000/16777216, 0xe0000000/268435456, 0xd0000000/33554432, I/O @ 0x00002000/128
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:09:29 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:50:00 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro NVS 140M (G86GL) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.3e.00.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 140M at PCI:1:0:0:
(--) NVIDIA(0):     LEN (DFP-0)
(--) NVIDIA(0): LEN (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LEN (DFP-0): Internal Dual Link LVDS
(WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1440x900"
(WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
(WW) NVIDIA(0):     HorizSync range (46.301-55.556 kHz) would exclude this
(WW) NVIDIA(0):     mode's HorizSync (37.0 kHz); ignoring HorizSync check for
(WW) NVIDIA(0):     mode "1440x900".
(WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1440x900"
(WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
(WW) NVIDIA(0):     VertRefresh range (50.000-60.000 Hz) would exclude this
(WW) NVIDIA(0):     mode's VertRefresh (40.0 Hz); ignoring VertRefresh check
(WW) NVIDIA(0):     for mode "1440x900".
(WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1440x900"
(WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
(WW) NVIDIA(0):     HorizSync range (46.301-55.556 kHz) would exclude this
(WW) NVIDIA(0):     mode's HorizSync (37.0 kHz); ignoring HorizSync check for
(WW) NVIDIA(0):     mode "1440x900".
(WW) NVIDIA(0): The EDID for LEN (DFP-0) contradicts itself: mode "1440x900"
(WW) NVIDIA(0):     is specified in the EDID; however, the EDID's valid
(WW) NVIDIA(0):     VertRefresh range (50.000-60.000 Hz) would exclude this
(WW) NVIDIA(0):     mode's VertRefresh (40.0 Hz); ignoring VertRefresh check
(WW) NVIDIA(0):     for mode "1440x900".
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (121, 120); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX

hopefully this means something to someone!!

---

### Post by JeppeM on 2008-11-03
i am having this issue as well... I havent tested the switching users part, but normal reboot and shutdown seems to work, but logout gives me the above error... I'm on a thinkpad R61 btw, if that makes any difference...

I also noticed that after a hardreset of the system (i never get out of the low-graphics dialog boxes), Compiz isn't fireing up due to the wrong hardware driver for my graphics card being selected (it's neither the 177 or 173 - when i highlight the 177, it says that a different version is selected...) Once i select the 177 driver again, everything goes back yo normal, until next time i try to logout...

Any help would be cool :D

---

### Post by jimmy the saint on 2008-11-03
use 173.  solved the same problem for me.

---

### Post by tich on 2008-11-04
that seems to be working okay.  the 173 driver gets me to the login screen and from there everything works fine.

it is a bit glitchy but it has never really looked particularly smooth and i think it is unfortunate that we can't use the shiney new (and recommended) driver; hopefully soon.

---

### Post by JeppeM on 2008-11-04
This is reported on launchpad here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/258357](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/258357)

the reply from SiLeNcE about 50 minutes ago says that it was fixed when he upgraded today, but with my fully updated system it looks like it's still there.

Note that jeonix in that bug report has a workaround which lets you use the 177 driver without it totally crashing... to do this, you have to edit /etc/gdm/gdm.conf and change GdmXserverTimeout from 10 to 40 or 60, 40 should be enough... Apparently, nvidia has been made aware of the bug as well, so waiting for them to respond i think :)

Run this command to edit gdm.conf

```
gksudo gedit /etc/gdm/gdm.conf
```

And then find GdmXserverTimeout and change it to 40 or 60... I think that gnome needs to be restarted for it to take affect, but to be sure, i did a full reboot and it seems to work for me...

---

### Post by jimdb on 2008-11-05
I am also having a black screen on logout problem, but with SiS graphics hardware on my Acer 5000 laptop. I found a handful of threads regarding nVidia problems and possible fixes, but nothing seems to apply to my bug. I tried changing the GdmXserverTimeout, shutting down the network before logging out and disabling the splash screens, as suggested in other threads.

I haven't found anything relevant in the logs yet.

To summarize, only logout goes black. Suspend, hibernate, restart and shutdown work as expected.

Jim

---

### Post by rowan on 2008-11-07
Just confirmation really, I was seeing this problem on the **177** version of the Nvidia drivers. I tried setting "GdmXserverTimeout = 60", but that did not work. Downgrading the Nvidia drivers to **173** has solved the problem.

---

### Post by hstenzel on 2008-12-19
Another voice in the chorus:  I also had this problem -- hang on logout or gdm restart on a Lenovo T61p with nVidia Corporation Quadro FX 570M.

I had problems with version 177 of the NVIDIA accellerated graphics driver, and success with version 173.

---

