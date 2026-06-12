---
title: "Scaling driver for Tablet PC TC1000 (longrun?)"
date: 2008-12-23
forum: Hardware
---

### Post by mplexus on 2008-12-23
Hello all.

I installed 8.10 in tablet pc TC1000 and now i'm experimenting with cpu scaling. Cpu is Transmeta Crusoe TM5800.

My question is: which program (driver?) should I use in order to automatically change cpu freq according to either cpu load or battery (battery/ac) state.

I load module thermal and in cpu scaling applet I am able to manually choose between Performace (1 GHz) and Powersave (300MHz).

I find that five cpufreq modules (cpufreq_powersave, .._ondemand, .._stats, .._conservative, .._userspace) are being loaded (by default).

Should I use module thermal ?

Should I use module acpi-cpufreq ? When I try to load it I get this error message: FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.27-9-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy

Should I start /etc/init.d/powernowd (and powernowd.early) ?

I do load module longrun (accompanied by modules cpuid and msr). But as shows the cpu scaling applet the cpu frequency doesn't change automatically according to cpu load/battery.

---

### Post by mplexus on 2008-12-25
Well, cpufreq-acpi does not load but longrun does. I suppose this is the appropriate driver for Crusoe processors. The thing is that only two governors are available, performance and powersave.

Can i somehow enable ondemand governor?
Do i need this?

Can software change cpu freq on demand so that i don't have to use cpufreq-set manually ?

Also, with cpufreq-info i get that cpu freq is set at 800 MHz while the cpufreq-applet shows 1 GHz.

Just to share my ubntu 8.10 experience.

-=~=-
This post [http://www.razdva.cz/vencik/TC1000_And_Linux/](http://www.razdva.cz/vencik/TC1000_And_Linux/) helps. There is a script for (manually?) changing between the two governors.

---

### Post by rasker on 2009-01-12
I am trying to configure a similar machine (Sony Vaio PCG-C1MHP) and these are my findings:


With a crusoe processor you only have performance and powersave kernel governers.

I believe Performance is effectively the same as ondemand, using cpufreq-info repeatedly you should see the processor frequency vary with load. The same with Powersave but I guess the processor tries to use the lowest frequency for the load.

To switch between the governors you can use cpufreq-set -gpowersave or cpufreq-set -gperformance.

I haven't been able to get the applets working either but I don't think they are supported as cpufreq_userspace governor is not supported (basically the cpu does it's own power management).

You can try to manually set the cpu speed with cpufreq-set. Check the harware limits using cpufreq-info --hwlimits and then cpufreq-set -f<value>. This did not work for me though leading me to believe that it can't be done on crusoes.

Thermal management is a different problem. You would need a script to be run if the laptop overheated and probably you can only go from performance to powersave. Most likely the crusoe would do this anyway if it were overheating.

---

