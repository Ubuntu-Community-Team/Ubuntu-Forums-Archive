---
title: "not installing smp kernel on a p4Ht pc."
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by ashokpappu on 2006-01-16
Hello All,
I installed ubuntu 5.04 on my P4 3.0GHz with Ht technology(Dell dimension 8300). I enabled HT in my bios but for some reasom the SMP kernel is not installed on my system.. when I install FC4 it is using the smp kernel. what should I do to enable my ubuntu to take advantage of HT technology and use smp kernel?
Please advise
Thanks
Ashok Pappu

---

### Post by Sutekh on 2006-01-17
Have you installed the SMP kernel?  The default kernel on Ubuntu is not a SMP one.

For you P4s I'd install the linux-686-smp package either using apt-get;
```

sudo apt-get install linux-686-smp

```
or by searching in Synaptic and installing it that way.

When you boot up you should have the option to boot into Ubuntu with your choice of kernel, SMP or not.

---

