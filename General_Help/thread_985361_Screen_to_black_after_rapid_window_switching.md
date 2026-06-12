---
title: "Screen to black after rapid window switching"
date: 2008-11-17
forum: General Help
---

### Post by minchina on 2008-11-17
I have been having this problem intermittently for the past month or so.  I am running 8.04 on a thinkpad t60 with an ATI graphics card and the fglrx driver.  When I am running firefox and at least one other program (usually open office, but sometimes other things as well) and I quickly bring up firefox and then minimize it (to quickly check something), the system will hang for two or three seconds and then go to a black screen. The screen is not off and the computer does not shut down, but I have to reboot to get back. I assume this is a problem with the driver, but I was wondering if anyone else had been having this problem as well.

thanks

---

### Post by knowledgeispwr on 2008-11-19
I have just noticed the same problem using Ubuntu 8.10 on a Thinkpad T60 when trying to open Open Office Writer when FireFox is running.  The screen will go to black, and I have to reboot.  I should clarify that I'm using Gnome.

---

### Post by knowledgeispwr on 2008-11-19
> **minchina said:**
> I have been having this problem intermittently for the past month or so.  I am running 8.04 on a thinkpad t60 with an ATI graphics card and the fglrx driver.  When I am running firefox and at least one other program (usually open office, but sometimes other things as well) and I quickly bring up firefox and then minimize it (to quickly check something), the system will hang for two or three seconds and then go to a black screen. The screen is not off and the computer does not shut down, but I have to reboot to get back. I assume this is a problem with the driver, but I was wondering if anyone else had been having this problem as well.

thanks

Are you using the proprietary device driver for your graphics card?  I deactivated it on my laptop (Thinkpad T60) and the problem seems to have gone away.  There seems to be no noticeable differences in performance for me.

---

### Post by minchina on 2008-11-22
I am using the fglrx driver.  It seems reasonable that it is a problem with the driver as it is clearly a video related problem.  I would rather not switch drivers because (historically, not recently), I have found the fglrx driver to do a better job.  The most frustrating thing is that I have not been able to reliably replicate the problem.  The probability of it happening increases as I rapidly bring up and minimize firefox, but there really isn't a reliable threshold.  If there is not some sort of fix within fglrx, I am inclined to wait until I upgrade to 8.10 in a few weeks and see if it fixes itself.  Also, I downloaded the newest firefox earlier this week and it has not happened since, so maybe it fixed itself.

---

