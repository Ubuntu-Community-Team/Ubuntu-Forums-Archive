---
title: "Touchpad Scrolling broken"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by torstenaf on 2006-12-15
The touchpad on my laptop doesn't scroll anymore.  I did a bunch of updates that were requested (just agreed to everything).  I rebooted to use my scanner in Win XP (for a bank program that doesn't work on Linux at all, speaks directly to the scanner) and when I came back into Linux, no scroll.

I do have a **synaptics** device listed in ```
/etc/X11/xorg.conf
```.

This is Ubuntu 6.10.

Thanks,
Torsten

---

### Post by torstenaf on 2006-12-17
I installed **ksynaptics** package and added **acpi=force** to my ```
/boot/grub/menu.lst 
```as well as running **grub-install**, and now the scroll function is back.

---

