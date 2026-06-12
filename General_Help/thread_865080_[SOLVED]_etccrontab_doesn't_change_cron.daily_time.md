---
title: "[SOLVED] /etc/crontab doesn't change cron.daily time"
date: 2008-07-20
forum: General Help
---

### Post by newlinux on 2008-07-20
I have modified my /etc/crontab to run my cron.daily at 5:25AM. Below is the line.
```

25 5	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

However, it still runs at 7:37, which was the original time. I'm pretty sure in the past (and on my older ubuntu distros) changing the /etc/crontab time is how I changed cron.daily's running time. What am I doing wrong?

---

### Post by newlinux on 2008-07-21
bump

---

### Post by newlinux on 2008-07-21
I think I need to revisit my coding basics (I'm years past my coding years). It appears that this line would test for presence of anacron, and if anacron exists it does nothing... Leading me to believe anacron is controlling the time of cron.daily not cron... I guess I'll investigate anacron.

---

### Post by newlinux on 2008-07-21
from what I can tell /etc/cron.d/anacron actually controls the time of cron.daily, weekly, and monthly, with the current way my /etc/crontab is setup.

---

### Post by newlinux on 2008-07-22
for anyone who cares, changing /etc/cron.d/anacron is the way to go, based on how the /etc/crontab is setup to have anacron run if it is installed instead of running the cron.daily, weekly and monthly.

---

### Post by Levander on 2008-07-24
I think maybe crontab is on your system because of an old, deprecated package.  Maybe when you dist-upgrade'd, it was just never removed?  

I've got a new hardy install here, and it doesn't even have a /etc/crontab.

---

### Post by Levander on 2008-07-24
Never mind, I spoke too soon.  That system doesn't have any cron system loaded at all...

---

### Post by Potatoj316 on 2008-07-24
I doubt this is it but have you tried ```
25 05 * * *
```

Also how did you edit the crontab?  Did you use crontab -e?

---

### Post by newlinux on 2008-07-24
Well, I already figured out the problem (well its not really a problem, more me figuring out how cron interacts with anacron). My changes to /etc/crontab were taking effect, but it wouldn't run cron.daily because anacron exists. So I needed to change the time cron calls anacron by changing /etc/cron.d/anacron. Or I could have taken out the test for anacron, but then cron.daily would get run by both cron and anacron everyday.

You edit user crontabs with crontab -e, but /etc/crontab you edit directly.

Thanks for the help.

---

