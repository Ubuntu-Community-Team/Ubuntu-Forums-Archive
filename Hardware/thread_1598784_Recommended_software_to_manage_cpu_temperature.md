---
title: "Recommended software to manage cpu temperature"
date: 2010-10-17
forum: Hardware
---

### Post by declanmullen on 2010-10-17
What is the currently recommended software to have Lubuntu 10.04 automatically detect that a CPU is approaching an unsafe high temperature and then automatically attempt to reduce the temperature by increasing fan speed and/or stepping down the CPU's GHz ?

My laptop is a Dell Inspiron 5150 with a Intel Pentium 4 Mobile 3.2GHz CPU. It's OS is "Mint LXDE 9" which is based upon "Lubuntu 10.04". It has the default packages installed with default configuration and with the latest updates applied.

With my laptop, I've noticed that the OS is not attempting to drop my CPU down from its 3.2GHz top speed step to its lower 1.5GHz speed step, when the temperature is way above its safe temperature (eg 75 C), and as a result my laptop is subsequently turning off. It doesn't even attempt to shutdown the OS before turning off.

FYI, I've been monitoring:
[LIST]
[*]The temperature via /sys/devices/virtual/thermal/thermal_zone0/temp
[*]The speed via /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
[/LIST]

Many thanks.

---

### Post by declanmullen on 2010-10-19
Took some good advice and cleaned the lint from the cpu fan. OS is now managing the cpu's temp/fan/speed very well. No extra software required.

---

### Post by TBABill on 2010-10-19
In case you ever need it, from the command line (if you don't want to configure the GUI applet):> sudo cpufreq-set --governor ondemand
 
To verify what it is set to:
> cpufreq-info

---

