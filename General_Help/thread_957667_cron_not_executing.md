---
title: "cron not executing"
date: 2008-10-24
forum: General Help
---

### Post by sinukas on 2008-10-24
Hey everyone, I cannot get cron to execute commands on my ubuntu-server box:


will@cataract:~$ crontab -l
# m h  dom mon dow   command
0 0 * * * php /home/will/cron/ips_alert_updater/intrushield/grab_alerts.php >> /home/will/CRON_DEBUG_WILL.txt
will@cataract:~$ sudo crontab -l
# m h  dom mon dow   command
0 0 * * * php /home/will/cron/ips_alert_updater/intrushield/grab_alerts.php >> /home/will/CRON_DEBUG_ROOT.txt


There are no logs appearing, signaling that the cronjob has run. I have checked the permissions, command, and script, they all work correctly. Am I missing something here? Does cron need to be turned "on" ???

will@cataract:~$ ps -ef | grep cron
root      4436     1  0 Oct21 ?        00:00:00 /usr/sbin/cron
will     14105 13572  0 15:09 pts/1    00:00:00 grep cron

---

### Post by geirha on 2008-10-24
It looks correct. Those scripts should run every day at midnight. And even if the script fails, the /home/will/CRON_DEBUG_*.txt files should be created, so it's very odd if even that doesn't happen.

If cron fails to run a scheduled process, it will mail the user about it. To read such mails, type ```
mail
``` in a terminal.

---

### Post by taladan on 2008-10-24
from looking at your crontab, looks like you're wanting it to run on the 0 minute at the 0 hour (midnight) every day...is this your intended behavior, and if so have you waited until midnight to see what it does?

Tal

---

### Post by sinukas on 2008-10-24
Woops, that's the problem then! I was trying to get it to run every minute! thanks for pointing that out!

---

### Post by The Cog on 2008-10-24
Every minute would be * * * * *.

---

