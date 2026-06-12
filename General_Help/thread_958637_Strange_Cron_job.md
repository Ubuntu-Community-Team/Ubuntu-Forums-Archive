---
title: "Strange Cron job"
date: 2008-10-25
forum: General Help
---

### Post by extruct on 2008-10-25
Hello, I got Ubuntu Hardy Heron 8.04.1LTS 32bit Desktop edition.
I installed apache + php5 + mysql since I'm a web developer. They all not run by default I start them when needed.
Today I payed attention to strange cron job that runs every 30min:
```

Oct 25 20:09:01 dpc /USR/SBIN/CRON[14436]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

Oct 25 20:39:01 dpc /USR/SBIN/CRON[14548]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

Oct 25 21:09:01 dpc /USR/SBIN/CRON[14652]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

```
What it does?

Another one runs every hour:
```

Oct 25 20:17:01 dpc /USR/SBIN/CRON[14479]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Oct 25 21:17:01 dpc /USR/SBIN/CRON[14679]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```
What it does?

Sorry if those questions are noob questions >.<

Thanks a lot!

---

### Post by geirha on 2008-10-25
```
$ cat /etc/cron.d/php5 
# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm

```

The hourly one runs all the scripts in /etc/cron.hourly/ (if any)

---

