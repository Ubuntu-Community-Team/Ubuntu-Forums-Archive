---
title: "CPU frequency scaling xeon E5420 on S5000V"
date: 2009-11-29
forum: Hardware
---

### Post by priyadarshan.hari on 2009-11-29
I am new to ubuntu. I have been trying to enable cpu frequency scaling for the past few days in VAIN with my ubuntu 9.04 jaunty. I have searched the forms and tried most of the suggestions.

I have tried the following modules acpi_cpufreq, powernowd, cpudyn, cpufreqd. Nothing works for me. I always get the error message like the following:

FATAL : Module acpi_cpufreq not found.

My processor is now  operating at  full speed with the CPU fan and cabinet fan making a loud noise. As I am typing my Ph.D thesis the noise is distracting me and driving me crazy.

I am using Xeon E5420 x 2 quad core on S5000vSA motherboard. 

Has anyone been able to enable CPU frequency scaling on the above hardware? I have also not been able to enable temperature monitoring on this system. Is the above hardware supported by ubuntu?

I will be grateful to the community for any help in this direction.

[LEFT]PS: I have tried to piggy bank my problem as a part of thread older thread "CPU Frequency Scaling not working for my in ubuntu 9.10" under the same Forum**. I did not get reply for the past 5 days. So  I thought posting it as a newer thread may get some advice.**
[/LEFT]

---

### Post by markonhismobile on 2010-06-03
Have you tried "sudo modprobe p4_clockmod" ?

After that you can try installing cpudyn or cpufrequtils and having a play with them.

This worked for me on a HP DL380G3 using older 2.4Ghz Xeon CPU's whilst I've been trying to get throttling working :-)

So far I've only got 1 CPU scaling and was googling for suggestions and found this thread so thought I'd chip in.

---

### Post by priyadarshan.hari on 2010-06-06
Great! Thanks, will try and let you know.

:
:
:

Tried -  but I got the following error message:

"FATAL: Error inserting p4_clockmod (/lib/modules/2.6.28-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): No such device"

How does one find out if my processor supports frequency scaling?
:
:
:

Searched intel specifications:  Supports EIST (Enhanced intel speed step technology)
See wiki:
[http://en.wikipedia.org/wiki/List_of_Intel_Xeon_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Xeon_microprocessors)
:
:
:
More info:
The following message was displayed by dmesg:

[98005.579924] p4-clockmod: Unknown p4-clockmod-capable CPU. Please send an e-mail to <cpufreq@vger.kernel.org>

What does this mean? 
I have sent a mail to "cpufreq@vger.kernel.org" indicating my problem.

---

