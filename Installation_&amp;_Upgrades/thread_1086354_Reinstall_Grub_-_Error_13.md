---
title: "Reinstall Grub - Error 13"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by jallp82 on 2009-03-03
**Had to change (hd0,0) to (hd0,2)**



I installed Ubuntu right the first time, Vista first then Ubuntu.  I ended up having to reinstall Vista to a new partition so obviously it over wrote the Grub boot loader.  I followed the official documentation at [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) and it installed and recognized both operating systems, but I'm having issues getting it to actually load the OS's.  

At first it wasn't letting me load either system, gave a Error 22 for Ubuntu and Error 13 for Vista.  I got the Ubuntu fixed, it screwed up the (hd0,1) command.

Here is the Vista part from the menu.lst file

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

