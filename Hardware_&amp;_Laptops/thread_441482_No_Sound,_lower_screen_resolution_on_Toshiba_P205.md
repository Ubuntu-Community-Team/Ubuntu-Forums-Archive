---
title: "No Sound, lower screen resolution on Toshiba P205"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by nanonomic on 2007-05-12
Hi, I just recently bought a Toshiba Satellite P205-S6237 from circuit city.  


I loaded Ubuntu 7.04 onto it for a project for school.   I'm thinking of keeping Linux on it and NOT switching back to vista.


The only real problems im having right now is that the sound isnt working and the monitor resolution is not set at its maximum.


The monitor resolution on Vista was 1440*900, which was a great widescree resolution.  But now on Linux it only does 1280*800.  I really want to keep Linux, but i really want 1440*900 too.




and also the sound isnt working......i have no idea why..if anybody has any ideas......


thanks

---

### Post by adameye on 2007-05-12
did you try this one?
[http://ubuntuforums.org/showthread.php?t=438689&highlight=toshiba](http://ubuntuforums.org/showthread.php?t=438689&highlight=toshiba)

---

### Post by vinucube on 2007-05-13
Tried 915resolution?

Installing 915resolution and adding the following line to /etc/rc.local works on Toshiba P205 S6237 running FC6.

/usr/sbin/915resolution 4d 1440 900 24 1440 900

---

