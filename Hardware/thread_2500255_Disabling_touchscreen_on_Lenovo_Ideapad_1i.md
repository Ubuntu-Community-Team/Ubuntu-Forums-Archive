---
title: "Disabling touchscreen on Lenovo Ideapad 1i"
date: 2024-08-27
forum: Hardware
---

### Post by hey-that-guy-has-a-dog on 2024-08-27
Hi, everyone.

I'm trying to disable the touchscreen on my new laptop. I've attempted several of the methods I've found online, to no success yet.

I'm running Ubuntu 24.04 on a Lenovo Ideapad 1i. (It was cheap)

It doesn't seem to be an xinput device, here are the results of xinput list.

```
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:15                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:15                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer-gestures:15                id=8    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-touch:15                           id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:15                        id=9    [slave  keyboard (3)]

```

Likewise, I can't see the touchscreen if I open BIOS (though obviously, that's a lot harder to copy and paste from).

Using modprobe to disable hid_multitouch also disables the touchpad.

Adding the following in /etc/udev/rules.d/99-disable-touchscreen.rules does nothing at all:
```
# Disable all touchscreen devices
SUBSYSTEM=="input", ATTR{ID_INPUT_TOUCHSCREEN}=="1", ATTR{enabled}="0"

```

You'd think it'd be a lot easier to break something than to make it work. Any help would be appreciated, I'll happily provide more info if needed.

---

### Post by hey-that-guy-has-a-dog on 2024-10-19
Bumping on the off chance anyone can help

---

### Post by Holger_Gehrke on 2024-10-19
'xinput' (as you can tell from the warning it prints) doesn't really work with Wayland. To get a list of the actual devices you can run 'libinput list-devices'. Sadly, the 'libinput' command does not have the capability to make settings. AFAIK, Wayland is developed with the idea of 'graphical tools first', so if the various settings applets don't offer a way to disable the touchscreen, you'll be stuck trying to figure out why the udev rule isn't working. I'd suspect the device doesn't set 'ID_INPUT_TOUCHSCREEN', so I'd try to find some other identifier, probably trying 'udevadm info' with the path to the device in '/sys/class/input/'; there probably is something like ID_PRODUCT and ID_VENDOR if the touchscreen is connected through USB.

Holger

---

