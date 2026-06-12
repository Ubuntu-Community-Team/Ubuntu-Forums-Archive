---
title: "Bluetooth mouse"
date: 2010-08-18
forum: Hardware
---

### Post by Shura0 on 2010-08-18
Hi all,
please help to connect my bluetooth mouse to the PC with Ubuntu **10.04**.
Mouse **A4Tech BT-630**. It's discoverable, I can connect it to my PC, all looks fine, but mouse does not move cursor.

When I connect mouse
**dmesg:**
```
 Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   57.452365] input: BlueTooth Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:41/input5
[   57.452626] generic-bluetooth 0005:09DA:80F0.0001: input,hidraw0:  BLUETOOTH HID v0.1e Keyboard [BlueTooth Mouse] on 00:0A:3A:5B:46:03
```**Xorg.0.log**
```
(II) config/udev: Adding input device BlueTooth Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device BlueTooth Mouse (/dev/input/event5)
(**) BlueTooth Mouse: Applying InputClass "evdev pointer catchall"
(**) BlueTooth Mouse: Applying InputClass "evdev keyboard catchall"
(**) BlueTooth Mouse: always reports core events
(**) BlueTooth Mouse: Device: "/dev/input/event5"
(II) BlueTooth Mouse: Found 12 mouse buttons
(II) BlueTooth Mouse: Found scroll wheel(s)
(II) BlueTooth Mouse: Found relative axes
(II) BlueTooth Mouse: Found x and y relative axes
(II) BlueTooth Mouse: Found absolute axes
(II) BlueTooth Mouse: Found keys
(II) BlueTooth Mouse: Configuring as mouse
(II) BlueTooth Mouse: Configuring as keyboard
(**) BlueTooth Mouse: YAxisMapping: buttons 4 and 5
(**) BlueTooth Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "BlueTooth Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) BlueTooth Mouse: initialized for relative axes.
(WW) BlueTooth Mouse: ignoring absolute axes.
```I've found a similar issue here: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727)
and comment #10 helped me, but it is not what I want. Now if I switch off and switch on my mouse I need to pair my mouse again. It's very inconvenient. Moreover, after that manipulations mouse is in discoverable mode, it blinks LEDS and I suppose it is not good for battery.
And after *'hidd --search'*** Xorg.0.log** contain the following:
```
(II) config/udev: Adding input device Terax Inc.           Bluetooth Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Terax Inc.           Bluetooth Mouse (/dev/input/event5)
(**) Terax Inc.           Bluetooth Mouse: Applying InputClass "evdev pointer catchall"
(**) Terax Inc.           Bluetooth Mouse: Applying InputClass "evdev keyboard catchall"
(**) Terax Inc.           Bluetooth Mouse: always reports core events
(**) Terax Inc.           Bluetooth Mouse: Device: "/dev/input/event5"
(II) Terax Inc.           Bluetooth Mouse: Found 12 mouse buttons
(II) Terax Inc.           Bluetooth Mouse: Found scroll wheel(s)
(II) Terax Inc.           Bluetooth Mouse: Found relative axes
(II) Terax Inc.           Bluetooth Mouse: Found x and y relative axes
(II) Terax Inc.           Bluetooth Mouse: Found absolute axes
(II) Terax Inc.           Bluetooth Mouse: Found keys
(II) Terax Inc.           Bluetooth Mouse: Configuring as mouse
(II) Terax Inc.           Bluetooth Mouse: Configuring as keyboard
(**) Terax Inc.           Bluetooth Mouse: YAxisMapping: buttons 4 and 5
(**) Terax Inc.           Bluetooth Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Terax Inc.           Bluetooth Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) Terax Inc.           Bluetooth Mouse: initialized for relative axes.
(WW) Terax Inc.           Bluetooth Mouse: ignoring absolute axes.
(II) config/udev: removing device Terax Inc.           Bluetooth Mouse
(II) Terax Inc.           Bluetooth Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Terax Inc.           Bluetooth Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Terax Inc.           Bluetooth Mouse (/dev/input/event5)
(**) Terax Inc.           Bluetooth Mouse: Applying InputClass "evdev pointer catchall"
(**) Terax Inc.           Bluetooth Mouse: Applying InputClass "evdev keyboard catchall"
(**) Terax Inc.           Bluetooth Mouse: always reports core events
(**) Terax Inc.           Bluetooth Mouse: Device: "/dev/input/event5"
(II) Terax Inc.           Bluetooth Mouse: Found 12 mouse buttons
(II) Terax Inc.           Bluetooth Mouse: Found scroll wheel(s)
(II) Terax Inc.           Bluetooth Mouse: Found relative axes
(II) Terax Inc.           Bluetooth Mouse: Found x and y relative axes
(II) Terax Inc.           Bluetooth Mouse: Found absolute axes
(II) Terax Inc.           Bluetooth Mouse: Found keys
(II) Terax Inc.           Bluetooth Mouse: Configuring as mouse
(II) Terax Inc.           Bluetooth Mouse: Configuring as keyboard
(**) Terax Inc.           Bluetooth Mouse: YAxisMapping: buttons 4 and 5
(**) Terax Inc.           Bluetooth Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Terax Inc.           Bluetooth Mouse" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) Terax Inc.           Bluetooth Mouse: initialized for relative axes.
(WW) Terax Inc.           Bluetooth Mouse: ignoring absolute axes.
```**dmesg:**
```
input: Terax Inc.           Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:41/input6
[  262.151346] generic-bluetooth 0005:09DA:80F0.0002: input,hidraw0: BLUETOOTH HID v0.1e Keyboard [Terax Inc.           Bluetooth Mouse] on 00:0A:3A:5B:46:03
[  307.742547] input: Terax Inc.           Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:43/input7
[  307.743185] generic-bluetooth 0005:09DA:80F0.0003: input,hidraw0: BLUETOOTH HID v0.1e Keyboard [Terax Inc.           Bluetooth Mouse] on 00:0A:3A:5B:46:03
```Could you please help me? How to force Xorg to discover my mous as 'Terax Inc. Bluetooth mouse'? I'm ready to provide any debug information.

---

