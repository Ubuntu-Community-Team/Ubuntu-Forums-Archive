---
title: "Gigantic Urgent Error Please View!!!"
date: 2008-07-10
forum: General Help
---

### Post by racie on 2008-07-10
I rebooted Ubuntu after doing a how-to that worked for people with my exact same problem.  I used terminal and ONLY copied and pasted, but after I rebooted it, this screen came up:
[img]http://img87.imageshack.us/img87/93/giganticuserrorqx8.png[/img]

What in the world does this mean and what do I do?  I am dual-booting my computer, so right now I'm on Vista because Ubuntu isn't working.  What do I type at this screen to make it continue?  I follow the how-to exactly, being careful in each step.  Unfortunately, I can't seem to find which thread it was in, but I CAN'T GET PAST THIS SCREEN!  HELP!

---

### Post by wannadumpwindows on 2008-07-10
What were you trying to do?

That could be caused by all kinds of things. People need a little more info to be able to help you.

---

### Post by racie on 2008-07-11
Oh yeah sorry, I was trying to get my wireless card to work.  I can't find the how-to, thought.  It was in the middle of a huge thread.  It was a post about a how-to for an Atheros AR5007 wireless card that apparently worked for many people.

---

### Post by wannadumpwindows on 2008-07-11
Odd that messing around with your wireless card dropped you to a busybox on login . . . .

Ive got the exact same card, and had to mess with it for weeks to get it working, screwing things up left and right, and never had any problems like that.

EDIT: Not even thinking. LoL.

---

### Post by VMC on 2008-07-11
Well lets start with some basics. Dump the file systems lists, Grub list to start.

From the Livecd Terminal type this:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

by the way how are you running Vista? Is it on another computer.

---

### Post by racie on 2008-07-11
No, I'm dual-booting. I don't have a LiveCD either.  I installed Ubuntu from Wubi.

---

