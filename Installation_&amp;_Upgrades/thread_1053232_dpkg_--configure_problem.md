---
title: "dpkg --configure problem"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by The Barold on 2009-01-28
Am trying to upgrade from Gutsy to Hardy, pc kept freezing during download and installing. Now have tried *sudo dpkg --configure -a* on terminal and stays at *Setting up acpi-support (0.109-0hardy2) ...* with blinking cursor under it. have tried *sudo apt-get install -f*, *sudo apt-get update* and *sudo apt-get upgrade*. If I close terminal and click on the update icon it tells me ***Not all updates can be installed***.

If I click "Partial Upgrade" button, then it tells me, 
```
Unable to get exclusive lock

This usually means that another package management 
application (like apt-get or aptitude) already running. 
Please close that application first.
```

If I try to run Synaptic it tells me,
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```

---

### Post by birddog165 on 2009-01-28
> **The Barold said:**
> If I try to run Synaptic it tells me,
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```

Have you "run 'dpkg --configure -a' to correct the problem."?

---

### Post by The Barold on 2009-01-28
Yes
**Now have tried sudo dpkg --configure -a on terminal and stays at *Setting up acpi-support (0.109-0hardy2) ...* with blinking cursor under it.**

---

### Post by avtolle on 2009-01-28
How long did you wait before closing the terminal and trying to do the partial upgrade? From my Hardy experience, it is good to wait until the icon that appears when installing, etc. in the panel "disappears" from the panel before trying any other package manager.

Also, on the issue you identified while running ```
sudo dpkg --configure -a
```how long did the cursor flash before you closed the terminal? I don't know what your computer's specs are, but depending upon the package, configuration can take a while, even on a relatively "fast" machine. It may well be that you waited for 30 minutes, but if you were impatient and exited the terminal in say, 30 seconds, that might not have been enough time.

---

### Post by The Barold on 2009-01-28
Well when I started the terminal command, the orange starburst upgrade icon went gray, then after awhile it went orange again, thats when I shut down the terminal and tried it from the update manager.

I waited a good 15-20 minutes

---

### Post by avtolle on 2009-01-28
Thanks for the response. Have you tried clicking on the orange starburst again, now that it has been a while since closing the terminal to see what might happen? I've a feeling that the same thing as you experienced before may happen.

Alternatively, you might open Synaptic and see if it lists any broken packages in the bottom notification area. If any are identified there, on the left side "list", there will be "Broken" included therein, upon which you might click and see if that fixes.

---

### Post by The Barold on 2009-01-28
Well, it seemed to have solved itself, the pc froze and I restarted and tried terminal command again, and now I am on Hardy. Thanks for the responses though!

---

