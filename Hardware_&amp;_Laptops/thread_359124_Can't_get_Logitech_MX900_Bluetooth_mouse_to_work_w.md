---
title: "Can't get Logitech MX900 Bluetooth mouse to work with evdev"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by minneyar on 2007-02-11
I've got a Logitech MX900 Bluetooth mouse that I'm trying to get to work on 6.10 with evdev so that I can use all of its buttons.  I've read through every post on evdev and Bluetooth that I could find here, but it's still not working for me.

In my /proc/bus/input/devices, I have two Logitech entries:

```
I: Bus=0003 Vendor=046d Product=c705 Version=2704
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-3.1/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse0 event4 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b001 Version=2201
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:14:5C:5E
S: Sysfs=/class/input/input5
H: Handlers=mouse1 event5 ts1
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0
```

As you might expect, the one labeled "USB Receiver" seems to represent the actual receiver, while the one labeled "Bluetooth Mouse" is the mouse.  That one also doesn't appear until after the mouse has been paired to the receiver.

I've tried using both of these pointer configurations in my xorg.conf:

```
Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "evdev"
  Option "CorePointer"
  Option "Name" "Logitech Bluetooth Mouse"
  Option "Phys" "00:07:61:14:5C:5E"
EndSection
```

```
Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "evdev"
  Option "CorePointer"
  Option "Name" "Logitech USB Receiver"
  Option "Phys" "usb-0000:00:02.0-3.1/input0"
EndSection
```

With the first configuration, X will not start. The following interesting lines appear at the bottom of /var/log/Xorg.0.log:

```
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-00:07:61:14:5C:5E: Core Pointer
(II) Configured Mouse-00:07:61:14:5C:5E: Found 2 absolute axes.
(II) Configured Mouse-00:07:61:14:5C:5E: Configuring as pointer.
(**) Configured Mouse-00:07:61:14:5C:5E: Configuring in Absolute mode.
(**) Configured Mouse-00:07:61:14:5C:5E: AbsoluteScreen: -1.

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7be067b]
3: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7be16fd]
4: /usr/lib/xorg/modules/input/evdev_drv.so(evdevNewDriver+0x44) [0xb7be1860]
5: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7be03f1]
6: /usr/bin/X11/X(InitInput+0x16f) [0x809f21f]
7: /usr/bin/X11/X(main+0x355) [0x806e5e5]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d888cc]
9: /usr/bin/X11/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting
```

With the latter configuration, X starts, but the mouse cursor doesn't respond to any input.  It's as though it recognizes the device properly, but it doesn't recognize any data is being sent to it.  In that case, the Xorg log has this:

```
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:02.0-3.1/input0: Core Pointer
(II) Configured Mouse-usb-0000:00:02.0-3.1/input0: Found 3 relative axes.
(II) Configured Mouse-usb-0000:00:02.0-3.1/input0: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:02.0-3.1/input0: WHEELRelativeAxisButtons: 4 5.
(II) Configured Mouse-usb-0000:00:02.0-3.1/input0: Found 8 mouse buttons
(II) Configured Mouse-usb-0000:00:02.0-3.1/input0: Configured 10 mouse buttons
(II) XINPUT: Adding extended input device "Configured Mouse-usb-0000:00:02.0-3.1/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Configured Mouse-usb-0000:00:02.0-3.1/input0: 3 valuators.
(**) ../../src/evdev_btn.c (90): Registering 10 buttons.
(II) Configured Mouse-usb-0000:00:02.0-3.1/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) Configured Mouse-usb-0000:00:02.0-3.1/input0: On
```

I've tried setting up rules in /etc/udev/rules.d to alias the device to /dev/input/event9, as some guides have suggested, but that doesn't change anything.  X continues to respond exactly the same as it does above, depending on which device I alias to that node.

For what it's worth, if I do "cat /dev/input/event4", I don't appear to get any data from it.  Doing "cat /dev/input/event5" produces data as I move the mouse around, though.  Also, if I use the "mouse" driver with the device "/dev/input/mice" or "/dev/input/mouse1", I can use my mouse, although several of the buttons aren't recognized.

So, does anybody have any clue what's going on here?   I've been beating my head against it for hours, and I'm stumped.

---

