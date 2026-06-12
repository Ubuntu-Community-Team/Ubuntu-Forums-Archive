---
title: "Not seeing input on bluetooth keyboard"
date: 2004-12-07
forum: Hardware &amp; Laptops
---

### Post by blemmenes on 2004-12-07
I've got a bluetooth keyboard that I had been using fine under debian unstable, but I can't get it to type anything under Ubuntu.

I get it paired and connected to hidd correctly however no text appears when I type.

I'm using a DBT-120 USB dongle, which works fine with other things like my phone etc.  And I even tried pairing the keyboard on a windows box and it works there using this dongle.

I'm thinking it might be something with the UDEV config but nothing jumps out at me.

Below is the SYSLOG output when I turn on the keyboard and pair it.

```

Dec  7 09:37:58 localhost kernel: Bluetooth: HIDP (Human Interface Emulation) ver 1.0
Dec  7 09:37:59 localhost hidd: New HID device 00:0A:DF:00:13:BB (CSR HIDEngine Keyboard)
Dec  7 09:37:59 localhost hal.hotplug[7224]: DEVPATH is not set
Dec  7 09:37:59 localhost input.agent[7212]:      evbug: blacklisted
Dec  7 09:37:59 localhost input.agent[7212]:      evdev: already loaded
Dec  7 09:37:59 localhost input.agent[7225]:      evbug: blacklisted
Dec  7 09:37:59 localhost input.agent[7225]:      evdev: already loaded
Dec  7 09:38:00 localhost udev[7256]: configured rule in '/etc/udev/rules.d/udev.rules' at line 49 applied, 'event3' becomes 'input/%k'
Dec  7 09:38:00 localhost udev[7256]: creating device node '/dev/input/event3'

```

Using this keyboard on Debian sid I would see similar entries up to the point of the DEVPATH not set message... everything else is new as of using it on Ubuntu.

For reference it's a FrogPad keyboard (not that it should matter).

Any pointers would be appreciated

---

### Post by mterring on 2004-12-21
No help for your problem, but I'm experiencing the same problem with a bluetooth mouse (Logitech MX900).  It seems to load associate with the evdev driver, but not mousedev or tsdev as it does under Debian.

I've compared all the hotplug stuff from the working Debian to Ubuntu but can't find any (meaningful) differences.  I'm suspecting it's something to do with HAL, which my Debian didn't use, but I don't know anything about HAL so I can't diagnose it.

Does anyone have a working bluetooth keyboard or mouse with Ubuntu?

---

