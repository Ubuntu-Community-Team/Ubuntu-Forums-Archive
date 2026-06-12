---
title: "Cronjobs aren't working any idea?"
date: 2008-11-22
forum: General Help
---

### Post by nappymonster on 2008-11-22
hi all,
I have a command (/usr/bin/killall /usr/bin/python -s SIGSTOP) i need to run daily on my ubuntu box at 6pm, but it needs to run as root to work, which is why I think cronjobs aren't working. I also need /usr/bin/killall /usr/bin/python -s SIGCONT to run at 11pm daily (again, as root).

Any ideas on how to make this work?
thanks,
Nappymonster

---

### Post by drs305 on 2008-11-22
To run commands requiring root privileges, you can set up a root cron job with the command:
```
sudo crontab -e
```
These jobs will be run as root.

For more info, here is the community documentation:
[CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

