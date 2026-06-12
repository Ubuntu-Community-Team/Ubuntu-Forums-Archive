---
title: "/proc/acpi/ibm missing...."
date: 2009-02-28
forum: Hardware
---

### Post by eggmanpete on 2009-02-28
I own an IBM ThinkPad X61 and my /proc/acpi/ibm has gone missing...what gives?


On ubuntu 8.10, 
uname -a 
```
"Linux 23 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux"
```

---

### Post by eggmanpete on 2009-02-28
```
x@x:~$ sudo modprobe thinkpad-acpi
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.27-9-generic/kernel/drivers/misc/thinkpad_acpi.ko): Invalid argument

```

---

### Post by curley_sue on 2010-06-11
following:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566647)

I removed all linux-backports-modules-alsa-*
which resolved the problem

---

