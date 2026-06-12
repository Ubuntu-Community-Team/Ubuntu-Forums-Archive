---
title: "understanding cpu usage"
date: 2008-11-08
forum: General Help
---

### Post by alluoshi on 2008-11-08
Hello,
I would like to understand the meaning of (cpu usage is %25) when you run the command "ps" or "top". If I am using a cpu 1 GHZ, does the %25 mean that at that time, the cpu is working at 25% of its frequency? (250 MHZ)?
Please clarify what that means.
Thank you

---

### Post by soro2005 on 2008-11-08
It's not about the frequency, but about the percentage of the entire capacity that's being used. If, say, a CPU can perform so many operations a second, then 25% of so many are being used by actual processes, the rest is idle. Of course, the CPU might scale down to save energy if that's what it's configured to do. There is a frequency indicator among the gnome panel applets.

---

### Post by alluoshi on 2008-11-08
Thank you. This makes more sense.
If I have a process running for 20 minutes, what is the best method to express the cpu usage during this period (20 minutes)? As I noticed, the cpu capacity varies every second from 0% to %50. I need a way to convey the cpu usage during this period. I am thinking of counting the number of ticks of the cpu during this period. Would that work? Is there any better way?
Thank you

---

