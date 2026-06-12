---
title: "Installed GRUB to the wrong partition"
date: 2008-10-12
forum: General Help
---

### Post by Yacoby on 2008-10-12
Heya.
First, sorry if this is in the wrong place, forum is rather bit.

By mistake, I did this:
```
grub-install /dev/sda1
```
Which is where windows is :(

When booting grub, windows is no longer listed, and I can't access the files and unfortunately I have a lot of data on there that I would quite like to keep.

Does anyone have any easy suggestions on how to fix it with very low chance of screwing up the data on there?

EDIT:
```
sudo fdisk -lu
```
Seems to show the windows partition. hmm
Showever, when looking at it, it is empty


fixboot semi works, I can get to the files now.

---

### Post by caljohnsmith on 2008-10-12
Using "fixboot" from the Windows Install CD (as you mentioned) is the way to fix the Windows partition boot sector if something happens to it, like in your case installing Grub there. That should make your Windows partition bootable again, so if you don't see a choice for Windows in your Grub menu, you just need to add one:
```
gksudo gedit /boot/grub/menu.lst
```
And add:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
Let me know how it goes.

---

