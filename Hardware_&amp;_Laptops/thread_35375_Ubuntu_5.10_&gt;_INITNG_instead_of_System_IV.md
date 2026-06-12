---
title: "Ubuntu 5.10 &gt; INITNG instead of System IV"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by ludi on 2005-05-18
Hi everybody.
Please devs, could you take a look (if you didn't) at this project:

The next generation init system
> 
About:
Initng is a full replacement of the old and in many ways depricated sysvinit tool. It is designed with speed in mind, doing as much as possible asynchronously.
 In other words: It will boot your unix-system much faster, and give you more control and statistics over your system.

Initng is written by Jimmy Wennlund.

Scroll down to README to find out more.
[http://jw.dyndns.org/initng/](http://jw.dyndns.org/initng/)

-------
Regards.

---

### Post by nocturn on 2005-05-19
This was posted in another thread already.

Don't hold your breath for 5.10 though.  Initng is too new, it will take a while before it replaces System IV...
Startup speed is nice, but not if it costs you in stability, so let this go through distro's like Gentoo and the likes first.  When it makes Debian (testing), it will probably pop up in Ubuntu.

---

### Post by ludi on 2005-05-19
Yes, you are right.
Whatever, just an idea. 
Regards.

---

### Post by AndersAA on 2005-05-27
chances are you'll be able to grab a .deb package and have it working as a drop in replacement though :), commited changes earlier today so it doesn't overwrite sysvinit's reboot and halt, which means it can be installed and tested without fear of screwing up your main system ;)

---

