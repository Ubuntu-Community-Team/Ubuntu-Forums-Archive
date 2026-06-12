---
title: "Cannot get Direct App. Launch Button to work (keycode &gt; 255)"
date: 2009-11-29
forum: Hardware
---

### Post by gokalpo on 2009-11-29
Hello,
I have a HP 2710p convertible laptop/tablet PC with an 'i' button on the side. This button is supposed to bring up an informational application in a Windows environment. Anyway, this is not relevant since I run exclusively Ubuntu on this PC.
In include/linux/input.h, this key is listed as follows (hex 0x166 = 358 ):
```
#define KEY_INFO                0x166   /* AL OEM Features/Tips/Tutorial */
```I would like to bind this key to an useful function, such as calling my display rotation script but haven't succeeded on doing so. The Gnome keyboard shortcuts configuration utility doesn't recognize it when I press it.
I have tried listening for the key using acpi_listen but nothing shows up when it is pressed.
I used showkey to listen in scancode and keycode mode.
In scancode mode, showkey does not detect anything.
In keycode mode, showkey detects it with keycode 358:
```
$ sudo showkey -k
kb mode was RAW
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
keycode  28 release
keycode 358 press
keycode 358 release

```(Ignore keycode 28, it's for the Enter key)

How can I get this key recognized under Gnome/X?

---

