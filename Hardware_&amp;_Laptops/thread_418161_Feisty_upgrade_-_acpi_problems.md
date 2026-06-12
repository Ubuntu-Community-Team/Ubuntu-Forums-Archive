---
title: "Feisty upgrade - acpi problems"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by qwerkus on 2007-04-22
Hi,

After upgrading to 7.04, I got really into acpi troubles: at first, the laptop (centrino 1,6Ghz) kept rebooting all the time because of "critical temperature reached". Now I'm able to log on, but the proc freq seems to be stuck at 600Mhz, although ac power is on.
Any Ideas to get it working ?

Here the /proc/cpuinfo:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.60GHz
stepping	: 6
cpu MHz		: 600.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips	: 1197.80
clflush size	: 64

From the VERY long dmesg (i'm coming from FreeBSD...), I kept the following lines:

[...]
ACPI: CPU0 (power states: C1[C1] C2[C2]
ACPI: Core revision 20060707
ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
Total of 1 processors activated (3194.13 BogoMIPS).
ENABLING IO-APIC IRQs
TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Brought up 1 CPUs C3[C3] C4[C3])
[...]
ACPI: Processor [CPU0] (supports 8 throttling states)
**ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] **
ACPI: Invalid passive threshold
ACPI: Thermal Zone [THRM] (57 C)]
[...]

What does the bolded message mean ?

If more information is needed, I can provide it.

Thanx for Help.

qwerkus

---

### Post by turten on 2007-04-22
Check [this]("http://ubuntuforums.org/showpost.php?p=2501067&postcount=7")

---

### Post by powaz on 2007-04-22
Have the same problem with a centrino 2.0, hope the ubuntu developers come out with a fix soon. It's a really troublesome problem.

---

### Post by qwerkus on 2007-04-23
Thanks for replies, guys. It's always good to know your not the only one...
Just a question: WHERE can you read the Ubuntu RELEASE-NOTES ? Because I already saw some porblems caused by the new Kernel at Gentoo's forum, I wondered if the Ubuntu team brought up some patch; but couldn t find ANY detailed release notes, including the realease-compatibility list.

---

