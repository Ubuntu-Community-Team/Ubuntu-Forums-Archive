---
title: "Get faster bootime?"
date: 2008-11-03
forum: General Help
---

### Post by _sAm_ on 2008-11-03
Came across a tip on a blog to make Ubuntu boot faster;
> Instead of starting one service at a time, let’s start them all as fast as possible, and in parallel.  This will actually slow down older, single core machines, but faster P4’s, and multiple core CPU machines will benefit from this.  Run this command, and reboot:
```
sudo perl -i -pe 's/CONCURRENCY=none/CONCURRENCY=shell/' /etc/init.d/rc
```

I have a new cpu, but I want to check here first before I try. So, is it safe, will it work - and what will the command do?

Bonus question; will I notice any different between using realtime and noatime in /etc/fstab? Perhaps rsync need the timestamp?

Thanks for any answers

---

### Post by mempman on 2008-11-03
I'm not sure how this will happen.  I.e. for a perl command to be executed, which you have above, you need to have bash going.  and bash is not started until somebody logs in via tty[0-6].

---

### Post by oldos2er on 2008-11-03
You don't need to run perl to do that, just open /etc/init.d/rc in gedit with "gksu gedit /etc/init.d/rc" and manually change CONCURRENCY=none to CONCURRENCY=shell. Save, and reboot.

---

### Post by scouser73 on 2008-11-04
I came across this article to increase the boot time; [http://www.kshoster.net/node/22]("http://www.kshoster.net/node/22")

---

