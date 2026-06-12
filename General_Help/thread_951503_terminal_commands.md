---
title: "terminal commands"
date: 2008-10-18
forum: General Help
---

### Post by justborn on 2008-10-18
what is the command to check if my comp is connected or not?


please help me wid the command i know to do it GUI

---

### Post by shawnrgr on 2008-10-18
you sould be more specific. connected to what?

if you want to see if your internet is working you can always ping google ;) 'ping google.com' you can also run 'ifconfig' to see if your getting an ip.

---

### Post by cicatrix1 on 2008-10-18
ifconfig

shows a detailed output of all network devices.  You'd want to verify that the IP of the device you want is reasonable.

> **justborn said:**
> what is the command to check if my comp is connected or not?


please help me wid the command i know to do it GUI

---

### Post by cariboo on 2008-10-18
You can use ping to see if your connected. In a terminal type:

```
ping www.google.com
```

If you are connected you should get a result something like this:

```
ping www.google.com
PING www.l.google.com (209.85.171.147) 56(84) bytes of data.
64 bytes from cg-in-f147.google.com (209.85.171.147): icmp_seq=1 ttl=244 time=54.6 ms
```

Jim

---

