---
title: "Is possible configure an setting to run an software using 16 bits colors ?"
date: 2022-11-28
forum: Hardware
---

### Post by aug7744 on 2022-11-28
Hello.
OS is configured to use 24 bits colors.
Is possible configure an setting to always when running an software in 16 bits colors even if the OS is using 24 bits ?
Only trying see if is possible an better performance in an "old" IGP Radeon HD 3000.

Thanks for reading.

---

### Post by TheFu on 2022-11-28
The OS doesn't care about any GUI settings.

Wayland or X/Windows have a color depth setting, so that is where you should look to modify it.  I don't know how and wouldn't know anything about Wayland settings.  For X/Windows, the color depth should be a parameter in a custom config file for xorg.

So, the first question is which of those are you using?  X/Windows or Wayland?

---

### Post by aug7744 on 2022-11-28
Thanks for your reply.
Using X/Windows

---

### Post by TheFu on 2022-11-28
[https://bbs.archlinux.org/viewtopic.php?id=225215](https://bbs.archlinux.org/viewtopic.php?id=225215) was found by google for research and steps.

---

