---
title: "Wayland and no xinput"
date: 2018-01-21
forum: Hardware
---

### Post by sushi-addiction13 on 2018-01-21
A big thing that is making me worry, wayland and the lack of xinput.

 Is there no way to emulate scroll wheel in horizontal and vertical? Also setup two different devices to be used at the same time?

My current setup is so holding right click allows scroll horizontal & vertical on both devices. Also adjust the speed of the second device. Both already have a physical vertical scroll but emulated scroll gets used much more.

```
xinput set-button-map "Kensington Kensington Slimblade Trackball" 1 2 3 4 5 6 7 8 9 10 11 12
xinput set-prop "Kensington Kensington Slimblade Trackball" "Evdev Wheel Emulation" 1
xinput set-prop "Kensington Kensington Slimblade Trackball" "Evdev Wheel Emulation Axes" 7 6 4 5
xinput set-prop "Kensington Kensington Slimblade Trackball" "Evdev Wheel Emulation Timeout" 200
xinput set-prop "Kensington Kensington Slimblade Trackball" "Evdev Wheel Emulation Button" 3
xinput set-button-map "USB OPTICAL MOUSE " 1 2 3 4 5 6 7 8 9 10 11 12
xinput set-prop "USB OPTICAL MOUSE " "Evdev Wheel Emulation" 1
xinput set-prop "USB OPTICAL MOUSE " "Evdev Wheel Emulation Axes" 7 6 4 5
xinput set-prop "USB OPTICAL MOUSE " "Evdev Wheel Emulation Timeout" 200
xinput set-prop "USB OPTICAL MOUSE " "Evdev Wheel Emulation Button" 3
xinput set-prop "USB OPTICAL MOUSE " "Device Accel Constant Deceleration" 1.5
########
#xinput --list
#xev | grep button
#xinput list-props "Kensington Kensington Slimblade Trackball"
#xinput query-state "Kensington Kensington Slimblade Trackball"
#xinput list --name-only | hexdump -C #This gets names that have spaces at beginning end & multiple middle spaces
```

---

### Post by cruzer001 on 2018-01-21
Hello

This is still under development, but libinput is the package for wayland.  I'm on xorg (16.04) but your question interest me so I had a look around.

[https://wiki.archlinux.org/index.php/Libinput](https://wiki.archlinux.org/index.php/Libinput)

[https://wayland.freedesktop.org/libinput/doc/latest/faq.html](https://wayland.freedesktop.org/libinput/doc/latest/faq.html)

May have to stay on xorg for a while longer.

---

### Post by TheFu on 2018-01-21
Have you tried using the X11 fallback mode?  It can be selected prior to login.
Doing everything that X11 does isn't what Wayland is about.

---

### Post by sushi-addiction13 on 2018-01-21
> **cruzer001 said:**
> Hello

This is still under development, but libinput is the package for wayland.  I'm on xorg (16.04) but your question interest me so I had a look around.

[https://wiki.archlinux.org/index.php/Libinput](https://wiki.archlinux.org/index.php/Libinput)

[https://wayland.freedesktop.org/libinput/doc/latest/faq.html](https://wayland.freedesktop.org/libinput/doc/latest/faq.html)

May have to stay on xorg for a while longer.

Yes, libinput may eventually be able to handle it with another program sending it info. Problem is it's not getting much attention.

This thread [https://ubuntuforums.org/showthread.php?t=2374936](https://ubuntuforums.org/showthread.php?t=2374936) , post 6 & 9
has some info that may help on gnome. It's not clear if the user was using wayland.

It also looks like there is no way to configure speed of each device when using more than one.

---

