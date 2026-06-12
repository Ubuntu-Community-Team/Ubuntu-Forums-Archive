---
title: "Loaded ubuntu dual with XP, but GRUB won't boot XP"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by eric.stone on 2006-02-04
Worthy Ones,
I just loaded ubuntu, dual boot on my son's emachine which is running 
XP.  Ubuntu runs nicely, but when I select XP in the GRUB loader it hangs with the message, "chainloader  +1".  Thanks in advance to all.
Eric
:-k

---

### Post by Herman on 2006-02-04
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")
Here's (above) a link to a web page I made which explains all about how to find your /boot/grub/menu.lst file and how to check it for mistakes and edit the file to make your computer boot up the way you want. Not only can you make it boot, you can also do some pretty clever tricks with GRUB when you know how. This web-page will get you started I hope. You can probably skip the top half if you find it excessive. 
The bottom of the last illustration may be relevant to your problem. Here's what mine's like for an example:```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
``` Have a look and compare yours to mine and see if it's the same or not. 
If your computer is like mine and has one hard disk, with Windows XP on the first partition, it should work to make a backup of your menu.lst, and then edit your 'menu.lst' entry and make it like mine.
The way to do that is explained in the link.
If you have more than one disk, or it's sata, then you might have to do something different. I have no experience with those, I have read about them though. Someone that has one and has multi disk/sata experience would be a better help if that is the case. :D (Herman)

---

### Post by eric.stone on 2006-02-04
Thanks, Herman.

---

