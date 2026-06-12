---
title: "Upgrading to 4.5.2 stable reduced battery life (16.04 LTS)"
date: 2016-05-05
forum: Hardware
---

### Post by redguy41 on 2016-05-05
Hi everyone,

I'm having a very specific problems with Ubuntu 16.04 LTS and battery on my Lenovo z51-70 80K.

```
Linux gaj-Lenovo-Z51-70 4.5.2-040502-generic #201604200335 SMP Wed Apr 20 07:37:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

When I first installed 16.04 LTS, at kernel 4.4.0, I had a decent battery life of about 3 hours average, but I **upgraded to 4.5.2** to solve the suspend problem and some other issues, and now it's less than 1.40 hours, even at low brightness. What could have caused a drop between the kernels? 4.5.2 is stable, and the same thing happened when upgrading to 4.4.8 (lts).

I did a **tlp -stat output** of both kernels in use (4.4.0 and 4.5.2), and the only difference I can notice is that the latest kernel 4.5.2, outputs this, compared to the 4.4.0 which saves battery:

```

/sys/devices/system/cpu/intel_pstate/min_perf_pct      = 18
/sys/devices/system/cpu/intel_pstate/max_perf_pct      = 100
/sys/devices/system/cpu/intel_pstate/no_turbo          = 0


x86_energy_perf_policy: program for your kernel not installed.


```

When I try to install linux-tools, as explained at TLP's troubleshooting website, which says:

```
tlp-stat -p shows "x86_energy_perf_policy: program [for your kernel] not installed."


Depending on the distro your mileage may vary:


Ubuntu: install the meta-package linux-tools (or linux-tools-lts-* for HWE stack kernels), no package available for mainline kernels.

```

I get:
```

Package linux-tools is a virtual package provided by:
      linux-tools-virtual 4.4.0.21.22
      linux-tools-lowlatency 4.4.0.21.22
      linux-tools-generic 4.4.0.21.22
    You should explicitly select one to install.

```

So no tools for 4.5.2 kernel. Or should I install HWE stack tools? What does HWE mean in relation to the stable 4.5.2 kernel?
Many thanks.

P.s. It might be worth noting that I use a hybrid graphics system INtel and ATI, but I haven't installed any propriertary drivers, or manually upgraded any. I also hear the fan working more at 4.5.2.

---

### Post by weatherman2 on 2016-05-05
Have you run "top" in a command window to see if any processes are burning CPU power constantly?

---

### Post by redguy41 on 2016-05-05
Yeah, but still, nothin g changes in the system. I boot into two different kernels at the same system. Something else is the case.

---

### Post by redguy41 on 2016-05-06
PowerTop output:

[ATTACH=CONFIG]268871[/ATTACH]

---

