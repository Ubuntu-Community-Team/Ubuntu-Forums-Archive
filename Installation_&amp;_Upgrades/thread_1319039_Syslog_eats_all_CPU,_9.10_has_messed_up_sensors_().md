---
title: "Syslog eats all CPU, 9.10 has messed up sensors (?)"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by dosia on 2009-11-08
After upgrade to 9.10 I noticed that PC works very slow. top showed me, that all free CPU is eaten by processes dd and rsyslogd. Then, using help from #ubuntu, I found gigantic var/log/syslog file, which contained 1,2GB of line informing of processor overheating (it's true, I have a little bit broken power supply). (Killing processes and deleting files didn't help or helps temporarily). Then someone adviced me to install lm-sensors. After rebooting it looked fine, but HDD space started to dramaticly shrink. It ate 1,5GB in half hour. I had to clear old packages to even write it there. When I wrote this post, 200MB disapeared. dd and rsyslogd are using all CPU again, and syslog is still growing larger. On IRC channel I saw another one with this problem, so it's not just me. What can I do?

---

### Post by mitsoulis on 2009-11-09
> **dosia said:**
>  dd and rsyslogd are using all CPU again, and syslog is still growing larger. 

I have exactly the same problem ...

---

### Post by LucidStrike on 2009-11-11
Had the same problem. Didn't notice until I was informed that I had about 200MB left on the partition. It read 0KB within minutes. Searched around for large files and emptied the trash, but none of it added up to what was missing. I had read about out of control var/log files, so I checked there and deleted all of the contents, after verifying that it was taking up the vast majority of the space. I think that initial freed about 40GB, but over 100GB had been freed after a reboot. Yeah, a couple of applications complained but nothing concerning.

Now, rsyslogd and dd eat 38% and up from boot. My CPU is workin' really hard for nothing.

---

### Post by userid on 2009-11-28
This is super annoying, use the fix in [post 57 here]("https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/453444") as a temporary improvement.

---

