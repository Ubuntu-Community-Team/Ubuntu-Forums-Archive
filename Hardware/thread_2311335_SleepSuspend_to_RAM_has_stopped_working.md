---
title: "Sleep/Suspend to RAM has stopped working"
date: 2016-01-26
forum: Hardware
---

### Post by LVDave on 2016-01-26
I use KUbuntu 14.04 64bit on a Dell Precision T3500, and since I "sleep" the system at night when I head off to sleep, its kind of annoying to wake up the next morning, press the flashing green power button and have nothing happen.. Nothing, as in hold the button down for minutes, no shutdown or nothing, requiring a pull of the power cord. This just recently developed in the last few days, and since the system has developed some other less annoying weirdness, and since I keep a separate /home partition, I decided to reinstall, and see if this would solve the problems. After reinstall, other problems were gone, but pressing the KDE menu item "Leave/Sleep" did the same thing.. Some googling had me try installing acpitool and trying an 
"sudo acpitool -s" which obediently closed the system down, with the flashing green power light and then pressing that power button brought it right back up.. I guess my question is, what the heck changed? Whats the difference between an "acpitool -s" sleep and what the KDE menu does. I can live with using "acpitool -s" to sleep the system from a shell if necessary, but I'd like to fix it so the KDE menu choice works as it should...

Thanks
Dave

---

