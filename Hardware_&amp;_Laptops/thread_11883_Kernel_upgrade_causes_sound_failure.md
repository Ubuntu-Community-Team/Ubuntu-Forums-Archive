---
title: "Kernel upgrade causes sound failure"
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by excelsior on 2005-01-20
I have an Ensoniq ES1371 [Audio PCI-97] soundblaster. Since I upgraded my kernel the sound doesn't work. Has anyone else experienced a similar problem? 

I'm a newbie, having used ubuntu for 2 weeks and prior to that I had endured Fedora Core for 2 months. So a simple explanation would be appreciated :)

---

### Post by fashions on 2005-01-20
[QUOTE=excelsior]I have an Ensoniq ES1371 [Audio PCI-97] soundblaster. Since I upgraded my kernel the sound doesn't work. Has anyone else experienced a similar problem? 

I'm a newbie, having used ubuntu for 2 weeks and prior to that I had endured Fedora Core for 2 months. So a simple explanation would be appreciated :)[/QUOTE]


I am not having any luck with my Ensonig ES1371 card so far either, is anyone?
[http://ubuntuforums.org/showthread.php?t=10799](http://ubuntuforums.org/showthread.php?t=10799) was my last post and haven't gotten a responce yet. :???:

---

### Post by Soulman on 2005-01-21
[http://www.alsa-project.org/](http://www.alsa-project.org/)

Go here and do a search for your sound card.  They will tell you which parts of alsa in the kernel config to comment.  I usually build them into the kernel, don't like modules personally.  Anyway hope this helps.

---

