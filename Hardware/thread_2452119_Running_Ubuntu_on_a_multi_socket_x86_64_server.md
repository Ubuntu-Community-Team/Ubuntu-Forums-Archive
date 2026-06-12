---
title: "Running Ubuntu on a multi socket x86_64 server"
date: 2020-10-17
forum: Hardware
---

### Post by rinjo2 on 2020-10-17
Hi,

Is Ubuntu 18.04 LTS officially supported on a x86_64 server with 18 cpu sockets with 16 cores per socket?

Regards,
Rinjo

---

### Post by CelticWarrior on 2020-10-17
Why wouldn't it be? Please check with the manufacturer for officially supported OSes.

---

### Post by rinjo2 on 2020-10-18
We tried running Ubuntu 18.04 LTS on such a server configuration and started observing some random crashes. Our tech support mentioned that is not supported. I had my doubts so was just trying to know if there are some known limitations with Ubuntu.
Thanks for your response.

---

### Post by scorp123 on 2020-10-19
> **rinjo2 said:**
> Our tech support mentioned that is not supported.

But that could have dozens of reasons other than the CPU's. Those are the least concern. A server does not only have CPU's. There are usually also RAID cards that probably require special drivers (or a special Linux kernel), several network cards and their chipsets which might be proprietary too, management hardware such as ILO port adapters and the virtual hardware associated with it, and so on.

You should check the compatibility of those components too, not just the number of CPU's.

---

### Post by Yellow Pasque on 2020-10-19
Not exactly sure if 18.04 is different, but the Ubuntu 20.04 kernel is configured to handle a large amount of CPUs/cores (8192):

```
grep NR_CPU /boot/config-`uname -r`

CONFIG_NR_CPUS_RANGE_BEGIN=8192
CONFIG_NR_CPUS_RANGE_END=8192
CONFIG_NR_CPUS_DEFAULT=8192
CONFIG_NR_CPUS=8192
```

> We tried running Ubuntu 18.04 LTS on such a server configuration and started observing some random crashes.

If you exceeded the kernel's maximum number of CPU's, the most likely results would be the system failing to boot or the system boots/runs okay, but not all CPU's are available.

---

### Post by CelticWarrior on 2020-10-19
> **Yellow Pasque said:**
> Not exactly sure if 18.04 is different, but the Ubuntu 20.04 kernel is configured to handle a large amount of CPUs/cores (8192):

```
grep NR_CPU /boot/config-`uname -r`

CONFIG_NR_CPUS_RANGE_BEGIN=8192
CONFIG_NR_CPUS_RANGE_END=8192
CONFIG_NR_CPUS_DEFAULT=8192
CONFIG_NR_CPUS=8192
```



If you exceeded the kernel's maximum number of CPU's, the most likely results would be the system failing to boot or the system boots/runs okay, but not all CPU's are available.

Exactly!

The premise in the OP is nonsensical.

**@rinjo2 - Please post the hardware specifications as complete as you can.**&#8203; The number of CPUs/cores is totally irrelevant.

---

