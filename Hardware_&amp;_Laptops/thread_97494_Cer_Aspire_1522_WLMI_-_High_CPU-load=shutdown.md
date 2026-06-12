---
title: "Cer Aspire 1522 WLMI - High CPU-load=shutdown"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by tux73 on 2005-12-01
On my Acer Aspire 1522 WLMI (AMD 64 3000+) using Breezy with a 2.6.12-10-K7-Kernel it happens all the time, that the temperature rises extremely fast when switching t0 1800MHz (max) at high CPU load.
cat /dev/urandom > /dev/null
doesn't make anything to the temperature when in powersave mode. But in Userspace/on demand/performance mode (when CPU is on 1800MHz) the system shuts down after a few minutes.
I have GKRellm showing my temperatures. Normally I have 45&#176;C on THRC and about 43&#176;C on THRS. However, no problem when using powersave mode.

Any other mode where the CPU is switching to higher speed causes the fan to run faster (=loader) and the temperature rises straight to 90&#176;C where the system shuts down.

I didn't had that in the past. I installed Hoary from an "old" CD to crosscheck, but it is the same. 

The fan is running. I cleaned it (no change).

Any idea?


STOP. Pls. close this thread. Seems to be a hardware problem. Same issue when booting in BIOS only.

---

### Post by daller on 2005-12-02
SOLVED!

I don't have authority to close the thread, but at least I can answer it (An answer indicated some degree of attention to the thread...)

I primarily answer threads that's unanswered! (So please post "SOLVED!" as a new post!)

---

