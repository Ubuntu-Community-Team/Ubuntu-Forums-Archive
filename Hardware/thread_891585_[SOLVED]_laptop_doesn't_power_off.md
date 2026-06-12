---
title: "[SOLVED] laptop doesn't power off"
date: 2008-08-16
forum: Hardware
---

### Post by shane2peru on 2008-08-16
Ok, I have the most up to date Ubuntu installed and everything is up to date.  I'm using a 32bit computer (the regular ubuntu install)  I have a toshiba Satellite with about 700MB of ram and a 40GB hdd.  Everything is pretty standard, an intel Celeron M processor.  When I shutdown the computer it often doesn't shutdown.  It starts shutting down, and then hangs or something and the light doesn't shut off.  I end up having to hold the power button down the get it to power off.  It has stayed like that all night long because I forget to check that it shut down properly.  This is very annoying problem.  I have searched the forums, and added the force=apci thing to my menu.lst on the boot line, but that hasn't seemed to help much.  Beside that I really don't understand that.  Any ideas or help would greatly be appreciated.  I'm 100% Linux, no windows on this laptop.

Shane

---

### Post by shane2peru on 2008-08-18
Ok, this is a seriously annoying problem that I'm having, and as much as I really love ubuntu, this has already driven me away once.  If someone has any idea it would be greatly appreciated if you would please share!  :confused:

Shane

---

### Post by shane2peru on 2008-08-18
Is this 2008???   I mean really after searching the forums some more I finally dug up some ooooold threads and found a solution.  Here is one:  [http://ubuntuforums.org/showthread.php?t=187186&highlight=laptop+powerdown](http://ubuntuforums.org/showthread.php?t=187186&highlight=laptop+powerdown)   
Reading through this thread **posted in 2006** I found 1.  We still have this same problem after some 4 different releases.  2.  No one is quite sure how to fix it besides trial and error.  At any rate post number 10 helped me adding force=apci lapic  seems to have fixed my problem.  Hopefully this will help someone else.  I must admit, I don't have any understanding of these two items that I added to my menu.lst, but they seem to have helped.

Shane

---

### Post by shane2peru on 2008-08-19
This is not completely solved.  See this bug report:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221316](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221316)

The solution here helped a little, but the real problem is the driver.

Shane

---

