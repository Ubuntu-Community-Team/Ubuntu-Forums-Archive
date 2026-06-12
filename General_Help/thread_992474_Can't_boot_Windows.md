---
title: "Can't boot Windows"
date: 2008-11-24
forum: General Help
---

### Post by woopud on 2008-11-24
Just installed 8.10 on my HP laptop which had XP on it, hard drive was divided in two partition with XP on the first one and I installed Ubuntu on the second partition (50 GB each).  For some reason Windows doesn't show up in GRUB, I can still access the Windows partition from Ubuntu.  How do I add Windows to my GRUB ?

Bert

---

### Post by adult swim on 2008-11-24
push alt+f2 and run ```
gksudo gedit /boot/grub/menu.lst
``` scroll down to the bottom where your other grub entries are and add ```
title		Windows
root		(hdX,Y)
chainloader	+1
```
where X and Y are your disk number and partition number respectively.  say you have windows on your only hard drive and it is on the second partition you would use root (hd0,1)  the numbers start couting from 0, that is why the second partition is noted as 1.

---

