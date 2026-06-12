---
title: "Error loading a module into the kernel"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by ThrobbingBrain66 on 2006-08-01
So I'm attempting to load the toshiba.ko and toshiba_acpi.ko modules into my kernel.  When I run
```
modprobe toshiba
``` and ```
 modprobe toshiba_acpi
``` I get the following error:

**FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-26-686/kernel/drivers/acpi/toshiba_acpi.ko): No such device**

[B]FATAL: Error inserting toshiba (/lib/modules/2.6.15-26-686/kernel/drivers/acpi/toshiba.ko): No such device
[/B]

However, when I run ```
find /lib/modules/`uname -r` -name "tosh*"

```

the results are:

/lib/modules/2.6.15-26-686/kernel/drivers/acpi/toshiba_acpi.ko
/lib/modules/2.6.15-26-686/kernel/drivers/char/toshiba.ko


so the modules are there, but I'm unable to load them.  any ideas?

---

### Post by ThrobbingBrain66 on 2006-08-02
bump :)

---

### Post by DarkAngel88 on 2006-09-19
I have the exact same problem.. do you have any update on this ?

---

### Post by zgornel on 2006-09-19
You probably must modify accordingly /etc/modules.conf.

---

