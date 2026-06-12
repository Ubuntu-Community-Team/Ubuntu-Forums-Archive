---
title: "Strange automount problem"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by kurbacik on 2006-06-28
I have a quirky problem: when I connect my digital camera through usb cable to my laptop, automount works on the usb port on the right side of my laptop, while it doesn't work at all (not even manaul mounting) for the two usb ports on the left hand side. The laptop does absolutely nothing if the usb cable is plugged in on the left side. I can see this with dmesg and looking at /var/log/message. This behavior is new to me, I've never had this problem previously with Dapper and with Breezy. Does anybody have a similar problem? I run Ubuntu 64bit on an HP zv5000 laptop.

:confused:

---

### Post by kurbacik on 2006-07-05
I have looked into this problem of mine, and now I've found out that if I unload the ohci_hcd module and then reinstall it, then the two left-hand usb ports on my laptop work normally again. At this point I wish to find a way that lets me unload and reload this module automatically instead of having to do it by hand every time.

---

### Post by kurbacik on 2006-07-05
Just by putting the module ochi_hcd in the blacklist file in /etc/modprobe.d/blacklist and inserting the module in /etc/modules doesn't work. I still get the only working result when I unload and reload manually the module.

---

