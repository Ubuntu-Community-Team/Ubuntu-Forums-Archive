---
title: "Wrong? version reported in Webmin"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by LG_Auction on 2009-02-18
The story...

I installed 7.04 server, then added 7.04 desktop. Upgraded to 8.04.

Now if I look at the <System> <About Ubuntu> is see 8.04. If I log in to Webmin, it reports 7.04.

Am I running parts of two versions?

I'm new, can't you tell. I like what I see and how it works.

Thanks in advance,

Bob

---

### Post by graymatter7 on 2009-05-17
Hi! From the command line you can use uname, or  

% lsb_release -a 

to get accurate os version info. Webmin reports version info from the config file in

/etc/webmin/config

The entry in this file doesn't get updated when you upgrade your os. You can, of course, change it by hand to reflect the correct version. Kernel information reported by Webmin should be correct, however.

---

