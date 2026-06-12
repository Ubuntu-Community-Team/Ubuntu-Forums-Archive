---
title: "Frequent Suspend Hurt SSD?"
date: 2012-08-09
forum: Hardware
---

### Post by huangyingw on 2012-08-09
Hello,
    I always use pm-suspend to suspend/wake up my laptop while in meeting.
    I am using SSD, will this frequent suspend/wake up hurt my SSD?

---

### Post by Mark Phelps on 2012-08-09
NO, it will not hurt it.  Every SSD has a limited number of writes, but to put that in perspective, I have an SSD in my desktop and according to the diagnostic routine, it is expected to last for 10 more years!  So, I would not worry about it.

---

### Post by huangyingw on 2012-08-09
> **Mark Phelps said:**
> NO, it will not hurt it.  Every SSD has a limited number of writes, but to put that in perspective, I have an SSD in my desktop and according to the diagnostic routine, it is expected to last for 10 more years!  So, I would not worry about it.
How you do the diagnostic routine in Ubuntu? I could also like to have a test on my laptop.

---

### Post by efflandt on 2012-08-09
Suspend just flushes anything waiting to be written and puts the computer into a low power state.  So I do not see how that would affect SSD at all, unless you have some other suspend issues that could corrupt your drive.

For some reason my desktop cold boots quicker from SSD than waking from suspend with nvidia.  But it does not use much power idling, so other than turning off my monitor (HDTV) I don't even use suspend.

---

### Post by huangyingw on 2012-08-09
> **efflandt said:**
> Suspend just flushes anything waiting to be written and puts the computer into a low power state.  So I do not see how that would affect SSD at all
Yes, when suspend, just flushes everything into memory, there is no hurt to SSD.
But, when waking up, the temporary data in memory, would have to be written back, into SSD or somewhere? I guess this frequent and unnecessary write will count in the SSD's write limit.

---

### Post by QsoftStudios on 2012-08-13
It should be fine.

---

### Post by typhoon_tip on 2012-08-13
> **huangyingw said:**
> But, when waking up, the temporary data in memory, would have to be written back, into SSD or somewhere? I guess this frequent and unnecessary write will count in the SSD's write limit.

No, this happens only when hibernating and when is *going* into hibernating mode (dumping RAM to HDD), when it exit the mode, it reads back the RAM from dump file.

Going/Exiting sleep mode has no effects on HDD other than what mentioned above (flashing residual cache), that would be done anyway any given time. RAM is battery-protected in sleep mode. This is why if you flat-out your battery while in sleep, the laptop will simply restart from a fresh boot.

---

### Post by huangyingw on 2012-08-13
Thank you for clarification
> **typhoon_tip said:**
> No, this happens only when hibernating and when is *going* into hibernating mode (dumping RAM to HDD), when it exit the mode, it reads back the RAM from dump file.

Going/Exiting sleep mode has no effects on HDD other than what mentioned above (flashing residual cache), that would be done anyway any given time. RAM is battery-protected in sleep mode. This is why if you flat-out your battery while in sleep, the laptop will simply restart from a fresh boot.

---

