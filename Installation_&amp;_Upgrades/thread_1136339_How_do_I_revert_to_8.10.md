---
title: "How do I revert to 8.10?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by MeanStreak on 2009-04-24
I've experienced severe issues with my ATI graphics drivers since upgrading to 9.4. I still am unable to login. I don't have any more time to troubleshoot this issue - I need my computer working again. How do I revert to the previous (working) version of Ubuntu?

---

### Post by sports fan Matt on 2009-04-24
AFAIK, the only way is to backup and reinstall..Lets see if someone else has any other solutions

---

### Post by pbpersson on 2009-04-24
There is NEVER any way to go backwards.  Developers spend months designing the path to go FORWARD, there is no reverse gear in the transmission of progress.

---

### Post by MeanStreak on 2009-04-24
Problem solved! I booted into Recovery Mode, selected the command line option and ran:
```
apt-get remove xorg-driver-fglrx
```
 
I can now login and very thankful.

---

