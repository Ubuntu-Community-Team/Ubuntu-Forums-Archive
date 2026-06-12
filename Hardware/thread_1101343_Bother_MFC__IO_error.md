---
title: "Bother MFC:  I/O error"
date: 2009-03-20
forum: Hardware
---

### Post by briancb on 2009-03-20
I tried to follow the instructions given but find that there is no such file as "/etc/udev/rules.d/40-basic-permissions.rules" in 9.04.

Where is this file now?

Or what should I do in 9.04 to produce the same result?

Thank you for your help

Ubuntu 8.04/8.04.1, 8.10
    1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
    2. Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

    3. Restart the OS.

---

### Post by briancb on 2009-03-20
> **briancb said:**
> I tried to follow the instructions given but find that there is no such file as "/etc/udev/rules.d/40-basic-permissions.rules" in 9.04.

Where is this file now?

Or what should I do in 9.04 to produce the same result?

Thank you for your help

Ubuntu 8.04/8.04.1, 8.10
    1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
    2. Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

    3. Restart the OS.

I meant brother MFC

Solved:

[http://ubuntuforums.org/showthread.php?p=6927446](http://ubuntuforums.org/showthread.php?p=6927446)

---

