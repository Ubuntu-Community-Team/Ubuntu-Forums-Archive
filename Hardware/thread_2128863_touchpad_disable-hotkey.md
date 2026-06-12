---
title: "touchpad disable-hotkey"
date: 2013-03-24
forum: Hardware
---

### Post by nekoexmachina on 2013-03-24
Hi! 
My laptop has fn-f9 as disable-touchpad hotkey and it DNW.
Here is xev output for fn-f9:
```
KeyRelease event, serial 35, synthetic NO, window 0x4e00001,
    root 0xd9, subw 0x0, time 29749654, (346,70), root:(347,96),
    state 0x0, keycode 199 (keysym 0x1008ffa9, XF86TouchpadToggle), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
 
```
Here is /etc/acpi/events/asus-touchpad 

```
event=hotkey (ATKD|HOTK) (0000006[ab]|00000037|1008ffa9)
action=/etc/acpi/asus-touchpad.sh

```
And hotkey doesn't work. 
I've tried to run /etc/acpi/asus-touchpad.sh and it works flawless, but the hotkey just doesn't. What should I add to /etc/acpi/events to fix this?




p.s. the thing is, on pre-installed win8 it doesn't work, too. lol.

---

### Post by nekoexmachina on 2013-04-01
Update for the thread. Could not find a system-wide solution, so just put a script /etc/acpi/asus-touchpad.sh to my WM's hotkeys.

---

