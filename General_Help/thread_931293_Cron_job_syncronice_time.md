---
title: "Cron job syncronice time"
date: 2008-09-27
forum: General Help
---

### Post by frodemt on 2008-09-27
Hi.

I have this VMware machine that I rund Ubuntu on. When I use suspend - restore on VMware, the clock gets messed up.

I figured that setting up a cron job syncronicing the time against a ntp server would solve this problem. 

But I dont know where to start as I am new to both scripting and cron jobs. Can someone help me get started?

Thanks.

---

### Post by ajmorris on 2008-09-27
> **frodemt said:**
> Hi.

I have this VMware machine that I rund Ubuntu on. When I use suspend - restore on VMware, the clock gets messed up.

I figured that setting up a cron job syncronicing the time against a ntp server would solve this problem. 

But I dont know where to start as I am new to both scripting and cron jobs. Can someone help me get started?

Thanks.

hi there,
cron jobs are used to set a scheduled task on a regular basis, however, they are set by a time interval, i.e daily, or every 2 hours. I think for your task, you would be better off with a simple bash script, that gets issued on restore... 
something like:
I am however, hopeless at coding... but you would need something that checks for VMWare resume... im assuming that the guest OS can pick this up. I'll tag this for help with the unanswered posts team, and hopefully someone more experienced with this topic will be able to help you :)

AJ

---

### Post by mali2297 on 2008-09-27
I have this script in my cron daily (note that it is essentially a one-line script):
```

#!/bin/sh
#
# /etc/cron/daily/rdate: synchronize system clock
#

/usr/bin/rdate -s ntp.lth.se

# End of file

```

However, if the clock gets messed up every time you resume from suspend, then perhaps you should put the script in /etc/acpi/resume.d/ instead.

---

### Post by forger on 2008-09-27
You don't have rdate installed by default, however use ntpdate instead in the script above:
/usr/bin/ntpdate time.nist.gov

also use gnome-schedule:
```

sudo apt-get install gnome-schedule
gksu gnome-schedule

```
(you need root hence "gksu", since you can't change the time as a simple user)

---

### Post by ajmorris on 2008-09-27
> However, if the clock gets messed up every time you resume from suspend, then perhaps you should put the script in /etc/acpi/resume.d/ instead.I believe he means the VMWare resume, not resume from a memory suspend...

---

