---
title: "remove all cron jobs from removed software"
date: 2008-10-09
forum: General Help
---

### Post by drewtown on 2008-10-09
I removed both Munin and Cacti yet their cronjobs are still running.  How can I remove them?

Oct  9 11:00:01 ubuntu-server /USR/SBIN/CRON[17178]: (www-data) CMD (php /usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Oct  9 11:00:01 ubuntu-server /USR/SBIN/CRON[17181]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)

---

### Post by geirha on 2008-10-09
There are at least two places they may be listed:
```
sudo crontab -e
gksudo gedit /etc/crontab
```

---

