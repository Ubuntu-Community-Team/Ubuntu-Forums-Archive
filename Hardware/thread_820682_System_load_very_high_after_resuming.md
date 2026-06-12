---
title: "System load very high after resuming"
date: 2008-06-06
forum: Hardware
---

### Post by dschouten on 2008-06-06
After resuming from suspend, the system load as reported by top and gnome-system-monitor is higher than possible. I am running an HP DV2000 series laptop with a T2450 Duo 2.0 GHz processor, and the load is reported by top as

top - 10:35:23 up 12:24,  2 users,  load average: 12.37, 3.46, 1.92

This is obviously wrong, and it decreases linearly within about 1 minute to a reasonable level for an idle system (about 0.5).

Any ideas? 

Note that it might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/199088](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/199088), which I have also been experiencing from time to time.

---

### Post by sdennie on 2008-06-06
I think this is fairly normal.  It may not be possible to properly compute load after a resume so, as long as your CPU usage is what you'd expect it to be, it's not anything to worry about.

---

