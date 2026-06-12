---
title: "USB repeater -&gt; dmesg spamming and slowdown"
date: 2011-11-09
forum: Hardware
---

### Post by Dr3Daemon on 2011-11-09
Hello all,

When I plug my USB repeater cable into my machine (Lucid 64bit) I just get the following messages repeatedly spamming to dmesg:


```
[ 1046.761411] hub 2-6:1.0: unable to enumerate USB device on port 1
[ 1046.940783] hub 2-6:1.0: unable to enumerate USB device on port 2
[ 1047.121410] hub 2-6:1.0: unable to enumerate USB device on port 3
[ 1047.300784] hub 2-6:1.0: unable to enumerate USB device on port 1
[ 1047.480787] hub 2-6:1.0: unable to enumerate USB device on port 2
[ 1047.661416] hub 2-6:1.0: unable to enumerate USB device on port 3
[ 1047.850791] hub 2-6:1.0: unable to enumerate USB device on port 1
[ 1048.030790] hub 2-6:1.0: unable to enumerate USB device on port 2
[ 1048.210791] hub 2-6:1.0: unable to enumerate USB device on port 3

```

This in itself is not a problem, but it seems to be slowing things down (e.g. boot, logging in and possibly the software I am running).

From bits and bobs I have gleaned off the internet, I think that Ubuntu thinks the 1-port repeater is a 4-port hub, and is complaining it can't find the other ports (which don't exist).

Anyway, does anyone know what is going on or how I can stop this happening?

Thanks

---

### Post by Dr3Daemon on 2011-11-10
For what it's worth, I get this problem on 11.10 as well.

---

