---
title: "/etc/cron.daily/find script"
date: 2008-11-06
forum: General Help
---

### Post by sulekha on 2008-11-06
Hi all,

I have read that the locate command database is normally updated only once each day,as documented in the /etc/cron.daily/find script, but i didn't find any find script  in /etc/cron.daily/ directory ?

**NB: i use ubuntu 8.04.1**

---

### Post by Sorivenul on 2008-11-07
I believe this is actually the mlocate script in Ubuntu, at least in mine.  However, if I need to update my find database more frequently than the cronjob I just run:
```
sudo updatedb
```
This is more or less what the cronjob does, AFIK.

---

