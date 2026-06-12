---
title: "Stopping X windows from loading devices"
date: 2010-09-27
forum: Hardware
---

### Post by triss on 2010-09-27
Hi,

I'd like to stop x windows loading up particular devices and using them as mice/keyboards. 

Currently X windows treats the big red knob on my NI Audio Kontrol 1 (a sound card with buttons on) as the left right controls on a mouse and the buttons on it send a, b, c.

I'd also like to disable wacom tablet I have acting as a mouse currently as I only intend to use it as an interface for my musical noodlings in supercollider/sc.

Do I need to use xinput or something to do this?

Here's what /var/log/Xorg.0.log says about my Audio Kontrol:

```
(II) config/udev: Adding input device Audio Kontrol 1 (/dev/input/event8)
(**) Audio Kontrol 1: Applying InputClass "evdev keyboard catchall"
(**) Audio Kontrol 1: always reports core events
(**) Audio Kontrol 1: Device: "/dev/input/event8"
(II) Audio Kontrol 1: Found absolute axes
(II) Audio Kontrol 1: Found keys
(II) Audio Kontrol 1: Configuring as mouse
(II) Audio Kontrol 1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Audio Kontrol 1" (type: KEYBOARD)
(II) Audio Kontrol 1: initialized for absolute axes.
(II) config/udev: Adding input device Audio Kontrol 1 (/dev/input/js0)

```

---

### Post by triss on 2010-09-29
sorry to bump this.

so is there no way to stop devices being loaded by the evdev catchall?

---

### Post by Favux on 2010-09-29
Well, I'd think you'd need to modify the "evdev keyboard catchall" snippet.  The evdev.conf should be in /usr/lib/X11/xorg.conf.d.

After the:
```
Driver "evdev"
```
line you could try adding something like:
```
MatchProduct "Audio Kontrol 1"
Option "Ignore" "yes"

```
Or whatever match line(s) works like MatchVendor or whatever.

---

