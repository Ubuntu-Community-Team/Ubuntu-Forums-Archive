---
title: "modprobe and acpi-cpufreq not found"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by skaramanger on 2007-08-25
Greetings,

I am trying to get cpu throttling working, but everytime I attempt to load the needed module I get:

terry@tzlaptop:~$ sudo modprobe /lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko
FATAL: Module /lib/modules/2.6.20_16_generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi_cpufreq.ko not found.                 ^    ^
                        note above.:confused::(

terry@tzlaptop:~$ 

terry@tzlaptop:~$ ls -l /lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko 
-rw-r--r-- 1 root root 12896 2007-06-07 16:59 /lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko

Is there something amiss with my path,modprobe or ????

Tia,
Skaramanger

---

### Post by 5-HT on 2007-08-26
Just do a  simple 'modprobe acpi_cpufreq'. No need for paths as only the module for the currently running kernel will load.

cheers,

---

### Post by skaramanger on 2007-08-26
Thanks for your reply 5-HT,

I guess I should've noted the following:

terry@tzlaptop:~$ sudo modprobe acpi_cpufreq
Password:
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
terry@tzlaptop:~$ 

Combined with the previous messages, I am confused as to what that message means, with respect to the previous messages.

Thanks again,

Terry

---

### Post by 5-HT on 2007-08-28
Hmm, we'll we're getting somewhere because the module is found and attempted to load but failed. What processor are you running? acpi-cpufreq is a newer module  that will/has replaced the deprecated speedstep centrino module. Maybe you'll have better luck with that?

---

### Post by skaramanger on 2007-08-31
> **5-HT said:**
> Hmm, we'll we're getting somewhere because the module is found and attempted to load but failed. What processor are you running? acpi-cpufreq is a newer module  that will/has replaced the deprecated speedstep centrino module. Maybe you'll have better luck with that?

I'm not sure about that 5-HT, my laptop is a gATEWAY Solo 5300.  It's got a 650mhz PIII processor with 512Mb of ram. 

Terry

---

