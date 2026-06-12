---
title: "Dell XPS M1530: touchpad not Synaptics?"
date: 2008-08-08
forum: Hardware
---

### Post by christian.convey on 2008-08-08
I'm using Ubuntu 8.04.  I wanted to make the touchpad move the cursor much faster than it does by default.

The xorg.conf file that was produced by the installation has a section for the touchpad, and the driver specified in that section is "synaptics".

However, when I look at /var/log/Xorg.0.log, I see these lines:

Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

It sounds to me, from the error messages, that my touchpad is meant to be handled by some other driver.  Does anyone know how I can resolve this?

---

### Post by Spoke on 2008-10-22
I have been having a similar issue with the same computer.

I have Hardy 8.0.4 and my problem is that even though the touchpad works, the special configurations do not, as the vertical and horizontal scrolling and other settings.

The relevant portions of xorg.conf and of the log files are attached.

```
Section "InputDevice"
   Identifier  "Configured Mouse"
   Driver      "mouse"
   Option      "CorePointer"
   Option      "ZAxisMapping" "4 5"
   Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
   Identifier  "Synaptics Touchpad"
   Driver      "synaptics"
   Option      "SendCoreEvents"  "true"
   Option      "Device" "/dev/psaux"
   Option      "Protocol"  "auto-dev"
   Option      "LeftEdge"  "85"
   Option      "RightEdge" "715"
   Option      "TopEdge"   "85"
   Option      "BottomEdge"   "715"
   Option      "FingerLow" "25"
   Option      "FingerHigh"   "30"
   Option      "MaxTapTime"   "180"
   Option      "MaxTapMove"   "220"
   Option      "ClickTime" "0"
   Option      "VertEdgeScroll"  "on"
   Option      "HorizEdgeScroll" "on"
   Option      "VertScrollDelta" "100"
   Option      "HorizScrollDelta"   "100"
   Option      "MaxSpeed"  "0.99"
   Option      "AccelFactor"  "0.08"
   Option      "SHMConfig" "true"
EndSection

Section "ServerLayout"
   Identifier  "Default Layout"
  screen "Default Screen"
   Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
   Load     "glx"
   Load     "synaptics"
EndSection

```

and Xorg.0.log
```
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2
)
Current Operating System: Linux xxxxx-xxxx 2.6.24-19-generic #1 SMP Wed Aug 20 2
2:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
...
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
...
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
...
(II) "glx" will be loaded. This was enabled by default and also specified in the
 config file.
...
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
...
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Reloading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
...
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 18 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "85"
(**) Option "RightEdge" "715"
(**) Option "TopEdge" "85"
(**) Option "BottomEdge" "715"
(**) Option "VertScrollDelta" "100"
(**) Option "HorizScrollDelta" "100"
(**) Option "FingerLow" "25"
(**) Option "FingerHigh" "30"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "220"
(**) Option "ClickTime" "0"
(**) Option "VertEdgeScroll" "on"
(**) Option "HorizEdgeScroll" "on"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
...
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

Is there anything I am overlooking?

This also happens to happen randomly, sometimes when I switch from the Windows Vista partition to the Ubuntu the scroll works and the Xorg.0.log comes clean, but it is spotty and I have not been able to reliably reproduce it.

Any help is welcome.

---

### Post by Agrajag27 on 2008-10-23
I'm still waiting for someone to fix the intermittent scroll action on this pad. It's the one thing that drives me nuts with Ubuntu. Roughly half my boots have no ability to scroll using the touchpad. 

I don't get it.

Must be a way to get that to work reliably.

---

