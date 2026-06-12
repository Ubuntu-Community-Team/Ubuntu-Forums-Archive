---
title: "Hotplug messed - almost all usb unrecognized"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by cheuschober on 2006-03-19
Hiya. Completely stumped on this one. My hotplug subsystem seems to be very messed. Right now I'm having trouble with -anything- other than a strict usb thumbdrive being recognized on my Toshiba A45 without a reboot -- on a laptop that's a bit of a problem for when, say, I want to plug in my printer which works just peachily, mind you, if I restart the system.

Lately I tried my intellimouse optical (usb) and the mouse had a 'kiniggit' fit -- the laser blinks rapidly until I unplug it. The device doesn't show in 'lsusb' and dmesg puts this out:

```
[4600566.322000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4600566.416000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4600566.416000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4600566.493000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4600566.493000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4600566.581000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4600566.581000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4600566.662000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4600566.662000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4600566.803000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4600566.803000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4600567.113000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4600567.113000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4600567.257000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4600567.257000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4603951.365000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4603951.365000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4603952.286000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4603952.286000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4603952.667000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4603952.667000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4603952.757000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4603952.757000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4603953.087000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4603953.087000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4603953.266000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4603953.266000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4607003.777000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?[4607409.344000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
```

The last two lines about enabling a port will occur on any usb port I try to plug any non thumbdrive device into. If they work with a reboot then I know there has to be a way to make these devices work without one. Besides, the reason I moved to linux from M$ was so that I wouldn't lose work from having to reboot each time I wanted to do something crazy like change wireless networks. :-p

Any and all help is greatly appreciated as always.

Regards,
~Chad

---

