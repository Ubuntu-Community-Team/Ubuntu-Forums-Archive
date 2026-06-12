---
title: "[SOLVED] On Battery, Power manager ridiculously wrong"
date: 2008-08-18
forum: Hardware
---

### Post by persiansown on 2008-08-18
When I'm running ubuntu on my MSI Wind and decide to unplug it from the AC adapter, it shows a battery remaining time of upwards of 800,000 hours.  the percentage appears to be correct but this number is horribly wrong.  I looked around for fixes and couldn't find anything about this issue.  Can anyone help?

---

### Post by Sam Lars on 2008-08-18
Have you drained your battery a significant amount, maybe a few times?

---

### Post by persiansown on 2008-08-18
thats what I'm doing now.  its at 49 percent with 436448 hours remaining....

---

### Post by Sam Lars on 2008-08-18
Try running it down a time or two, maybe restarting.
Are you using the power manager, like the icon in the tray?  Right click on it, you can get to information, and it tells you how much power you're using, how accurate the estimation is, etc.

---

### Post by persiansown on 2008-08-18
Its still not working, its been powered down completely and restarted a couple of times.  the charge time is accurate as is the power drain estimate in the power meter.  is there any way I can just reinstall it?  I wouldn't mind setting up my powersaving settings again...

---

### Post by monikersupreme on 2008-08-18
I had a similar issue - my battery life under the Hardy battery manager was ridiculously low (1hr 50mins for a full dual-battery charge that usually lasts 5+ hours). I found, though, after draining my battery that I am getting something closer to typical usage (~4.5hrs) although not as good as what I had in XP. 

Dunno if this helps... probably not... just thought I'd commiserate though:)

---

### Post by persiansown on 2008-08-18
I just don't understand why charging time is accurate but discharging time isn't

---

### Post by persiansown on 2008-08-19
alright I fixed it by deleting the file that was trying to learn my battery.  all better.  i forget the file.  I think it was in home/.gnome2/power or something

---

### Post by Sam Lars on 2008-08-19
Great, that's the idea.

---

### Post by Theist17 on 2010-12-11
Sam Lars, were you being serious or sarcastic there? Because deleting files seems like a shady way to fix any problem, and I just want to make sure before I go deleting stuff.

EDIT: Sorry for resurrecting an old thread, I searched for this kind of thing and this was one of the most likely-looking result threads.

---

### Post by Sam Lars on 2010-12-11
It's certainly not the best option, but if it fixes the problem, then it may be worth it.
Instead of removing it, you could also move it or rename it in case you want to get it back again.

---

