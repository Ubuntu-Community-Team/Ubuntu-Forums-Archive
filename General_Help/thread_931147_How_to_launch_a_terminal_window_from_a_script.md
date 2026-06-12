---
title: "How to launch a terminal window from a script?"
date: 2008-09-27
forum: General Help
---

### Post by Excalibre on 2008-09-27
I do a nightly backup through a cron job and I'd like it to give me an update in the morning so I don't forget to glance at the logs -- but I'm not real familiar with scripting. So what would I put in a script to launch a terminal window afterwards and run a command in it?

Thanks in advance!

---

### Post by lykwydchykyn on 2008-09-27
```
xterm -e commandname
```
of course, other console apps (gnome terminal, konsole, xfterm4, etc) have their own switches too.

---

### Post by Excalibre on 2008-09-27
> **lykwydchykyn said:**
> ```
xterm -e commandname
```
of course, other console apps (gnome terminal, konsole, xfterm4, etc) have their own switches too.
Okay, thanks.

It worked when I ran it from a command line but did not work when I set it as a cron job. My guess is that since the cron job runs as root it would have started it on root's desktop, were root signed on. Is there a way to stick it on a particular user's desktop?

---

