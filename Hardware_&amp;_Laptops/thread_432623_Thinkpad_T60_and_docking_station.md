---
title: "Thinkpad T60 and docking station?"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by bjorntj on 2007-05-04
Isn't it possible to get those two to cooperate under Ubuntu (Linux)?
I have a external screen I would like to use that support a larger resolution than my laptop, but I can't find a way to make this work..
The Fn - F7 combination doesn't work and I only get the same resolution on my ext. screen as on my laptop, but something is strange there too, because when I start Firefox, the picture disappear from my ext. screen and I have to reboot the get it back...

Anyone please?


Regards,

BTJ

---

### Post by jjordan on 2007-05-04
Yes, it is possible.  I am using a Fujitsu p1510 sitting in a docking station attached to a 20 inch monitor.  Both screens are showing useful, diffrent, information.   I have them set up as a "Twinview" which means that I actually have to X-Windows sessions running.  My mouse moves across both screens and keyboard input goes to whatever window has the focus. I cannot drag a window from one screen to the other although I could set it up to do that.  There are many howto's around to help you set this up.  Look fro "twinhead", "twinview" and xinerama.

Here is a place to start:
[http://help.lockergnome.com/linux/Dual-Head-ATI-Mobility-1300-ftopict416233.html](http://help.lockergnome.com/linux/Dual-Head-ATI-Mobility-1300-ftopict416233.html)

Not really a trivial undertaking but with some study and effort you can do it.

-j

---

### Post by bjorntj on 2007-05-04
Oki, that looks promising... I'll have a look at it, thx.... :)


BTJ

---

### Post by bjorntj on 2007-05-07
Well, I manged to get it to work but I have one problem....

When I try to maximize a program running on the external screen, the monitor just goes blank and the only way to recover is to restart the X-server...

How to do I fix this problem?


BTJ

---

### Post by bjorntj on 2007-05-08
No one knows? btw, it happends when the window get bigger than half the screen also and not only maximized...


BTJ

---

### Post by El Puño on 2008-06-05
> **bjorntj said:**
> No one knows? btw, it happends when the window get bigger than half the screen also and not only maximized...
BTJ


Nope, because it's a major Linux problem in my opinion.


The lack of a functional display control is one of Linux' major problems. I experiense display problems all the time in different situations, and it's very annoying  :mad:  :

- issue with docking station.
- issue when upgrading the nvidia driver and/or the kernel.
- issue when connecting another monitor.


By the way - same problem in Hardy, same problem in Fedora (9), same problems with PcLinuxOS. This means that the problem must be core functionality of the x-server ??


Linux Beating Winblows ?   Not until such basic problems are eliminated !!

---

