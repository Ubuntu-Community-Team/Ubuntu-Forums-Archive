---
title: "Issue shutting down an ACER laptop"
date: 2008-10-14
forum: Hardware
---

### Post by skippy2222 on 2008-10-14
hello, 

I'm new to this forum and a new Ubuntu user, I installed 8.04 desktop edition yesterday, it's been a while since i used a Linux distro, although I work on solaris every day. I'm no Linux expert but having a UNIX background I somewhat familiar with the jargon.

The installation was a painless experience, I halved a disc (or gave a logical partition) to this installation to try it out before completely removing windows. My reasons are the main reason I was keeping windows before is now no longer an issue so I am free to remove it from the laptop.

Anyway, onto the problem, while trying to shut down some type pf draw routine happened and drew some whole and broken white lines across the screen (it almost spookily looked like the cover to a ps2 game called manhunt) anyway these lines faded over the next 20 minutes to very muted colours but the machine did not shut down until I intervened and used the power button.

could some of the experienced hands advise is this a known issue in Ubuntu? Does it have a bug number I can follow?

Obviously the aesthetic possibilities of Ubuntu are quite appealing can anyone advise wether this stock Acer laptop 1GB ram can handle such settings?

If I have covered old ground here I apologise, I am still working my way round the site at the moment.

best regards

---

### Post by nixscripter on 2008-10-15
Definitely sounds like a video graphics problem.

When it happens, try killing the X server (Cntl-Alt-Backspace) and look at the log (/var/log/Xorg.**n**.log for some number n). Does the driver complain?

---

### Post by skippy2222 on 2008-10-21
thanks for the advice, for some reason it now doesn't complain or repeat the issue, without extra software or any corrective measures, bizarre, Id like to know what I have done to solve it.....

---

