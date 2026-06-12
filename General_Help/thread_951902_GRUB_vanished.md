---
title: "GRUB vanished"
date: 2008-10-18
forum: General Help
---

### Post by L-mental on 2008-10-18
I have my dual boot notebook, with both XP and Ubuntu 8.04.
So everything was OK, but I don't know why yesterday I started up the computer to find out it goes to windows without the grub screen. If I start from the Ubuntu CD, I can see the Ubuntu partition... but I don't know how to restore the grub screen so I can choose.
I have just 1 hard disk, with 50G for XP and 40G to Ubuntu. 

This is the second time it happens, but I cannot remember how I solved it the first time... I just remember it took me like a week... but now I don't have that time, so here I am asking for some help!!

---

### Post by caljohnsmith on 2008-10-18
From the Live CD, open a terminal (applications > accessories > terminal), and try the following:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know if that is enough to restore your Grub, or if you get other errors on start up. :)

---

### Post by L-mental on 2008-10-18
OK, lesson learned.

You're absolutely right, of course.
Linux administration handbook, second edition, page 28.
[www.gnu.org/software/grub/manual](www.gnu.org/software/grub/manual)

so tonight i'm staying awake to study the GRUB manual. Way to go... it's a long journey from user to admin, and tonight i'm starting to understand why the experience it's showed on coffe levels!!!

THX!!

PS:Got no smiley with the coffee!

---

### Post by caljohnsmith on 2008-10-18
Glad to help out, and if you are interested in learning more about Grub, a more practical guide than the official Grub manual can be found at Herman's website:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

Anyway, glad it worked; cheers and have fun. :)

---

