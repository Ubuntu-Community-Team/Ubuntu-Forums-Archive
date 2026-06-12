---
title: "IBM S50 (8183 KMJ) Becomes Unresponsive and Lagged"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by Jimmy Beserker on 2005-08-05
Hi all,

I have installed 5.04 on an IBM ThinkCentre S50 (8183-KJM) without any real problems. After a short amount of time, idle or not, certain elements of the machine become very unresponsive. What is strange is that things like navigating the menus etc still work fine, but the System Monitor reports 0.0% usage of the CPU, as does top.

Things like the system beep last for about 5 seconds instead of a few milliseconds. Running any commands on the command line (/etc/init.d/apmd stop etc) take quite a while to go through, and yet there is still no CPU utilisation displayed.

Logging in/restarting the machine can take 30 minutes or more to go complete.

H/T is disabled, as per the bug fix in the latest kernel.

Any ideas, anyone?

---

### Post by Jimmy Beserker on 2005-08-05
Fixed. Removed the powernowd service.

```
$> sudo /etc/init.d/powernowd stop
$> sudo rm /etc/rc*.d/S20powernowd
```

---

