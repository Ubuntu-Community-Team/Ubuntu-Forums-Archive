---
title: "Windows was reinstalled and ubuntu is completely gone and GRUB cannot be restored"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by rwdrummer on 2009-07-09
I reinstalled windows XP and I guess the mbr and grub got erased.  I tried almost everything on the terminal to try and restore grub.  Everytime I do something (sudo grub >root (hd0,0) setup (hd0)) an error comes up (error 15) (error 17) or you do not have permission or something like that.  When i run fdisk -l it seems to not find anything.  The problem is that apparently it seems as though there is no partition for ubuntu, but I haven't formatted it.  I have really important files in there what can I do to access them.

---

### Post by merlinus on 2009-07-09
Can you boot from the live cd?  If so, open a terminal and post results of
```

sudo fdisk -l
```

---

