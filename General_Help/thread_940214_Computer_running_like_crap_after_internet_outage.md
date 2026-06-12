---
title: "Computer running like crap after internet outage"
date: 2008-10-06
forum: General Help
---

### Post by TurboRush on 2008-10-06
Hey everybody,

Looking for some input on where to start. Last week we had an internet/phone/cable outage that lasted for about 6hrs, it does not appear we had a power outage, but there was a comcast guy outside of our house working for quite a while.

Whether coincidence or not, before the outage my computer ran like a champ. No matter what I was doing, nothing crashed, Firefox always loaded like lightening and my web site screamed on a small inside a small VM. Post outage the whole system seems sluggish, my web site takes 5 - 10 seconds to load vs. 1 second.. Pidgin is suddenly crashing consistently, firefox takes way too long to load and the system in general just seems like I should be running windows... :lolflag:

Only things that were different in the days leading up to this were: lots of avi --> mpeg conversions dumping output to /dev/null, and I reset my router when initially trying to troubleshoot my other issues. I've combed through my logs and don't see anything out of the ordinary...

Any ideas of where to go next, what to look at?

AMD 64 dual core
3g ram
2 HDD's (performance between the 2 appears to be equal still)

Thanks

----
Resolved:

Kind of resolved, luckily I use SpiderOak for offsite backup. I went and pulled in a version of the VM before the outage and loaded it up and everything is cranking again. I am surmising that one (or more) of the VM files must have gotten damaged whether by coincidence or not. This probably resulted in the VMServer needing to do multiple reads/passes of files and thus slowed the overall system down.

---

### Post by TurboRush on 2008-10-07
Bumping it up for any ideas.

---

