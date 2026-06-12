---
title: "Dual boot XP and Ubuntu System Clock error"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by jakenbake42 on 2009-02-16
I installed Windows XP and then Ubuntu on my machine and now, the clock is always 3 hours ahead on boths operating systems, and I don't know how to fix that
What do I do?
Thanks in advance! :]

---

### Post by Tobi-fp on 2009-02-16
Try going into boot setup:

Its usually done by pressing F2 on startup..

---

### Post by jakenbake42 on 2009-02-16
Ok that worked for the first boot of ubuntu and xp after doing that
but I launched Ubuntu again
what i did in the setup was changed the time hit enter, and then the escape key to leave set up
something I did wrong?
something I can do?

Thanks again! :]

---

### Post by caljohnsmith on 2009-02-16
Are you using 8.04 or 8.10? How about opening a terminal (Applications > Accessories > Terminal) and do:
```
cat /etc/default/rcS | grep -i utc
```
Does that show "UTC=yes"? If so, that's most likely your problem. You can change it by doing:
```
gksudo gedit /etc/default/rcS
```
And then change it so "UTC=no". Let me know how that goes.

---

### Post by jakenbake42 on 2009-02-16
> **caljohnsmith said:**
> Are you using 8.04 or 8.10? How about opening a terminal (Applications > Accessories > Terminal) and do:
```
cat /etc/default/rcS | grep -i utc
```
Does that show "UTC=yes"? If so, that's most likely your problem. You can change it by doing:
```
gksudo gedit /etc/default/rcS
```
And then change it so "UTC=no". Let me know how that goes.
I'm running Ubuntu 8.10
and I put that into the terminal and it said

UTC=no

Thanks so much though.
Is there anything else I can do?

---

### Post by caljohnsmith on 2009-02-16
At least when you are in Ubuntu, if you right-click the time shown in the top panel on the desktop, you can choose "Adjust Date & Time", and then once you adjust the time to be correct, click the "Set System Time." Then if you reboot, is the time OK or is it still 3 hours off?

---

### Post by jakenbake42 on 2009-02-16
> **caljohnsmith said:**
> At least when you are in Ubuntu, if you right-click the time shown in the top panel on the desktop, you can choose "Adjust Date & Time", and then once you adjust the time to be correct, click the "Set System Time." Then if you reboot, is the time OK or is it still 3 hours off?
I'm afraid that didn't work either :[
I tried what Tobi-fp recommened, hitting F2 at startup, and that worked at the initial boot of Ubuntu, and then XP, but the second time I booted Ubuntu it was back at 3 hours ahead

Thanks friend!

---

### Post by octesian on 2009-02-16
Maybe your region settings are incorrect and its set to automatically update the time?

---

