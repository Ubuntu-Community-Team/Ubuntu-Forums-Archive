---
title: "UTC time"
date: 2008-08-01
forum: General Help
---

### Post by becca23 on 2008-08-01
How do you change the UTC time? Currently my system has the wrong UTC time and this is causing alot of problems with some file sharing applications I'm using.

---

### Post by NilsE on 2008-08-01
It use to be on the time gui but it is not there anymore.  You can either have it on or off. To turn it off and see if that helps.

In a terminal:

gksudo gedit /etc/default/rcS

Look for  this line:  UTC=yes

Change it to: UTC=no

And save it:Then set the time if it is wrong in the System/Administration/Time and Date 

Then either reboot or do this: 

sudo /etc/init.d/hwclock.sh restart

---

