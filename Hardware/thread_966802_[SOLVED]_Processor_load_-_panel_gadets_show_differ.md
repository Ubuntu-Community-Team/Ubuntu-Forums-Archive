---
title: "[SOLVED] Processor load - panel gadets show different values"
date: 2008-11-01
forum: Hardware
---

### Post by mkarnicki on 2008-11-01
Hi guys,

I've upgraded to 8.10, on my HP tx1320 (AMD64).

System monitor on my panel shows <30% processor load, whereas
CPU Freq Scaling Monitor shows (just sometimes) 100% or little less processor load at the same time. How is that possible? I'm using powernowd in LEAP mode.

Picture taken during watching youtube video, attached.

---

### Post by sdennie on 2008-11-01
You are looking at two distinct pieces of information.  One is showing how utilized your CPUs are while the other is showing what speed they are running at.  The 100% numbers just mean that your CPU is being used enough that it's beneficial for the kernel to push them up to maximum speed.  That number and the actual CPU load are actually inversely proportionate.  If, for example, the 100% number was instead 50%, the CPU load would be approximately double because it would take more time to execute instructions at 50% CPU speed.

---

### Post by mkarnicki on 2008-11-01
I see, very helpful. Thank you :)

---

