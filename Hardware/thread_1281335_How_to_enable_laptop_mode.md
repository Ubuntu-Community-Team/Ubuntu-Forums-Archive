---
title: "How to enable laptop mode?"
date: 2009-10-03
forum: Hardware
---

### Post by linux_ocean on 2009-10-03
I want to enable laptop mode on my ubuntu jaunty.
but I don't know how should I enable it!
does anyone know about it?

---

### Post by DC^ on 2009-10-03
Hallo,

You have to do a few things:

First:
```
sudo gedit /etc/default/acpi-support
```Second:
Edit: ENABLE_LAPTOP_MODE=false to ENABLE_LAPTOP_MODE=true

Hope it helps.

---

### Post by linux_ocean on 2009-10-03
thank you.
It can solve my problem.

---

