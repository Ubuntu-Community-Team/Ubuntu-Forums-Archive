---
title: "Unable to Unmount Device"
date: 2008-07-18
forum: General Help
---

### Post by GameBox 47 on 2008-07-18
Well, I forgot to press "Eject" before removing my PSP and the icon still shows up on the desktop, but when I put my PSP back in, it can't access it, none of the files show, even though they are there (shows up on PSP).  How do I fix this?  I get this message when trying to unmount the device:

Unable to unmount SONY PSP.
/sbin/umount.hal: /media/SONY PSP is not recognized by hal

Help please.

---

### Post by jonlemur on 2008-07-18
Have you tried restarting the computer?  It seems that may be the simplest solution.

Another possibility would be to do ```
 tail -f /var/log/messages
``` before you plug in the device, then put it in and find where it's being assigned in /dev.  Then perhaps you could mount it using that device name.

---

### Post by uberlube on 2008-07-18
Ya. Remaining icons tend to happen from time to time. Restart is best solution.

---

### Post by GameBox 47 on 2008-07-19
Thanks alot guys.  Sorry for being such a Linux noob.  Lol.

---

### Post by Shunsuke_01 on 2008-07-19
> **GameBox 47 said:**
> Thanks alot guys.  Sorry for being such a Linux noob.  Lol.

Same thing happens with my iPod & External HDD. Just remember to eject/unmount volumes before removing them! 

If you forget, just ignore the icons that are left. They should disappear when you restart and I don't think they affect the computer in any way.

---

