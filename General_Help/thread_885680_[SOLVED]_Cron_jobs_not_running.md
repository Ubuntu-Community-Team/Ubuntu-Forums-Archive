---
title: "[SOLVED] Cron jobs not running"
date: 2008-08-10
forum: General Help
---

### Post by G1ZmO65 on 2008-08-10
I was looking to power down my home server at a specific time each day so I set a cron job but it doesnt run.

I'm probably doing something silly wrong but I can't see it (noob)

Paul

```
root@ubuntu:~# crontab -l
17 11 * * * /etc/webmin/cron/tempdelete.pl
20 16 10 8 * shutdown -P 0 #Auto Shutdown
```

btw I also get this error:
```
root@ubuntu:~# cron
cron: can't lock /var/run/crond.pid, otherpid may be 5051: Resource temporarily unavailable
```

---

### Post by mike2357 on 2008-08-10
Don't worry about the error message you got when you ran "cron."  You shouldn't ever have to run it.  It should be already running, and you can verify it by running
ps -eaf | grep cron

Regarding your shutdown command, I think the problem is the PATH.  Jobs run from cron with a very limited path.  On my system, root's cron path is only /bin and /usr/bin.  So change the shutdown command to reference the full path:
/sbin/shutdown . . .

I'm not sure what the problem is with your other cron command.  Is it also not running?

"man 5 crontab" is a great resource on the ins and outs of cron.

---

### Post by G1ZmO65 on 2008-08-10
Hmm still don't know why it's not running :(
Could CRON be halted or something?

```
root@ubuntu:~# ps -eaf | grep cron
root      7144  5158  0 20:53 pts/0    00:00:00 grep cron
root@ubuntu:~# crontab -l
17 11 * * * /etc/webmin/cron/tempdelete.pl
53 20 * * * /sbin/shutdown -P 0 #Auto Shutdown
root@ubuntu:~# date
Sun Aug 10 20:53:32 BST 2008
```

btw I think the webmin cron command is just some sort of cleanup that webmin installed but dont know if it's running either.

---

### Post by G1ZmO65 on 2008-08-10
I tried putting this in /etc/crontab to no avail

```
30 21 * * *     root    shutdown -P 0
```

Took a different tack and made a script to test it:

```
root@ubuntu:~# mkdir scripts
root@ubuntu:~# cd scripts
root@ubuntu:~/scripts# vim test
root@ubuntu:~/scripts# chmod 755 test
root@ubuntu:~/scripts# ./test
-------------------
1 minute has passed
-------------------
root@ubuntu:~/scripts# crontab -e
crontab: installing new crontab
root@ubuntu:~/scripts# crontab -l
17 11 * * *     /etc/webmin/cron/tempdelete.pl
# 53 20 * * *   /sbin/shutdown -P 0 #Auto Shutdown
* * * * *       /scripts/test
root@ubuntu:~/scripts# date
Sun Aug 10 21:41:22 BST 2008
root@ubuntu:~/scripts# date
Sun Aug 10 21:44:05 BST 2008
```

The script obviously works so cron can't be running imo

Any suggestions?

Paul

---

### Post by mike2357 on 2008-08-10
OK, your cron isn't running, that's problem number 1.

To restart it:
sudo /etc/init.d/cron restart

Here's the output when I run ps -eaf | grep cron
root      5263     1  0 Aug07 ?        00:00:00 /usr/sbin/cron
mike     18015 17994  0 17:06 pts/0    00:00:00 grep cron

I never put anything in /etc/crontab, although some people do.  I figure /etc/crontab is for the system, and I just use crontab -e, which modifies files in /var/spool/cron/crontabs.  I never modify those files directly.  That's what crontab -e is for.

See if restarting cron works.  That's troublesome that it wasn't running.  If you continue to find it not running, I'd look at /var/log/auth.log and /var/log/syslog, search on cron and see if you see anything going on.

A debugging trick is to follow each cron command (on the same line but before your comment) with:
> OUTPUT_FILE_OF_YOUR_CHOOSING 2>&1
This will send the output of the cron command to an output file that you can examine later.  If the file is created, you know the command at least executed.

Good luck.

---

### Post by G1ZmO65 on 2008-08-11
Thanks Mike,

```
root@ubuntu:~# ps -eaf | grep cron
root     10575     1  0 09:20 ?        00:00:00 /usr/sbin/cron
root     10832 10776  0 10:12 pts/0    00:00:00 grep cron
root@ubuntu:~# vim test.log
root@ubuntu:~# date
Mon Aug 11 10:12:38 BST 2008
root@ubuntu:~# /etc/init.d/cron restart
 * Restarting periodic command scheduler crond                     [ OK ]
root@ubuntu:~# cd scripts
root@ubuntu:~/scripts# crontab -e
crontab: installing new crontab
root@ubuntu:~/scripts# crontab -l
17 11 * * *     /etc/webmin/cron/tempdelete.pl
# 53 20 * * *   /sbin/shutdown -P 0 #Auto Shutdown
* * * * *       ./scripts/test > ./scripts/test.log 2>&1
root@ubuntu:~/scripts# ls
test  test.log
root@ubuntu:~/scripts# vim test.log
```

```
[Output of test.log]
-------------------
1 minute has passed
Mon Aug 11 10:31:01 BST 2008
-------------------
```

so CRON seems to be running now so changed the crontab:

```
root@ubuntu:~/scripts# crontab -l
17 11 * * *     /etc/webmin/cron/tempdelete.pl
# 53 20 * * *   /sbin/shutdown -P 0 #Auto Shutdown
* * * * *       ./scripts/test
```

and would expect the output to the screen every minute but it doesnt happen (am I wrong?)

---

### Post by mikjp on 2008-08-11
-- deleted --

---

### Post by G1ZmO65 on 2008-08-11
Ok it's now working but still have no idea why CRON wasn't working before.

```
root@ubuntu:~# crontab -l
17 11 * * * /etc/webmin/cron/tempdelete.pl
45 15 11 08 *   /sbin/shutdown -P 30 #Auto Shutdown
root@ubuntu:~#
Broadcast message from root@ubuntu
        (unknown) at 15:45 ...
The system is going down for power off in 30 minutes!
root@ubuntu:~# shutdown -c
```

on another plus side I learned a bit more about CRON, how to set up CRONTAB and running scheduled scripts :)

Cheers

Paul

---

