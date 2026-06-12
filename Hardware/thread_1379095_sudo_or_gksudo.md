---
title: "sudo or gksudo?"
date: 2010-01-12
forum: Hardware
---

### Post by Kognit on 2010-01-12
Hi

I have a problem with a touchpad when trying to disable it. With my model of laptop the only solution is workaround (sudo modprobe -r psmouse and sudo modprobe psmouse). But the problem begins when i try to create a keyboard shortcut for those commands and it just doesn't work (in terminal without the keyboard shortcuts works just fine), but if i put gksudo instead of sudo the keyboard shortcut works. Is it possible that this is potentially harm for the system?

Thx

---

### Post by jongkind on 2010-01-12
No, this will not harm your system: gksudo is just the graphical frontend of sudo.

---

