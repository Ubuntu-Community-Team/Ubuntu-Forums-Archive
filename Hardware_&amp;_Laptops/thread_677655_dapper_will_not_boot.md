---
title: "dapper will not boot"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by jl_swan on 2008-01-25
i cannot get os to boot without "pci=noacpi".  can anybody tell me why this is?

Thank you

---

### Post by overdrank on 2008-01-26
> **jl_swan said:**
> i cannot get os to boot without "pci=noacpi".  can anybody tell me why this is?

Thank you

HI and welcome, if you have Ubuntu installed you can just add that to the kernel in the boot menu list. Using this command ```
gksudo gedit /boot/grub/menu.lst
```

---

