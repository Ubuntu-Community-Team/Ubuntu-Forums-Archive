---
title: "Frequency Scaling"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Scopse on 2008-01-28
Hey there,

I know there are plenty of threads out there on the subject of Frequency Scaling, and I've search through the majority of them, but not alot of it makes sense because I've been using Ubuntu for only a few weeks now. I've tried alot of the things suggested, and not got anywhere, partly because my lack of knowledge of how to use commands to move files an things like that.

The problem I have is obviously the main error of 'Frequency Scaling Not Supported'. I've added powernow-k8 to /etc/modules as a previous thread said I should, the problem is though as I run powernowd in the Terminal I get this error:

desktop:~$ sudo /etc/init.d/powernowd start
 * Starting powernowd...                                                        /etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported

From that I think I need cpufreq installed, but going to the synaptic package manager and trying to install cpufreq I have to remove Powernowd for it to be installed, and if I install powernowd, I have to remove cpufreq. That's about as far as I've got, I really don't understand alot else so if anybodys got any further help for my situation it'd be great. I'm fed up after Googling for the past 3 hours. 

Can anyone give me a simple HowTo?

---

