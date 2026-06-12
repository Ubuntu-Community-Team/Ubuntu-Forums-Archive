---
title: "Dual CPU"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by Skyguy906 on 2007-12-31
Where would I look to find conformation that Ubuntu has found and is using both CPU's (SMP)

---

### Post by Zafrusteria on 2007-12-31
You can try running this command you should get something like  the following which is from my twin core AMD 6000+. Note it find 2 CPUs.

```
cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
driver: powernow-k8
CPUs which need to switch frequency at the same time: 0 1
hardware limits: 1000 MHz - 3.00 GHz
available frequency steps: 3.00 GHz, 2.80 GHz, 2.60 GHz, 2.40 GHz, 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
available cpufreq governors: powersave, userspace, ondemand, conservative, performance
current policy: frequency should be within 1000 MHz and 3.00 GHz.
The governor "performance" may decide which speed to use
within this range.
current CPU frequency is 3.00 GHz.
analyzing CPU 1:
driver: powernow-k8
CPUs which need to switch frequency at the same time: 0 1
hardware limits: 1000 MHz - 3.00 GHz
available frequency steps: 3.00 GHz, 2.80 GHz, 2.60 GHz, 2.40 GHz, 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
available cpufreq governors: powersave, userspace, ondemand, conservative, performance
current policy: frequency should be within 1000 MHz and 3.00 GHz.
The governor "performance" may decide which speed to use
within this range.
current CPU frequency is 3.00 GHz
```

As a simple test :-) run ONE folding at home process and you will see when using top that 50% of your CPU time is used. If you find 100% is used then you only have one CPU or only one is being found.

As an alternative try tar zipping the /usr directory it will use only one process and again only show up as 50% of your CPU time.

```
cd /
sudo tar zcf somefile.tgz ./usr &

```

There should be no output from the command above and the comand should run in the background. So you can run top.

Hope that helps.

---

### Post by tgalati4 on 2007-12-31
Run the gnome system monitor and you will see two lines.  Change the color of one of the lines (why is this not the default?) and you will see how the load is shifted between the two processors.

---

### Post by jarthurs on 2007-12-31
Open a terminal session and type:

*cat /proc/cpuinfo* this will give you the details of all the processors installed (or cores) starting with Processor 0

Alternatively at the command line type *top* this will give you the total processor usage at the top of the screen, press '1' to give the CPU usage breakdown for each CPU/core.

Hope this helps,
Jason.

---

### Post by firehelix on 2008-01-03
any hints on where to look if it's NOT seeing both processors / cores?

---

