---
title: "OnDemand Governor"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by luca_linux on 2005-04-10
Hi!
I've an Asus M6N laptop and I've just installed Ubuntu Hoary.
I've noticed that the default cpu scaling governor is "userspace" and I have to choose the "ondemand" one manually through ```
cpufreq-selector --governor ondemand
``` 
Is there a way to set the ondemand governor as the default one?
Thanks in advance and sorry if this topic has been already discussed.

---

### Post by mirtux on 2005-04-10
Hi,
  you can set it modifying the file /etc/cpuspeed.conf in the appropriate way... for example changing the respective rules from performance to ondemand and so on..

Hope this will help,
MC

---

### Post by luca_linux on 2005-04-11
I haven't cpuspeed.conf or cpufreqd.conf. Any ideas?

---

### Post by luca_linux on 2005-04-12
Guys, could you check if you have the /etc/cpufreqd.conf file?

---

### Post by mirtux on 2005-04-13
Hi, (ciao)
  do you have cpufreqd demon installed on your system?

Regards,
MC

---

### Post by luca_linux on 2005-04-13
No, just powernowd.
But I think the ondemand governor does not depend on any daemon...it should be directly controlled by the cpufreq kernel driver, shouldn't it?

---

### Post by mirtux on 2005-04-13
I think that powernowd does not use the .conf we were speaking about. The goveror however is a kernel space feature but your frequency system manager has to call the appropriate governor, the one that you've chosen... You must tell powernowd what governor it has to use....

Regards,
MC

---

### Post by luca_linux on 2005-04-13
What's powernowd .conf file? I tried to find it but didn't manage to.

---

### Post by luopio on 2005-11-24
Not sure if you've already resolved this, but AFAIK powernowd uses the "userspace" governor and sysfs-interface to the in-kernel-cpufreq to control the speed (look at the deb-description of powernowd). 

So you can't use "ondemand" gov with powernowd. But you can switch to cpufreq and configure /etc/cpufreq.conf. Just change the profiles. This is what I changed: 
```
[Profile]
name=hi_boost
#minfreq=66%
minfreq=33%
maxfreq=100%
#policy=performance
policy=ondemand
```

Then start cpufreq. If nothing happens check if you have the needed modules in the kernel (for me: *speedstep_centrino* for scaling and governors *cpufreq_ondemand* and *cpufreq_performance*) 

I'm not entirely sure, but I have the feeling that the ondemand-gov reacts better to the need for more speed than the userspace-gov. If someone can confirm this I'll change back to cpufreq instantly 8-)

---

