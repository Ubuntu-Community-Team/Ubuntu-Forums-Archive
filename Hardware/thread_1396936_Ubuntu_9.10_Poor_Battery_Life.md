---
title: "Ubuntu 9.10 Poor Battery Life"
date: 2010-02-02
forum: Hardware
---

### Post by android73 on 2010-02-02
Hello,

I recently installed Ubuntu 9.10 on my Acer Aspire 5735 and have noticed that my battery only lasts about an hour from full charge. I ran Powertop diagnostic but am unsure what I am supposed to do next.  I have read in some forums about "laptop-mode" but am unsure about what it actually does or even how to enable it? I am fairly new to Linux and it seems from what I have read that to increase battery life can be quite complicated. Any adive would be greatly appreciated. Thank you!

---

### Post by Riverside on 2010-02-15
There is, I suspect, a bug in gnome-power-manager in 9.10 which affects users of some make and model of laptops and not others.

I have a Dell Inspiron 6400 and got approximately 4.5-5 hours battery life running Ubuntu 8.04 and subsequently 9.04.  Since installing 9.10 this has gone down to approximately 2.5 hours.

The issue appears to be not power consumption but incorrect reading of the battery's charge level.  After charging the battery to 100% (as shown by both the gnome-power-manager panel applet and the Dell hardware battery charge light itself), as soon as I unplug AC power the panel applet then immediately begins showing only 60% battery charge remaining.

After approximately 2.5 hours of use a critical warning is shown and eventually the laptop shuts down.

Others elsewhere are reporting this same Ubuntu 9.10 60% charge after AC power disconnection reading with a newly, fully charged battery, so this appears to be a bug in 9.10 rather than a fault with my battery or charger.

---

### Post by mikenz on 2010-03-02
hello,

I recently upgrade from 9.04 - 9.10 to my hp dv5 laptop and now my battery will not charge any ideas of updates that could help me with this problem?

---

### Post by cjhabs on 2010-03-02
> **mikenz said:**
> hello,

I recently upgrade from 9.04 - 9.10 to my hp dv5 laptop and now my battery will not charge any ideas of updates that could help me with this problem?

I have a dv5-1235dx running 9.10 and have found that it works except when I plug or unplug the cord while up and running - then it doesn't recognize the change - but if I power down, plug/unplug, it is ok.

---

### Post by mikenz on 2010-03-02
It's still not good enough, Have you not found a solution so it charges while running?

---

### Post by cjhabs on 2010-03-03
> **mikenz said:**
> It's still not good enough, Have you not found a solution so it charges while running?

No - it is not a big deal for me, so I am living with it.

---

