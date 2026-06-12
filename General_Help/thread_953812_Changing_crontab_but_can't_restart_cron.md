---
title: "Changing crontab but can't restart cron"
date: 2008-10-20
forum: General Help
---

### Post by eludlow on 2008-10-20
I am using a system that I am not a super user of.  Is there a way to reload cron so that any changes of my crontab will take effect?

On the systems I can admin, I simply run

```
sudo /etc/init.d/cron restart
```

but how am I supposed to do this on the system I can't sudo?  Is it possible?

This is driving me mad!

Thanks,
Ed Ludlow

---

### Post by master_d on 2008-10-20
I believe you can make changes to your user's crontab by using the crontab binary and cron will automatically pick up these changes after you save the file.  I could be wrong, but I think editing the crontab manually using vi or nano would require you to reload crond by the method you described above or by killing it and rerunning it.  

try crontab -e and see if that works for ya.

---

### Post by eludlow on 2008-10-20
Mmm not working for me :(

I don't think it's a problem with my cron job...running the command from shell works fine!

Ed

---

### Post by master_d on 2008-10-20
can you post the line that you're trying to put into the crontab?

---

### Post by eludlow on 2008-10-20
```
0 0 * * * php /home/ed/cron_scripts/doMysqlDump.php
```

Running "php /home/ed/cron_scripts/doMysqlDump.php" from the command line works fine.

Ed

---

