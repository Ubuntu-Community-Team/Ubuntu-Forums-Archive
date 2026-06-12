---
title: "PCI-Express Device Error, Playing Videos or Visualisations Cause Program to Crash"
date: 2009-02-08
forum: Hardware
---

### Post by blazingpie on 2009-02-08
Hi all,

Looking through /var/log/syslog I see this:

```

Feb  8 19:16:11 desktop kernel: [  119.396948] +------ PCI-Express Device Error ------+
Feb  8 19:16:11 desktop kernel: [  119.396966] Error Severity^I^I: Uncorrected (Non-Fatal)
Feb  8 19:16:11 desktop kernel: [  119.396970] PCIE Bus Error type^I: Transaction Layer
Feb  8 19:16:11 desktop kernel: [  119.396975] Flow Control Protocol ^I: First
Feb  8 19:16:11 desktop kernel: [  119.396980] Receiver ID^I^I: 0010
Feb  8 19:16:11 desktop kernel: [  119.396984] VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
Feb  8 19:16:11 desktop kernel: [  119.396991] pcieport-driver 0000:00:02.0: broadcast error_detected message
Feb  8 19:16:11 desktop kernel: [  119.396998] pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
Feb  8 19:16:11 desktop kernel: [  119.397027] pcieport-driver 0000:00:02.0: broadcast resume message
Feb  8 19:16:11 desktop kernel: [  119.397040] pcieport-driver 0000:00:02.0: AER driver successfully recovered

```

Can someone shed some light as to what this means? I see it during bootup as well and I don't seem to have any graphics problems (I did have a problem with videos crashing but it seems unrelated as it caused by pulseaudio), but tailing the log I often see it appear many times a second

---

### Post by benjy on 2009-02-20
What, if you don't mind my asking, was the solution you found to the crashing videos? I have pretty much exactly the same problem and also have similar repeated dmesg outputs...

Google only seems to come up with results for bugs registered but no useful replies yet.... how many people does this effect?

---

### Post by theOtherMarino on 2009-02-25
Hello all,

I've been struggling with my NVIDIA Geforce 7300SE for some ... weeks now. No 3D, Ubuntu in low graphics mode, yadah yadah.

I've tried:
- the envyng thing - NOPE!
- the 96, 173, 177, 180.11 nvidia drivers provided through synaptics - NOPE!
- the 180.22 nvidia driver (nvidia site) - NOPE!
- the 180.29 nvidia driver (nvidia site) - NOPE!

So I switched back to 180.11, the latest ubuntu supported driver, and will try to work from there, but it will fait to load, and ubuntu will be in low graphics mode.

As my NVIDIA Geforce 7300SE is a PCI-EXPRESS card, I have also a big, really big bunch of "+------ PCI-Express Device Error ------+" messages in my syslog (/var/log/syslog).

Amongst these messages, some are "Corrected"
```

+------ PCI-Express Device Error ------+
Error Severity^I^I: Corrected
PCIE Bus Error type^I: Data Link Layer
Replay Timer Timeout  ^I: First
Transmitter ID^I^I: 0010
VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h

```

Many are Uncorrected (Non-Fatal)
```

+------ PCI-Express Device Error ------+
Error Severity^I^I: Uncorrected (Non-Fatal)
PCIE Bus Error type^I: Transaction Layer
Flow Control Protocol ^I: First
Receiver ID^I^I: 0010
VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
pcieport-driver 0000:00:02.0: broadcast error_detected message
pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
pcieport-driver 0000:00:02.0: broadcast resume message
pcieport-driver 0000:00:02.0: AER driver successfully recovered

```

And - more upsetting - some are Uncorrected (Fatal)
```

+------ PCI-Express Device Error ------+
Error Severity^I^I: Uncorrected (Fatal)
PCIE Bus Error type^I: Transaction Layer
Malformed TLP         ^I: First
Receiver ID^I^I: 0010
VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
TLB Header:
4a000001 02000004 00100f00 00000000
pcieport-driver 0000:00:02.0: broadcast error_detected message
nvidia 0000:02:00.0: device has no AER-aware driver
pcieport-driver 0000:00:02.0: Root Port link has been reset
pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
pcieport-driver 0000:00:02.0: broadcast resume message
pcieport-driver 0000:00:02.0: AER driver successfully recovered

```

---

### Post by theOtherMarino on 2009-02-25
First, let's try to understand what is the AER Driver ([http://lwn.net/Articles/193468/](http://lwn.net/Articles/193468/) - See also [http://ols.108.redhat.com/2007/Reprints/zhang-Reprint.pdf](http://ols.108.redhat.com/2007/Reprints/zhang-Reprint.pdf) for a nice glossy PDF). Oh, BTW, please not that the AER-Driver is "Copyright © Intel Corporation 2006".
> 
1.3 What is the PCI Express AER Driver?

PCI Express error signaling can occur on the PCI Express link itself or on behalf of transactions initiated on the link.

PCI Express defines two error reporting paradigms: the baseline capability and the Advanced Error Reporting capability. The baseline capability is required of all PCI Express components providing a minimum defined set of error reporting requirements. 

Advanced Error Reporting capability is implemented with a PCI Express advanced error reporting extended capability structure providing more robust error reporting.

The PCI Express AER driver provides the infrastructure to support PCI Express Advanced Error Reporting capability. The PCI Express AER driver provides three basic functions:

- Gathers the comprehensive error information if errors occurred. 
- Reports error to the users.
- Performs error recovery actions.

AER driver only attaches root ports which support PCI-Express AER
capability.

[...]
> 
3.2.2.1 Correctable errors
Correctable errors pose no impacts on the functionality of the interface. The PCI Express protocol can recover without any software intervention or any loss of data. These errors do not require any recovery actions. The AER driver clears the device's correctable error status register accordingly and logs these errors.

3.2.2.2 Non-correctable (non-fatal and fatal) errors
If an error message indicates a non-fatal error, performing link reset at upstream is not required. The AER driver calls error_detected(dev, pci_channel_io_normal) to all drivers associated within a hierarchy in question.
For example, EndPoint<==>DownstreamPort B<==>UpstreamPort A<==>RootPort.
If Upstream port A captures an AER error, the hierarchy consists of Downstream port B and EndPoint.

A driver may return PCI_ERS_RESULT_CAN_RECOVER, PCI_ERS_RESULT_DISCONNECT, or PCI_ERS_RESULT_NEED_RESET, depending on whether it can recover or the AER driver calls mmio_enabled as next.

If an error message indicates a fatal error, kernel will broadcast error_detected(dev, pci_channel_io_frozen) to all drivers within a hierarchy in question. Then, performing link reset at upstream is necessary.

As different kinds of devices might use different approaches to reset link, AER port service driver is required to provide the function to reset link. Firstly, kernel looks for if the upstream component has an aer driver. If it has, kernel uses the reset_link callback of the aer driver.

If the upstream component has no aer driver and the port is downstream port, we will use the aer driver of the root port who reports the AER error. As for upstream ports, they should provide their own aer service drivers with reset_link function.

If error_detected returns PCI_ERS_RESULT_CAN_RECOVER and reset_link returns PCI_ERS_RESULT_RECOVERED, the error handling goes to mmio_enabled.


I know, I know, to this point, this is a as obscure as some middle-age alchemy recipe. What we need is a usable diagnosis, and a workable solution.

More upsetting, the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/321412](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/321412) seems to say that there is no solution to these errors. Even the next realease (now-alpha3 Jauny) with its 2.6.28 based kernel brings the same pci-express errors. My current Ubuntu uses a 2.6.27-11.27 kernel.

AFAIK, there is nothing that can be done to prevent the "PCI-Express Device Error". Period.

And the "Uncorrected (Fatal)" error messages are all nvidia-related...
[PRE]
+------ PCI-Express Device Error ------+
Error Severity^I^I: Uncorrected (Fatal)
PCIE Bus Error type^I: Transaction Layer
Malformed TLP         ^I: First
Receiver ID^I^I: 0010
VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
TLB Header:
4a000001 02000004 00101c00 00000000
pcieport-driver 0000:00:02.0: broadcast error_detected message
nvidia 0000:02:00.0: device has no AER-aware driver
pcieport-driver 0000:00:02.0: Root Port link has been reset
pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
pcieport-driver 0000:00:02.0: broadcast resume message
pcieport-driver 0000:00:02.0: AER driver successfully recovered
[/PRE]

Seems that the NVIDIA driver is not compatible with AER, and neither is ATI, from what I have read on different fora. Or is it ubuntu? I don't know.

---

### Post by theOtherMarino on 2009-02-25
Another way of investigation is this one:
> 
2.1 Include the PCI Express AER Root Driver into the Linux Kernel

The PCI Express AER Root driver is a Root Port service driver attached
to the PCI Express Port Bus driver. If a user wants to use it, the driver
has to be compiled. Option CONFIG_PCIEAER supports this capability. It
depends on CONFIG_PCIEPORTBUS, so pls. set CONFIG_PCIEPORTBUS=y and
CONFIG_PCIEAER = y.


I checked into /boot/config-2.6.27-11.generic, both are set to "y".
> 
2.2 Load PCI Express AER Root Driver
There is a case where a system has AER support in BIOS. Enabling the AER
Root driver and having AER support in BIOS may result unpredictable
behavior. To avoid this conflict, a successful load of the AER Root driver
requires ACPI _OSC support in the BIOS to allow the AER Root driver to
request for native control of AER. See the PCI FW 3.0 Specification for
details regarding OSC usage. Currently, lots of firmwares don't provide
_OSC support while they use PCI Express. To support such firmwares,
forceload, a parameter of type bool, could enable AER to continue to
be initiated although firmwares have no _OSC support. To enable the
walkaround, pls. add aerdriver.forceload=y to kernel boot parameter line
when booting kernel. Note that forceload=n by default.

I added the "aerdriver.forceload=y" line in /boot/grub/menu.lst, but it had no effect. 
This option is not listed in the "consolidated list of the kernel parameters" ([http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)), but as it is driver-specific, this may not be relevant.

I tried to pass the command at boot time in grub, but I had an "Unrecognized command" message.

So what... Ubuntu keeps on loading in low graphics mode...

---

### Post by theOtherMarino on 2009-02-25
Here is my xorg.conf (I removed what has been commented by HAL):
```

Section "Monitor"
	Identifier     "Generic Monitor"
	HorizSync       30.0 - 70.0
	VertRefresh     50.0 - 130.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Generic Video Card"
	Monitor        "Generic Monitor"
	Option         "NoLogo" "False"
	Option         "AddARGBGLXVisuals" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
	Load           "glx".
EndSection


Section "Device"
	Identifier     "Generic Video Card"
	Driver		"nvidia"
	Option		"NoLogo"	"False"
EndSection


Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

```
Here is the Xorg.0.log - The GLX thing seems to load fine.

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux marino-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 25 17:20:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation G72 [GeForce 7300 SE] rev 161, Mem @ 0xdc000000/0, 0xc0000000/0, 0xdd000000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[... Big bunch of lines ...]
	[70] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[71] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.11  Wed Nov 26 11:23:16 PST 2008
(II) Loading extension GLX
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
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver  180.11  Wed Nov 26 11:00:06 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
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
	[... Big bunch of lines ...]
	[69] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[70] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[71] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "False"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 SE/7200 GS (G72) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.35.72
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 SE/7200 GS at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     AOC A770 (CRT-0)
(--) NVIDIA(0): AOC A770 (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[... Big bunch of lines ...]
	[69] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[70] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[71] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Option "Device" "/dev/psaux"
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb80ce400]
Saw signal 11.  Server aborting.
(II) UnloadModule: "kbd"
(II) UnloadModule: "mouse"

6167 5769
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

```

Here is the :0.log file:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux marino-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Feb 25 17:20:09 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
6167 5769
cp: cannot stat `/etc/X11/xorg_conf': No such file or directory

```

I can't see why there is an erro message "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)" in the :0.log and not in the Xorg.0.log... 


When I try to use "nvidia-settings", this keeps on telling me "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."



Damn damn damn...

---

### Post by theOtherMarino on 2009-02-27
Meekly, meekly, meekly, I come back here...

I checked in synaptics for anything regarding the linux kernel, headers, etc. Chose to keep/install the generic packages, unistall anything else.

Then I unistalled anything that related to nvidia.

Then I downloaded the nvidia installer from their site (no, I didn't use envyng, which kept on giving me the 177 driver).

Then,
-> ctrl-alt-f1 to get to the console.
-> sudo /etc/init.d/gdm stop to stop the Gnome Desktop Manager
-> sudo init 3 to stop the X server
-> sudo sh [my upload directory]/NVIDIA-Linux-x86-180.29-pkg1.run
-> Answer to the questions (generally, agree with anything)
-> sudo init 5 to start the X server
-> sudo /etc/init.d/gdm start to start the Gnome Destop Manager

... And... It works. I even installed compiz, and I have all the nifty effects.

Just crossing my fingers.


Marino
[http://markup.fr](http://markup.fr)

---

### Post by theOtherMarino on 2009-03-09
Well, no, it did not work.

- The "PCI-Express Device Error" were still there.
- The computer was hanging randomly, with no other way to go on that a hard reboot.
- 3D was sloooooow.
- Nicer: the two ps2 ports of the mainboard went idle. I suspected a problem with the mainboard, so I bought an USB keyboard.

Today, I removed the NVIDIA GeForce 7300 SE, and the "PCI-Express Device Error" disappeared. I had to swich back to the mainboard graphic card, but now, the computer works fine.

Sadly, I could not figure out what was the problem, but as the "PCI-Express Device Error" appear at boot time, it may be either a problem with the mainboard, its bios, ubuntu handling of the pci bus, the nvidia card or it driver.

---

### Post by theOtherMarino on 2009-03-09
Found this on [http://bbs.archlinux.org/viewtopic.php?id=59811:](http://bbs.archlinux.org/viewtopic.php?id=59811:)

> PCIE aer (Advanced Error Reporting) driver reports any errors (fatal, non-fatal, correctable or non-correctable) on the PCIE bus to the system. As your's is of Uncorrected (Non-Fatal) type, that means there is some problem with your PCIE bus configuration.

In case your bios is not 'ok' (contains bad config data), you may try the following kernel parameter that would avoid using bios to configure your pci bus.
```
pci=nobios
```


Going on, I found that "maybe" my NVIDIA GeForce 7300 SE was not compatible with a PCI-E 2.0 bus.

Still looking for a workable solution or a black magic trick.

---

### Post by theOtherMarino on 2009-03-09
Ok, my mainboard is a MSI K9VGM-V ([http://www.msicomputer.com/product/p_spec.asp?model=K9VGM-V](http://www.msicomputer.com/product/p_spec.asp?model=K9VGM-V)) which comes with one PCI Express X16 slot (supports PCI Express Bus specification v1.0a compliant)...

My NVIDIA GEFORCE 7300 SE is a PCI-E x16 card too...

Dang! Should work... Does not!

---

### Post by benjy on 2009-03-11
I'm still looking into this error myself aswel I know it's possible to remove the error my adding this to your grub boot line (at the end will do)

pci=conf1

This seems to remove the error. However I'm leaning towards thinking it is my mobo that's causing the majority of crash problems, or more specifically the built in eth port as torrents cause crashes nearly as much as video playback does. I have never in over 5 years of using many distros of linux had this many problems. I know it's not ubuntu and is more of a hardware issue - it's just getting to the damn root!

---

### Post by theOtherMarino on 2009-03-17
Still trying, but it bites.

I've check in the BIOS if the mainboard graphic chipset was desactivated.

The "Primary Graphic's Adapter" has three options : "PCIEx", "Internal" and "PCI". "PCIEx" is activated, so I guess it should be ok.

The "Max Payload Size" is set at 4096.

I'll also change back the the GRUB configuration file (sudo gedit /boot/grub/menu.lst):

```

aerdriver.forceload=n

```

I'll check whether the BIOS has a native support of the AER driver.

Stay tuned.

---

### Post by theOtherMarino on 2009-03-17
Benjy, I really guess that suppressing the error messages is not the best way to solve a problem. They did it at Tchernobyl :-( What I'd like to get is a reason for these "PCI-E device error". BIOS, hardware or software. What frightens me a bit would be to discover that my mobo could not bear a graphic card with Linux or Ubuntu.

BTW, what is a  your mobo? Same as mine, a MSI K8VGM-V?

---

### Post by theOtherMarino on 2009-03-17
BTW, there's a bug open in lanchpad: [https://bugs.launchpad.net/ubuntu/+bug/306962](https://bugs.launchpad.net/ubuntu/+bug/306962)

---

### Post by theOtherMarino on 2009-03-17
The MSI website does not list the 7300 se : [http://www.msicomputer.com/product/p_archives.asp?class=vga](http://www.msicomputer.com/product/p_archives.asp?class=vga)

---

### Post by kwacka on 2009-03-17
Folks at Fedora are having the same problem - seems to be MSI boards. [http://forums.fedoraforum.org/showthread.php?t=201871](http://forums.fedoraforum.org/showthread.php?t=201871)

one poster gives their solution:

> I was able to get rid of the error by adding pci=nommconf to kernel attributes.

if that doesn't work try a combination of pci=nommconf, pci=nomsi or iommu=calgary 

I'll try it when I get home.

---

### Post by theOtherMarino on 2009-03-17
Found on [http://www.linuxquestions.org/questions/red-hat-31/red-hat-installation-and-core-2-duo-479778/](http://www.linuxquestions.org/questions/red-hat-31/red-hat-installation-and-core-2-duo-479778/)
> 
hmm, it took me a while to figure it out, but a while back they added support for memory mapping to the PCI Bus. That could cause problems with some cards or bridges I suppose, so pci=nommconf probably means no-memory-mapping-configuration on the pci bus. Don't take my word for it but it makes sense.

On [http://www.centos.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=6511&forum=29:](http://www.centos.org/modules/newbb/viewtopic.php?viewmode=flat&topic_id=6511&forum=29:)

> To get past the "Probing PCI hardware bus 00" hang, you need to boot with "pci=nommconf" on the kernel cmdline on the 965 systems.


On [http://h18004.www1.hp.com/products/servers/linux/k8-notes.html](http://h18004.www1.hp.com/products/servers/linux/k8-notes.html), you can find the same advice.

On 

> The pci=nommconf kernel parameter disables the MMCONFIG PCI configuration space access method, which forces the kernel back to PCI type 1 configuration accesses. The MMCONFIG access method appears to be severely broken on a number of systems; on such systems, the NVIDIA Linux graphics driver can't reliably access the PCI configuration space of NVIDIA devices, which results in various stability problems, particularly if multi-core CPUs are used with multiple GPUs.

Congrats kwacka! You mays hav got it!

I'll try it and post my results.

---

### Post by theOtherMarino on 2009-03-17
Once server is installed, edit /etc/grub.conf or /boot/grub/grub.conf and append pci=nommconf at the end of kernel line:

kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=60da6da4-2e4f-42cc-b4ef-88fcf4bd3ec0 ro quiet splash  pci=nommconf

BTW: from what I can read, the pci=nomsi parameter relates to the detection of SATA HD drives... No problem of SATA HD drive detection on my system. I may be luckier than I usually think I am. However, it's interresting to read this thread [http://www.mail-archive.com/fedora-kernel-list@redhat.com/msg00075.html[\URL]. It dates back to kernel 2.6.20, but is informative. Specialy this one [url]http://www.mail-archive.com/fedora-kernel-list@redhat.com/msg00093.html](http://www.mail-archive.com/fedora-kernel-list@redhat.com/msg00075.html[\URL]. It dates back to kernel 2.6.20, but is informative. Specialy this one [url]http://www.mail-archive.com/fedora-kernel-list@redhat.com/msg00093.html)

> On Fri, Mar 30, 2007 at 03:09:08PM -0400, Dave Jones wrote:
> Isn't that needed though to access higher config space on PCIE ?
> Or do we not have any drivers that use that yet, making it a nonissue?
> 

Yeah, you need it to access Extended config space on PCI-Express, but the
only people who need it right now are Infinibarf, and I just provided
pci=mmconf to turn it back on.

The parameter iommu=calgary is discussed here [http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)

> Most modern Linux has support for IOMMU. An IOMMU is a device that will support mapping memory addresses. There is currently high-end branded server hardware that support this, but no desktop machines support IOMMU, AFAIK. An example IOMMU is the AGP and PCI Express graphics cards.
[...]
Since current hardware support is limited to high-end expensive server most Linux distro does not enable calgary DMA address mapping with memory protection by default.

I may try this last one if everything else fails.

---

### Post by theOtherMarino on 2009-03-18
No more "PCI-E device error" messages at boot with pci=nommconf... I hope the screen won't freeze.

---

### Post by kwacka on 2009-03-18
Thanks for the in-depth links theOtherMarino.

No more PCIerrors here - nothing in dmesg after the pci=nommconf was added.

(K9VGM board, nVidia 7300).

using google for "pci=nommconf" gives up links for 3 years ago for a multitude of problems - sound, video, et al. Possibly something else that should be turned off by default?

---

### Post by theOtherMarino on 2009-03-18
Yes, I noticed that it seemed to be a long unsolved problem. I guess that GRUB or some other script should fine-tune this automatically.

I quoted the thread [http://www.mail-archive.com/fedora-kernel-list@redhat.com/msg00093.html](http://www.mail-archive.com/fedora-kernel-list@redhat.com/msg00093.html). I read it from the beginning to the end. The very last gives a patch, but these guys are from redhat. I do not know if they have included this pach in their distribution since this 2007 thread.

---

### Post by theOtherMarino on 2009-03-19
Damn! My screen froze this morning... Gained more stability (one day and a half without any problem), but still...

---

### Post by theOtherMarino on 2009-03-19
And I'm using jedit (a java editor jedit.org) as a code editor. It has become painfully slooooow... Seems that java does not like my graphic card neither.

---

### Post by theOtherMarino on 2009-03-20
Had to disable some options in jedit.

Utilities > global settings > text area > Anti aliased smooth text [SET IT TO "none"]
Utilities > global settings > text area > fractionnal font metrics [DISABLE IT]

Got my jedit run fast again. Did it relates to the pcie error thing?

Another app will automatically freeze the whole display: amule...

---

### Post by theOtherMarino on 2009-03-20
Trying the pci=nomsi parameter brought me the +--- PCIE device errors ---+

---

### Post by theOtherMarino on 2009-03-21
Found this in the dmesg:

```
[    1.345983] pci 0000:00:00.0: MSI quirk detected; MSI disabled
```

Found the xplaination here [http://forums.fedoraforum.org/archive/index.php/t-167879.html](http://forums.fedoraforum.org/archive/index.php/t-167879.html)

> The MSI message is harmless and simply indicates that a Good Thing has happened: your hardware doesn't handle message signalled interrupts well, and the kernel has detected that condition and disabled them, switching to legacy interrupts instead.

Ok, ok. What's next?

```
[    1.345994] PCI: VIA PCI bridge detected.Disabling DAC.
```

Seems normal [https://www.x86-64.org/pipermail/patches/2007-June/004127.html](https://www.x86-64.org/pipermail/patches/2007-June/004127.html)

> Several reports that VIA bridges don't support DAC and corrupt data

Let's go on:
```
[    1.346410] pcieport-driver 0000:00:03.0: found MSI capability
```

Oh, cool, the MSI thing that had been previously disabled is back again... LOL

---

### Post by theOtherMarino on 2009-03-21
BTW: this page [http://linux.com/base/ldp/howto/BootPrompt-HOWTO-4.html](http://linux.com/base/ldp/howto/BootPrompt-HOWTO-4.html) "Boot Arguments to Control PCI Bus Behaviour (`pci=')" gives the list of the pci-related boot parameters. The pci=nomsi is not listed (?).

On a page, I've read one can use more than one value: pci=nommconf,noacpi

In the /boot/grub/menu.lst, you can choose to modify the "defoptions" lines. These options will be taken into account at each boot fot the current kernel, but not its alternatives. This line will not be reset when upgrading. DO NOT REMOVE THE "#", for it's not acomment mark. If you do so, you needn't modify the "kernel" line.

```
# defoptions=quiet splash acpi=force pci=nommconf

kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=60da6da4-2e4f-42cc-b4ef-88fcf4bd3ec0 ro quiet splash
```

And, oh, after each modification of your menu.lst, do not forget to do a "sudo update-grub" ;-)

Re-BTW: > ACPI = Advanced Configuration and Power Interface

APIC = Advanced Programmable Interrupt Controllers

ACPI is the system that controls your dynamic speed fans, the power button behavior, sleep states, ect.

APIC is the replacement for the old PIC chip that used to come imbedded on motherboards that allowed you to setup interrupts for your soundcard, ide controllers, ect.
[...]
However, many computers ship with buggy or out of spec. ACPI firmware which can cause any number of wackiness. If you are noticing your machine randomly powering off or failing to boot disabling this often helps.

I'll try the noapic parameter too... That sounds like unmastered black magic, but I've rather that to an animal sacrifice. And I'm not alone to get into black magic : [http://kerneltrap.org/mailarchive/linux-kernel/2007/9/5/168070](http://kerneltrap.org/mailarchive/linux-kernel/2007/9/5/168070) "Why do so many machines need "noapic"?" is great fun.

---

### Post by theOtherMarino on 2009-03-22
Second thought: the fact that kernel developpers said :

> There are 48 bugs in bugzilla which mention "noapic"

[http://bugzilla.kernel.org/buglist.cgi?query_format=advanced&short_desc_type=allwordss](http://bugzilla.kernel.org/buglist.cgi?query_format=advanced&short_desc_type=allwordss)...

And there are 173,000 on the internet ;)
[http://www.google.com/search?hl=en&q=linux+noapic&btnG=Google+Search](http://www.google.com/search?hl=en&q=linux+noapic&btnG=Google+Search)

We screwed this pooch a long time ago - years.  Perhaps if some of the many
noapic users could run a bisection search to work out when it broke we
could start fixing things.  But they all have a workaround so there's no
motivation.


... and ...

> Well, I think it broke soon after 2.6.9.

Please see [http://bugzilla.kernel.org/show_bug.cgi?id=3639#c10](http://bugzilla.kernel.org/show_bug.cgi?id=3639#c10)
-


... and ...

> I reported the all the problems (starting 2001), no developer 
seemed interested.

I can report them against the latest RC6 kernel tomorrow and put them
into bugzilla, if we now REALLY care.


... sounds weird. I'd like to read the equivalent for the Microsoft teams. Kernel 2.6.9 dates back from 2004. Has this been fixed? Still searching...

So adding noapic to my defoptions. One never knows, specially with nifty kernel/BIOS interactions.

The nolapic parameter may/might -don't forget the power of prayer too- be somehow eventually in some (unknown and uncertain) way useful. To read more about the lapic (the Local Advanced Programmable Interrupt Controller), see here [http://osdev.berlios.de/pic.html](http://osdev.berlios.de/pic.html)

I know, I know: I don't really... well, really don't know what I'm actually doing, but surgery too has had its pathfinders.

---

### Post by theOtherMarino on 2009-03-23
Comparing two dmesg, they happen to be different... I also get a warning:

```
[    3.203191] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
```

This is "normal". See [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710:](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/296710:)

> This bug was fixed in the package linux - 2.6.28-10.33

I'm running Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic). So I guess this issue will be fixed in Jaunty.

Also discovered this warning :

```
[  651.197650] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
```

This bug is reported here : [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/248577](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/248577)

> This bug was fixed in the package avahi - 0.6.23-4ubuntu2

So I guess this issue will be fixed in Jaunty (bis). 

Two kernel warnings... Didn't know Intrepid was so alpha/experimental. Gutsy Gibbon users will have to upgrade to Intrepid Ibex in april 2009. Cheer up, folks.

---

### Post by theOtherMarino on 2009-05-25
Now using 9.04 Jaunty jackal... "ope"? Maybe, for the PCI-Express Device Errors are still there, and the machine will still freeze after "some" (unpredictible) time when trying to plug my nvidia 7300 fs in.

Still met a guy on a forum who used a nvidia 9800 gts with his k9vgm-v... Yet another jackalope?

---

### Post by benjy on 2009-06-11
Wow, thOtherMarino, thanks for doing all this research! I found references to it on your website and despite trying a number of boot options have not as yet been able to run as smoothly as I have with Linux before. 

I have an Asrock AliveSata2-Glan with geforce 7300gs. Not exactly blistering speeds but it's suitable for most of my needs. 

The most success has come from pci=nommconf which stops the ever-repeating pcie error message and seems to lend some stability - as you I get around a day and a half, sometimes more before a totally unexplained crash.

It seems like people with setups like us either must use an older kernel or simply can't run recent Linux distributions for any real length of time.

Looks like Slack is my only option for the time being, until I can afford a mobo upgrade.

Boo hiss!

---

