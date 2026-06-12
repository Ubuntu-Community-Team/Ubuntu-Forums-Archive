---
title: "help with cpufreqd on a T43?"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by Athauglas on 2006-07-29
Heya.

Something that has bothered me about using ubuntu is that my battery life is no where close to what it is when I use XP. That makes me sad, and I want to improve it.

My machine is a T43 2687DDU. This model uses a pentium M 750 (dothan) and a mobility X300.

I have enabled laptop-mode and messed around with the config file, but no matter what I do I cannot get the HDD to actually spin down. I hear the heads parking quite often, but the disc is always spinning.

Thats problem #1. The other serious one is that after installing cpufreqd (plus dependencies and removing powernowd, of course) i receive an error telling me that my CPU doesn't support scaling, or that it's not configured right. Powernowd worked fine and took the CPU down to 800MHz (from 1.86GHz)... but in windows I have seen this one run as slowly as 333MHz.

Here is what "sudo cpufreqd -D" gives me:

pmu_init : /proc/pmu/info: No such file or directory
apm_init : /proc/apm: No such file or directory
sensors_post_conf : no sensors.conf found, sensors disabled!
plugins_post_conf : Unable to configure plugin sensors_plugin, removing
nforce2_post_conf : Unconfigured, exiting.
plugins_post_conf : Unable to configure plugin nforce2_atxp1, removing
parse_config_profile : Unable to calculate absolute values for profile "On D emand High".
parse_config_profile : Unable to normalize frequencies for profile "On Deman d High".
parse_config_profile : Unable to calculate absolute values for profile "On D emand Low".
parse_config_profile : Unable to normalize frequencies for profile "On Deman d Low".
parse_config_profile : Unable to calculate absolute values for profile "Perf ormance High".
parse_config_profile : Unable to normalize frequencies for profile "Performa nce High".
parse_config_profile : Unable to calculate absolute values for profile "Perf ormance Low".
parse_config_profile : Unable to normalize frequencies for profile "Performa nce Low".
parse_config_profile : Unable to calculate absolute values for profile "Powe rsave High".
parse_config_profile : Unable to normalize frequencies for profile "Powersav e High".
parse_config_profile : Unable to calculate absolute values for profile "Powe rsave Low".
parse_config_profile : Unable to normalize frequencies for profile "Powersav e Low".
write_cpufreqd_pid : the daemon is already running.
main : Unable to write pid file: /var/run/cpufreqd.pid


I installed Dapper from the disc I ordered, and have stuck to Synaptic for installing things, so hopefully that means no surprise configuration weirdness.

Bottom line is that in windows, my battery life can sometimes be more than an hour longer, and the machine is cool to the touch. In ubuntu, it warms my legs considerably, even when idle. I have no reason to even use windows once I get things set up nicely with ubuntu. I'm still pretty nubbish with linux, but I can get around okay, and follow instrucions.

So, ideas? Thanks in advance.

---

### Post by zgoda on 2006-07-29
Cpufreqd requires a bit more traditional configuration work (I mean, editing config file by hand) than powernowd. You have to specify, which driver should be used (most probably acpi) and define some profiles and behaviours in /etc/cpufreqd.conf. Please, read manual page for cpufreqd.conf (man cpufreqd.conf) to get more detailed instructions.
If you want scaling "to the bottom", use 0 as minimum processor speed. In my case this wasn't good idea, as I have Celeron-M machine and running at 175MHz with ondemand scaling governor has made any more CPU-consuming work taking really long time. YMMV, hovewer.

---

### Post by Athauglas on 2006-07-29
> **zgoda said:**
> Cpufreqd requires a bit more traditional configuration work (I mean, editing config file by hand) than powernowd. You have to specify, which driver should be used (most probably acpi) and define some profiles and behaviours in /etc/cpufreqd.conf. Please, read manual page for cpufreqd.conf (man cpufreqd.conf) to get more detailed instructions.
If you want scaling "to the bottom", use 0 as minimum processor speed. In my case this wasn't good idea, as I have Celeron-M machine and running at 175MHz with ondemand scaling governor has made any more CPU-consuming work taking really long time. YMMV, hovewer.

Ah, the man page is the first thing I looked for, but never found it.  Thanks for pointing out what it's called.  I'll have a look this afternoon. :)

---

