---
title: "Fix for hot dual HD laptop"
date: 2011-05-12
forum: Hardware
---

### Post by s3MA00RRNY on 2011-05-12
(Notebook Review is probably a better place to post this, but I don't really frequent those forums. I forgot my password.)

I recently was having terrible heat problems with a G60Vx laptop (still not 100% fixed). While the core temperatures were mostly fine, the motherboard temperature was off the charts. Other than the usual things, such as making sure your heatsinks are seated correctly and whatnot, change the positioning of your hard drives if you have two:


[LIST]
[*]New drive should be **_*bracketed*_** (not free standing, unless you want to break it) in the old one's slot. There's better airflow because there's no motherboard underneath. The new drive is usually hotter, so keeping it away from the MB is almost always better.
[*]Make the new drive your primary drive, so you don't have to access the old one as much (it doesn't heat up as much if you're not using it).
[*]Set hdparm options to suspend the old drive if it is idle.
[/LIST]
This probably applies to other laptops with dual HDs. Hope this helps someone.

---

