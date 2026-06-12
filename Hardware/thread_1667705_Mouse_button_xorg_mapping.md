---
title: "Mouse button xorg mapping"
date: 2011-01-15
forum: Hardware
---

### Post by tsh on 2011-01-15
Is there any user documentation for the mouse button mappings in xorg? I guess I may have a bug to file, but I'd rather check if it is a configuration thing first. I gather I ought to be able to enable mouse scrolling somehow even with just two physical buttons.
My /var/log/Xorg.0.log contains:
```
[    65.549] (II) config/udev: Adding input device Kensington      Kensington USB/PS2 Orbit (/dev/input/event3)
[    65.549] (**) Kensington      Kensington USB/PS2 Orbit: Applying InputClass "evdev pointer catchall"
[    65.549] (**) Kensington      Kensington USB/PS2 Orbit: always reports core events
[    65.549] (**) Kensington      Kensington USB/PS2 Orbit: Device: "/dev/input/event3"
[    65.564] (II) Kensington      Kensington USB/PS2 Orbit: Found 3 mouse buttons
[    65.564] (II) Kensington      Kensington USB/PS2 Orbit: Found relative axes
[    65.564] (II) Kensington      Kensington USB/PS2 Orbit: Found x and y relative axes
[    65.564] (II) Kensington      Kensington USB/PS2 Orbit: Configuring as mouse
[    65.564] (**) Kensington      Kensington USB/PS2 Orbit: YAxisMapping: buttons 4 and 5
[    65.564] (**) Kensington      Kensington USB/PS2 Orbit: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    65.564] (II) XINPUT: Adding extended input device "Kensington      Kensington USB/PS2 Orbit" (type: MOUSE)
[    65.564] (II) Kensington      Kensington USB/PS2 Orbit: initialized for relative axes.
[    65.564] (II) config/udev: Adding input device Kensington      Kensington USB/PS2 Orbit (/dev/input/mouse0)

```

which suggests that mouse wheel emulation has been detected - but i am reasonably sure this device only has 2 buttons (with the 3rd emulated).  Also EmulateWheelButton: 4 sees wrong shouldn't this be 2 or 3 (whichever is 'middle').

Is editing xorg.conf the preferred ubuntu way of applying a customisation like this, or is there a way to influence the autodetection (which then needs to be fixed since this is a common device)

---

