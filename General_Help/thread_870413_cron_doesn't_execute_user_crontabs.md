---
title: "cron doesn't execute user crontabs"
date: 2008-07-25
forum: General Help
---

### Post by Apo2k4 on 2008-07-25
Hi, on two of my machines cron does not execute user crontabs, while root crontabs work just fine.

I've got this root crontab:
* * * * * echo test > /tmp/test
and this user crontab:
* * * * * echo test > /tmp/test2

Looking at the cron logs, I see this:
Jul 26 01:31:01 deepthought /USR/SBIN/CRON[22667]: (root) CMD (echo test > /tmp/test)
Jul 26 01:32:01 deepthought /USR/SBIN/CRON[22731]: (root) CMD (echo test > /tmp/test)
Jul 26 01:33:02 deepthought /USR/SBIN/CRON[22743]: (root) CMD (echo test > /tmp/test)

Cron seems to be running, but there's nothing about my user crontabs at all... when I do crontab -e as a user, I get BEGIN EDIT and END EDIT messages.
Any ideas, why it doesn't work as it should?
Cheers,
Apo

(Edit: Both are 8.04, one's a normal desktop install upgraded from 7.10, the other one's a minimal server install)

---

### Post by RealPSL on 2008-07-27
There are only 2 things that I can see that could even be remotely wrong.
[LIST=1]
[*]Your crontab file does not have a newline at the end as required
[*]You are being denied running cron as a regular user by the cron.deny & cron.allow files
[/LIST]

I doubt it is the latter because Debian systems by default allow all users to run cron jobs.

---

### Post by Apo2k4 on 2008-07-27
Well, it certainly isn't the first one... I have newlines in both crontabs.
Are the cron.deny and .allow files supposed to be in /etc/? Because they're not...

I just saw this in /var/log/messages:
Jul 27 16:50:01 deepthought kernel: [76500.250832] cron[12160]: segfault at 00000000 eip 00000000 esp bf950fbc error 14
Jul 27 16:50:01 deepthought kernel: [76500.289280] cron[12161]: segfault at 00000000 eip 00000000 esp bf950fbc error 14
Jul 27 16:51:02 deepthought kernel: [76560.202878] cron[12201]: segfault at 00000000 eip 00000000 esp bf950fbc error 14
Jul 27 16:51:02 deepthought kernel: [76560.707270] cron[12202]: segfault at 00000000 eip 00000000 esp bf950fbc error 14

I'm beginning to think that this might be related to pam-mount - both computers that have the problem have that installed, while the one that works doesn't. Is it possible that cron somehow has problems authenticating itself?

Edit: It was indeed pam-mount! I've creanted custom common-auth and custom-session files for cron in /etc/pam.d/ and now it's working!

---

### Post by mike2357 on 2008-07-27
You are right.  It could be a pam authentication problem.  This thread might help:

[http://ubuntuforums.org/showthread.php?t=820909]("http://ubuntuforums.org/showthread.php?t=820909")

---

### Post by castawaybcn on 2009-07-16
> **Apo2k4 said:**
> Edit: It was indeed pam-mount! I've creanted custom common-auth and custom-session files for cron in /etc/pam.d/ and now it's working!

I know this is rather old, but could you please tell me how you added those in /etc/pam.d/cron?

I am having a similar issue posted [here]("http://ubuntuforums.org/showthread.php?t=1212273") and still could not find a way around it...

thanks

---

