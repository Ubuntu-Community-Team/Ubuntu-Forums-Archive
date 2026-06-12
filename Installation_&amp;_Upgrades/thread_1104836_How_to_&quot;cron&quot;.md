---
title: "How to &quot;cron&quot;?"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by lvbing on 2009-03-24
my ubuntu works 7x24h,i want it reboot at midnight everyday.
i read "wiki" and do:

```
$ crontab -e
00 00 * * * reboot
```

save and reboot my ubuntu. but Nothing ever happens in this time!:(

Why? How can i do?

---

### Post by stumbleUpon on 2009-03-24
You need to be root to reboot the machine....!!

So do 'sudo su' and then 'cd' to the root directory. Edit the crontab there.

---

