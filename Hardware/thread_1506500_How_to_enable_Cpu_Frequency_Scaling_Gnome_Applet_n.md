---
title: "How to enable Cpu Frequency Scaling? Gnome Applet not working"
date: 2010-06-10
forum: Hardware
---

### Post by asbesto on 2010-06-10
My fresh installed Ubuntu 10.04 on my HP Pavilion zd8000 says "Cpu Frequency Scaling Unsupported" while installing the CPU Frequency Scaling Applet.

I think this is very bad for a fresh installation. I also have this problem on many other computers, running 9.10 version of Ubuntu: the cpu scaling is never working by default!

Also, it show only a CPU (i have a dual core here), and the speed is half of the processor. 

cpufreq-selector says: No cpufreq support

I have powernowd, but it's seem not working!

I installed cpudyn, but it does nothing; the applet is still not working.

cpufreq-info says:

```

root@gemini:~# cpufreq-info 
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
root@gemini:~# 

```


What I have to do to have the gnome cpu speed working?!?!?!?:confused::confused:

Note: i solved by "modprobe p4_clockmod". I don't know why isn't loaded by default. :confused:

---

### Post by FactTech on 2010-06-22
I had a similar problem with a fresh install of Lucid on my laptop. After modifying /etc/modules to include p4_clockmod and rebooting, I now find that, although the GNOME CPU frequency scaling applet says it is working, it is stuck on "Performance", and it is not responsive to attempts to change it. This is quite irksome, as it was working fine in the previous Hardy installation.

Are you seeing this same behavior, or are you able to select whatever governor you like?

[FYI for anyone stumbling on this thread -- there is additional information about the precise cause of this issue in Launchpad bug 432706 at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706) ]

---

