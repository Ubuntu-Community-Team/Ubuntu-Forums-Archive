---
title: "question about rysnc + cron"
date: 2008-10-22
forum: General Help
---

### Post by toast4u on 2008-10-22
I have a question regarding rsync.  I would like to sync the new files between my Hardy laptop and my Hardy server.  I am new to Linux, but I seem to have come up with two commands that work when run from the command line.  But while they work okay when run manually, they will not work when I try to run them as scheduled tasks with the Gnome Schedule 2.0.2 (aka “Scheduled Tasks”) crontab front end.  In the rsync.log file I told it to use, I get error messages for both the send and receive commands (unexplained error – code 255).  My network setup should be okay – like I said these commands run fine if I cut and paste them into the terminal.  Can anyone help me out?

The commands:
```
rsync -azu -vv --port=443 --log-file=/var/log/rsync.log -e "ssh -p 443 -i /home/default/.ssh/id_rsa" /home/default/Documents/PM2/* user@myserver.dyndns.org:/home/user/disk2/Backups/laptop/Linux/home/default/Documents/PM2

rsync -azu -vv --port=443 --log-file=/var/log/rsync.log -e "ssh -p 443 -i /home/default/.ssh/id_rsa" user@myserver.dyndns.org:/home/user/disk2/Backups/laptop/Linux/home/default/Documents/PM2/* /home/default/Documents/PM2
```

The error messages:
```
2008/10/22 06:00:01 [10669] rsync: connection unexpectedly closed (0 bytes received so far) [sender]
2008/10/22 06:00:01 [10669] rsync error: unexplained error (code 255) at io.c(454) [sender=2.6.9]
2008/10/22 06:15:01 [11140] rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
2008/10/22 06:15:01 [11140] rsync error: unexplained error (code 255) at io.c(454) [receiver=2.6.9]
```

---

### Post by toast4u on 2008-10-29
Anyone have any ideas about this?

---

