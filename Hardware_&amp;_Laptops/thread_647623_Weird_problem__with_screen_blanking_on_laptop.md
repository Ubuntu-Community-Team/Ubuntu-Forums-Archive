---
title: "Weird problem  with screen blanking on laptop"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by MoridinBG on 2007-12-22
I've got HP TC4200 TabletPC and it has got really weird problem.
Almost everything works out-of-the box, with some issues:

1. The battery shows some really strange values about remaining charge, but it would be because it is almost dead.
2. It seems that newer versions of wacom-tools and xorg-input-wacom does not support the touchscreen. I had to downgrade to wacom-tools version 0.7.2

And the most annoying issue, stil nsolved is that if I close the lid of the laptop the screen blanks, which is OK, but then if I open it and activate it, the screen blanks again after some period of time. Moving the mouse/stylus/keyboard does not stop it. After something like 45 seconds the screen just blanks. After reactivating it it blanks again after some more 45 seconds! Pluging/unpluging the power does not prevent it. The only solution is restart!  It is REALY ANNOYING reactivating the screen every 45 seconds! It has done this at least 5 or 6 times, while I was writing this post.

---

### Post by MoridinBG on 2007-12-28
BUMP!

It's really annoying! If I close the lid the screen starts blanking itself every 45 seconds. Doesn't matter if I'm doing anything. dmesg and /var/log/messages contain nothing about this...

---

### Post by MoridinBG on 2007-12-30
Not even a clue about that?

---

### Post by rg_stephens on 2008-01-09
I have a tc4200 that I've had for more than a year. I have the problem when I come out of suspend mode, but the screen comes back when I move the mouse. I assume this is a bug in Gnome Power Manager, because I can shut this down and the problem goes away, although I lose a lot of features. I also found that I can run gconf-editor from the command prompt and I can tweak a lot of display settings.

I was having intermittent display problems back when I was running WinXP. I think it's just a buggy video card or driver. Let me know if you fix it.

---

### Post by jacktar on 2008-01-10
Some of the 4000 series suffer from intermittent backlight failure. This is caused by oxidation of the contacts on the lamp to inverter board connector.

You can fix this by re-seating the connector 3 or 4 times. It is at the bottom of the screen under the bezel.

---

### Post by jacktar on 2008-01-10
Hang on .. I'm thinking of Toshiba 4000 !  Sorry about the confusion.

---

