---
title: "Acer laptop randomly goes into standby."
date: 2012-11-23
forum: Hardware
---

### Post by immerohnegott on 2012-11-23
It hasn't happened often, but very occasionally my Aspire 5560 will just up and decide to go into sleep mode. I haven't found anything interesting in syslog, there's a few lines about anacron a couple of seconds before "sleep requested"...

```
Nov 23 15:59:21 the-sorcerers-bone anacron[4966]: Anacron 2.3 started on 2012-11
-23
Nov 23 15:59:21 the-sorcerers-bone anacron[4966]: Will run job `cron.daily' in 5
 min.
Nov 23 15:59:21 the-sorcerers-bone anacron[4966]: Jobs will be executed sequenti
ally
Nov 23 15:59:23 the-sorcerers-bone NetworkManager[886]: <info> sleep requested (
sleeping: no  enabled: yes)
```

nothing in syslog for 45 minutes or so before that.

Any ideas? The only other info I've got on this is that sleep is a bit dodgy on this machine anyway - closing the lid will put the contraption to sleep, but opening the lid doesn't wake it.

Running Xubuntu Precise.

---

### Post by ahallubuntu on 2012-11-23
There's nothing unusual about your laptop not waking up when you open the lid.  Acers are designed that way; you have to hit a key to wake it.  My Acer netbook is the same way. On the other hand, my Dell laptop wakes up automatically when I open the lid.

Ubuntu defaults to putting your computer to sleep after certain periods of inactivity - more quickly on battery vs. on AC power.  You can change the power settings and not have it ever go to sleep if you prefer. Have you looked at power settings (under system settings)?  Or are you saying you'll be in the middle of typing something and it will suddenly suspend on its own?

---

### Post by immerohnegott on 2012-11-24
Right-o. This last time, I was in Chromium browsing through the Steam autumn sale when XScreensaver's lock dialog popped up and the machine went to sleep. 

I've got it set to never go to sleep under battery, unless the power level is like 6% or something really low. My battery was at around 45%.

It came right out of sleep and has been on since. This has only happened a few times, but I find it entirely bizarre.

---

