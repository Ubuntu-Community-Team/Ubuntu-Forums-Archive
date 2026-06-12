---
title: "cron not executing /etc/crontab"
date: 2008-08-08
forum: General Help
---

### Post by IvoLucien on 2008-08-08
Hi folks,

I'm new to Ubuntu (8.04), but have done a bunch of research trying to get this to work. I'm probably just missing something simple...

cron (v3.0pl10100ubuntu2) isn't executing [FONT="Courier New"]/etc/crontab[/FONT] or [FONT="Courier New"]/etc/cron.daily[/FONT], etc. - it doesn't run anything in [FONT="Courier New"]/etc/crontab[/FONT]

My test entry in crontab is: [FONT="Courier New"]* * * * * root touch /root/crontest[/FONT]
(the whole file is appended)

1) cron is running (confirmed via ps)
2) reloaded config using [FONT="Courier New"]/etc/init.d/cron reload[/FONT] - it said [FONT="Courier New"][OK][/FONT]
3) [FONT="Courier New"]/root/crontest[/FONT] exists, with 644 perms
4) the PATH is set in [FONT="Courier New"]/etc/crontab[/FONT] and includes [FONT="Courier New"]/bin[/FONT] (for touch)
5) manually running [FONT="Courier New"]touch /root/crontest[/FONT] works
6) only using the system crontab, editing it with vim
7) tried [FONT="Courier New"]echo test > /root/crontest[/FONT] in [FONT="Courier New"]/etc/crontab[/FONT] previously, no luck
8) there is no [FONT="Courier New"]/var/log/cron.log[/FONT] or [FONT="Courier New"]cron.log[/FONT] anywhere
9) if I run the run-parts commands manually, they work

I bow before the wise and kind Ubuntu community.  ^_^

*warm thoughts*

Ivo
Seattle WA USA

/etc/crontab:
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
cd /

# m  h  dom mon dow  user  command
  *  *   *   *   *   root  touch /root/crontest
 17  *   *   *   *   root  run-parts --report /etc/cron.hourly
  5  4   *   *   *   root  run-parts --report /etc/cron.daily
 15  3   *   *   7   root  run-parts --report /etc/cron.weekly
 45  4   1   *   *   root  run-parts --report /etc/cron.monthly
#

```

---

### Post by IvoLucien on 2008-08-08
I figured it out!

I had made the faulty assumption that the crontab file was pretty much a script that was executed.  So I added a "cd /" line at one point, and that bolloxed the file.

I'm still wondering why there's no cron.log file...

---

