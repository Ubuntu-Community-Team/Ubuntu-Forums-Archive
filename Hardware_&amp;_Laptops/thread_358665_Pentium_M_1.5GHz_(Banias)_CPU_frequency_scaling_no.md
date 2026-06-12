---
title: "Pentium M 1.5GHz (Banias) CPU frequency scaling not working"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by automatthias on 2007-02-11
Hi,

I have an Fujitsu-Siemens Amilo Pro V2000D laptop. When running Slackware 9.0 on it, back in 2005, I had no problems with getting the CPU frequency scaling to work. Unfortunately, it doesn't want to work with Edgy Eft. My processor is:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Celeron(R) M processor         1500MHz
stepping	: 5
cpu MHz		: 1499.868
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up
bogomips	: 3001.80
clflush size	: 64

So, basically, it's Pentium M 1.5GHz, Banias, (6, 9, 5). It should be supported by the speedstep-centrino kernel module. Here's a snippet from speedstep-centrino.c:

static const struct cpu_id cpu_ids[] = {
        [CPU_BANIAS]    = { 6,  9, 5 },      &#8592; This matches my processor
        [CPU_DOTHAN_A1] = { 6, 13, 1 },
        [CPU_DOTHAN_A2] = { 6, 13, 2 },
        [CPU_DOTHAN_B0] = { 6, 13, 6 },
        [CPU_MP4HT_D0]  = {15,  3, 4 },
        [CPU_MP4HT_E0]  = {15,  4, 1 },
};

When trying to insert the speedstep-centrino module:

sudo modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.17-11-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

I also tried speedstep-ich and speedstep-smi and acpi-cpufreq: the same results.

To get some more debug info, I compiled vanilla 2.6.20 from kernel.org and passed cpufreq.debug=7 option. Trying to insert the module again:

sudo modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

Here's my dmesg (grep -E (speed|freq)):

[   11.983448] Kernel command line: root=/dev/hda5 ro cpufreq.debug=7 quiet splash
[   13.278975] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.984000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    6.784000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[    7.180000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  310.872000] speedstep-lib: x86: 6, model: 9
[  310.872000] speedstep-ich: Intel(R) SpeedStep(TM) capable processor not found
[  317.560000] acpi-cpufreq: acpi_cpufreq_init
[  317.560000] acpi-cpufreq: acpi_cpufreq_early_init
[  317.560000] cpufreq-core: trying to register driver acpi-cpufreq
[  317.560000] cpufreq-core: adding CPU 0
[  317.560000] acpi-cpufreq: acpi_cpufreq_cpu_init
[  317.560000] cpufreq-core: initialization failed
[  317.560000] cpufreq-core: no CPU initialized for driver acpi-cpufreq
[  317.564000] cpufreq-core: unregistering CPU 0
[  473.808000] speedstep-lib: x86: 6, model: 9
[  473.808000] speedstep-ich: Intel(R) SpeedStep(TM) capable processor not found
[  774.028000] speedstep-lib: x86: 6, model: 9
[  774.028000] speedstep-smi: No supported Intel CPU detected.

What's interesting is that speedstep-centrino didn't output any messages in dmesg. All of the messages above come from the other modules.

I'm currently out of ideas: Where to look? How to debug? Any ideas?

---

