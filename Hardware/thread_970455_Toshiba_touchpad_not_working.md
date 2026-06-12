---
title: "Toshiba touchpad not working"
date: 2008-11-04
forum: Hardware
---

### Post by tornike on 2008-11-04
Hello, I have recently switched from windows vista to ubuntu 8.04 and touchpad on my satellite pro 200 has stopped working. I have tried to find a solution in your forums and googled a bit but without success.
It seems as if the touchpad is detected and modules are loaded. This is the output from my /var/log/Xorg.0.log:

```
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
.
.
.

(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "SHMConfig" "true"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
.
.
.

(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
```

ls -l /dev/input/by-path (looks like following):

```
lrwxrwxrwx 1 root root 9 2008-11-04 11:26 pci-0000:00:1d.0-usb-0:1:1.0-event-mouse -> ../event2
lrwxrwxrwx 1 root root 9 2008-11-04 11:26 pci-0000:00:1d.0-usb-0:1:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2008-11-04 10:14 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 9 2008-11-04 10:14 platform-i8042-serio-4-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2008-11-04 10:14 platform-i8042-serio-4-mouse -> ../mouse3
lrwxrwxrwx 1 root root 9 2008-11-04 10:14 platform-pcspkr-event-spkr -> ../event6

```

my usb mouse works fine if I move it after "sudo cat /dev/input/event2" there is some output at the console but if I move touchpad after "sudo cat /dev/input/event9" nothing happens. It looks as if it's disabled somewhere I could not find (it's completely dead). Some help would be greatly appreciated.
Thanks.

---

