---
title: "Frequency changing &amp; Can't find powernow-k8"
date: 2009-07-27
forum: Hardware
---

### Post by mikesena on 2009-07-27
Hi,

I'm trying to get CPU frequency / scaling working on my laptop.

I've installed cpufreqd and the utils etc.

I added the Frequency applet onto my bar at the top, and I seem to be able to change govenors, but I can't specify the frequency.  I also don't think the govenors are working.

If I type cpufreq-set -f 800, it looks like its successful, but it doesn't change either of the cores.

I think I need to have a module, powernow-k8, but when I try to type: 'sudo modprobe powernow-k8', it says that it can't find it.  It also says that it can't find any modules beginning with cpufreq.

What's gone wrong? :P  I really need to get scaling working.

Michael

---

