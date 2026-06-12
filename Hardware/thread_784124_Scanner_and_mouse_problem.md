---
title: "Scanner and mouse problem"
date: 2008-05-06
forum: Hardware
---

### Post by jdarias on 2008-05-06
I have a Logitech LX5 mouse and a HP 4070 photosmart scanner. I enabled this one recently in my fresh (8.04) install.
The problem happens when i reboot and both devices are connected: Once X starts the mouse freezes. I have to disconnect the scanner, then boot, then connect it again in orden to make both devices work together.
As a side note, I have enabled evdev for my mouse, and disabled XFree86-DGA too, since both together rendered the mouse useless in 3d games.

---

### Post by jdarias on 2008-05-06
I got it sorted:
Looking back at  cat /proc/bus/input/devices i noticed a change of the info for my mouse, so i updated xorg acordingly. Now they both work. cya.

---

