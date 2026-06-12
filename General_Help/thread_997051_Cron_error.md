---
title: "Cron error"
date: 2008-11-29
forum: General Help
---

### Post by thefiestysoldier on 2008-11-29
when I try to start cron (in sudo) I get this  error:

```
cron: can't lock /var/run/crond.pid, otherpid may be 4880: Resource temporarily unavailable

```

---

### Post by mike2357 on 2008-11-29
You shouldn't have to start cron as it should be set to start whenever you boot your computer.  To test:

ps -eaf | grep cron

You should see something like this:
root      5251     1  0 08:19 ?        00:00:00 /usr/sbin/cron

If you want to add/update/delete cron entries, the command is "crontab" for your commands, or "sudo crontab" for root's commands.

"man 5 crontab" has a wealth of information about using cron.

---

