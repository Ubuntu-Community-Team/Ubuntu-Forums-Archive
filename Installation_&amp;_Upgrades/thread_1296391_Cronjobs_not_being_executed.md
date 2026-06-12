---
title: "Cronjobs not being executed"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by sander3 on 2009-10-20
Hi,

Today I found out that the cronjobs aren't working on my system. I already tried to restart the service, but that didn't fix it.

I also tried to reinstall the cron programm (aptitude reinstall cron), with no result.

The service is running, and when i do 'sudo crontab -l', it gives me the cronjobs I want to run. 

This is the output of 'sudo crontab -l':

```

29 11 * * * /etc/webmin/cron/tempdelete.pl
50 14 * * * touch /data/cronjob_test
0 0 * * * /usr/local/sbin/quota_notify &> /dev/null
33 15 * * * /etc/cron.daily/0logwatch
@weekly /some_php_script.php 
@hourly /usr/sbin/ntpdate ntp.xs4all.nl
```

The touch command is the one I added to check if it was working, and the logwatch command is the one i was trying to add when I found out it wasn't working at all.

The rest was in there already.

My Ubuntu version is:
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.3 LTS
Release:        8.04
Codename:       hardy

I hope that someone can help me. :confused:

---

### Post by badger_fruit on 2009-10-20
shouldn't it read:-
29 11 * * * **perl** /etc/webmin/cron/tempdelete.pl

?

Mind you, the rest should still run OK though ...

---

### Post by sander3 on 2009-10-21
That webmin thing executes without perl too.

But the cronjobs are still not being executed.

So do you have any other sugestions?

---

### Post by laceration on 2009-10-21
put this on the top line of your crontab
```

PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/bin:/usr/local/sbin

```
plus any other path that programs are in that you have in crontab.

Also, do not simply write a command, but the whole path to a command.
Instead of 
```
touch ...
```
use
```
/bin/touch ...
```

---

### Post by sander3 on 2009-10-23
> **laceration said:**
> put this on the top line of your crontab
```

PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/bin:/usr/local/sbin

```plus any other path that programs are in that you have in crontab.

Also, do not simply write a command, but the whole path to a command.
Instead of 
```
touch ...
```use
```
/bin/touch ...
```


Okay, i have done everything you suggested. But still no cronjobs. :confused:

If i run ps, I see that cron is active:

root     13887     1  0 Oct20 ?        00:00:00 /usr/sbin/cron


But sometimes, people are talking about "crond". But i cannot find that. Maybe that's the problem?

---

### Post by laceration on 2009-10-23
Like you I only have the cron process and it is working.

Why are you running cron as root?  Maybe if you use it as user you'd have success.  Do crontab -e w/o sudo.  You might look at the man pages for cron and crontab to see how it handles root cron jobs.

Do something very simple to make sure it is not cron.  It could be your scripts and issues being root.
Something like

```
/bin/touch /home/yourusername/data/cronjob_test
```

I have written plenty of scripts that work everywhere except in cron.  Cron will not do anything with a user interface(even though some claim it will) and sometimes cron will not run a script that calls another program or script.  Sometimes you have to rewrite things just for cron.

Supposedly Cron is going to be replaced -- it is way outdated.

---

