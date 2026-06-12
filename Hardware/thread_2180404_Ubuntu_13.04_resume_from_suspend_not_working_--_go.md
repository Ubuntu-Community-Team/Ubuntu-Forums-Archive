---
title: "Ubuntu 13.04 resume from suspend not working -- goes to blank screen with cursor"
date: 2013-10-12
forum: Hardware
---

### Post by gmisch on 2013-10-12
Hi there,

I have a desktop machine (Intel Pentium G630 -- Sandybridge with HD3000 graphics) with the Intel H61 chipset. Ubuntu works well with this machine EXCEPT for when I put the computer to sleep. When I resume it from sleep (or suspend is what I guess is the Ubuntu nomenclature), it does not enable me to get to a working desktop. Instead, a blank screen with a hung cursor appears. Invoking a new shell (Ctrl+Alt+F4, F5, etc) so I could start the window manager (startx) does nothing. I have to reset the machine.

I'm thinking that this may be an issue with drivers, however, I have found out that this is a widespread problem. It has had similar behavior in Ubuntu 12.04/12.10 except sometimes the machine will resume successfully to a working desktop, only to freeze, requiring the REISUB trick to reboot.

Any ideas?

---

### Post by varunendra on 2013-10-14
Welcome to the forums gmisch !

Please post back the suspend log (open a terminal with Ctrl-Alt-T, and..) -
```
cat /var/log/pm-suspend.log
```
Copy the whole output using mouse pointer and paste it here in your next post, within '**Code**' box. (Please follow the "Using Code Tags" link in my signature to see how.)

---

