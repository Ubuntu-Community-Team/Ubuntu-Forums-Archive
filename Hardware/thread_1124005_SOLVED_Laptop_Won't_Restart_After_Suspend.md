---
title: "SOLVED: Laptop Won't Restart After Suspend"
date: 2009-04-12
forum: Hardware
---

### Post by sobrien on 2009-04-12
I recently upgraded my Lenovo T61 notebook computer from Ubuntu 8.04 to 8.10.  I had been using a Proprietary NVIDIA driver, but when I upgraded my machine, it wanted to use Version 180.

Everything worked well after I upgraded, EXCEPT that whenever I closed the top to Suspend the machine, it would properly shutdown, the little moon symbol would light up and it would be suspended just fine; BUT, when I opened the top, there would be some disk activity and it would act like it was restarting, but the display would never light up and come back to life.  The only way to recover was to hold the power button down to force the machine off and then re-boot.

After much searching and poking around, I finally discovered that if I downgraded to the "NVIDIA accelerated graphics driver version 173" my machine started working perfectly, and resumed from suspend just as it should!

The way to do this is to select:  System/Administration/Hardware Drivers and then Deactivate Version 180 then reboot, and then select System/Administration/Hardware Drivers and then Activate Version 173.

Having Version 173 as the activated driver seems to be the key to my problem.

Regards,
Steve

---

