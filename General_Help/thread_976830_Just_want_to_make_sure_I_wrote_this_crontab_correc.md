---
title: "Just want to make sure I wrote this crontab correctly"
date: 2008-11-09
forum: General Help
---

### Post by josephellengar on 2008-11-09
It's the root crontab:
.refreshscans and .fullscan are two shell scripts.  I want the first one to execute every 6 months and I want the second one to execute every three months.  Did I do this correctly?

* * * 1,7 * '/home/ross/.refreshscans'
* * * 1,4,7,10 * '/home/ross/.fullscan'

---

### Post by chrisamiller on 2008-11-09
Upon further reflection - mike below is correct.

---

### Post by mike2357 on 2008-11-09
man 5 crontab is a great source of information about the format of cronfiles.

```
* * * 1,7 * '/home/ross/.refreshscans'
```
I believe the above command means that in January and July, run .refreshcans every minute of every hour of every day of every day of the week.  If you only want the command to run once during the month, you probably need to set a specific time and date to run.  For instance, if the command is to run at 6:00 a.m. on the first day of the month, you would make this your cron entry:
```
00 06 01 1,7 * /home/ross/.refreshcans
```

The same concept applies to your second command; I won't repeat the details as I'm sure you get the idea.

I've never put my cron commands in single quotes.  I don't know if it makes a difference or not.

Lastly, a tip:  make sure your cron output has somewhere to go so if something goes awry, you can see the results.  Here's an example:
```

00 06 01 1,7 * /home/ross/.refreshcans >| OUT_ROSS_CRON 2>&1
```

As your script runs, output will be written to OUT_ROSS_CRON in root's home directory.

---

### Post by soro2005 on 2008-11-09
You may want to use anacron instead, to prevent the possibility that your computer's switched off right the minute it's scheduled to run the cron job.

---

### Post by josephellengar on 2008-11-09
Man anacron sounds exactly like what I'm looking for.  How do I run an anacron job that lets me run a command as root?  One command I want to do is a clamscan and that can only be done as root.

---

### Post by soro2005 on 2008-11-11
It seems to me that it's running everything as root anyway, unless you specify something else. You want half and full year, so you can't use the cron.daily and cron.weekly directories. You may have to edit /etc/anacrontab directly.

---

