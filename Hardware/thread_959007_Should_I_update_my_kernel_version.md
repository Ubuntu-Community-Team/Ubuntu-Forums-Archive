---
title: "Should I update my kernel version?"
date: 2008-10-26
forum: Hardware
---

### Post by yeahwo on 2008-10-26
Is that possible for latest 2.6.27 kernel support my display card (ATI Technologies Inc Mobility Radeon HD 3400 Series) ? My laptop is Lenovo T400 with double display card.

If so, I will update my kernel version from 2.6.24 to 2.6.27.

Seems that the current version does not work well with my display card. It crashes every time when I was trying to play some video. I thought it was due to the player application first. But turns out my video card can not pass the hardware test of Ubuntu. Then I downloaded a newest driver from ATI official site and installed it, things was getting worse.  I can only login with "failure safe mode" of gnome session instead of normal gnome session.  And I found I can not start scim in this mode.

Am I the only one who encounters this issue? Could anyone here help me?

Thanks a lot.

---

### Post by Lord Xeb on 2008-10-26
What Ubuntu version are you using? I would upgrade to Hardy to see if anything happens. Then what for 8.10 to mature a little more (about a month) then upgrade to that. That should help. Also, try installing the latest drivers from ATI. That will help out a lot as well.

---

### Post by cariboo on 2008-10-26
THe only way to safely upgrade to kernel 2,6,27 is to update to Intrepid Ibex v 8.10. the rc was releaesed on Thursday Oct 23rd. The final will be released on Oct 30th.

Jim

---

### Post by mikjp on 2008-10-26
Update the whole system, not just kernel. The problem might be in drivers or in X windowing (xorg).

---

### Post by silvanus2005 on 2008-10-26
I suggest, before updating try using the new version of Ubuntu on Live CD and see if it is working properly. If you have problems, don`t make the update.

---

### Post by yeahwo on 2008-10-26
thank you guys.

---

