---
title: "Problem scroll whell"
date: 2010-12-07
forum: Hardware
---

### Post by Fily1982 on 2010-12-07
have a  problem with the mouse wheel,if I scroll down a page okay, but when I  try to get the page starts to scroll quickly down until you find the  bottom, it is quite annoying, also because it allows me to scroll the page up, if I try to go back, go back. This is the result of lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 041e:3020 Creative Technology, Ltd SoundBlaster Audigy 2 NX
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0421:005e Nokia Mobile Phones 
Bus 003 Device 002: ID 03f0:6204 Hewlett-Packard DeskJet 5150c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0553:0a01 STMicroelectronics Imaging Division (VLSI Vision) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
and log of Xorg
```
II) config/udev: Adding input device 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel (/dev/input/event4)
(**) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: Applying InputClass "evdev pointer catchall"
(**) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: always reports core events
(**) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: Device: "/dev/input/event4"
(II) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: Found 3 mouse buttons
(II) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: Found scroll wheel(s)
(II) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: Found relative axes
(II) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: Found x and y relative axes
(II) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: Configuring as mouse
(**) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: YAxisMapping: buttons 4 and 5
(**) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel" (type: MOUSE)
(II) 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: initialized for relative axes.
(II) config/udev: Adding input device 3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "it"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
3 button optical mouse with scroll wheel 3 button optical mouse with scroll wheel: dropping event due to full queue!
```
[COLOR=#000000]The  last lines are repeated a lot, whenever I use the scroll wheel, is  there a way to change the mouse settings? In these particular  EmulateWheelButton: 4, EmulateWheelInertia 10, EmulateWheelTimeout: 200
[/COLOR]Let me know if it's a configuration problem of Xorg or if is a physical problem of the mouse.

---

