---
title: "safe changing of scaling_available_frequencies"
date: 2006-08-19
forum: Hardware &amp; Laptops
---

### Post by Krzysztof on 2006-08-19
Hi all laptop experts,
I'm playing with laptop-mode-tools. It behaves very well, I must say.
However my lowest CPU freq. is always 60%. I found out that lm uses
frequencies listed in
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
and it contains:
1660000 1660000 1660000 1660000 1660000 1660000 1660000 1660000 1328000 996000

Can I safely change it to say:

1660000 1660000 1660000 1660000 1660000 1660000 1328000 996000 500000 300000

It also looks like settings concerning CPU frequency scaling governors
(in /etc/laptop/mode) are not used. Is it possible that there is some kind of conflict between laptop-mode-tools and powernowd, which I have also installed ?

Thanks.
K.

---

