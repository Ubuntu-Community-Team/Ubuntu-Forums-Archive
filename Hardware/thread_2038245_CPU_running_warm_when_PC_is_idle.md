---
title: "CPU running warm when PC is idle"
date: 2012-08-06
forum: Hardware
---

### Post by KaizerLinux on 2012-08-06
Ubuntu 12.04, AMD Phenom II X4 955 Processor × 4.

I've begun noticing over the past few days that when I leave my PC for a while, the CPU fan is running full blast when I come back. I installed Psensor to check what was going on.

When I'm using the PC for light work such as browsing, the CPU runs at around 37-40C. But when I leave it for a while and come back (around an hour or so), I'm getting pretty consistent temperatures of around 46C. I have no programs running on it, and the screen is dark. Once I start using it again, the temp goes back down to between 37-40C

Now, I know 46C isn't that high, but I just find it strange that it runs cooler when I'm using it, even for light work, than when it's sitting idle.

---

### Post by errrn on 2012-08-06
the same thing happens to me.
I even posted the same thing a few weeks ago, but I didn't get any responses.

---

### Post by KaizerLinux on 2012-08-06
> **errrn said:**
> the same thing happens to me.
I even posted the same thing a few weeks ago, but I didn't get any responses.

Did you report it in launchpad? If not, I think I'll pop by and submit a bug report. If you did, link me.

EDIT: Reported. Head over and add your info :) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1033487](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1033487)

---

### Post by KaizerLinux on 2012-08-07
Bump.

It seems that the CPU is running at around 30-40% capacity when the monitor is off, so no wonder it heats up. No idea what's causing it though. Could it be Compiz? And is there a way to log process CPU usage?

---

### Post by QsoftStudios on 2012-08-13
Hows your memory usage as well, this might be a mem leak.

---

