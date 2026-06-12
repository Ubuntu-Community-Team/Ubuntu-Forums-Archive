---
title: "Nessus can't run"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by markomk on 2008-12-29
hi i just download a nessus 3.0 and installed but i can't run :S
when i type:nessus 
say that its not installed,but when i type apt-get install nessus says that i have the newest version :S

how to run nessus? :S:confused::confused:
before i use just when type nessus.

---

### Post by cariboo on 2008-12-29
Did you install nessusd? To make sure nessusd in a terminal type:

```
ps ax | grep nessusd
```

you should get a result something like this:

```
ps ax | grep nessusd
  772 ?        S      0:00 nessusd: waiting for incoming connections
  924 pts/2    S+     0:00 grep nessusd
```

Jim

---

