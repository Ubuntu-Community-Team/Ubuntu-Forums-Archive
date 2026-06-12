---
title: "XF86AudioRaiseVolume and XF86AudioLowerVolume stopped to work in Gnome Shell 3.4.1"
date: 2014-05-02
forum: Hardware
---

### Post by LastStarDust on 2014-05-02
Hello,
recently I cannot raise and lower volume through the dedicated XF86 knob of my keyboard. That used to work properly. I cannot remember what upgrade broke the key.
My configuration is this:
[LIST]
[*]Keyboard: Microsoft Reclusa
[*]Ubuntu 12.04: 3.2.0-61-generic #92-Ubuntu SMP Mon Mar 31 23:47:59 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[*]GNOME Shell 3.4.1
[/LIST]

The command
```
pactl set-sink-volume 0 -- +10%
```
works neatly.

xev doesn't show any keycode, but if I issue ```
killall gnome-settings-daemon
``` I get the right xev output
```
XF86AudioLowerVolume Keycode: 122
XF86AudioRaiseVolume Keycode: 123
```

I tried to add in keyboard preferences a new shortcut with "pactl set-sink-volume 0 -- +10%" command and bind XF86AudioRaiseVolume Keycode to it, but the problem isn't solved.

---

