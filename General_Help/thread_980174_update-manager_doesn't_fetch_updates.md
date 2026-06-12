---
title: "update-manager doesn't fetch updates"
date: 2008-11-12
forum: General Help
---

### Post by Dareus on 2008-11-12
As in topic title: to see if there are some packages that i could upgrade, the only way is to use apt-get.

update-manager should automatically fetch updates from time to time, but even after some hours it doesn't see nothing. :(

How could i have back the default behaviour? :confused:

---

### Post by Pro-reason on 2008-11-12
Is update-manager running but not updating, or just not running at all?

---

### Post by Dareus on 2008-11-13
There's no «update-manager» running, there's only «python /usr/bin/update-notifier-kde», but i suppose it's correct

---

### Post by Pro-reason on 2008-11-14
Ah, sorry.  I didn't realise you were using KDE.  I'm currently using GNOME, so I can't investigate.

---

### Post by todak on 2008-11-14
For KDE I believe the command would be ```
adept-notifier
```

---

