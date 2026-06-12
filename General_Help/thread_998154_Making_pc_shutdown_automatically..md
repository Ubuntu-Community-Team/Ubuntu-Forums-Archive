---
title: "Making pc shutdown automatically."
date: 2008-11-30
forum: General Help
---

### Post by OmnificienT on 2008-11-30
Hello,

How can I make my pc shutdown automatically at a certain time?

I tried: shutdown 23:00. It seems to work. Could I also automate this and could I also create a script, which would set this?

Thank You,

OmnificienT

---

### Post by taurus on 2008-11-30
Look at cron (/etc/crontab).

```
man cron
```

---

### Post by ColdFFF on 2008-11-30
> **taurus said:**
> Look at cron (/etc/crontab).

```
man cron
```

Or install gnome-schedule in Synaptic Package Manager and use Scheduled Tasks under System Tools in the Applications menu.

---

### Post by KeyserSoze93 on 2008-11-30
```
echo "00	23	*	*	*	poweroff" >crontab
sudo crontab crontab
```

---

