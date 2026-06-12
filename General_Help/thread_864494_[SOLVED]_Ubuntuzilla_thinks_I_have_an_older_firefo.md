---
title: "[SOLVED] Ubuntuzilla thinks I have an older firefox version"
date: 2008-07-19
forum: General Help
---

### Post by drexell0680 on 2008-07-19
I keep getting a notification box telling me a firefox update is available, that I'm running FF-3.0 and FF-3.0.1 is available.  I updated earlier from repositories, and when I check the version in firefox it says I'm using 3.0.1.  How do I stop the ubuntuzilla notification?

---

### Post by DagMan on 2008-07-19
try maybe just reinstalling it.  you shouldn't lose your settings.
sudo apt-get install --reinstall firefox

---

### Post by nanotube on 2008-07-20
so, it looks like you are running FF from the repos, rather than using the mozilla build installed by ubuntuzilla.
so... just uninstall ubuntuzilla, and edit your crontab and delete the update checker jobs ```
crontab -e
```

---

### Post by drexell0680 on 2008-07-20
Got it, thanks for the help!

---

