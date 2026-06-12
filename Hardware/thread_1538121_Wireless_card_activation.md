---
title: "Wireless card activation"
date: 2010-07-24
forum: Hardware
---

### Post by fortmac on 2010-07-24
I have a new dell studio xps with a broadcom 1490 wireless adapter.  I am running 10.04.  I initally had trouble getting the drivers to work but I used this page [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) ... notably these two lines of code:

```
~$ sudo apt-get update
~$ sudo apt-get install bcmwl-kernel-source
```

After this ubuntu has a driver for my card and see's it as a device (eth1).  However when I unplug my wired connection, the wireless just sits there and tells me "wireless not activated" and will not see my home wireless network or anything.

Is there something simple I'm overlooking or am I using the wrong driver?

---

