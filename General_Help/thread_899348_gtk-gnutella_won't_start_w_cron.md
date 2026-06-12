---
title: "gtk-gnutella won't start w/ cron"
date: 2008-08-24
forum: General Help
---

### Post by sr_guy on 2008-08-24
I've tried both using gnome-schedule and kcron. I'm trying to start gtk-gnutella. I setup to run on all days starting at midnight, but the task never starts. I even used its full directory /usr/bin/gtk-gnutella. That hasn't worked. Once I've accomplished getting a cron task to start it I'll create one to kill it at around 6am. Any ideas?

---

### Post by akudewan on 2008-08-24
Can you post the output of 
```

crontab -l

```

---

### Post by sr_guy on 2008-08-24
# gnome-schedule
55 8 * * *      /usr/bin/gtk-gnutella
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
kg@kgbuntu:~$

---

### Post by akudewan on 2008-08-24
This looks like its scheduled to start gtk-gnutella at 8:55AM. To start it at midnight, you need to do this:

Run "crontab -e" in a terminal and change the "55 8" to "0 0". It will look like this:
```

0 0 * * *      /usr/bin/gtk-gnutella

```
(Press Ctrl+X to exit from here, Y to save)

In order to kill the process at 6:00am, you'll have to run the same "crontab -e" and add a second line:
```

0 0 * * *      /usr/bin/gtk-gnutella
0 6 * * * killall -15 gtk-gnutella

```

Hope this helps :) Looks like you have a night-unlimited internet connection ?

---

