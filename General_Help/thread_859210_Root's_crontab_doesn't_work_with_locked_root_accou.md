---
title: "Root's crontab doesn't work with locked root account"
date: 2008-07-14
forum: General Help
---

### Post by gfunkdave on 2008-07-14
I just noticed that the commands I've got running in root's crontab aren't working. My syslog seemed to be saying that the problem was that root had an expired account:

```

Jul 14 09:44:01 meadows-server CRON[24997]: User account has expired

```

When I reenabled the root account with passwd -u, everything works - but now my root account is enabled. How do I disable the root account and have crontab work? Obviously passwd -l disables it but also marks it as expired, which puts me back at square 1.

I'm running Ubuntu Hardy AMD64.

---

### Post by sujoy on 2008-07-14
you can set an absurd password, (say the md5sum of a word), that way the root account ought to be pretty safe. and it won't be deactivatedd too, thereby allowing you to run the root's crontab.

however, remember to set your username (or any other), in suoders file with all permissions, username ALL=(ALL) ALL

---

### Post by gfunkdave on 2008-07-14
Good point - though if Ubuntu ships with root disabled, and using root's crontab is the preferred way to do things (over editing /etc/crontab), then isn't this a pretty big oops?

---

### Post by mhmjr on 2008-07-21
> **gfunkdave said:**
> Good point - though if Ubuntu ships with root disabled, and using root's crontab is the preferred way to do things (over editing /etc/crontab), then isn't this a pretty big oops?

This link helped me get the resolution to this:


[ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=846093&highlight=cron+root+user+expired")

The code from cdenley got me most of the way, then I hand edited the /etc/shadow entry for root removing the '1' in the 2nd to last field of this file. That field indicates how many days since January 1st 1970 that the account in question has been disabled:

[http://tldp.org]("http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html")

-mhmjr

---

