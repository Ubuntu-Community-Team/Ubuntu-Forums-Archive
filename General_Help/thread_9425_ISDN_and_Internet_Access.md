---
title: "ISDN and Internet Access"
date: 2004-12-28
forum: General Help
---

### Post by zerwas on 2004-12-28
Hi,

I hope, I am posting to the right forum.
I followed exactly the [ISDNhowto](http://www.ubuntulinux.org/wiki/IsdnHowto), but got no success. I get an error like this when i do a 'pon provider'
> 
Dialing 123456
Protocol Error Layer 3

The freaky is, when I rmmod the concerned modules and modprobe them again, it sometimes works. But sometimes it simply says: CAPI not installed (no such file or directory)
I hope, anybody has an idea.

Thanks,
zerwas

---

### Post by zerwas on 2005-01-01
Ok, i got a solution.

All I have to do after booting is
```

rmmod avmfritz && modprobe avmfritz protocol=2

```
I don't know why it works, but it does.  :)

---

