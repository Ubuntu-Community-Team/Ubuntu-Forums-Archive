---
title: "ALPS touchpad and 2.6.11"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by ethzero on 2005-05-31
I've installed a 2.6.11 kernel (the one in the ubuntu repository) and compiled in the ALPS driver, but i can't get the driver to work.  The touchpad is detected correctly on boot:

```
ALPS Touchpad (Glidepoint) detected
input: AlpsPS/2 ALPS TouchPad on isa0060/serio1
```

But i see the following in the X.org log:

```
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(**) Option "Device" "/dev/psaux"
...
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/psaux"
(--) <default pointer>: Device: "/dev/psaux"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: Core Pointer
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(==) <default pointer>: Buttons: 3
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded

```

Though it fails to initialize with the synaptics driver, the touchpad still works using some default driver.  But i want to disable tapping (like everyone else apparently) so i want the touchpad to work with the synaptics driver.  Any ideas?

---

