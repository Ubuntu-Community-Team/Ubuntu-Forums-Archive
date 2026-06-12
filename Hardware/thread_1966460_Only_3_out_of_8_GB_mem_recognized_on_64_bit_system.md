---
title: "Only 3 out of 8 GB mem recognized on 64 bit system"
date: 2012-04-27
forum: Hardware
---

### Post by dannyvanderzande on 2012-04-27
I installed my ubuntu server 11.10 last week and everything has been running fine. Upon receiving my new memory this morning I ran "top" and I saw that my old 4 GB mem wasnt totally recognized. Only 3 GB was...

Upon removing the old (ddr2) mem and installing 8 GB (ddr3) mem I tried again and it still only recognized 3 GB of memory.

I know this is the case when running an X86 system, but I have a x64 system and kernel running. Just to be sure I checked again with:

grep flags /proc/cpuinfo
The output was 4x the following:

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx **lm** constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts tpr_shadow vnmi flexpriority

According to the www --> lm should mean it's a 64 bit cpu.

Than I ran uname -a
output:

Linux thuis-server 3.0.0-17-server #30-Ubuntu SMP Thu Mar 8 22:15:30 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

So that also states I have a 64 bit system running..

I haven't got the slightest clue what could possibly be the problem so I'm hoping somebody here can help me out on how to get my 8 gb recognized.

edit: I've been going through my settings once again and I enabled memory remapping in the bios, that did the trick!

---

