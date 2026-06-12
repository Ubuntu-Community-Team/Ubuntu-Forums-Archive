---
title: "Trouble hibernating computer"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by PremierSullivan on 2007-03-08
Im having trouble getting my computer to hibernate.  It wasnt detecting my swap partition originally, and it wont hibernate if there is a usb device in.  Now I got the swap partition working, so I can get it to hibernate correctly if I unplug every usb device.  How can I fix this so that it will hibernate even if usb devices are plugged in?

Im runnig kubuntu edgy 6.10 on a Dell Inspiron E1705

---

### Post by vespo on 2007-03-23
Hi

in /etc/defaults/acpi-suppprt try editing to unload "all" modules before usspend/hibernate

---

