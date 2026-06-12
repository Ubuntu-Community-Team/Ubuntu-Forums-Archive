---
title: "Cant install programs and Update software"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by errormessage on 2009-04-18
Hi, I recently installed ubuntu 8.10. It was working perfectly until I tried to install a new program. It says 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Every time, I already tried doing dpkg --configure -a and rebooted but it still doesn't work. It was running fine though. 
   So then I thought, oh I just need to install updates. When I went to do that, I got the same error! Please help!

---

### Post by oldos2er on 2009-04-18
Can you copy and paste the command
```
sudo dpkg --configure -a
```
and its output?

---

### Post by errormessage on 2009-04-18
Thank you, it works.
Sorry, I'm a newb to Linux. Not really to computers, but linux for sure!
So far I'm loving it!

---

