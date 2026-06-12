---
title: "Process Priorities"
date: 2005-11-04
forum: General Help
---

### Post by kaptainlange on 2005-11-04
In an attempt to keep KDE from getting all sluggish whenever I'm doing something CPU intensive, I made an attempt at setting the process priority (-10) for my X server slightly higher than the default priority (0).  While I certainly appears to have worked, and kept this setting after I rebooted, I want to confirm if it is in fact running at that new priority level.  Could any of you give me some help as to how to check the priorities of current processes.

Another quick question to, is there any drawback other than taking cycles from other processes.  eg. Frequent crashing and so on.  I know gcc will take a bit longer to compile something, but I'm in no rush.

---

### Post by kevin908 on 2005-11-04
Try this:
```
ps -eo "%p %c %n"
```

Look (or grep) for Xorg. The far right column is the current nice value of the process.

-Kevin

---

### Post by Harleen on 2005-11-04
You can look for the process priority in the system monitor provided by KDE. It can be started with "ksysguard" or by pressing  <CTRL>+<ESC>.

And beside slowing down other processes there shouldn't be any influences of the nice level to your applications.

---

