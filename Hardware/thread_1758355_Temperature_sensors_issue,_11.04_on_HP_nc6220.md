---
title: "Temperature sensors issue, 11.04 on HP nc6220"
date: 2011-05-14
forum: Hardware
---

### Post by backwoodsman on 2011-05-14
On boot, the temperature sensors get read once, then never again until the next boot.  This is a big problem because the fan never comes on, and the system will overheat.  If rebooted when warm, the sensors get read, and then the fan works at whatever speed is appropriate for that temperature, regardless of where the temperature goes from there.

This happens the same with any GUI -- KDE4, Trinity/KDE3, and XFCE.  The sensors & fan work normally in XP, and in other Linux distros, so it's not a hardware issue.

Any ideas?  This problem is a deal killer if I can't find a solution very soon.

---

### Post by backwoodsman on 2011-05-23
Update:  Looks like it's a kernel issue.  Temp sensors work fine with some old distros, like PCLinuxOS 2007, but not with any new distros I've tried.

acpid is running, but doesn't seem to be doing anything regarding temperature.

The BIOS has a setting to always run the fan when on AC power, but it runs very slowly, not fast enough to adequately cool the machine when it's working hard.

I'm pretty much out of ideas, so hopefully someone can give me some hints on how to fix this.

---

