---
title: "Can Dual Boot Slow my Computer?"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by TheNerdAL on 2009-07-22
If I install Ubuntu With Dual Boot, will it slow my Windows and Ubuntu?

I am downloading Ubuntu Using Wubi.:)

---

### Post by yeats on 2009-07-22
What are your computer's specs (processor, memory)?  In general, Ubuntu will run faster than Windows, whether you're dual booting or not.  I've never used Wubi, so I can't speak to that specifically.

---

### Post by Bucky Ball on 2009-07-22
Wubi, probably to definitely. Hard drive install, no. They are not working at the same time. Ubuntu usually faster than MS on separate partition but not always. :)

---

### Post by az on 2009-07-22
No.  Why should it?

Well, there are two small exceptions.  The first is the bootloader - it will prompt you every time you boot and wait a few seconds before booting the default OS.  So that will delay the time it takes to start booting by however many seconds you have it set to.  The second is that Ubuntu takes up disk space.

That in of itself won't slow Windows down at all unless you only leave Windows a very small amount of free space (like less than a Gig).  If you leave it normal amount of free space, you won't notice any difference.

---

### Post by Sef on 2009-07-22
I have installed Wubi and notice no difference except as noted by az in the boot time.

---

### Post by hetx on 2009-07-22
If I remember correctly a Wubi installation uses a virtual hard drive image on the Windows partition. So Ubuntu will run a little slower than a "real" installation but when you're in Windows you wont notice a difference in performance at all.

---

