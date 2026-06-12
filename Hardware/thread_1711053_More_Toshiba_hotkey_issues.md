---
title: "More Toshiba hotkey issues"
date: 2011-03-20
forum: Hardware
---

### Post by neepheid on 2011-03-20
Hi folks

I've installed Ubuntu 10.10 on a Toshiba Portege R100 and dealt with some of the gotchas like screen res being incorrectly detected but the hotkeys have got me in a bit of a tizz because I've got them partially working.

I have added toshiba_acpi to /etc/modules and fnfxd is running as root.  I have the following hotkeys working:

mute (Fn-Esc)
lock screen (Fn-F1)
battery status (Fn-F2)
suspend (Fn-F3)
hibernate (Fn-F4)
LCD/CRT (Fn-F5)
wireless on/off (Fn-F8)

The brightness is strange - Fn-F6 doesn't do anything and Fn-F7 pops up a notification angrily indicating that it's already at full brightness.

I can alter the brightness if I do the following:

```
echo "brightness:x" > /proc/acpi/toshiba/lcd
```

However, I can only do this logged on as root - sudo gives me permission denied.

Volume up/down (Fn-1 and Fn-2) don't work at all.  In dmesg I get "toshiba_acpi: Unknown key 102" for Fn-1 and 103 for Fn-2.

A possibly related problem is that when I close the lid of the laptop, the screen blanks as I have set it to, but when you open the lid the screen doesn't come back.  I can get the screen back by toggling LCD/CRT a couple of times but the display is frozen.  Any ideas?

Sorry for rambling first post.

---

### Post by neepheid on 2011-03-20
Weird update: after I came back from testing suspend and hibernate, I now find that the Fn key behaviour has changed:

Fn-Esc - mute does nothing
Fn-F1 - lock does nothing
Fn-F2 - battery info does nothing
Fn-F3 - suspend does nothing
Fn-F4 - hibernate does nothing
Fn-F5 - LCD/CRT still works
Fn-F6 - brightness down working, but no on screen notification
Fn-F7 - brightness up working, but no on screen notification
Fn-F8 - wireless on/off does nothing
Fn-1 - volume down still does nothing but no longer generates errors in dmesg
Fn-2 - volume up as above

---

### Post by neepheid on 2011-03-20
Also, machine does not lock up when lid is closed.

---

### Post by neepheid on 2011-03-23
Interesting update: brightness down doesn't work from cold boot on AC power but brightness up works (but brightness already at max).  If I change to battery power (and back to AC power) then brightness hotkeys work as intended.

Hotkeys broken as stated above on resume from hibernate, but not from suspend.

---

### Post by neepheid on 2011-03-26
Any ideas out there?

---

