---
title: "thinkpad hibernation/sleep problem"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by gawdin on 2008-03-11
I have an R50e (yes I know it is old) running Ubuntu 7.10

sometimes when resuming from a screensaver and as far as I know all the time when resuming from sleep or hibernate my computer goes to a blank or black screen. only way out as far as I know is a hard boot. does anyone know if this is a fixable problem? I don't know how similar it is to the dell laptop problems or other laptops? SUSE did not have this problem so I think it may be Ubuntu. thanks for any help

---

### Post by brdohman on 2008-03-11
I'm currently running a thinkpad r52, and have the same issues with hibernation.  When I tell my computer to hibernate, it will, but I am not able to get it out.

I have to do a hardboot as well to get back into ubuntu.

---

### Post by gawdin on 2008-03-11
glad I am not the only one

---

### Post by Arthur Archnix on 2008-03-11
I've infrequently encountered a similar issue, it's likely an issue with the video card as opposed to the laptop itself or else network manager. I've never tried to narrow it down much because it is so infrequent on my laptop.

1. From personal experience, I've yet to experience this symptom after add this to my xorg.conf under my intel driver:
```
option "NoDRI"
```
This may break compiz. I'm not sure. I use metacity.

2. If switching to TTY1 by doing Ctrl+Alt+f1  then switching back to TTY7 with Ctrl+Alt+f7 gets your video to turn on, you may want to try forcing the system to do that all the time automatically.
```
gksudo gedit /etc/default/acpi-support
```
scroll down to this line and uncomment it.
```
 #DOUBLE_CONSOLE_SWITCH=true

```

---

