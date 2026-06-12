---
title: "strange cron problem"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by MrBordello on 2009-03-24
Hi everyone,
my cron daemon is acting very strange. I have some cronjobs (added as root via crontab -e):

```

* * * * *       root    /usr/bin/python /root/check.py >> /root/check.py.log
*/10 * * * *    root    /usr/bin/python /root/update.py >> /root/update.py.log

```

tail /var/log/syslog shows this:

```

Mar 24 19:10:01 tobi /USR/SBIN/CRON[6049]: (root) CMD (root^I/usr/bin/python /root/update.py >> /root/update.py.log)
Mar 24 19:10:01 tobi /USR/SBIN/CRON[6056]: (root) CMD (root^I/usr/bin/python /root/check.py >> /root/check.py.log)
Mar 24 19:11:01 tobi /USR/SBIN/CRON[6095]: (root) CMD (root^I/usr/bin/python /root/check.py >> /root/check.py.log)

```

So everything seems allright. The thing is: The scripts don't execute. The log files (check.py.log and update.py.log) stay empty.

If I manually execute
```
/usr/bin/python /root/check.py >> /root/check.py.log
```
or
```
/usr/bin/python /root/update.py >> /root/update.py.log
```
It works.

I already did google and all ... I really don't know what to do ... :(

Ok, got it. For reasons unknown I have to write my crontab entries like this:

```

* * * * *       /usr/bin/python /root/check.py >> /root/check.py.log
*/10 * * * *    /usr/bin/python /root/update.py >> /root/update.py.log

```

:)

---

