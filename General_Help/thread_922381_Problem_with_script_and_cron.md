---
title: "Problem with script and cron"
date: 2008-09-17
forum: General Help
---

### Post by aehirst on 2008-09-17
Im running server 8.04 and im trying to get a little backup script working.

I have saved the script in /root as calbackup.

The script is :
#!/bin/bash
tar -czvf /mnt/nas/earth/calendar-`date +%Y-%m-%d`.tar.gz  /var/www/davhome

And the cron is:

00 06 * * * /root/calbackup

The script runs fine but the tarball it creates is corrupt and about 42kb. If I run the script manually it is 52kb and works fine.

Could anyone shed shome light on my problem
Thanks for any help

---

### Post by isomer on 2008-09-17
Are you getting any errors returned to /var/adm/messages or to root's mailbox?  (Assuming you are running this as root).

I have seen cron problems before where environment variables are not available as when run from a shell, but I don't think that is your particular problem.

---

### Post by aehirst on 2008-09-17
Thanks for the fast reply.
/var/adm does not exsist and im not sure how to check root mailbox.
It is root where I have added to cron job.

---

### Post by isomer on 2008-09-17
Sorry, had my Unix head on instead of my Linux head :)

Try /var/log/messages.

---

### Post by aehirst on 2008-09-17
Ok found it :)

It only seems to have some sort of restart logged, nothing else.

---

### Post by justleen on 2008-09-17
syslog is where cron logs..

Try not padding the cron times? (just a hunce, i never use times like that)

you could also try to create your own log from cron

```

0 6 * * * sh -x /root/calbackup  2>&1 /tmp/backuplog

```

---

### Post by aehirst on 2008-09-17
I have added the log request to the cron but nothing is being created.
This is what syslog displays:

```
Sep 17 14:01:01 earth /usr/sbin/cron[4154]: (root) RELOAD (crontabs/root)
Sep 17 14:02:01 earth /USR/SBIN/CRON[6668]: (root) CMD (/root/calbackup.sh)
Sep 17 14:02:27 earth crontab[6672]: (root) BEGIN EDIT (root)
Sep 17 14:02:47 earth crontab[6672]: (root) REPLACE (root)
Sep 17 14:02:47 earth crontab[6672]: (root) END EDIT (root)
Sep 17 14:03:01 earth /usr/sbin/cron[4154]: (root) RELOAD (crontabs/root)
Sep 17 14:04:01 earth /USR/SBIN/CRON[6677]: (root) CMD (/root/calbackup)
Sep 17 14:17:01 earth /USR/SBIN/CRON[6684]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 17 14:17:52 earth crontab[6686]: (root) BEGIN EDIT (root)
Sep 17 14:19:45 earth crontab[6686]: (root) END EDIT (root)
Sep 17 14:24:47 earth crontab[6697]: (root) BEGIN EDIT (root)
Sep 17 14:33:13 earth crontab[6697]: (root) END EDIT (root)
Sep 17 15:02:12 earth -- MARK --
Sep 17 15:12:32 earth crontab[6704]: (root) BEGIN EDIT (root)
Sep 17 15:13:28 earth crontab[6704]: (root) REPLACE (root)
Sep 17 15:13:28 earth crontab[6704]: (root) END EDIT (root)
Sep 17 15:14:01 earth /usr/sbin/cron[4154]: (root) RELOAD (crontabs/root)
Sep 17 15:15:01 earth /USR/SBIN/CRON[6713]: (root) CMD (sh -x /root/calbackup  2>&1 /tmp/backuplog)
Sep 17 15:15:42 earth crontab[6722]: (root) BEGIN EDIT (root)
Sep 17 15:17:01 earth /USR/SBIN/CRON[6726]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 17 15:18:41 earth crontab[6722]: (root) REPLACE (root)
Sep 17 15:18:41 earth crontab[6722]: (root) END EDIT (root)
Sep 17 15:19:00 earth crontab[6728]: (root) BEGIN EDIT (root)
Sep 17 15:19:01 earth /usr/sbin/cron[4154]: (root) RELOAD (crontabs/root)
Sep 17 15:19:05 earth crontab[6728]: (root) END EDIT (root)
Sep 17 15:20:01 earth /USR/SBIN/CRON[6737]: (root) CMD (sh -x /root/calbackup  2>&1 /tmp/backuplog)
Sep 17 15:21:09 earth crontab[6752]: (root) BEGIN EDIT (root)
Sep 17 15:21:16 earth crontab[6752]: (root) REPLACE (root)
Sep 17 15:21:16 earth crontab[6752]: (root) END EDIT (root)
Sep 17 15:22:01 earth /usr/sbin/cron[4154]: (root) RELOAD (crontabs/root)
Sep 17 15:22:01 earth /USR/SBIN/CRON[6757]: (root) CMD (sh -x /root/calbackup  2>&1 /tmp/backuplog)

```


Thanks again

---

### Post by justleen on 2008-09-17
abd what does /tmp/backuplog contain?

---

### Post by aehirst on 2008-09-17
nothing, no file was created

---

### Post by bingoUV on 2008-09-17
Change justleen's command slightly thus
```

0 6 * * * sh -x /root/calbackup  2>&1 >> /tmp/backuplog

```

The way it was, /tmp/backuplog went as an additional argument to the script calbackup instead of redirecting the output to /tmp/backuplog.

---

### Post by aehirst on 2008-09-17
Ok now im confused, now I have the log working every tar.gz I make is perfect.

Was there an issue in the way I had my cron command?

---

