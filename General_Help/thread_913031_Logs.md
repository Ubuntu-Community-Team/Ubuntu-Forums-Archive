---
title: "Logs?"
date: 2008-09-07
forum: General Help
---

### Post by x-g on 2008-09-07
I have been using ubuntu for a few weeks now and every once and a while I get a hang.  No mouse, nothing.  I've been poking around and I found gnome-system-log.  This seems to have a lot of information in it, but I don't know where (which log file) I should be looking in.  I'm hoping to see some sort of information as to the cause of the crashes.

I'm not looking for someone to diagnose my crashes, I just want to know what the different logs are, and where I should look to find info on crashes.

Thanks!

---

### Post by Yannick Le Saint kyncani on 2008-09-07
> **x-g said:**
> I just want to know what the different logs are, and where I should look to find info on crashes.

Hi x-g, logs are kept in /var/log/, you might want to check /var/log/messages first.

Good luck :)

---

### Post by john.nicholls on 2008-09-08
I keep a terminal window open at /var/log and use the command
```
tail -f syslog
```. This keeps the file open so you can continually monitor what is going on.

---

