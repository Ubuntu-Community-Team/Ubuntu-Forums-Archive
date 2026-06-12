---
title: "Celeron 3200 + coreremp"
date: 2011-03-21
forum: Hardware
---

### Post by ilna on 2011-03-21
Can anybody verify coretemp does work with this CPU?

---

### Post by ilna on 2011-03-21
BTW, to see a core temp you don't need to install lm-sensors. Just

```
sudo modprobe coretemp
```

to load the module. Then, to see first core temperature, repeat few times

```
sudo cat /sys/devices/platform/coretemp.0/temp1_input
```

You will see a temp in C multiplied by 1000 (i.e. in millidegree).

---

### Post by ilna on 2011-03-21
Aha, I see, I'm the only Celeron E3200 owner in the world... :)

---

### Post by ilna on 2011-03-22
Up.

I still hope some E3200 owner will try those two listed command. The thing is, I'm configuring self-made home NAS. Last one must be (almost) silent. As a result, funs must have lowerst possible rpm. To get needed rpm I need to monitor CPU cores' temperatures. 

You see, such simple issue is an absolute **show stopper** for me.

Please, try!

---

