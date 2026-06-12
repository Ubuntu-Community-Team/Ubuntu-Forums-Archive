---
title: "Problem with screen brightness in windows and ubuntu after update"
date: 2014-04-23
forum: Hardware
---

### Post by Tony_Ivanov on 2014-04-23
Hello,
I'm having problems with the screen brightness controls - *only with the Fn+F2/F3 buttons, I can control it from within the display options in the OS* 
I have a Compaq CQ62 with an Intel HD Graphics video in a dual boot system with Windows 7 and Ubuntu 14.04.
Yesterday I updated from 13.10 to 14.04 with some Grub problems which I solved, but after the update I can't control my laptop's screen brightness in Windows 7 nor Ubuntu.
I have read about the solution where you add this:

```
sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf
``` Add the following lines to this file:
 ```
[INDENT] Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection [/INDENT]

```

It did not solve the problem.
Why can't I control the brightness in Windows, too? This seems a little bit disturbing.

Any help will be appreciated!

---

### Post by brunofin on 2014-04-23
Generally speaking, if you have a problem which persists in multiple operating systems, it means it can be a hardware problem.

---

### Post by Tony_Ivanov on 2014-04-24
I'm really sorry I wasn't thorough enough - only the hotkey combination of fn+ F2 or F3 isn't working (for brightness up/down), but I can control which display to use and volume up/down, so the keys are working.

---

