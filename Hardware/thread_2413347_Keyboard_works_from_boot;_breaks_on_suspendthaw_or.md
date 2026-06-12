---
title: "Keyboard works from boot; breaks on suspend/thaw or disconnect/reconnect"
date: 2019-02-24
forum: Hardware
---

### Post by frkbmb on 2019-02-24
[IMG]https://ruggedpcreview.com/images4/dell_7212_rugged_extreme_tablet_angle2_410_72.jpg[/IMG]
I'm using a Dell Latitude 7212 Rugged Extreme Tablet that ships with a keyboard cover with an integrated touchpad that interfaces with the tablet via this port on the bottom that I couldn't identify.

The keyboard and touchpad work perfectly until I either suspend/thaw the tablet or physically disconnect and reconnect the keyboard cover. In both cases, the keystrokes are completely ignored, yet the touchpad keeps functioning. On Win10, both suspend/thaw and disconnect/reconnect do not affect functionality of the keyboard cover.

I'm running Bionic 18.04.

Here is the dmesg entry for the keyboard:

```

[    6.803686] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    6.804338] i8042: Warning: Keylock active
[    6.805971] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.805990] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.809712] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[   12.184527] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6

```

Here is the hwinfo entry for the keyboard; it is the same before and after reproducing the problem

```

user@bionic:~/Documents$ hwinfo --keyboard
23: PS/2 00.0: 10800 Keyboard                                   
  [Created at input.226]
  Unique ID: c3zD.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:68
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

There are no ACPI errors.

Attempted thus far:
[LIST]
[*]Add ```
atkbd.reset=1 i8042.nomux=1 i8042.reset=1
``` as kernel arguments
[*]Install ```
xserver-xorg-input-all
```
[*]Install ```
#!/bin/sh

###############################################################################
# Pm-utils script to unbind i8042 on hibernate/suspend and
# bind it on thaw/resume.
#
# Copyright: Copyright (c) 2009 Nicolay Doytchev
# License:   GPL-3
###############################################################################


###############################################################################
# INSTALL:
#   1. Copy this script to /etc/pm/sleep.d/
#   2. Make it executable:
#       sudo chmod +x /etc/pm/sleep.d/01i8042
#
# UNINSTALL:
#   1. Delete the script from /etc/pm/sleep.d/
#       sudo rm /etc/pm/sleep.d/01i8042
###############################################################################


case "$1" in
    hibernate|suspend)
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
    ;;
    thaw|resume)
        echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
    ;;
esac



```
[/LIST]

Please let me know how I can investigate further. Thank you!

---

### Post by sgoudelis on 2019-11-19
I dont know the solution to your problem but I want to ask how this tablet run on ubuntu ? Are there any issues ?

---

