---
title: "Troubleshooting unscheduled shutdowns"
date: 2009-04-24
forum: Hardware
---

### Post by lottotx on 2009-04-24
I have an issue with my machine (running Ubuntu 8.04.2) shutting down unexpectedly.  I am never around when the machine shuts down and I have been unable to find anything suspicious in the logs.  

I suspect my problem may be either a failing UPS or a thermal shutdown.

I have looked in /var/log/dmesg, /var/log/messages, and /var/log/syslog and have found nothing suspicious.  

The system power supply was recently replaced but I've run my own load and line regulation tests on it and it works fine.

Any other places to look or other ideas are very much appreciated.

Thanks,
Lotto

---

### Post by Bakon Jarser on 2009-04-24
Unhook it from the UPS and if you stop getting shutdowns then you've found the problem.  Install temperature monitoring software to see if anything is overheating.  I think the program for that is lm-sensors but I'm not really sure.

---

