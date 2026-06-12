---
title: "Ubuntu 10.04 does not shutdown"
date: 2010-08-06
forum: Hardware
---

### Post by syednizamudeen on 2010-08-06
My Laptop is Acer Aspire 5542G.I'm running Ubuntu 10.04 x64 and when I try to shutdown from panel or with shutdown command,it does not shutdown but RESTARTS.Windows 7 runs on parallel,It gets shutdown without an issue.I ran Ubuntu under windows for a month.i.e via Wubi My Computer did shutdown,but it doesnt when I installed Ubuntu separately.

---

### Post by garvinrick4 on 2010-08-06
Will it shutdown using:

```
sudo shutdown -h now
```

---

### Post by syednizamudeen on 2010-08-08
I tried.But didn help..

---

### Post by garvinrick4 on 2010-08-09
Have you tried a new or different kernel to boot from?
I am sure you have Googled problem and gone to launchpad.net to
look for salution? Looks like one of those hunt and peck problems, keep
on it until you get it solved. Here is one thread with some fixes might work.
[http://ubuntuforums.org/showthread.php?t=1466589](http://ubuntuforums.org/showthread.php?t=1466589)

---

### Post by garvinrick4 on 2010-08-10
What does it say in /etc/default/halt
```

gksudo gedit /etc/default/halt
```Mine:

# Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
HALT=poweroff

---

