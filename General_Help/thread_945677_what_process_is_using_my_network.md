---
title: "what process is using my network?"
date: 2008-10-12
forum: General Help
---

### Post by wwonkers on 2008-10-12
Hi all

When my computer is idle, the network is getting used up a little bit in pulses, like this:

[img]http://dl.getdropbox.com/u/91797/network.png[/img]

How can I find out what process is using the network?

---

### Post by spiderbatdad on 2008-10-12
[http://linux.die.net/man/8/netstat](http://linux.die.net/man/8/netstat)

for example:```
sudo netstat -tulpen
```

---

### Post by wwonkers on 2008-10-12
Just want I needed. Thanks.

---

