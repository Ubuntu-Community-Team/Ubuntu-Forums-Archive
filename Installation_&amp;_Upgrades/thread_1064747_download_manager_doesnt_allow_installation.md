---
title: "download manager doesnt allow installation"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by mat429 on 2009-02-09
Hi, 

i have just attempted to download some additional programs via the add/remove programs application.

i get the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i try to run the configure i get an error saying i need to be a superuser..

any help much appreciated.

Thanks

Mat

---

### Post by Partyboi2 on 2009-02-09
You need to put sudo infront of the command to give you admin rights so type
```
sudo dpkg --configure -a
```

---

### Post by mat429 on 2009-02-09
DOH!  :)

many thanks

mat

---

