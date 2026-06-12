---
title: "Mouse Acceleration Profile is not applied"
date: 2010-10-23
forum: Hardware
---

### Post by sssent on 2010-10-23
Hi,

I have some trouble changing the acceleration profile for my trackpoint.

Maverick recognizes it as a PS/2 Generic Mouse. I can set the acceleration profile from the default 0 to 2 with:
```

xinput set-prop "PS/2 Generic Mouse" "Device Accel Profile" 2

```It works beautifully until restart.

I'm trying to make it stick with adding the following to /usr/share/X11/xorg.conf.d/99_MyInputSettings.conf:
```

Section "InputClass"
    Identifier    "Trackpoint AccProfile"
    MatchProduct    "PS/2 Generic Mouse"
    MatchDevicePath    "/dev/input/event*"
    Option        "AccelerationProfile"        "2"
EndSection

```After restart the log at /var/log/Xorg.0.log says the InputClass above is applied, yet the acceleretation profile remains set to 0, and the pointer still moves like my grandmother.

Any idea what went wrong?

---

