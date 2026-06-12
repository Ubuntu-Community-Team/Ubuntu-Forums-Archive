---
title: "Mimic a hard shutdown with software?"
date: 2011-01-04
forum: Hardware
---

### Post by Jarnk on 2011-01-04
Is there any way you can force a hard shutdown using a script?  By hard shutdown, I mean the same as if you held the power button for 5 seconds.

---

### Post by Vermind on 2011-01-04
I think you are looking for
```
sudo halt --force --poweroff
```
This really makes your machine power off immediately, and will not let any programs save their data or terminate cleanly.

There is a cleaner, safer shutdown which allows programs to terminate. This is:
```
sudo shutdown -h now
```

Then there is also an emergency reboot system request, which is the most dangerous. That one you can access by pressing the keys ctrl-alt-sysreq-b.

---

