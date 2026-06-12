---
title: "PC clock WAY off (Solved)"
date: 2005-11-15
forum: General Help
---

### Post by fin on 2005-11-15
Since installing Ubuntu my clock is way way off (while running XP). I reset and its fine, but later it goes back to f'd up.

Like right now - it says 3:05am but its really 10:05pm

Help?

Am I being hacked? Is it a bad crystal? Can't be a bad battery... this computer is only 4 months old. MOBO?

---

### Post by Remmelas on 2005-11-15
I'm looking for a solution to this as well, at least, an elegant one.  the problem is in how linux handles clock time, and how windows does.  In windows, the clock is assumed to be what ever time it is locally in your time zone.  In linux, the clock is assumed to be GMT, and then the OS applies a timezone offset.  For example, my timezone is GMT-7(mountain time).  So, the offset is cuz Ubuntu syncs your clock to GMT on boot.

---

### Post by Kokanee on 2005-11-15
You did the same as me.  During the install you would have set the clock to GMT.  This always seems to mess things up for me.  That option needs to be turned off.  Unfortunately I don't know how to change it once it's installed.

---

### Post by earobinson on 2005-11-15
I searched for "time windows" and i found this: [http://www.ubuntuforums.org/showthre...t=time+windows](http://www.ubuntuforums.org/showthre...t=time+windows)
[http://ubuntuforums.org/showthread.php?t=87649](http://ubuntuforums.org/showthread.php?t=87649)

---

### Post by fin on 2005-11-15
[QUOTE=Remmelas]I'm looking for a solution to this as well, at least, an elegant one.  the problem is in how linux handles clock time, and how windows does.  In windows, the clock is assumed to be what ever time it is locally in your time zone.  In linux, the clock is assumed to be GMT, and then the OS applies a timezone offset.  For example, my timezone is GMT-7(mountain time).  So, the offset is cuz Ubuntu syncs your clock to GMT on boot.[/QUOTE]

I assumed that in the SP2 edition of XP, the clock connects with the 'atomic clock' and all should be good.

How does Ubuntu screw that up? Since I haven't booted into it, since my last boot into XP?

Yes, I'm confused.

---

### Post by fin on 2005-11-15
[QUOTE=earobinson]I searched for "time windows" and i found this: [http://www.ubuntuforums.org/showthre...t=time+windows](http://www.ubuntuforums.org/showthre...t=time+windows)
[http://ubuntuforums.org/showthread.php?t=87649](http://ubuntuforums.org/showthread.php?t=87649)[/QUOTE]


Not Found

The requested URL /showthre...t=time+windows was not found on this server.

---

### Post by Remmelas on 2005-11-15
hmm, followed the threads linked earlier, and my clock is in perfect sync in windows and ubuntu now(funny that I actually booted into windows for the first time in 3 months to see if it fixed.)
1- sudo gedit /etc/default/rcS
and change UTC=yes to UTC=no
2- I rebooted into ubuntu so that the clock sync scripts would run(I could have run them manually, but, didn't)
3- Booted into windows just to verify and yup, both are in sync now.

---

### Post by fin on 2005-11-15
[QUOTE=Remmelas]hmm, followed the threads linked earlier, and my clock is in perfect sync in windows and ubuntu now(funny that I actually booted into windows for the first time in 3 months to see if it fixed.)
1- sudo gedit /etc/default/rcS
and change UTC=yes to UTC=no
2- I rebooted into ubuntu so that the clock sync scripts would run(I could have run them manually, but, didn't)
3- Booted into windows just to verify and yup, both are in sync now.[/QUOTE]


Sweet! Thank you.

Guess I need to reinstall now that I have a solution, lol

---

### Post by earobinson on 2005-11-15
the second link worked btw and you dont need to reinstall

---

### Post by fin on 2005-11-15
[QUOTE=earobinson]the second link worked btw and you dont need to reinstall[/QUOTE]


No?

How do I get around this?

---

### Post by fin on 2005-11-16
[QUOTE=fin]No?

How do I get around this?[/QUOTE]


Solved?

---

### Post by fin on 2005-11-16
[QUOTE=fin]Solved?[/QUOTE]


Solved?

My PC clock is still way off.

---

### Post by fin on 2005-11-16
[http://www.metacolo.com/papers/dc11-havenco/photos/sealand-external-behind.jpg](http://www.metacolo.com/papers/dc11-havenco/photos/sealand-external-behind.jpg)

---

