---
title: "C2D: Only one core detected"
date: 2008-05-12
forum: Hardware
---

### Post by blankphoto on 2008-05-12
It was working well for about 3 weeks and now this.

cat /proc/cpuinfo

processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 15
model name : Intel(R) Core(TM)2 CPU 6400 @ 2.13GHz
stepping : 6
cpu MHz : 2128.418
cache size : 2048 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 10
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips : 4287.37
clflush size : 64


Any idea how to force detection? This was working fine for like 3 weeks and now this.

cpufreq-info gives this after reboot

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
no or unknown cpufreq driver is active on this CPU


Update: I have verified throught the Live CD that both cores are functioning, but the installed version is not finding one of them.

Update: It seems also that my sound card is no longer being found.

---

### Post by RAOF on 2008-05-12
It's likely that you've accidentally installed the -386 flavour of the kernel.  This flavour doesn't have SMP enabled, so no dual core.

Make sure you have the 'linux-generic' package installed - this will ensure that you've got the most recent -generic kernel + associated drivers/firmware installed - and then remove the linux-image-*some.numbers-here*-386 package.

---

### Post by blankphoto on 2008-05-13
> **RAOF said:**
> It's likely that you've accidentally installed the -386 flavour of the kernel.  This flavour doesn't have SMP enabled, so no dual core.

Make sure you have the 'linux-generic' package installed - this will ensure that you've got the most recent -generic kernel + associated drivers/firmware installed - and then remove the linux-image-*some.numbers-here*-386 package.


THANK YOU THANK YOU THANK YOU

My sound is back, as well as both cores.

What happened was I was installing virtualbox and got the other images in there... They looked like they were part of it, what can I say I'm a newbie.

---

### Post by cjrcl on 2010-07-24
Yes, the generic pae kernel support SMP, but sometimes it may fail to recognize all of the cores due to the inconsistence of ACPI settings in BIOS and the linux kernel.

Go into BIOS settings and enable ACPI or edit your grub configuration file to pass parameter acpi=off to the linux kernel works for me!

---

