---
title: "Pentium D 3.4G running only at 2.4G. Ubuntu 8.10"
date: 2008-12-01
forum: General Help
---

### Post by mT3 on 2008-12-01
Hi, I'm new to Linux and while I'm playing around the system I found this tool "sysinfo" showing that my CPU is pentium 3.4G.

But the frequency is only running at 2400 Mhz , 2.4G.

Is this normal like this? Or I'm not getting the full potential speed of my CPU?

Any inputs would be appreciated.

---

### Post by Ahadiel on 2008-12-01
Either
A) It's actually a 2.4ghz CPU
or
B) You have some cpu frequency scaling program installed that adjusts it's speed according to what you're doing.

---

### Post by sdennie on 2008-12-01
Try the following command to get more information:

```

cpufreq-info

```

You may not have that installed but instructions will be provided to install it if not.

---

### Post by Quarg on 2008-12-01
It's probably being scaled to what you are doing, my processor normally runs at 800MHZ even though it's a 1.73GHZ processor, it scales it down for power usage.

---

### Post by mT3 on 2008-12-01
> **vor said:**
> Try the following command to get more information:

```

cpufreq-info

```

You may not have that installed but instructions will be provided to install it if not.


Thanks for the advice! Just did a apt-get for cpufreq, it tells me my cpu range is 2.4g-3.4g and is currently at 2.4g for CPU1 and 3.4g for CPU0

Would it be better to change CPU1 to performance setting? My Ubuntu runs fine, but faster is always good!

And I don't really care about power usage because it's a desktop.

---

### Post by Cyhawk on 2008-12-01
> **mT3 said:**
> Thanks for the advice! Just did a apt-get for cpufreq, it tells me my cpu range is 2.4g-3.4g and is currently at 2.4g for CPU1 and 3.4g for CPU0

Would it be better to change CPU1 to performance setting? My Ubuntu runs fine, but faster is always good!

And I don't really care about power usage because it's a desktop.

You can force it higher, but it should automatically scale to what your doing, so when you need the power, it will boost it up, then scale back to the minimum it needs/can. (In this case, min is 2.4, so thats as slow as it gets)

This is good, think of it as power on demand. It will also increase the lifespan of your hardware since less power == less heat == less lifespan damage.

---

### Post by sdennie on 2008-12-01
Changing it to performance probably won't make a noticeable difference because, when it's needed, the CPU can go from min speed to max speed faster than a human will notice the change in speed.  Probably the only thing switching to performance will do is make your CPU run hotter but, to do it, try:

```

sudo cpufreq-selector -g performance

```

---

### Post by mT3 on 2008-12-01
I just tried it... Did not notice anything at all! It was fast already before. I think I'm gonna change it back to ondemand. Creating less heat when not needed is a good point. Thanks again guys.

---

