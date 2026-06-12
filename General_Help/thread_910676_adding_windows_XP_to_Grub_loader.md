---
title: "adding windows XP to Grub loader"
date: 2008-09-04
forum: General Help
---

### Post by joobleblob on 2008-09-04
I'll be quick  and breif.

I installed ubuntu hardy first THEN windows XP so their partitions are in that order
I had some trouble so remounted grub, windows XP doesn't show on grub loader
what might I need to do to get it as an option, I'd like to keep grub, I have a basic knowlege of terminal but most things I'll need explicit instructions for and I have the boot/grub/menu.lst open and ready for editing if needed

thanks in advance

-disclaimer to prevent public scorn at my name, I only use windows to run games, ubuntu zealots all the way! -

---

### Post by kk0sse54 on 2008-09-04
open the terminal and type ```
sudo gedit /boot/grub/menu.lst
``` scroll down and under Ubuntu add an entry for Windows pointing grub to the correct partition

---

### Post by joobleblob on 2008-09-04
pointing it in what way? what parameters would I need to use?
an example would be useful, thanks for your prompt response

---

### Post by kk0sse54 on 2008-09-04
Here's an example of mine :) ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```
really what you need to find out is where root is located .Instead of the normal sda1 or sda2 instead it needs to be hd0,1 or hd0,2 look at your Ubuntu entry where that is located, if windows comes after then its jus the next number up.

---

### Post by zvacet on 2008-09-04
```
sudo fdisk -l
```

and you will see on witch partition Windows are.If it is for example sda2 you will put in grub (hd0,1) and if it is sda3 it will be (hd0,2)...When you find out where Windows are you can follow **C!oud´s** advice.

---

