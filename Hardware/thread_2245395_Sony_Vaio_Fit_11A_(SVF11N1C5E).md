---
title: "Sony Vaio Fit 11A (SVF11N1C5E)"
date: 2014-09-23
forum: Hardware
---

### Post by lynx_deb on 2014-09-23
Hi guys

i'm trying to install Ubuntu 14.04 (also tried 14.10) on this Vaio in the title.. (Bay-Trail-D based)
The installation is fine, but after a reboot Ubuntu doesn't start :(

Remove quiet e splash from the grub line, i see that it stuck after loading XHCI module of usb3 or sometime to i2c IRQ38. The only way to start the system is putting on the kernel line acpi=off but obviously i loose all function regarding FN button, battery managment and so on..

There is another method, may be recompile ACPI table to get it work?

Thanks!

---

### Post by lynx_deb on 2014-09-24
anyone? :(
i'm gonna to install Windows again to dump ACPI table.. and hope that will work

---

### Post by jorgerpaez on 2014-11-23
Hi!!!
I have the same problem, and i don't want to re install window*****
Could you fix it?
Thanks! and sorry my bad english!!!

---

