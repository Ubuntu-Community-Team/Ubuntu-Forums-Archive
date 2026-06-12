---
title: "Removing Boot Menu"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by jgirata on 2009-06-17
Hi, I recently installed Ubuntu Easy Peasy on an Asus Eee PC.  I realize that Easy Peasy has its own forum, but I think this is more of a general Ubuntu question.

When Ubuntu boots, it first brings up a menu that asks me to select between the normal boot, safe mode, and just the command line.  Is there a way to remove this menu and default to the normal OS?

---

### Post by sedawk on 2009-06-17
I think the definition for these menus is in file /boot/grub/menu.lst .

I do not recommend to remove any of the entries.

What you can do is to reduce the timeout, so this menu will be
gone after 1-2 seconds and boot the default entry.

---

### Post by jgirata on 2009-06-17
Thank you for your quick reply.

I'll just set it to 1 second, that will be good enough.

Thanks again!

---

