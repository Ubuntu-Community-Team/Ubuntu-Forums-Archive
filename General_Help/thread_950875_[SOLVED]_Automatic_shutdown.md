---
title: "[SOLVED] Automatic shutdown"
date: 2008-10-17
forum: General Help
---

### Post by medic2000 on 2008-10-17
I want my Ubuntu to shutdown at a specific time. And i want to do it in a very simple way. Which program you suggest?

---

### Post by Elfy on 2008-10-17
You could do it with cron or there is a program - I've never done/used either but this thread seems to give info on cron and the program which is in the repository - ghutdown

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gshutdown](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gshutdown)

[http://gshutdown.tuxfamily.org/en/index.php](http://gshutdown.tuxfamily.org/en/index.php)

---

### Post by sparky-steve on 2008-10-17
The simplest way would be to create a simple bash script, something like:

```
#!/bin/bash
# this will shutdown in 5 minutes
/sbin/shutdown -h +5
```

Save that in /root - call it something like byebye.sh

Then edit crontab for root and put something like:

```
55 22 * * * /root/byebye.sh
```

That will start the script at 22.55 every night, shutting down in five minutes time, ie 2300hrs

You dont have to have the 5 minutes, I'd just use that so I could cancel if I wanted.

There are bound to be even easier ways; Possibly that dont require to run as root.

---

