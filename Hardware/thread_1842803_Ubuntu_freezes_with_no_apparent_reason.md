---
title: "Ubuntu freezes with no apparent reason"
date: 2011-09-12
forum: Hardware
---

### Post by Blasphemous on 2011-09-12
Sometimes my Lubuntu 11.04 **freezes **with no apparent reason: the screen **remains stationary, **like a photo, and I **can't even move the mouse **or go back to console by pressing CTRL-ALT-F1/F2.

On the internet I found some other users who were affected by this problem, and it seems that it** is connect with the video drivers.**

I've got an old  **ATI Radeon RV100 QY [Radeon 7000/VE] **and, according to what I read online there are **no ****proprietary drivers **for my hardware, so I'm forced to use the open source ones that come with my distro.

So, how can I possibly **change the driver versio**n in order to fix the problem?

---

### Post by Sylos on 2011-09-12
Have checked to see if it is a hardware malfunction?

I have been lead to the conclusion (by others who are wiser) that freezes can often be caused by an ailing power supply (happend to me). Might be worth a check before getting too involved with the video drivers.

---

### Post by Blasphemous on 2011-09-12
Yeah but, how do I check that?
Actually, everything seems to be ok speaking about hardware...

---

### Post by Sylos on 2011-09-12
Checking the PSU involves using a multi meter to check the voltages being generated on each of the pins going into the MB. You can check online for what the voltages should be. The testing would usually be done when the PC is running under heavy load - video, web browser, audio etc. If the psu is faulty you would expect one or more of the voltages to be dropping below what it should. This lack of power on one or more rails can then cause the system to freeze as varying aspects stop functioning.

It may not be the PSU but it is always worth a check imho as you could waste weeks fiddling with software trying to solve a hardware problem.

---

