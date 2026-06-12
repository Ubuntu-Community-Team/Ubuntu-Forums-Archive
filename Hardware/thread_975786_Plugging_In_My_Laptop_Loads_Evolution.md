---
title: "Plugging In My Laptop Loads Evolution"
date: 2008-11-08
forum: Hardware
---

### Post by woodsby on 2008-11-08
Anyone else having this problem?  Everytime I plug in my eee pc 900a running ubuntu 8.10, it tries to load evolution.  I am running the eeepc lean kernel, but I'm pretty sure this was happening with the generic 2.6.27-7 kernel - before I uninstalled it.  So, I uninstalled evolution - this didn't work.  I uninstalled Nautilus-sendto - didn't work either.  I searched udev for anything that may be calling evolution - no luck.  I'm at a loss... anyone have any ideas?

---

### Post by 3guk on 2008-11-10
This occurs because the asus-acpi module sends hotkey events when connecting to AC power with the wrong code (for the Eee; it's surely the right one on other Asus laptops).

Comment out all lines in /etc/acpi/events/asus-mail (by prepending a #), and restart acpid with sudo /etc/init.d/acpid restart.

---

### Post by woodsby on 2008-11-11
> **3guk said:**
> This occurs because the asus-acpi module sends hotkey events when connecting to AC power with the wrong code (for the Eee; it's surely the right one on other Asus laptops).

Comment out all lines in /etc/acpi/events/asus-mail (by prepending a #), and restart acpid with sudo /etc/init.d/acpid restart.

Thanks.  I commented out the lines, I'll check it when I get home.

---

