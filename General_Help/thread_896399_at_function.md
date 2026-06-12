---
title: "at function"
date: 2008-08-21
forum: General Help
---

### Post by Maelgwyn on 2008-08-21
Hi guys,

I'm reading up on the at function as part of cron, but can't get my head around it! I'm hoping somebody will be able to help me out.

My ISP gives me free data between 01:00-07:00 daily, and I'd like to setup cron/at to open Transmission between these times. Is it possible to run something like ```
at 1 AM tomorrow
``` to run every day?

---

### Post by kpkeerthi on 2008-08-21
at will only let you run a command/program once. To schedule repeating job, use cron. You can also cron graphical applications. You will find some help [here]("https://help.ubuntu.com/community/CronHowto"). Look under **Tips** section for scheduling GUIs.

---

### Post by DagMan on 2008-08-21
when you edit crontab
crontab -e
you'lle see something like this
# m h  dom mon dow   command

# is a comment so the system doesn't look at it as a command
m is the minute
h is the hour
dom is the day of month by hour
mon is the month
dow is the day of week
command is the command to run and you need to specify the full path to the command.  

If you run a script, only call other proceses from that script, don't have a process that is a child process of a child process of the script.  Also, don't have any output to the terminal be it stdout or stderror so put >/dev/null 2>&1 at the end of each command in the cron script, otherwise it will error out.

Looking again 
# m h  dom mon dow   command

you can use wildcards so for example
* 3 * * * /usr/local/bin/script
runs the script /usr/local/bin/script at 3 am every day.

* 1 * * * /usr/local/bin/script runs it at 1 am every day.
remember that the script can't produce output if it were to run at a terminal, so you redirect it to a log file or to /dev/null
a better solution to what I said before would be >/dev/null 2>/path/to/error/log-file for example.

another example
1 2 23 10 * /usr/local/bin/script 
2:01 am Oct 23 

I don't know how to use the at command but perhaps this helps.

Always make sure you hit enter after the cron entry.  I always put a comment after one to make it visible.
1 2 3 4 5 5 /path/yto/something
#

---

### Post by qstraza on 2008-08-21
what command do you want to execute every day at 1am ?

---

### Post by Maelgwyn on 2008-08-21
> **qstraza said:**
> what command do you want to execute every day at 1am ?

I want Transmission to run, or another BitTorrent application if that's easier :P

---

### Post by qstraza on 2008-08-21
thats not too hard, just write a bash script which will run azureus or what ever you like and than add a script to a cron

take a look at this site:
```
http://www.htmlbasix.com/crontab.shtml
```

If you dont know how to write a bash script:
```
#!/bin/bash
azureus
```

You should set azureus so it starts downloading the torrent at startup...

Run all this as normal user.
You can use any other torrent client ofcourse, or wget, if u like to DL from non-torrent.

Hope this helps you

Oh and about stopping, you could write a script which kills azureus:
```
#!/bin/bash
killall azureus
```

Now learn cron ;)

---

