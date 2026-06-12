---
title: "Toshiba L30-113A ACPI"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by run_time on 2007-09-03
Hi, 
In the past few days i became quite frustrated with my Toshiba Satellite L30-113a laptop. Thing is i can’t get the ACPI to work. Or should i say it works partially, the functional keys work, i got the sound and the wireless working, yet an important thing in the laptop is not working – namely the CPU fan. I did some research and found that Toshiba are not very Linux friendly, yet there must be some solution.

So far i have done this:

I turned on Toshiba support in the ACPI at the kernel and compile it.
The ACPI recognized and displayed the battery and the functional keys

#cat /proc/toshiba/  - missing
#cat /proc/acpi/toshiba  - missing

#lsmod | grep acpi

pcc_acpi               14080  0
dev_acpi               12292  0
asus_acpi              17308  0

It is clear that toshiba_acpi is missing and the module is not loaded

#sudo modprobe toshiba_acpi

FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.20-16-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

#find /lib/modules/`uname -r` -name "tosh*"

/lib/modules/2.6.20-16-generic/kernel/drivers/acpi/toshiba_acpi.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/char/toshiba.ko

Yet the module is present but it’s not loaded!

#lsmod | grep cpu

cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0

#toshset – says that the module is not loaded

#acpi -V
    Battery 1: charged, 100%
    Thermal 1: ok, 54.0 degrees C
 AC Adapter 1: on-line

#dmesg – nothing suspicious

---

### Post by danwood76 on 2007-09-13
Hi, I have an L30-10V (which I assume is similar mine is a PSL33E)

The ACPI seems to be working fine on mine.
I installed Feisty 7.04 from the DVD image.

regards,
Danny

---

