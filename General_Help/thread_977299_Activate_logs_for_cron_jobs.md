---
title: "Activate logs for cron jobs"
date: 2008-11-10
forum: General Help
---

### Post by ierpe on 2008-11-10
Im having problems with cron jobs, and I cant find any logs to see whats going wrong( or at least if they're being executed...)

How can I set up the logs for the cron jobs?

Thanks.

---

### Post by ciscosurfer on 2008-11-10
Here are two good places for you to start:

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

Let's say you want to see that you (who is using sudo to run aptitude, for example) have accessed a program via sudo, you'd check /var/log/auth.log and might see something like this:```
Nov 8 14:27:17 happy-desktop sudo:     happy : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/bin/aptitude update
```

---

### Post by ierpe on 2008-11-10
Thanks :)

---

