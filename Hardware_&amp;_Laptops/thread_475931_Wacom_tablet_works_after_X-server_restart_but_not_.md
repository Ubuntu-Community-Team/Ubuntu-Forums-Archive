---
title: "Wacom tablet works after X-server restart but not after a straight boot."
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by thaines on 2007-06-16
Title says it all really, I'm running Ubuntu Feisty Fawn (7.04), the 64 bit x86 version and using a Wacom Volito 2. After I boot the tablet does not work if I log in straight away, well it works as a mouse, but Gimp et al will not detect its pressure sensitivity. wacdump shows the drivers are working fine.

If I boot the computer and then reboot X and then login it works fine though, so I have to conclude that the boot order is wrong between the wacom driver and something else. Presumably some kind of service/registry that acts as the go between for the driver and programs like the gimp.

Obviously this problem is not critical, its just tedious, plus I tend to forget to reboot x after a normal boot! So, anyone know what it is I likely need to reorder, and where I go to reorder it?

Thanks to all in advance,
Tom

---

