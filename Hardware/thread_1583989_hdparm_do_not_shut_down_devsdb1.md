---
title: "hdparm do not shut down /dev/sdb1"
date: 2010-09-28
forum: Hardware
---

### Post by sknitti on 2010-09-28
Hello,

I installed Mythbuntu a few weeks ago everything works good.
There is only one thing that does not work.
I want to shut down my second hd -> /dev/sdb

So I installed:

```
sudo apt-get install hdparm
```

and edited /etc/hdparm.conf by adding the line:

```
command_line {hdparm -Y -S 1 /dev/sdb1}
```

but it does not work.
If I do a:

```
sudo hdparm -Y -S 1 /dev/sdb1
```

everything works fine until next boot.

Does someone knows whats happend here or any hints what I should further investigate?

Thanks in advance

Steffen

---

### Post by IcarusR on 2010-09-28
Se this bug report on launchpad

[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120]("https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120")

---

