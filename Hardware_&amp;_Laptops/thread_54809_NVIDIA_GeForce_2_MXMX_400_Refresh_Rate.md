---
title: "NVIDIA GeForce 2 MX/MX 400 Refresh Rate"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by ThePotato on 2005-08-06
Hi all,
I'd like to install Ubuntu, but aswell as a problem with my wireless network (See [Here](http://www.ubuntuforums.org/showthread.php?p=289087#post289087)) , I have tried the Live CD and can get my desired resolution of 1280*1024, but not my desired refresh rate of 80Hz as I have currently on XP.  Of course, the Live CD is only meant as a trial, so if I install it, would I be able to change that?  The graphics card is as per the subject.  Thankyou for your time.

---

### Post by mo_x on 2005-08-06
Yes, you can change the configuration in the /etc/X11/xorg.conf file. Change the values of HorizSync and VertRefresh to match your monitor.

---

### Post by ThePotato on 2005-08-12
Any chance of a 'Bluffer's Guide' to doing this so that I can get it done quickly when I get Ubuntu installed?

---

### Post by heimo on 2005-08-12
This may help:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

