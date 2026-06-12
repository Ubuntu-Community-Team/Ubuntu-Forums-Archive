---
title: "better or audible low battery warning"
date: 2008-08-16
forum: General Help
---

### Post by bailey86 on 2008-08-16
Hi,

I keep getting caught out by my laptop battery running out.

Now I know I get the 16 minutes left pop-up - but it doesn't seem to get seen by me every time.

Is there any way of having an audible warning that the battery is going to run out - or at least some better visual indication to nag you as the battery is getting close to losing all power.

This is on a Dell 6400 with 8.04 BTW.  It came with Ubuntu pre-installed and has been great.

---

### Post by olejorgen on 2008-08-16
Doesn't gnome power utils have a setting for automatic suspend/hibernate when the battery gets under a certain level? Not exacly what you want, but it'll save your work.

Anyway, it should be easy to hack together a script, but I guess it should be dozen already. On my main ditstro atm (arch), I use a simple script that suspends when the battery is critically low.

---

### Post by bailey86 on 2008-08-16
> **olejorgen said:**
> Doesn't gnome power utils have a setting for automatic suspend/hibernate when the battery gets under a certain level? Not exacly what you want, but it'll save your work.

Anyway, it should be easy to hack together a script, but I guess it should be dozen already. On my main ditstro atm (arch), I use a simple script that suspends when the battery is critically low.

Thanks for that.

It fails to suspend or hibernate on this Dell properly.  I'm waiting to see if some upgrade fixes that aspect cos you're right - if it suspended when the battery was low then it would be no problem.  I could plug the power in and resume just like my wife can on her mac.

---

### Post by bailey86 on 2008-08-16
> **bailey86 said:**
> Thanks for that.

It fails to suspend or hibernate on this Dell properly.  I'm waiting to see if some upgrade fixes that aspect cos you're right - if it suspended when the battery was low then it would be no problem.  I could plug the power in and resume just like my wife can on her mac.

Actually, I've just tested it and the suspend is working when the lid is closed.  Although, sometimes it does not when the lid closes.  And resume worked fine.

I'll let it run down and see what happens.

---

### Post by olejorgen on 2008-08-16
It's a dell with ubuntu pre-installed, and suspend doesn't work flawlessly? You could call dell-support if the computer came with one of those over-priced deals.

---

