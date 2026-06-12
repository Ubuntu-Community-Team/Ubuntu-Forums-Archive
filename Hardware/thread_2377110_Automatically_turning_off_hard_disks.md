---
title: "Automatically turning off hard disks"
date: 2017-11-09
forum: Hardware
---

### Post by zanox on 2017-11-09
Hi! Is there the possibility to turn off hard disks after boot? (except for the ssd where system run obviously). And also turning off them at every unmount operation?

---

### Post by efflandt on 2017-11-09
Since modern hard drives no longer support hdparm settings to do that automatically, I wrote a script that I call "hd-standby" which I put in /etc/cron.hourly/. You give it a list of drives and if any of those drives are "not mounted" and "not already in standby", it puts them into standby (and logs that) which stops them from spinning, but they can still wake up if you mount them by clicking on them in your file manager or whatever. It does nothing for any drives that are mounted.

See: [https://ubuntuforums.org/showthread.php?t=2350621](https://ubuntuforums.org/showthread.php?t=2350621)

Note that you need to use **sudo** prefix if creating/editing the the script in /etc/cron.hourly or copying it to there, so it does that as root. And it needs execute permission (sudo chmod +x /etc/cron.hourly/hd-standby). Or if you want to test the script you can do it as **sudo /etc/cron.hourly/hd-standby** or if you cd to that directory as **sudo ./hd-standby**

---

### Post by zanox on 2017-11-09
Very thorough answer! thank you very much!

---

