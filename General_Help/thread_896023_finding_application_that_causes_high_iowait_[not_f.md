---
title: "finding application that causes high iowait [not firefox]"
date: 2008-08-20
forum: General Help
---

### Post by vajorie on 2008-08-20
I observe occasional very high iowaits in the system-monitor-applet. How can I find which application is causing this? Neither top nor system-monitor is providing that info. 

PS. already turned Firefox' security database things off. 
PSS. This is up-to-date hardy

---

### Post by sdennie on 2008-08-20
You could try:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

That will turn on disk activity logging.  To watch it:

```

tail -f /var/log/syslog

```

To turn it back off use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

