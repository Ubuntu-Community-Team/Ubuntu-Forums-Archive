---
title: "ext3 performance tweak"
date: 2008-11-03
forum: General Help
---

### Post by freonchill on 2008-11-03
saw this performance boost tweak today

[http://www.hackosis.com/2008/11/03/linux-speed-your-file-system-up-40/](http://www.hackosis.com/2008/11/03/linux-speed-your-file-system-up-40/)

just wondering how dangerous (e.g. normal user who just surfs the web and uses wine) this would be?

or if this "performance boost" would not be upwards of 40% when using it on a typical machine?

(yea, i know, most machines are not typical)
just looking for some more insight than i know about linux/ubuntu

thanks

---

### Post by freonchill on 2008-11-07
bump

anyone?

---

### Post by kaibob on 2008-11-07
I changed fstab to noatime a few years ago and didn't notice any difference. This may be hardware dependent with a more noticeable difference with older or slower machines. 

I believe (but am not sure) that the default in current versions of Ubuntu is relatime, which is somewhere between atime and noatime. Perhaps this is why the change to noatime is not noticeable.

If you are new to Linux or aren't able to fix fstab if things go wrong, it's probably best just to leave things as they are IMO.

Some interesting reading on the topic:

[http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148)

[http://lwn.net/Articles/245002/](http://lwn.net/Articles/245002/)

---

### Post by wgrant on 2008-11-07
We use relatime by default, but your fstab may not have it if you upgraded. It gives most of the benefit of noatime, but without breaking apps that depend on knowing whether a file has been accessed since it was modified.

---

