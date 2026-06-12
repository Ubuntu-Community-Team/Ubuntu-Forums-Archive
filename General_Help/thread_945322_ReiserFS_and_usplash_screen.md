---
title: "ReiserFS and usplash screen"
date: 2008-10-12
forum: General Help
---

### Post by pofigster on 2008-10-12
Taking the advice of some friends and a lot of people here I decided to make my /home partition formated with ReiserFS (my root is ext3).  The one issue I have now is that whenever I'm starting up the usplash screen (which  I have customized) cuts out and it goes into verbose mode to tell me that the ReiserFS system is fine.  Is there a way to stop that?  It's not life and death, sure, but it is annoying and ugly.

---

### Post by Pelham123 on 2008-10-12
There was a bug posted for this a while back:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/22658](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/22658)

Maybe the solution will work for you?

---

### Post by exploder on 2008-10-12
Have you tried this?

sudo update-initramfs -u

It might be worth a shot and it will not hurt anything.

---

