---
title: "[SOLVED] aticonfig --initial issue..."
date: 2008-10-29
forum: Hardware
---

### Post by Izek on 2008-10-29
Here's the issue when I run that command:

```
ian@ian-desktop:~$ aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
```

---

### Post by CowzRule on 2008-10-29
Try running the command with sudo
> sudo aticonfig --initial

---

### Post by Izek on 2008-10-29
Thanks, it works thanks to sudo.

---

