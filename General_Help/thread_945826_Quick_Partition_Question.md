---
title: "Quick Partition Question"
date: 2008-10-12
forum: General Help
---

### Post by Emarian on 2008-10-12
I'm about to install Ubuntu on an older computer that has XP and OSx86 installed on it. I don't want GRUB to pick up any of the other operating systems. I've never used the hidden partition feature inside of gParted, but if I flag both partitions as hidden, will that hide them from GRUB until I unhide them?

I'm not comfortable changing settings in the GRUB installer. Personally, I have an idea for another computer. I'd just like to know if the hidden thing will work or not.

---

### Post by Sam on 2008-10-12
I'm not sure about the hidden flag, but why don't you edit the grub menu.lst file after installation ?

At the end of the /boot/grub/menu.lst file, you'll found something like:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional
lock
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Other operating system
lock
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

You just have to remove any OS you don't want by removing its corresponding paragraph.

---

