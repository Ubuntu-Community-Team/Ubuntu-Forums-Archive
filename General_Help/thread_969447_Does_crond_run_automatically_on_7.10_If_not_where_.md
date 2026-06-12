---
title: "Does crond run automatically on 7.10? If not where should I set that?"
date: 2008-11-03
forum: General Help
---

### Post by qwert231 on 2008-11-03
I run ps -A and don't see crond running.

Where should it be set to run at boot?

---

### Post by conscious on 2008-11-03
On my system, I see cron running, not crond. Cron should run automatically. You can check the logs for any messages from it:
```
cat /var/log/syslog | grep cron
```

Cron is started by the script /etc/init.d/cron , which you should have. If the script is in place but cron doesn't seem to be running, you may need to update the symlinks in /etc/rc?.d with
```
sudo update-rc.d cron defaults
```

---

