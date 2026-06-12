---
title: "Touchpad not recognised by Maverick"
date: 2010-10-16
forum: Hardware
---

### Post by habib_seif on 2010-10-16
Hi all,

Touchpad of Dell n4030 is recognised by maverick as a generic ps/2 mouse, and therefore, its vertical scrolling does not work. Here is the output of "cat /var/log/Xorg.0.log | grep -i mouse" command:

```
[    21.239] (==) intel(0): Silken mouse enabled
[    21.426] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event5)
[    21.426] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    21.426] (**) USB Optical Mouse: always reports core events
[    21.426] (**) USB Optical Mouse: Device: "/dev/input/event5"
[    21.445] (II) USB Optical Mouse: Found 3 mouse buttons
[    21.445] (II) USB Optical Mouse: Found scroll wheel(s)
[    21.445] (II) USB Optical Mouse: Found relative axes
[    21.445] (II) USB Optical Mouse: Found x and y relative axes
[    21.445] (II) USB Optical Mouse: Found absolute axes
[    21.445] (II) USB Optical Mouse: Configuring as mouse
[    21.445] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    21.445] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.445] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    21.445] (II) USB Optical Mouse: initialized for relative axes.
[    21.445] (WW) USB Optical Mouse: ignoring absolute axes.
[    21.446] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    21.462] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event9)
[    21.462] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    21.462] (**) PS/2 Generic Mouse: always reports core events
[    21.462] (**) PS/2 Generic Mouse: Device: "/dev/input/event9"
[    21.481] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    21.481] (II) PS/2 Generic Mouse: Found relative axes
[    21.481] (II) PS/2 Generic Mouse: Found x and y relative axes
[    21.481] (II) PS/2 Generic Mouse: Configuring as mouse
[    21.481] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    21.481] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.481] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    21.481] (II) PS/2 Generic Mouse: initialized for relative axes.
[    21.482] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
```

I also tested maverick with Dell 6000 and the touchpad works perfectly. So, I think the touchpad modules are present and don't have any problem. The problem is to detect the touchpad of dell n4030.

Do you have any idea to solve the problem?

Cheers,
Habib

---

### Post by jamesisin on 2012-02-28
Any luck with this problem?

---

### Post by ahsan101 on 2012-02-28
A possible Kernel bug, have you tried mainline kernel's? they seems to be promising!

---

### Post by jamesisin on 2012-02-29
Sounds complicated.  How's it go?

---

