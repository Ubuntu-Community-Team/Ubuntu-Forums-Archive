---
title: "Login Window Settings opens then disappears!"
date: 2008-08-30
forum: General Help
---

### Post by nethtrick on 2008-08-30
I just installed Hardy Heron 8.04.1 and I wanted to disable the obnoxious login window sound, and found a thread that says it's in the System->Administration->Login Window, under the "Accessibility" tab... The "Login Window" dialog opens then disappears before I can do anything!!

I've tried running it from the command line:
$sudo /usr/sbin/gdmsetup
Segmentation fault

I don't get the segmentation fault when I use 'gksudo'... But still the window opens then closes immediately.

Looks like the thing is just plain crashing... So I have two bugs I need to sort out, listed in order of personal priority:

1) Is there at least a way to edit the "drums" login setting without using the graphical gdmsetup tool?

2) What can I do to prevent the gdmsetup tool from crashing?


Thanks!

---

### Post by nethtrick on 2008-08-30
I just installed the recommended updates and it fixed the problem.

---

### Post by rbuergin on 2008-10-11
Hey, 

I've got the same problem. My system should be up to date.. or what update did you, then?

Thx, Greets Reto

---

### Post by nethtrick on 2008-10-11
I did a fresh install from the 8.04.1 Alternate AMD64 CD.

Then I had the problem.

I installed whatever the recommended updates were at that time (August 30th) and the problem was fixed.

Is there a way for me to check my update history? I can give more details then.

---

