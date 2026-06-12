---
title: "Little black dots to left of screen?"
date: 2008-07-26
forum: General Help
---

### Post by toxicgtr on 2008-07-26
Hey,

Just recently after applying some updates have discovered about 15 black dots at the top left of the screen. Is there any way to get rid of them?

Screenshot, you cant see all of them but there in that general area:

[[IMG]http://img67.imageshack.us/img67/7541/screenshot1hn9.th.png[/IMG]](http://img67.imageshack.us/my.php?image=screenshot1hn9.png)

---

### Post by ProbablyX on 2008-07-26
Have you restarted after applying the updates?

---

### Post by toxicgtr on 2008-07-26
Yip, was a few days ago.

---

### Post by ProbablyX on 2008-07-26
> **toxicgtr said:**
> Yip, was a few days ago.

Are they there when you boot, login or do they appear after you've logged on?

---

### Post by ProbablyX on 2008-07-27
Do you have an ATI graphics card?
If so I hear their latest drivers can cause graphics corruption

---

### Post by Addie MacGruer on 2008-09-24
Hi guys.

I got these when I changed to Hardy Heron.  It seems to be something up with Xorg and the Nvidia drivers.  To get rid of them, you need to edit your kernel line in /boot/grub/menu.lst to choose an appropriate vga= setting.  My 8800GT works with vga=773, but YMMV.

They'll also disappear if you change to a tty and back, or reset the x-server (ctrl-alt-backspace, or ctrl-alt-F1 ctrl-alt-F7).

Addie.

also in:

[http://ubuntuforums.org/showthread.php?t=784045](http://ubuntuforums.org/showthread.php?t=784045)

---

