---
title: "Automate shutdown when idle with Cron (Suspend does not work)"
date: 2009-08-25
forum: Hardware
---

### Post by njhomeowner on 2009-08-25
Hi,

I am trying to get Cron to execute a power-off shell script to shut down my machine after a predetermined length of time.  I found the following thread:

[http://ubuntuforums.org/showthread.php?t=530973](http://ubuntuforums.org/showthread.php?t=530973)

When I entered the modifications to /etc/crontab and then run a tail /var/syslog I see that cron is running the script every 5 minutes (or looks like it is anyway).  When I run the poweroff.sh script directly it shuts down the computer immediately.  If I leave the machine alone for an hour or more it does not shutdown.  Is this because there are some background processes keeping it above the threshold.  I did try lowering the threshold in the shell script to 2, which did not help.

Any suggestions on how I can make this work.  The suspend function does not work - the machine wont recover from it.  I need an alternative - it's for my wife's machine and she is constantly leaving it on.

HELP.

Thanks

---

### Post by njhomeowner on 2009-08-25
Oh, by the way, I did change the usernames in the crontab and shell scripts to match those of the machine I am using.

My experience level is beginner to intermediate, but my experience with Linux/Unix shell commands is nil - except for what I have learned by using Linux for the past 4 years. Thus most shell experience is cut and paste from users putting stuff in their threads.

I did read the post about people putting malicious code in threads - that's wrong (and I do know enough to recognize stuff like that)

Thanks

---

