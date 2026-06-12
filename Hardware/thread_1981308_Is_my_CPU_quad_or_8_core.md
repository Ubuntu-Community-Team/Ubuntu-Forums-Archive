---
title: "Is my CPU quad or 8 core?"
date: 2012-05-16
forum: Hardware
---

### Post by Tombradyhasamachinehead on 2012-05-16
My laptop has the i7-2630QM processor. The system says quad core, however ubuntu says it 8 core? Is it 8 core and intel made an error?

---

### Post by cmont899 on 2012-05-16
4-core, 8 after hyperthreading

---

### Post by smile-on on 2012-05-16
> **cmont899 said:**
> 4-core, 8 after hyperthreading

This means your CPU Chip has 4 phisical cores but OS can run 8 threads simultaniously by using hyperthread feature in each core. Do not worry, it is all automatic and build in in your OS hypervisor. No action required on your side. :)
Actual system performance depends on your typical workload. Test is only way to know the speed!

I worked in research lab few years ago at the begining of 4 cores cpu and we found that for some scientific math intence calculation disabling hyperthreading actually improves speed. Just Google, hint: cpu bound threads.:popcorn:

---

### Post by Shehbaz on 2012-07-04
Hi,

I have an intel i5 processor which shows 4 cores when I do cat /cpu/procinfo.

I wanted to know if hypervisor facility is available in i5 processors, and if so how can we enable this feature to run 8 cores?

---

### Post by efflandt on 2012-07-04
Which i5 cpu model?

Mine is i5 650 3.2 GHz which is actually 2 cores with hyperthreading, but appears to be 4 cores to any OS including Linux which can automatically independently run at different speeds which you can tell by running this script:

```
#!/bin/sh
while [ 1 ]; do
    grep MHz /proc/cpuinfo
    sleep 1
    echo
done
```

The hypervisor just manages that all automatically, it cannot create more threads than you actually have.

---

### Post by Yellow Pasque on 2012-07-04
It's 'hyperthreading' (not 'hypervisor'), and if your chip has it, it will probably be enabled by default in the BIOS.

---

