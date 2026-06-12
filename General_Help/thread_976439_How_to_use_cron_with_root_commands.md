---
title: "How to use cron with root commands?"
date: 2008-11-09
forum: General Help
---

### Post by josephellengar on 2008-11-09
I want to set something up that does freshclam daily, and also does a nice clamscan of my home directory monthly and does a nice clamscan of the whole computer monthly, but those all require root access, correct?  Any way to do this with root without editing sudoers?

---

### Post by geirha on 2008-11-09
```
sudo crontab -e
``` and add the jobs that should be run as root, or make scripts that run the commands and put them in /etc/cron.daily and /etc/cron.monthly.

---

### Post by bodhi.zazen on 2008-11-09
The biggest problem people have with cron jobs is with the shell. cron uses a minimal shell so be sure to use the full path for cron commands ;)

---

