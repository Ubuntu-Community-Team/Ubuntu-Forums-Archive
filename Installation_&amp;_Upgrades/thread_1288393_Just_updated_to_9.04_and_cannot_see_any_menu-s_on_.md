---
title: "Just updated to 9.04 and cannot see any menu-s on desktop"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by zPwn on 2009-10-11
Hi guys, 

well here's the thing, I recently updated from 8.10 to 9.04 and I cannot see the menu's on the desktop. 

Only thing I can use, is the run cmd (right click mouse), to access things, but I doubt that it was meant to be like that.. 

was my upgrade made in an unproper way ? it this fixable in any way..? 

thanks.

coz right now Im typing from the gnome, and I'd really like to be able to use my kde as well.

cheers

---

### Post by Intrepid Ibex on 2009-10-11
Hmm, you could try: ```
mv ~/.local ~/Desktop/local-backup
```, which will move your menu configuration (.local folder) to Desktop - and create a new one with default settings.

I once had exactly this kinda issue due my beginnings with Arch.

**E:** I had corrupted settings with my menu after messing around with it a bit... was kinda frustrated after first trying to figure out what the problem was and after that I had to 'redo' my menu.

If this works, you will of course lose all your settings, but ... gah... :/

---

### Post by zPwn on 2009-10-11
> **Intrepid Ibex said:**
> Hmm, you could try: ```
mv ~/.local ~/Desktop/local-backup
```, which will move your menu configuration (.local folder) to Desktop - and create a new one with default settings.

I once had exactly this kinda issue due my beginnings with Arch.

If this works, you will of course lose all your settings, but ... gah... :/

thanks, i'll surely try it out when I get home. Uhm, which settings am I going to lose, however?

---

### Post by Intrepid Ibex on 2009-10-11
I mean the menu settings, with the addition of some other stuff..

Actually good thing you asked for that, as it made me think about the situation a little deeper. So before executing the command I gave you, you should probably try this one first:

> mv ~/.local/share/applications ~/Desktop/local-backup

.. as it will only move the .desktop files that should only be the ones that have the (in addition of some minor configuration files) information used in your menu. This way you will loose as little of your settings as possible.

Cheers (or not if it doesn't work)!

---

### Post by zPwn on 2009-10-12
thanks again, but nothing changed after moving that folder to the desktop. My actual problem is that I'm not seeing any of the menus to navigate ~ maybe a picture explains better than words : 

[[IMG]http://img504.imageshack.us/img504/4708/snapshot1u.th.png[/IMG]](http://img504.imageshack.us/i/snapshot1u.png/)

[[IMG]http://img504.imageshack.us/img504/3189/snapshot2w.th.png[/IMG]](http://img504.imageshack.us/i/snapshot2w.png/)

---

### Post by zPwn on 2009-10-13
yawn, anybody guys? :>

---

### Post by McNils on 2009-10-13
Try to move your ~/.kde katalogs instead.

---

### Post by Intrepid Ibex on 2009-10-14
Yes, ~/.kde4 (if it exists in kde) is one possibility too.

---

### Post by zPwn on 2009-10-16
well guys, thanks for the input.. but those things didn't work. I just updated to 9.10 and now everything seems to be fine! Its kind of a weird issue I got there with 9.04...

---

### Post by Intrepid Ibex on 2010-02-21
It is indeed a better solution to do a fresh install, instead of updating UBUNTU, which is not a rolling release distribution. But then again there's no such thing as a perfect newbie operating system. That's why I use arch :).

Had to bump in order to tell this...

---

