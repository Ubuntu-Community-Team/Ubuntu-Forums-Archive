---
title: "ACPI no longer works with upgrade to edgy"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by superatrain on 2007-02-22
Hello all!
I've been running ubuntu-server on my old laptop for a couple of weeks, and decided to upgrade it from dapper to edgy. This update includes the updated 2.6.17-11-server kernel, rather than the 2.6.15-26-server kernel.

With this new kernel, my laptop will not start any acpi modules.

> modprobe acpi
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.17-server/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

I do not use cpufreq as the laptop is too old, but without acpi, the fans can't be turned on. I can run on kernel 2.6.15 for now, but Id rather find a way that will allow acpi to start w/o cpufreq, or anything related to it.

Also, while looking around on google, I found references to speedstep. Only the speedsetp-lib module loads, none of the others do, with similar errors. 

I tried the generic and 386 kernels as well, and the 386 kernel gave me a dmesg output:
"acpi_cpufreq unknown symbol cpu_online_map"

Thanks in advance,
Atrain

---

