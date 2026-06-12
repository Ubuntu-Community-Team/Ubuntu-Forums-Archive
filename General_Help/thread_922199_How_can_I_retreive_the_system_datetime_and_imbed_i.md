---
title: "How can I retreive the system date/time and imbed in a file name?"
date: 2008-09-17
forum: General Help
---

### Post by macey on 2008-09-17
Hi, I am running jobs via cron, the jobs create files but I want the files 'time/date stamped'
How can I achieve his?
Help much appreciated.

---

### Post by Kilnr on 2008-09-17
With this:
```
`date +%Y-%m-%d`
```
Be careful, those are backticks, not quotes.

[edit] Let me elaborate a bit... If you create the files by redirecting something to them, you'd use the above string like this:
```
echo "lots of stuff" > yourfile-`date +%Y-%m-%d`.txt
```

Oh yeah, you asked for time as well, check the manpage for date to see what else you can use.

---

### Post by macey on 2008-09-17
Thanks a lot!

---

