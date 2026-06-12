---
title: "USB Mouse woes"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by terrapin on 2006-07-13
I have a Logitech cordless usb mouse and it works fine for 10 or 15 minutes after I boot up and then quits working completely.

This same mouse has been working perfectly up until today.

Thought it might have something to do with /etc/X11/xorg.conf because I recently installed a proprietary driver from ATI, so I reverted to my backed-up version of xorg.conf, rebooted, mouse worked for 10 min then stopped :-k 

Perhaps an update release broke it?

---

### Post by sturmdogg on 2006-07-13
What laptop are you using? I'm having the same problem with my Asus A6R. Apparently there are issues with the fglrx drivers , x200m cards and ubuntu.

---

### Post by terrapin on 2006-07-13
I have a Toshiba Satellite L25-1216S, dual boot XP/Dapper system. Mouse works great in XP.

I do have an ATI x200 card
And yes... yesterday, I installed the fglrx drivers (I do remember noticing odd mouse activity yesterday).

Maybe the solution is to uninstall fglrx?

---

### Post by terrapin on 2006-07-13
I think the solution is this:

Disable fglrx in /etc/X11/xorg.conf and switch back to ati device driver. This isn't the optimal situation - I'd like to be able to use fglrx - but that's what I get for having a crappy card

---

