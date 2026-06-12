---
title: "Lilo problem after update"
date: 2005-11-16
forum: General Help
---

### Post by klemens on 2005-11-16
I have just installed breezy on my laptop.
After a full update, it doesn't reboot anymore.

I tried to get to the config file of lilo with the live cd, but i don't know how to navigate through the harddisk.

my boot harddisk is /dev/hda5 but can't mount it.
Pls help!

---

### Post by Kyral on 2005-11-16
The problem is that Ubuntu doesn't use LILO. It uses GRUB :D

Try loading the LiveCD and opening a terminal and using "install-grub" or something like that(can't remember command)

---

