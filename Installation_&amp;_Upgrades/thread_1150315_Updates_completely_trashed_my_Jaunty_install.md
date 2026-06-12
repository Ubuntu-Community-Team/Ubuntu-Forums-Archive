---
title: "Updates completely trashed my Jaunty install"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2009-05-06
I usually take the advice to install updates as they come available, but tonight I was running the update-manager while fiddling with Amarok and my system completely froze. I had no choice but to power cycle the machine and then when I went to log back in, the system completely froze again the instant I hit the "enter" button after entering my password. I rebooted again to the same behavior. I have the keyboard and mouse working right up until I hit enter after entering my password. Before that, I can switch to a console window, but I don't know what to do since I have no internet at this point (I have discovered that Ubuntu does not configure wireless connections unless you start X, which blows my mind, but there it is). I want to know what I can do. Honestly I don't know what to do except to reinstall a fresh system! Could the updates have caused it?

---

### Post by BetterSense on 2009-05-06
Bump, nobody else having this problem with Jaunty? Anyone know what I can do to fix it besides reinstall?

---

### Post by BetterSense on 2009-05-07
if anyone else has this problem I found this solution on another website.

```
sudo update-rc.d -f dbus remove
 sudo update-rc.d dbus defaults
 sudo update-rc.d -f hal remove
 sudo update-rc.d hal defaults
```

---

