---
title: "enabling ondemand governor ?"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by elsewhere on 2005-06-20
Due to issues I'm having with powernowd, I've been trying to enable the "ondemand" cpufreq governor on my laptop.  I haven't found a lot of documentation, but from what I've seen this should give me dynamic cpu scaling from the kernel, rather than having to use a userspace utility.

However, when I execute the following command to enable it:

sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

I get a permission denied after authenticating with my password.  Only way I can get the command accepted is to sudo su first and then run in a root shell.  I thought that was strange.

Then I noticed that no matter what I tried, the scaling_governor would stay at performance.  I can't get it to change at all.

ondemand is listed as being available in scaling_available_governors.

Am I missing something or doing something incorrectly ?

Laptop is a PIII 1.13G, I'm using the speedstep-smi module for scaling.
Scaling is enabled, it does work with powernowd and I can manually set frequencies by modifying scaling_cur_freq (although I have to be root to do that as well, won't let me use sudo to do it).

Any help or input is greatly appreciated...

Cheers,
KV

---

### Post by elsewhere on 2005-07-03
FWIW, I resolved this issue by avoiding the speedstep-smi module and using acpi-cpufreq instead, before loading the cpufreq_ondemand governor.

Dynamic scaling now works well for me in kernelspace, as opposed to userspace with a utility like powernowd.  

Anyways, hope this may help someone else down the road...

Cheers,
KV

---

### Post by mlord on 2005-07-04
The KDE control center has a "Power Control" menu tree, which includes a  point-and-click interface for configuring stuff like this, allowing independent settings for on-battery and on-ac_power etc..

Cheers

---

### Post by elsewhere on 2005-07-04
It does, but from what I gather it depends upon the kernel governors.  I always had the option in klaptop to set a profile (performance, ondemand, powersave etc.) but it wouldn't take effect due to the problem above.  From my googling, it seems that there was some sort of an issue with the speedstep-smi module.

Now that I've got it resolved, klaptop is doing everything it should and I can switch profiles on the fly with a simple right click in the task bar.

Hopefully this thread may help someone else in a similar situation, if they happen to be using a PIII in their laptop like I am.

Cheers,
KV

---

### Post by Panthios on 2005-09-29
:d :d

---

