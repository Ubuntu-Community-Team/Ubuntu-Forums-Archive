---
title: "[SOLVED] backup-manager: cronjob is not running"
date: 2008-11-11
forum: General Help
---

### Post by juk_de on 2008-11-11
Hi all!

I'm running backup-manager 0.7.6-3 on Hardy. Everything is working fine except the cronjob.

There is a script located in /etc/cron.daily, it has correct rights and when called manually is working fine.
```
#!/bin/sh
# cron script for backup-manager
test -x /usr/sbin/backup-manager || exit 0
/usr/sbin/backup-manager
```


```
-rwxr-xr-x 1 root root 111 2008-10-27 13:33 /etc/cron.daily/backup-manager
```

I can see that everyday at 6:25 cron is running the daily-job:
```
Nov 11 06:25:02 ubuntu /USR/SBIN/CRON[1684]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
```

Why isn't this script executed???

:confused:
Jürgen

---

### Post by geirha on 2008-11-11
What does anacron log? ```
grep anacron /var/log/syslog
```

---

### Post by juk_de on 2008-11-11
Only this one line per day:
```
Nov 11 06:25:02 ubuntu /USR/SBIN/CRON[1684]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
```

---

### Post by juk_de on 2008-11-12
I removed anacron and it works.

I don't understand why CRON is checking
```
test -x /usr/sbin/anacron
``` and executing the job only if the file does not exist (||)!

---

### Post by geirha on 2008-11-12
It checks if /usr/sbin/anacron is executable. If it isn't executable, cron runs the jobs instead. If it is executable, cron assumes anacron will take care of it. 

I recently noticed that anacron gets disabled when the laptop is on batteries, and reenabled as soon as the power chord is connected. Could this have been the case?

---

### Post by juk_de on 2008-11-12
No. It's a Vserver which is running 24/7. So i don't need anacron.

---

