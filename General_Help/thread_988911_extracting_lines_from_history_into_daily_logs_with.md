---
title: "extracting lines from history into daily logs with date as filename"
date: 2008-11-21
forum: General Help
---

### Post by u-blunt-2 on 2008-11-21
I have set my history to timestamp every entry. What I want is to automatically extract all commands in history output stamped with the current date. 
I am trying to get a cron job to execute this every day at 23:59.

```
history | grep `date '+%a_%d-%m-%y'` | cut -b 8- > /home/myusername/.history/`date '+%Y'`/`date '+%b'`/`date '+%d-%m-%y'`
```

This runs fine in terminal, but fails to run in cron. Any ideas ?

---

