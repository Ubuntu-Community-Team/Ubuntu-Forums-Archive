---
title: "Cron not running a certain script"
date: 2008-09-05
forum: General Help
---

### Post by obrienmd on 2008-09-05
Am I doing anything foolish here?  Here's my crontab -l as root:

# m h  dom mon dow   command
30 23 * * 0 /usr/bin/vmware_backup_daily.sh > /var/log/vmware/backup/backup-daily-`date +%G%m%d`.log
30 23 * * 1 /usr/bin/vmware_backup_daily.sh > /var/log/vmware/backup/backup-daily-`date +%G%m%d`.log
30 23 * * 2 /usr/bin/vmware_backup_daily.sh > /var/log/vmware/backup/backup-daily-`date +%G%m%d`.log
30 23 * * 3 /usr/bin/vmware_backup_daily.sh > /var/log/vmware/backup/backup-daily-`date +%G%m%d`.log
30 23 * * 4 /usr/bin/vmware_backup_daily.sh > /var/log/vmware/backup/backup-daily-`date +%G%m%d`.log
30 23 * * 5 /usr/bin/vmware_backup_weekly.sh > /var/log/vmware/backup/backup-weekly-`date +%G%m%d`.log
30 23 * * 6 /usr/bin/vmware_backup_daily.sh > /var/log/vmware/backup/backup-daily-`date +%G%m%d`.log
* * * * * logger "testing cron"

Notice the logger one at the end...  I simply added that to make sure that cron itself was working.  Indeed, the "testing cron" message shows up every minute in /var/log/messages.  However, none of my scripts get run @ 11:30pm on the night they are supposed to.  Any ideas?

Hardy Server x64.

---

### Post by isomer on 2008-09-05
Hi

Cron might be writing errors to /var/log/syslog, which might help show what is going wrong.  You could also uncomment the line in /etc/syslog.conf that allows the syslogger to write to a seperate log file - /var/log/cron.log by default.

Your problem might be a permissions problem with the script.  Has it been set to be executable?  I've missed that a few times.

---

### Post by matthewboh on 2008-09-05
You might want to also just try running the job from the command line using root
```
sudo /usr/bin/vmware_backup_daily.sh > /var/log/vmware/backup/backup-daily-`date +%G%m%d`.log
```
to see if it runs

---

