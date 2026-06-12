---
title: "battery warning"
date: 2009-01-10
forum: Hardware
---

### Post by yurib on 2009-01-10
hello,

whenever i boot ubuntu i get a warning balloon saying my battery capacity is low (somewhere around 40%) and that it means my battery is broken or old.
i have two questions:
1. how reliable is this information ? i get this warning even when the laptop is plugged to ac power.
2. if my battery is broken, is there anything i can do to fix it ?

thanks, yuri.

---

### Post by meditatingfrog on 2009-11-10
> **yurib said:**
> hello,

whenever i boot ubuntu i get a warning balloon saying my battery capacity is low (somewhere around 40%) and that it means my battery is broken or old.
i have two questions:
1. how reliable is this information ? i get this warning even when the laptop is plugged to ac power.
2. if my battery is broken, is there anything i can do to fix it ?

thanks, yuri.

I'm not sure about your battery, but I get the same message and it does appear that my battery is indeed at very low capacity.  I can only get 50 minutes out of the battery now (I used to get a lowly 2 hrs before).  I hate to say it but I think that Ubuntu's power management may be the cause of the battery failure.  This Toshiba laptop is rather new, not nearly old enough for the battery to fail or break this early in its lifespan.  

Until I get to the bottom of it, I won't be buying a new battery.  I've been staying home frequently anyway, so I've just been running my laptop without the battery, plugged directly into an AC outlet.  Maybe I'll keep the battery plugged in for the heck of it, even though I read without the battery plugged in is more efficient.

Are you dual booting?  Does your problem happen in Windows?  What kind of laptop do you have?

---

### Post by cwwees on 2009-12-03
I have a 3 month-old battery that should have 60-70 Whr capacity (by spec).  I noted the very short run-time in 9.10, so I checked the details.  Gnome power-manager reports a 3.3 Whr capacity for the battery and it shuts down the machine after ~20-25 minutes.  When I run the same battery in a Windows laptop, I get the same life.

I think the Ubuntu power management has written something into the battery memory which I can't over-write or renew.

Charlie

---

### Post by techunit on 2010-05-02
Is there a way to remove this notification if you already know this to be true. I have a battery that was a year and a half old that had reached 50% of its original capacity. I know this to be true, but I would like it to stop notifying me of it.

---

### Post by P4man on 2010-05-02
Open gconf-editor and change this key:
/apps/gnome-power-manager/notify/low_capacity

---

### Post by isbiyanto on 2010-05-17
thanks :guitar:

---

### Post by TomS2 on 2012-03-06
sorry to re-open this thread.
But what's the threshold for this battery warning?
Where can I see that?
Can I also configure it? if so, how?

---

### Post by Manyette on 2012-03-06
I would add to all that in laptops, some can tolerate being plugged in all the time, others are not so forgiving, and the battery should be removed/disconnected once it it charged. I cannot tell you which brands are susceptible to being overcharged and damaged though, for that you have to talk to the manufacturer, since few manuals will tell you the full story!

---

