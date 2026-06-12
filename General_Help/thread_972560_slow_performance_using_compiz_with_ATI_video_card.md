---
title: "slow performance using compiz with ATI video card"
date: 2008-11-05
forum: General Help
---

### Post by edwinw on 2008-11-05
I'm running Ubuntu 8.10 on a slightly older but not outdated system, Athlon 2200+ with 1.5 GB RAM and a Connect3d Radeon 9600 8x AGP video card.  The good news is that 8.10 is much more stable than 8.04 on my hardware.  As an aside, my system wouldn't ever stay up more than 2-3 days without getting a kernel panic (hard lock), while with 8.10 it's been working from day one (I had to fix the X-server after install but that wasn't a problem).

Anyway, 8.10 running with compiz is noticeably more sluggish in 8.10.  By the way I'm running the proprietary fglrx driver.  I can confirm that it's compiz causing the slowdown, when I switch to metacity the system is snappy enough, even with smooth scrolling in Firefox.  The specific symptoms: the scrolling in Firefox is somewhat laggy (with smooth scrolling turned off), and even the navigation on the taskbar menu is slightly laggy as well.

Any advice on extra options I should add to my xorg.conf file to improve compiz performance?  Or is it worth using Envyng to compile the fglrx driver for my system?  Thanks for any help!

---

### Post by slinkey1981 on 2008-11-06
I always let EnvyNG deal with my display drivers, whenever I try to use just the "Restricted Drivers" or (worse yet) the ones from the Manufacturer, I run into problems..

---

### Post by Izek on 2008-11-06
> **slinkey1981 said:**
> I always let EnvyNG deal with my display drivers, whenever I try to use just the "Restricted Drivers" or (worse yet) the ones from the Manufacturer, I run into problems..

EnvyNG will install the proprietary fglrx driver for most ATI Cards in 8.10, so it's a lose-lose deal at the moment.

I'm sluggish too since my ATI Radeon HD 3200's driver is currently beta for xorg 7.4. (xorg-driver-fglrx) Though, even when it isn't beta, it still may be sluggish.

---

