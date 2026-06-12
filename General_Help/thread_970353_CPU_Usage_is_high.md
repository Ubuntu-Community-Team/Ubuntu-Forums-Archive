---
title: "CPU Usage is high"
date: 2008-11-04
forum: General Help
---

### Post by Oziyak on 2008-11-04
Hi.
I'm running an AMD 3000+ single core s939 cpu with 3 gb of ram and 32-bit Ubuntu Intrepid 8.10.

So far I'm loving my experience... but have found that while Ubuntu has yet to use all my ram.... it really seems to be hard on my cpu.  It seems to always idle somewhere in and around 50% usage... and when running a wine app it's constantly at 100%.

Just wondering if this is normal... or if there are some settings I could set that would make it more effiecent.

Thanks for any input
Cheers

---

### Post by sagara on 2008-11-15
Hey Oziyak, welcome to ubuntu!

I must say that what you are experiencing is **not normal**.  When your machine is idle it should only be taking around 1-3% of CPU if any.  That is of course if you are not running any background intensive applications.

50% is really bad.  Run the command **top** on a terminal and post the output here.  Hopefully we can see what is hogging up your machine.

---

### Post by Tamlynmac on 2008-11-15
You can also look at the system monitor: 
system/administration/system monitor/Processes Tab

This gui will show whats running or sleeping.  By right clicking on the process you can stop or even kill the process. You may also wish to check your Session Preferences (system/preferences/sessions) for what is in the startup menu.

---

