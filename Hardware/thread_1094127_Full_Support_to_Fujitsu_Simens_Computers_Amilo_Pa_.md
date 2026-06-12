---
title: "Full Support to: Fujitsu Simens Computers Amilo Pa 1538"
date: 2009-03-12
forum: Hardware
---

### Post by falkTX on 2009-03-12
Recently my sister ask me to format her laptop; It had so many viruses that she couldn't even login. So I first started to back-up all the data. Since my external HD is in XFS format and she's using Vista, I had to load an Ubuntu LiveCD. That's when I got amazed... Everything worked with her laptop! Brightness, special buttons, wow... I asked myself: *Why can't I have the same thing with my laptop?*

So here I am trying to make _everything_ to work with Ubuntu. Like the title says, it a Fujitsu Siemens, and some little things don't work. Well, I want to change that!

Here's a list of things that doesn't work:
1. [Fn]+F8 (Brightness+)
2. [Fn]+F9 (Brightness-)
3. Silent Mode (Also has a button for this)
4. WLAN On/Off button

Also, the "Internet" button opens 'Home' instead of Firefox and brightness control is only possible using 'smartdimmer' and the nVidia Proprietary drivers must be installed.

'dmesg' reports when I press an unsupported special key:
[Fn]+F8
```
[ 1201.650372] atkbd.c: Use 'setkeycodes 7f <keycode>' to make it known.
[ 1227.765521] atkbd.c: Unknown key pressed (translated set 2, code 0x6f on isa0060/serio0).
```

[Fn]+F9
```
[ 1227.765530] atkbd.c: Use 'setkeycodes 6f <keycode>' to make it known.
[ 1227.851513] atkbd.c: Unknown key released (translated set 2, code 0x6f on isa0060/serio0).
```

SilentMode
```
[ 1313.336994] atkbd.c: Use 'setkeycodes 67 <keycode>' to make it known.
[ 1313.448346] atkbd.c: Unknown key released (translated set 2, code 0x67 on isa0060/serio0).
```

The WLAN On/Off button turns on/off a small light but doesn't change anything. Honestly I don't mind if it's always on, but it seems that if I turn it off while the BIOS splash appears, it will be always off, so I have to reboot if I do a mistake here.


So, what can I do to make brightness control work outside 'smartdimmer' and set keys to do the job? Can it be implemented on Ubuntu on a later release?

Please help

---

### Post by falkTX on 2009-03-12
(Just to subscribe)

---

### Post by falkTX on 2009-04-04
No replies for 3weeks.

I'll post a bug

---

