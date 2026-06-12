---
title: "Chrontab doesn't work?"
date: 2008-08-19
forum: General Help
---

### Post by danthegoodman on 2008-08-19
I am trying to schedule an auto-login script I wrote in python. I created a a crontab file under my username. 

```
* * * * * /media/disk/scripts/autologin.py
```

When I call the command from the terminal, the program runs as it should. I can see that command is getting called yet the output that I print in my python script is not being printed..

syslog:
```
Aug 19 01:09:01 ********* /USR/SBIN/CRON[7250]: (danny) CMD (/media/disk/scripts/autologin.py)
```

Help?

---

### Post by danthegoodman on 2008-08-19
Can anybody help me?

---

### Post by Cheesehead on 2008-08-19
1) Creating the crontab...did you create a new file (which rarely works), or did you use 
```
crontab -e
```
and add it there?

Since syslog claimed that cron picked it up, let's assume you have a valid crontab entry that's simply doing something unintended.


2) Cron isn't terribly bright, and it's operating environment is more limited than the command line.

Instead of the command '/media/disk/scripts/autologin.py', try ```
/usr/bin/python /media/disk/scripts/autologin.py
```
and let us know what the response is.

---

