---
title: "load-dependent cpu throttling"
date: 2010-09-04
forum: Hardware
---

### Post by Belveder on 2010-09-04
Hi,

I want to set up a small server based on an old notebook I found recently, so I set up Ubuntu 10.04 on the old IBM Thinkpad A22m. The 850 MHz P3 Mobile CPU only supports throttling and not direct frequency scaling, so I played around a bit.

I found out that "cat /proc/cpuinfo" always gives me a frequency of 697 (or something close to 700) Mhz rather than 850, which is really mysterious, because I set the BIOS settings to "Max Performance" anywhere I found it. Any ideas?

Ok, as usual I installed laptop-mode. I found the place where to configure the cpu frequency/throttling part in "/etc/laptop-mode/conf.d/cpufreq", however, the support of throttling seems to be really weak. You can only set a special mode for the three possible states (Batt only, AC only or Batt+AC), and that's definitely what I do not want to do. I'd rather like to have some daemon running that adjusts the throttling settings from T0 to T7 according to the system load. So I disabled the control and installed powernowd. However, that didn't solve the problem either, since it complains about the missing "governor", that clearly does not exist on the "throttling only" machine...

Any help is highly appreciated!

Regards

---

### Post by Belveder on 2010-09-14
bump

no idea? :icon_frown:

---

