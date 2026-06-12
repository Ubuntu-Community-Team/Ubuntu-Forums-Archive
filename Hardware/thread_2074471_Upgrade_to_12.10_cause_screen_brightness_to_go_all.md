---
title: "Upgrade to 12.10 cause screen brightness to go all the way down"
date: 2012-10-21
forum: Hardware
---

### Post by postalservice14 on 2012-10-21
I upgraded to Ubuntu 12.10 the other day on my Dell M90 and the screen brightness lowered all the way and the brightness FN keys no longer work.  I even went to the brightness controls in Ubuntu and I can't get the brightness to go up.

Thanks,

John

---

### Post by nhawki on 2012-10-22
Hi Postal, just found the same thing. If you go to System settings, software sources, additional drivers and select the first driver, nvidea binary xorg driver, it worked for me. You need to shut down after it downloads...
Good luck
nhawki :P

---

### Post by postalservice14 on 2012-10-22
> **nhawki said:**
> Hi Postal, just found the same thing. If you go to System settings, software sources, additional drivers and select the first driver, nvidea binary xorg driver, it worked for me. You need to shut down after it downloads...
Good luck
nhawki :P

That worked!  Thanks a ton.

---

