---
title: "Updates unable to update?"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by caffeinatedcupcake on 2009-09-23
I was trying to update the computer and i typed my password and stuff but every time i try to update it a window appears "an error occured"
inside it says:
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

how do i go about fixing this?




thankyou in advance,
CaffeinatedCupcake:)

---

### Post by drs305 on 2009-09-23
Open a terminal, (Applications, Accessories, Terminal) and type:

```

sudo dpkg --configure -a

```
You will be asked to enter your password. As you type you won't see it. Press ENTER once you have typed it completely.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

