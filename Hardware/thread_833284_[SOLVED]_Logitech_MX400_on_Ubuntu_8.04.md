---
title: "[SOLVED] Logitech MX400 on Ubuntu 8.04"
date: 2008-06-18
forum: Hardware
---

### Post by A.I. on 2008-06-18
I has a Logitech MX400 mouse with horizontal scroll by wheel.

On Ubutnu 7.10 all 9 buttons worked fine with xorg.conf:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection

```

But, when I reinstall system to 8.04 horizontal scroll didn't work and Xorg.0.log has:
```

(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "CorePointer"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(**) <default pointer>: Sensitivity: 1

```

xserver-xorg-input-evdev is installed and evdev module is loaded.

Manual device links from [this post]("http://ubuntuforums.org/showthread.php?t=65471") didn't work. I use
```

    Option      "Dev Name" "Logitech USB-PS/2 Optical Mouse"
    Option      "Dev Phys" "usb-0000:00:1d.1-2/input0"
    Option      "Device" "/dev/input/mice"

```
for "cat /proc/bus/input/devices" output:
```

I: Bus=0003 Vendor=046d Product=c043 Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

```

Any ideals? :)

---

### Post by A.I. on 2008-06-18
When I use:
```

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "Protocol" "evdev"
    Option      "Dev Name" "Logitech USB-PS/2 Optical Mouse"
    Option      "Dev Phys" "usb-0000:00:1d.1-2/input0"
    Option      "Device" "/dev/input/event2"
    Option      "Resolution" "800"
EndSection

```

Xorg.0.log write, that it didn't know evdev protocol:
```

(**) Option "Protocol" "evdev"
(EE) Configured Mouse: Unknown protocol "evdev"
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"

```

---

### Post by A.I. on 2008-06-19
OK, right xorg.conf
```

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "evdev"
    Option      "Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
    Option		"CorePointer"
EndSection

```

In Hardy evdev didn't understand Name option and you *must not* used it. Also you must add CorePointer option.

---

### Post by petri on 2008-07-08
Thanks A.I. it works for me too. :popcorn:

---

### Post by louisgag on 2008-12-19
Solved my problem! Thank you!

---

