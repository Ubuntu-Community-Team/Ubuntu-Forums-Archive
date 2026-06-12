---
title: "Wrong Grub"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Wolfpack Fan on 2009-02-24
Recently I installed OpenSuse (dual Boot with Ubuntu 8.04.)  It is installed on a partition on the same hard drive as Ubuntu.  When I boot my computer I get the grub that was created on the Suse partition and not Ubuntu. I would like to remove Suse, but I am worried about losing Grub.  Can anyone give me pointers?

Thanks

---

### Post by caljohnsmith on 2009-02-24
You can use the following to reinstall Grub to the MBR and point it to your Ubuntu partition for its boot files (and also menu.lst):
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition and the OpenSUSE partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use the one that corresponds to Ubuntu:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you are unsure which (hdX,Y) corresponds to the Ubuntu partition, note that:
```
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3
(hd0,3) = sda4
...etc.
```
Let me know how that goes.

---

### Post by Wolfpack Fan on 2009-02-25
I greatly appreciate your help.

It worked like a charm.

Thanks,
Chris

---

### Post by caljohnsmith on 2009-02-25
Glad that worked OK; cheers and enjoy your Ubuntu install. :)

---

