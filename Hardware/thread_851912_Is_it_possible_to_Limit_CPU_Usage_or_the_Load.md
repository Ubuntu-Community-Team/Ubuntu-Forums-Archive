---
title: "Is it possible to Limit CPU Usage or the Load?"
date: 2008-07-07
forum: Hardware
---

### Post by kranklin on 2008-07-07
I have an HP DV9308 Laptop and it tends to overheat, especial when i'm doing alot. I am dual booting Ubuntu and Vista. In Vista, I can change the power settings to to save the battery, it goes a little slower but doesn't overheat. Is there something i can do to reduce the load in Ubuntu.

I appreciate any suggestions.

p.s. I've been running ubuntu straight for about the past 3 weeks since I installed it and don't plan on quiting.

---

### Post by AlesUbu123 on 2008-07-07
In linux, there a re CPU frequency governors that regulate the frequency of the CPU. My computer is 1,6GHz, but when I am on battery it always runs on 800MHz. 

You could try installing package *cpufrequtils* from synaptic and then use the powersave frequency governor manually:
```
sudo cpufreq-selector -g powersave
```

If anything goes wrong, just ask.

---

### Post by kranklin on 2008-07-07
Thanks AlesUbu123.  Exactly what I needed. I have the CPU Frequency Scaling Monitor applet so I saw it goto 800 Mhz as soon as i ran it and stayed.

For the record, i'm running a dual core AMD64

---

### Post by jocko on 2008-07-08
You may also be interested in [this thread]("http://ubuntuforums.org/showthread.php?t=786402") about undervolting the cpu.
It will save both battery life and lower the temperature of the cpu.

---

### Post by airtonix on 2008-09-12
As an example, this sets virtual box to utilise only the first core of your multicore cpu.

```
taskset -c 1 virtualbox
```

---

### Post by hal10000 on 2009-10-15
you could also use a package called [COLOR="Red"]cpulimit [/COLOR] to limit the cpu usage of a process.

---

