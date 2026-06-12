---
title: "Aspire 1300 cpu frequency scaling problem..."
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by dedo on 2006-08-26
Hi!

I've got an Acer Aspire 1300DXV laptop, equipped with an AMD Duron Mobile 1200.

I'm experiencing a strange thing: under AC supply my CPU works only @ 500MHz and 600MHz (the battery has literally blown out! :( ).

I found that the frequency table files in /sys/system/devices/cpu/cpu0/ contain only 2 those values, consequently my powernowd daemon can only swith between 500 & 600MHz.

Another problem: my uP gets very hot compared to winXP; temperature goes up to 75-80°C, although the critical one seems to be 105°C according to cat /proc/acpi/thermal_zone/*/* .

Did anyone experience the same problem? I will be very happy if anyone having my same laptop will post here. 

Thanks. Bye.
Marco.

___________________________________________________________

Some News:
I've found that if I remove and reload for 2 times the module powernow-k7, the CPU starts to work correctly and 5 frequency steps are found, from 631MHz to 1200MHz...

Very strange thing, isn't it???

However, the problem now is to discover if this is really a bug or if it depends on something else...bah!

On this subject, I need to know how many ways exist to load modules at boot -time because my /etc/modules file contains only 2 entries, but lsmod gives me around 30 different modules loaded...
For the CPU the subsequent modules are loaded automatically at boot-time:

cpufreq_userspace       6816  1
cpufreq_stats           6912  0
freq_table              5152  2 powernow_k7,cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative    9256  0
powernow_k7             9192  0

and, as a daemon, the powernowd governors administrator.

Hope to see some replies... :roll: 

Bye. Marco.

---

### Post by smnr on 2006-09-27
Hi!

I also had the same problem.

I managed to fix it but I had to compile a kernel. I changed the Default CPUFreq governor from performance to userspace. You can find it in Power Management Options -> CPU Frequency Scaling.

Bye.

---

