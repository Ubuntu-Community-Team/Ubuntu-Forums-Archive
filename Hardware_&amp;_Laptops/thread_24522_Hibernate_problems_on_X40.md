---
title: "Hibernate problems on X40"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by mahnve on 2005-04-07
When trying to hibernate my TP X40, it always comes back up after a few seconds. I see in the hibernate.sh script that it includes the restart code - but I suppose it shoud wait to execute that, right?

Sleep works very well.

---

### Post by egibbs on 2005-04-28
Did you ever figure this out?  I'm having the same problem on a T42p and I'm stuck.  

Ed Gibbs

---

### Post by bubi on 2005-05-03
How big is your swap partition compared to your main memory?

Since hibernate saves the physical memoryspace on the swap partition you need  a swap partition size at least the size of the main memory.

I had the same problems myself but after I changed my partition scheme everything works fine.

---

### Post by mcclen on 2005-07-09
I have this problem as well, but I know why. I'm running mysql. For some reason, the hibernate script doesn't catch mysql and shut it down. So hibernate simply returns, but I do see a statement, something like "funny, mysql is still runinng". If I manually shutdown mysql, the hibernate works flawlessly.

As I understand it, it looks like hibernate selects what to kill/halt based on owner of the process id. Since mysql is running not as root, it seems to be missed. Suggestions on how to modify hibernate to include other "system" ids?

Thanks,

Chris

---

### Post by AlP on 2005-08-10
I fixed my X40 sleep-problem by adding STOP_SERVICES="mysql " in my /etc/defaults/acpi-support.

Now everything works fine.

---

