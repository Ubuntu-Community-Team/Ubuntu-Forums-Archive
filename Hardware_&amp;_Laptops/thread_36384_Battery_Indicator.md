---
title: "Battery Indicator"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by reset_button on 2005-05-23
Hey all,

Just wondering why my battery indicator never changes.  I seem to remember that you need to add something to grub.conf, but I don't remember what, and I don't seem to have a grub.conf file.

I appreciate any suggestions.

---

### Post by dave9191 on 2005-05-23
You have a /boot/grub/menu.lst file instead. As for adding something to the config file, it would most likely be a command for the kernel. Google your laptop model + battery , and something might come up. 

Dave

---

### Post by Arthemys on 2005-05-23
It's either
apm = on
or
acpi = on

Try one, then the other, apm is older, so use acpi if you can.

---

