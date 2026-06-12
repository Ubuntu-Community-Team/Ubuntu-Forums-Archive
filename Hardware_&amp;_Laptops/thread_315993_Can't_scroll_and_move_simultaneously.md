---
title: "Can't scroll and move simultaneously"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by samurai1200 on 2006-12-10
Weirdest. Problem. Evar. (I think.)

(Mouse: MS IntelliMouse Explorer 4.0)

On any window (be it Firefox, a terminal, a file browser... anything), I cannot move the cursor around and scroll simultaneously. This seems like a minute matter, but since the mouse has to be completely still to scroll, it becomes a great pain in the wrist and mind to have to focus on something like that.

I have verified that this is actually happening by running xev and testing it there. Scrolling only works when no input is coming in from the eye of my mouse (which is the only thing that produces "constant" input).

I have searched this forum and Google for days upon days trying to find a fix, but nobody seems to have a similar problem.  The strangest part -- I only have this problem SOMETIMES. Sometimes, I'll boot the computer and it'll work fine (i can scroll and move the cursor simultaneously), and other times, it won't.  However, since I installed Beryl, it seems to be happening more often than not... **but** this could very well be a product of my imagination.

My comp:
ASUS M2N32-SLI Deluxe Wifi Edition
AMD Athlon X2 3800+
eVGA NVidia Geforce 7600GT KO (256mb)
1gb Corsair DDR800 memory (128-bit, dual-channel)
160gb Seagate 7200rpm SATA HDD (Windows XP Pro x64)
80gb Seagate 7200rpm SATA HDD (Ubuntu Edgy Knot 3)

$ uname --all
Linux daniel-linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Thanks to all in advance.

---

### Post by The Muffin Man on 2006-12-10
I don't think this is such a weird problem, because I have it too, and it seems to be a relatively common problem in the google-ing that I have done.  For me, however, it happens 100% of the time.  I'm running beryl and imwheel (for the mouse buttons) on an otherwise unchanged edgy install.

---

### Post by samurai1200 on 2006-12-11
You ever find any workarounds (whether or not they actually helped you)?

---

### Post by The Muffin Man on 2006-12-11
I haven't found anything that works yet, though i have gotten the back/forward buttons to work.  It seems to me like it's not just an easy fix, and I'm probably just gonna buy a new mouse (this one's a loaner anyways).  But I'd like to find a fix...I'm talking to you, linux gods...

---

### Post by elcu on 2007-02-22
Wow, I never noticed it until I saw this thread.  Now it's starting to bug me too.  Any updates on a possible fix besides using a different mouse?

Explorer V4.0A, Ubuntu Edgy.

---

### Post by samurai1200 on 2007-02-22
Well, I havent used Ubuntu much since the last kernel patch or whatever, since it broke my X and im too lazy to fix it, but i just updated/flashed my bios (im on an asus board, nforce 590 chipset) and now the mouse-freezing and moving/scrolling problem has apparently gone away... i'm sure good 'ol edgy will prove me wrong soon enough.

---

### Post by elcu on 2007-02-23
It actually occurs in Windows too - at least with the builtin OS driver.

I noticed it playing an FPS and the behaviour is there in Firefox.

---

### Post by skiingdomo on 2007-05-20
Hi

I now have this problem too.

I had it in windows (before switching to ubuntu). in windows you just need to install the mouse driver from the CD.

I didnt have this problem with ubuntu when Iinstalled, the day 7.04 came out. This weekend Ihad to unplug and move my computer, and now I have this problem. 


God it is annoying. anyone had any luck?

---

