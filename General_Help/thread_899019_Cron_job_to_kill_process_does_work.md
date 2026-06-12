---
title: "Cron job to kill process does work"
date: 2008-08-23
forum: General Help
---

### Post by penjuin on 2008-08-23
Hey all,

I have been trying to set up a program I wrote to run with cron. It runs on a continuous loop until it receives a SIGINT, after which it cleans up and closes down. I can get the script to run with cron, but the kill command seems to do nothing (no errors but no results either). My crontab is:
```
0      *       *       *       *       /usr/bin/screen -fa -S check_folder -dm /home/jeremy/code/check_folder
10      *       *       *       *       /bin/kill -SIGINT `/bin/ps -C check_folder -o pid=`

```

If I run that exact kill command manually it shuts down the program without issue. Is there some little thing I am doing wrong?

---

### Post by LateNiteTV on 2008-08-24
why are you trying to use cron with it?

---

### Post by penjuin on 2008-08-24
The program basically checks a folder for submissions and then parses them and does some other magic. I eventually need to set it up so that documents can only be submitted at a certain time, but for now I would just like to have it working.

Both commands work perfectly outside of cron so I am confused as to why it is not working.

---

### Post by penjuin on 2008-08-24
I managed to work it out in the end. My program was crashing cron :oops:

---

