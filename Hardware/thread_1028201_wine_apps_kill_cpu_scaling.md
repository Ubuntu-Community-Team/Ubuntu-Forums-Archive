---
title: "wine apps kill cpu scaling"
date: 2009-01-02
forum: Hardware
---

### Post by aaron552 on 2009-01-02
I've been experiencing a strange bug (possibly) with wine and cpu scaling on my laptop. Whenever I start a wine app, usually WoW, My CPU sometimes becomes locked to the minimum frequency for an unspecified period, usually till I reboot. Restarting powernowd does not help neither does forcing the max speed (or performance governor) with cpufreq-selector. This is becoming more than annoying and any help would be appreciated.

---

### Post by aaron552 on 2009-01-03
Bump.
No one knows, huh?

---

### Post by Yorper on 2009-01-03
No much of a helpful reply, but maybe try checking over at wine. Check to see if their bugtracker has something like this reported and if not maybe even file it yourself as if this is a wine issue i'm sure they will want to know about it and get it fixed ASAP as i can imagine your frustration over this issue.

On the other hand it could be related to ubuntu and not wine.... Sorry i can't be of more help to you.

---

### Post by aaron552 on 2009-01-03
I'm guessing it may be bug in powernowd, since cpufreq-info returns:
```
CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 800 MHz
  available cpufreq governors: ondemand, conservative, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
```

---

### Post by juamez. on 2009-03-28
This is the same problem as I'm having!

[http://ubuntuforums.org/showthread.php?t=1108946](http://ubuntuforums.org/showthread.php?t=1108946)

---

