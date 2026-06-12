---
title: "Compaq n610c:  How can I get hibernate or suspend to work completely?"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by oldtappan on 2007-04-24
I'm on Fiesty and [ since my last post on this topic]("http://ubuntuforums.org/showthread.php?t=89519&highlight=n610"), I've noticed that hibernate works out of the box!!  That's great.  The only problem is that my Aironet 340 card (I'm not using the built-in W200 card) doesn't seem to be active after resuming from hibernate.  How can I fix this?

I also can't get suspend/resume to work.   If I put the laptop into suspend, the screen is blank when it resumes and I have to do hard reboot.   Is there any magic in the latest bits that will get this to work?

Thanks.

---

### Post by strabes on 2007-04-24
[http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

The important part is this: Perhaps the most important change goes into /etc/default/acpi-support. Change the line POST_VIDEO=true to read POST_VIDEO=. This was the point when it started working on my system.

---

