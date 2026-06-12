---
title: "Many applications fail to start after distribution upgrade"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by CharonM72 on 2009-01-04
I recently left my computer for a while, and when I got back upgraded to Ubuntu 8.10 and installed some 2500 software updates. After this, many applications such as Konsole, VLC, and others fail to start entirely, whether run from their shortcuts or from command-line. The apps are installed; nothing happens when I run the apps. I don't know whether it's the updates or the distribution upgrade, but something did it.

EDIT: I found these programs already running at startup in the System Monitor, and also eating all my processor. Which would explain why they aren't starting. Help?

---

### Post by lemming465 on 2009-01-06
The first thing I'd try is (from the command line)```

sudo -i
apt-get update
apt-get upgrade --fix-broken
reboot
```

---

### Post by Sef on 2009-01-06
> I recently left my computer for a while, and when I got back upgraded to Ubuntu 8.10....

What Ubuntu version did you upgrade from?

---

