---
title: "Changing the order of the Grub menu??"
date: 2008-07-16
forum: General Help
---

### Post by sirbingo on 2008-07-16
Hey Ya'll,

First off, I am a UBUNTU noob that's slowly learning the ways of Linux.

I've got a duel boot system.  Ubuntu on 1 drive and WinXP on another.

Anywho, I would like to tweak the order of the different operating systems on the initial boot up menu.

Right now the system will automatically boot into UBUNTU after a couple of seconds.  I want to either lengthen that initial delay and/or make the system default to a WinXP boot up.

Whats the best way of going about this.  I have a feeling I need to change something around in Grub perhaps?!?

Thanks!  :-k

---

### Post by scragar on 2008-07-16
```
gksudo gedit /boot/grub/menu.list
```

edit the timeout as you want.

you can also change the default option, although you will need to count up the results(I recomend going for saved, unless you have a raid array).

---

