---
title: "mouse not working"
date: 2012-05-30
forum: Hardware
---

### Post by lapor on 2012-05-30
Hi,

using Dell vostro A860 and Ubuntu 11.10, touchpad/usb mouse stopped working.
Even try with 12.04 liveUSB, but still have the same issue. When I get to desktop, first mouse cursor acts like it is pressing all the time (orange square), and when I press ESC button, it stops to work. I can move cursor, but I can't use buttons for mouse.

help

---

### Post by lapor on 2012-05-30
anybody?

---

### Post by lapor on 2012-05-31
If anyone will expirience the same problem, I found a solution. I found out that touchpad is broken, so I had to uninstall drivers for it with command:
rmmod psmouse

Aferwards touchpad stops to work, but USB mouse works normal.

---

