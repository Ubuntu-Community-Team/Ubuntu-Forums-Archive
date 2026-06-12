---
title: "Feisty on a Thinkpad R60e: power issues"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Banana Argument on 2007-04-21
Hello,

I've recently installed feisty on my IBM/Lenovo Thinkpad R60e (0657-4MU*) in a bid to break away from windows. For the most part it worked well; my hardware was all detected. I only have one substantial problem, and it has to do with power management.

Briefly, it doesn't work as well as it does in windows. I lose ~90 minutes of battery life (5h->3.5h), and, I assume as a result of the additional power usage, the heat and more importantly fan noise level is enormously increased. The fan runs at its "irritating whine" level virtually all the time.

I am new to linux on laptops so I don't know how to troubleshoot this. cat /proc/cpuinfo shows the CPU as running at 1000 Mhz, which is about the same as it is in windows during times of low load (980); aside from that, you will have to help me with commands I should issue to obtain additional information.

This seems like an integrator issue, for which a conclusive solution will probably be difficult to obtain. I'll try this anyway though: the romantic image of a day when I can remove windows from my life forever is one for which I have great passion.

*[http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=0657-4mu&quickPathEntry.x=0&quickPathEntry.y=0](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=0657-4mu&quickPathEntry.x=0&quickPathEntry.y=0)

---

### Post by ntetreau on 2007-04-23
You need to enable laptop-mode to get better battery life, take a look at my howto on the subject:

[http://ubuntuforums.org/showthread.php?t=419772](http://ubuntuforums.org/showthread.php?t=419772)

Nic

---

