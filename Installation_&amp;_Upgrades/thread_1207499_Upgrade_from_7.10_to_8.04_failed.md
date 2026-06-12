---
title: "Upgrade from 7.10 to 8.04 failed"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by boeman on 2009-07-08
I tried a do-release-upgrade from 7.10 to 8.04 and it started out all right. Somewhere along the process the upgrade failed on slapd, after which it tried to rollback, I think, but I had to ctrl+c since there was no more progress. After a reboot, doing a lsb_release -a, it shows that I'm running 8.04. 
I don't notice any strange messages in the logs, or witness strange behaviour. 

Is there a need to fix this? Since all seems to be running just fine...

---

### Post by Bucky Ball on 2009-07-08
Try:

```
uname -a
```

... in a terminal and see what shows up.

---

### Post by Sef on 2009-07-08
If all is running ok, then I would not worry.

---

### Post by boeman on 2009-07-09
> **Bucky Ball said:**
> Try:

```
uname -a
```

... in a terminal and see what shows up.

Gives me:

```
sylvain@atlas:~$ uname -a
Linux atlas 2.6.24-24-server #1 SMP Tue Jun 30 21:03:25 UTC 2009 i686 GNU/Linux

```

---

### Post by Bucky Ball on 2009-07-09
As far as I know, and someone correct me if I'm wrong, that is the latest kernel for 8.04 and all my machines were updated to it recently (they all run 8.04). 

Also, and I should have thought of this earlier as much easier, go System->Admin->System Monitor and hit the System tab if it is not already hit. Should be the first entry.

---

### Post by running_rabbit07 on 2009-07-09
If you open System Monitor it will also show the version and Kernal under the System tab.

---

