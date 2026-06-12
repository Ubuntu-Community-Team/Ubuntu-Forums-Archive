---
title: "[SOLVED] Files &amp;quot;lock&amp;quot; when transferred over from cd or dvd (Hardy)"
date: 2008-07-13
forum: General Help
---

### Post by fullmetalgerbil on 2008-07-13
Ok, here's what's going on and its a recurring problem. When I load files, music,pictures,etc., onto my machine from a cd or dvd the files appear in my folders with a cute little padlock icon next to them. This happened in April when I first installed Hardy on my desktop, it happened again when I installed it on my laptop, and its happening again now that I installed on a different desktop. Here's the thing-back in April I brought this up here because I thought it was a permissions issue, since any time I tried to move or delete the locked files I got a prompt saying I did not have permission.
 So, following peoples advice from the forum here I tried to sudo -rm -rf the files while logged in as root and still nothing. I eventually just gave up and loaded my computer with Ubuntu 7.10-which did not have this problem.
However, I'm back using 8.10 again. And again, anything I try to load from cd/dvd gets locked.
Any ideas?

---

### Post by tuxxy on 2008-07-14
Have you tried changing the files permissions?

---

### Post by mc4man on 2008-07-14
read thru here, any questions let me know
[http://ubuntuforums.org/showthread.php?p=5259083#post5259083](http://ubuntuforums.org/showthread.php?p=5259083#post5259083)

---

### Post by jerome1232 on 2008-07-14
Yeah they retain the read-only attribute, just right click 'em and select permissions, give yourself read and write access.

---

### Post by fullmetalgerbil on 2008-07-14
Problem solved, thanks a bunch folx!

---

### Post by CatKiller on 2008-07-14
Don't forget to mark the thread as Solved.

---

