---
title: "cron logging too much"
date: 2008-07-17
forum: General Help
---

### Post by cnschulz on 2008-07-17
Hi, 

Currently my logs are filling up with cron notifications about jobs that run successfully.

Im running munin and thus have many cron jobs running every 5 minutes.

Is there a way to only log cron jobs on error?

cheers

c.

---

### Post by unutbu on 2008-07-17
If it is /var/log/syslog that is filling up, then perhaps you could edit /etc/init.d/cron by changing

```
start)	log_daemon_msg "Starting periodic command scheduler" "crond"
        start-stop-daemon --start --quiet --pidfile /var/run/crond.pid --name cron --startas /usr/sbin/cron -- $LSBNAMES
```

to

```
start)	log_daemon_msg "Starting periodic command scheduler" "crond"
        start-stop-daemon --start --quiet --pidfile /var/run/crond.pid --name cron --startas /usr/sbin/cron -- **-L0 **$LSBNAMES
```

(All I did was add the -L0 flag).
I'm not entirely sure about the syntax for start-stop-daemon, so you might have to experiment a bit. Unfortunately, this will shut off all cron logging -- I don't know if that matters to you.

---

### Post by cnschulz on 2008-07-17
Thanks, 

Ill keep that in mind.. 

ive used the >> /dev/null thinking that would do the trick but it doesnt!! see the following log entry.

Jul 18 12:05:01 zoidberg /USR/SBIN/CRON[7108]: (root) CMD (/usr/bin/weather > /var/www/weather/hourly.txt  >> /dev/null)

---

