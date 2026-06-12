---
title: "Lenovo U350 - 10.10 - Suspend &amp; Hibernate"
date: 2011-02-04
forum: Hardware
---

### Post by hedrinbc on 2011-02-04
No longer solved... Here is where I am at...

```
sudo nano /etc/default/grub
```

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi backlight=video"
GRUB_CMDLINE_LINUX="acpi backlight=video"

```

Suspended once but not working now... any ideas?

---

### Post by mikewhatever on 2011-02-05
I believe the option is **acpi_backlight=video**, not sure it has anything to do with suspending.

---

