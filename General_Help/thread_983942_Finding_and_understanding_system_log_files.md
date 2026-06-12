---
title: "Finding and understanding system log files"
date: 2008-11-16
forum: General Help
---

### Post by Ameneon on 2008-11-16
Cheers, this is I guess more a general linux question than ubuntu as such, but in any event; just had xorg crash on me (at least, I was reoffered login and all applications and ongoing sessions started from within x had been shut down) and in Windows I'd know where to look at how to understand what the logs said, however in Ubuntu I entirely lack this foundation.

I do know that a number of logs are found at /var/logs and I've peeked through there but I don't know if this makes up all the logs of relevancy or whether there are other relevant logs hiding elsewhere. I also do not know how to understand or read the logs, nor which logs are important for what. Ie, the Xorg.0.log seems to only have information about the last startup of Xorg, which doesn't tell me whether Xorg actually crashed earlier or whether there was something else that caused me to be practically kicked out of the system.

In short, is there such a thing as a primer on linux system and application logs anywhere? :)

---

### Post by cmnorton on 2008-11-16
The logs are in /var/log, and your Xorg log should start with Xorg. Your best bet to a primer, is to search the internet and ask questions. Usually, you need root (sudo) privs to get at the logs. If you are in the right group -- offhand I have forgotten which one -- a regular user can view the logs.

---

### Post by geirha on 2008-11-16
Applications in general use one of two ways of logging. One is writing lines to a certain logfile, the other is logging to syslog. With syslog you can configure where the log lines should be sent and often the same lines can end up in several different files.

The applications themselves are responsible for letting the administrator know where the logs go, so read the applications' documentation. If they're logged to syslog, /etc/syslog.conf decides where the lines go based on their importance and category. 

```
man syslog.conf
```

---

### Post by Ameneon on 2008-11-16
> **cmnorton said:**
> The logs are in /var/log, and your Xorg log should start with Xorg. Your best bet to a primer, is to search the internet and ask questions. Usually, you need root (sudo) privs to get at the logs. If you are in the right group -- offhand I have forgotten which one -- a regular user can view the logs.

Ask questions is exactly what I'm doing here isn't it? :P But thanks, in any event. The problem is neither getting to the logs nor being able to read them (I can read them as "me", but if I couldn't I'm pretty sure I'd understand I needed to elevate privileges anyway :P), the problem is rather to understand what I'm looking for in the specific event of crashes, or if we go more generally; to understand what ends up where and what it means. Again, thanks for your response in any event, same to you, geirha. I'll google around for documentation on Xorg and log files in general..

---

### Post by cmnorton on 2008-11-17
I believe what goes in the log is whatever the daemon or application wants. I was able to debug what was a silent cron problem (format), because the cron log told me an entry was bogus; there were too many columns in the entry.

So, I believe it more about looking at what the different syslog facilities write to their respective logs and gaining experience from that.

You could start by looking at documentation on the syslog facility.

Edit:
-------------------
Said better than I could say it in one of the responses by [geirha]("http://ubuntuforums.org/member.php?u=243323").

---

