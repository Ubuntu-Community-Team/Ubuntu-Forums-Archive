---
title: "auto-installation with kickstart from usb"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by phnhat1984 on 2009-03-05
I try to install ubuntu server, using kickstart. But the server can not read kickstart description in usb stick. Command i try

linux ks=hd:sdb:/ks.cfg
with sdb is the name of usb stick mounted by ubuntu installer. Please someone help me. Thanks

---

### Post by ouzmoutous on 2013-02-16
Hi.
I know it's a 4 years old topic but I have the same problem.

I see an error when I boot. It says that it cannot find the kickstart file in /media/sdb/. And that's normal because when I do an "ls /media/" in the busybox of the install, there is nothing in here... But like you I've seen that my USB drive is on /dev/sdb1.
I also tried to point to the partition rather than to the USB drive :
 
```
linux ks=hd:sdb1:/ks.cfg
```

But same thing, is trying to look for /media/sdb/ks.cfg

I'm using the latest netinstall of Ubuntu. Have you find any solution since your first post ? :D

---

