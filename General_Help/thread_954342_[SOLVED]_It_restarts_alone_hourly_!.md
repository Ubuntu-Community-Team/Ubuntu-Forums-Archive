---
title: "[SOLVED] It restarts alone hourly ?!?"
date: 2008-10-21
forum: General Help
---

### Post by promeca on 2008-10-21
Since I turned on my PC today my Ubuntu Hardy started restarting hourly at *.09 mins and I have no idea why it's happening. I haven't installed anything new today and yesterday everything was alright.

Here are the logged restarts from today:

Oct 21 10:09:26 .... syslogd 1.5.0#1ubuntu1: restart.
Oct 21 11:09:41 .... syslogd 1.5.0#1ubuntu1: restart.
Oct 21 12:09:53 .... syslogd 1.5.0#1ubuntu1: restart.

The last thing before restarting is always a cron job - the php session close and one custom. But they both are working fine for days and nothing has been changed in them recently. 

I don't know where and what to inspect to find the problem. Any help?
Thanks in advance!

---

### Post by geirha on 2008-10-21
```
cat /etc/crontab
sudo crontab -l
```

Do those commands list any jobs that do shutdown or similar?

---

### Post by xzibiz on 2008-10-21
i have the same problem.:
here is my result:

> 
cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )


> 
sudo crontab -l
[sudo] password for xzibiz: 
no crontab for root


---

### Post by promeca on 2008-10-21
Exactly the same here:

> # m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


> no crontab for root


there is also nothing special in /etc/cron.d

If it might have something to do with it - yesterday when turning off the PC (I use hibernate) the hibernate failed (it froze on a black screen) and I turned it off by pressing the button. 

I also made some partial upgrade of the system

---

### Post by promeca on 2008-10-21
I can tell now that the computer restarts for first time exactly one hour after it is turned on and continues restarting every hour at that time. So maybe I should look for something in the logs after the restart (in the starting)

---

### Post by promeca on 2008-10-22
The problem just disappeared after 2 days of reading logs where no errors were found .... I don't like this.

---

