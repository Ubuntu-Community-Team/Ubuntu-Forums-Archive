---
title: "Why does the battery still run dry after 20 minutes?"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by lacerda_sch on 2007-06-26
I have a HP nx6125 laptop that I am running Ubuntu on. It has an AMD Athlon64 processor (configured to change frequency, if needed, with powernowd) and an ATI Xpress series X200 graphic card (set to low voltage mode).

I have tried lots of things, installed different CPU frequency control daemons, yet, after 20 minutes, my battery is empty. What the hell drains it so fast? The wireless? The bluetooth adapter? The monitor? Does anybody have ideas about this?

---

### Post by Syke on 2007-06-26
Nothing should drain a full battery that fast. I would suspect the battery to be worn out or faulty. If you left click on the battery icon you can see some stats for your battery. If the "Last full charge" isn't close to the "Design charge", then you likely have a battery problem. Also, right click the battery icon and select power history to check out power usage, time estimates, etc.

---

### Post by lacerda_sch on 2007-06-26
Any hardware problem is highly unlikely, because it is still okay under Windows (near 2 hours battery life). I suspect that for some reason the power manager does not correctly see the power level. I have tried draining it completely. It said 2 minutes remaining for 15 minutes, and it still did not shut down. This must be that bug I read about in some thread here. Thanks for showing me these tools though, they seem pretty useful. I will test the battery some more with them, and return if I have the results.

---

### Post by lacerda_sch on 2007-06-27
All right. I have tested the actual battery capacity. Interestingly, it turns out that after the gnome power tools report that the battery is on 0% charge, the laptop still runs for another, say, 40 minutes. Looks like the power manager is wrong about my battery's capabilities.

I can also confirm that this is not a hardware problem: my battery's design charge is listed to be 18 Wh and its currently 17.9 Wh. Plus, it is still fine under Windows.

I think the power tools are adapting to this capacity now. Last time I checked, the design charge was only 14 Wh. Funny. :)

Edit: check out the power history screenshots here: [http://lacerda.himmel.hu/](http://lacerda.himmel.hu/)

---

### Post by BluewookieJim on 2007-07-02
I may be having this same problem. I have a Dell i600d. It is about 1.5 years old. Under WinXP MCE2005 I can run for 1:45 to 2:00 hours on my battery. I've never let the system run all the way down since I installed Ubuntu, but at around :45 or :50 minutes, the battery meter always shows less than 10% remaining.

---

### Post by petroskhan on 2007-07-04
I am having a problem in the opposite direction.  With my battery monitor reporting 8% charge, as it is right now, it says that I have 39 hours, 18 minutes until it's fully charged.  When it's on the battery, it will show many, many hours of battery life.  Of course, it never actually lasts that long.  It will, on a full charge, tell me that I have roughly 30 hours or so of battery life.  After roughly 40 minutes, the meter suddenly tells me I have 10% remaining, and that I have only a couple of hours left.  This is getting REAL confusing.  Of course, it's great for showing friends, to show off how well Ubuntu maximizes my battery life.  Under windows, it shows normal, then I switch to Ubuntu, and voila!!  Days of battery life!  The miracle operating system.  ;)  

Of course, I would like to fix this problem.

---

### Post by galileon on 2007-08-04
> **petroskhan said:**
> I am having a problem in the opposite direction.  With my battery monitor reporting 8% charge, as it is right now, it says that I have 39 hours, 18 minutes until it's fully charged.  When it's on the battery, it will show many, many hours of battery life.  Of course, it never actually lasts that long.  It will, on a full charge, tell me that I have roughly 30 hours or so of battery life.  After roughly 40 minutes, the meter suddenly tells me I have 10% remaining, and that I have only a couple of hours left.  This is getting REAL confusing.  Of course, it's great for showing friends, to show off how well Ubuntu maximizes my battery life.  Under windows, it shows normal, then I switch to Ubuntu, and voila!!  Days of battery life!  The miracle operating system.  ;)  

Of course, I would like to fix this problem.

haha, I love it myself, but it seems that after a few minutes it returns to a more sensible value, for me it says 40hours then drops to the normal 3 hours (although i get 3h30-4h in woes32 coz of powermizer for nvidia :()

---

### Post by hessiess on 2007-08-04
my battery meter alwase ses time unknown!

---

### Post by kmcq on 2007-08-09
ive got a dell latitude c400 and the battery on ubuntu only seems to last 60 minutes, but i have never run it till it was dead to know for sure if its reporting accurate stats, i find it hard to believe however that a lithium ion powered battery can go dry in an hour...

---

### Post by skirkpatrick on 2007-08-09
Battery capacity was fine on my laptop with Dapper, then Edgy reported almost no charge after only a couple of minutes, then Feisty seemed to have fixed the problem again.

---

