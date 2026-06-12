---
title: "ASUS S400CA Suspend Issue"
date: 2013-07-01
forum: Hardware
---

### Post by Omizuk on 2013-07-01
Hello,

I have recently got an ASUS S400CA and installed UBUNTU and have found out that there is this problem with the wireless driver. Since I am quite new to Linux it is confusing to follow the thread, but could you clarify me what did you do to solve the problem?

---

### Post by Toz on 2013-07-01
*Moving post to its own thread because it is a different system. Initially posted in [http://ubuntuforums.org/showthread.php?t=2138930]("http://ubuntuforums.org/showthread.php?t=2138930").*

Can you provide some more information?

1. What version of Ubuntu are you using?
.
2. Can we see your suspend log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated
.
3. Open a terminal window, type in the following command, and post back the results:
```
cat /var/log/syslog | grep PM:
```

---

