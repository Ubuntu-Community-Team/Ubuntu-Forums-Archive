---
title: "[asus m6n]Incomplete Shutdown"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by zeno on 2005-03-23
Hi,

i have installed Hoary on my laptop (asus m6742) and i have a problem when i shutdown... the laptop writes "Power Down" but it remains still on... it seems to be a acpi or apm problem...
any ideas?

Thanks,
zeno

---

### Post by Strider on 2005-03-23
zeno,
you need to add "nolapic" to the boot options in grub.  This will take care of the shutdown issue.

Edit /boot/grub/menu.lst.  Look for the section the menu option that you boot from and add "nolapic" to the end of the kernel line.

Let me know if it works.

---

### Post by zeno on 2005-03-24
[QUOTE=Strider]zeno,
you need to add "nolapic" to the boot options in grub.
[/QUOTE]

Thanks a lot to Strider... i have added "nolapic" option and now the laptop shutdowns in the right way!
Excellent trick!

Bye,
zeno

---

