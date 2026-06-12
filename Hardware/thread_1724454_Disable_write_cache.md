---
title: "Disable write cache"
date: 2011-04-08
forum: Hardware
---

### Post by sakishrist on 2011-04-08
Hi,

How do I disable write cache on a disk?

---

### Post by sakishrist on 2011-04-09
Answering my own question:

A script has to be made in /etc/init.d that contains:```
**[COLOR=Blue]#!/bin/bash[/COLOR]**
hdparm -W0 /dev/hdx[x]
```And then a link to it has to be created in /etc/rc.d with name SxxOriginalName. xx is from 00 to 99, lower means it will be executed earlier.

---

### Post by sakishrist on 2011-04-17
I have noticed that this method does not always work, maybe it worked just the first time but now the cache is on again.

Could you please help me?

---

