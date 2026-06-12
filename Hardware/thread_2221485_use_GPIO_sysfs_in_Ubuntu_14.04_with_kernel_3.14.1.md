---
title: "use GPIO sysfs in Ubuntu 14.04 with kernel 3.14.1"
date: 2014-05-02
forum: Hardware
---

### Post by hankthetank2 on 2014-05-02
Hello,

I am trying to get a viperboard USB GPIO board running on ubuntu.
I already got a newer kernel, because I understood that the 3.13 kernel doesn't support the viperboard so well.

What I want to do is to use the /sys/class/gpio sysfs interface for GPIO so I can develop raspberry pi projects on my PC and then use them
on my RPi.

My Problem - the /sys/class/gpio firectory is missing.
The config of the kernel shows:
# CONFIG_GPIO_SYSFS is not set

Does this mean I have to compile a new kernel?

Thanks in advance,

Hinrich

---

