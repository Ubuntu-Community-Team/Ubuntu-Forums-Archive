---
title: "Start screen corrupted"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by kowalinator on 2009-06-23
Ok so i just upgraded to Ubuntu 9.04 and it was the biggest mistake of my life! Im still new to linux so i just upgraded through the updater and now when it try to start ubuntu it goes to the loader screen, and then its gets all messed up, random dots, some streaks of color, etc. 

I have an ati radeon 4870, im guessing this is the problem since ati isnt friendly with linux apparently. So ya just wanted to know if there is a way to bypass it or if i can roll back to 8.10 where there wasnt any problems :D. I have a dual-boot with windows if that matters...

---

### Post by raymondh on 2009-06-23
> **kowalinator said:**
> Ok so i just upgraded to Ubuntu 9.04 and it was the biggest mistake of my life! Im still new to linux so i just upgraded through the updater and now when it try to start ubuntu it goes to the loader screen, and then its gets all messed up, random dots, some streaks of color, etc. 

I have an ati radeon 4870, im guessing this is the problem since ati isnt friendly with linux apparently. So ya just wanted to know if there is a way to bypass it or if i can roll back to 8.10 where there wasnt any problems :D. I have a dual-boot with windows if that matters...


I am assuming you have updated/installed any hardware drivers (system > admin > hardware drivers) ....

Am sorry, there is no known NETWORK downgrade hence are looking at a fresh re-install of 8.10.  Now, if you have a separate /home partition, you can just re-write the root (/) partition whilst making sure /Home is NOT FORMATTED.  Should you have a straight-up install where everyting is within root, you can likewise point the installer to the same partition hence leaving windows alone.

Should you require assitance in manual installations, let the forum know.

Good luck.

---

### Post by kowalinator on 2009-06-23
I cant upgrade the drivers since i cant even get into ubuntu, the loader comes up and as soon as the bar fills up the screen gets all messed up. If i could get into ubuntu i think i should be able to figure it out, but getting there is the problem :(

---

