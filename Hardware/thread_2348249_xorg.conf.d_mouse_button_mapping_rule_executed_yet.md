---
title: "xorg.conf.d mouse button mapping rule executed yet ineffective"
date: 2017-01-02
forum: Hardware
---

### Post by zhangweiwu on 2017-01-02
I have this:
```

$ cat /etc/X11/xorg.conf.d/00-mouse-remap.conf 
Section "InputClass"
   Identifier     "Bluetooth Mouse left-handed"
   MatchIsPointer "on"
   MatchProduct   "Lenovo Mice N700"
   Driver "evdev"
   Option "ButtonMapping" "3 2 1 4 5 6 7 8 9"
EndSection

```

/var/log/Xorg.0.log apparently recognizes this new rule and went through the '3 2 1' mapping when this mouse is added:

```

[   831.547] (II) config/udev: Adding input device Lenovo Mice N700 (/dev/input/event16)
[   831.547] (**) Lenovo Mice N700: Applying InputClass "evdev pointer catchall"
[   831.547] (**) Lenovo Mice N700: Applying InputClass "evdev keyboard catchall"
[   831.547] (**) Lenovo Mice N700: Applying InputClass "Bluetooth Mouse left-handed"
[   831.547] (II) Using input driver 'evdev' for 'Lenovo Mice N700'
[   831.547] (**) Lenovo Mice N700: always reports core events
[   831.547] (**) evdev: Lenovo Mice N700: Device: "/dev/input/event16"
[   831.547] (**) evdev: Lenovo Mice N700: ButtonMapping '3 2 1 4 5 6 7 8 9'
[   831.547] (--) evdev: Lenovo Mice N700: Vendor 0x17ef Product 0x6060
[   831.547] (--) evdev: Lenovo Mice N700: Found 9 mouse buttons
[   831.547] (--) evdev: Lenovo Mice N700: Found scroll wheel(s)
[   831.547] (--) evdev: Lenovo Mice N700: Found relative axes
[   831.547] (--) evdev: Lenovo Mice N700: Found x and y relative axes
[   831.547] (--) evdev: Lenovo Mice N700: Found keys
[   831.547] (II) evdev: Lenovo Mice N700: Configuring as mouse
[   831.547] (II) evdev: Lenovo Mice N700: Configuring as keyboard
[   831.547] (II) evdev: Lenovo Mice N700: Adding scrollwheel support
[   831.547] (**) evdev: Lenovo Mice N700: YAxisMapping: buttons 4 and 5
[   831.547] (**) evdev: Lenovo Mice N700: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

The result is simply that the mouse buttons ain't swapped.

To the apparent answer that Ubuntu's xorg.conf.d is located at /usr/share/X11/xorg.conf.d : Yes, I tried that too. Makes no difference.

Thanks! Using 16.10 64bit.

---

### Post by zhangweiwu on 2017-01-02
Advanced search does not work for me - I tried to search for "xorg.conf ButtonMapping", and I get this:

```

You don't have permission to access /search.php on this server.

Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

```

Does it behave differently for you?

---

