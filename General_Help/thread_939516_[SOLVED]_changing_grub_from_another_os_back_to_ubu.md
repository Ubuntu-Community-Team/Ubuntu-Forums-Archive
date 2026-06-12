---
title: "[SOLVED] changing grub from another os back to ubuntu"
date: 2008-10-06
forum: General Help
---

### Post by SteveNorman on 2008-10-06
So I tried to install Debian again and cant boot it. It now owns grub. 

How can I get the Ubuntu grub as the default?

Note this is not the same as editing /boot/grub/menu.lst to pick which one loads first, but is an issue with getting the grub from ubuntu to be the default from which to choose os's 

In other words,, the grub from ubuntu was overwritten when I installed debian. I cannot edit this because I cant get debian to boot. So I want ubuntu's grub to be the loader vs debians

---

### Post by anystupidname on 2008-10-06
You'll have to boot from a liveCD
mount your ubuntu file system and
reinstall grub

something like this:```

sudo mount -t ext3 /dev/sda2 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by SteveNorman on 2008-10-06
thanks,,I will give it a go when I get home tonight.

---

### Post by geirha on 2008-10-06
If you are able to boot into ubuntu from the current grub, do that, and run ```
sudo grub-install
```

If not, use anystupidname's suggestion, though you'll need sudo in front of those commands.

---

### Post by SteveNorman on 2008-10-07
I still can boot into ubuntu,geirha after sudo grub-install do I do what anystupidname says?

---

### Post by geirha on 2008-10-07
sudo grub-install run from ubuntu should reinstall ubuntu's grub, so that should be enough. 

However I see that command was incomplete, you need to specify the harddrive to install on too, so ```
sudo grub-install /dev/sda
```

---

### Post by caljohnsmith on 2008-10-07
Using "grub-install" is not necessary unless you don't have Grub's files in place in the /boot/grub directory, which is not your case; it could work for you, but it is an overkill. :) Instead you can use the "root" and "setup" commands in the Grub CLI:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
The above commands should return your Ubuntu/Debian partitions in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4). Choose which one is Ubuntu, and use it as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR (Master Boot Record) and point Grub to whichever partition you specified with "root" for Grub's files (menu.lst, etc). Let me know how it goes or if you run into problems.

---

### Post by SteveNorman on 2008-10-08
caljohnsmith this worked perfectly. Thank you all very much for the help!

---

### Post by caljohnsmith on 2008-10-08
That's great news, glad it worked Steve. Cheers and have fun with Ubuntu. :)

---

