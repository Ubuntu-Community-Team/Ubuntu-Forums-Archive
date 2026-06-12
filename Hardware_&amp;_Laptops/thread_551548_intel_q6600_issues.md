---
title: "intel q6600 issues"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by steffmeister on 2007-09-15
hi folks!

I looked in google for following issues and searched ubuntuforums, but found nothing, correct me if I am wrong! (and after fiddling around in the german forums...)

I have an experimental Ubuntu running, that means, installed an 7.04, and upgraded to current gutsy... so I am currently using following kernel: 
"Linux skywalker 2.6.22-11-generic #1 SMP Fri Sep 7 04:31:16 GMT 2007 x86_64 GNU/Linux"

I have a Asus Extreme Strike motherboard btw.

my problems are now:
1) the q6600 is a quad core with 2.4GHz each core, BUT:
> steff@skywalker:/sys/devices/system/cpu/cpu0/cpufreq$ cat cpuinfo_max_freq 
900000
the maximum frequency reported for each core is 900MHz... ie NOT 2.4GHz, whys that?

2) a "cat /proc/cpuinfo" returns no flags in line power management, this sounds also not normal?

3) a "cat /proc/acpi/thermal_zone/THRM/temperature" seems to returns ALWAYS 40°C?


if any further information about my system is needed, just say it.

I'd be happy at nearly every comment... mfg steff

---

### Post by steffmeister on 2007-10-11
*bump*

---

### Post by steffmeister on 2007-10-16
is it possible that that can be related to dsdt?

i checked a wiki page, telling me to recompile my dsdt... but i was "unsuccessful", because of these warnings...

> steff@skywalker:~$ iasl -sa dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl 4841: Method (RVLT, 1, NotSerialized)
Warning 1086 - ^ Not all control paths return a value (RVLT)

dsdt.dsl 4974: Method (RTMP, 1, NotSerialized)
Warning 1086 - ^ Not all control paths return a value (RTMP)

dsdt.dsl 5182: Method (OCOP, 1, NotSerialized)
Warning 1086 - ^ Not all control paths return a value (OCOP)

dsdt.dsl 5974: Store (SGFD (0x01), Local3)
Warning 1091 - ^ Called method may not always return a value

dsdt.dsl 5992: Store (SGFD (0x02), Local3)
Warning 1091 - ^ Called method may not always return a value

dsdt.dsl 6010: Store (SGFD (0x03), Local3)
Warning 1091 - ^ Called method may not always return a value

dsdt.dsl 6028: Store (SGFD (0x04), Local3)
Warning 1091 - ^ Called method may not always return a value

dsdt.dsl 6046: Store (SGFD (0x05), Local3)
Warning 1091 - ^ Called method may not always return a value

dsdt.dsl 6063: Method (SGFD, 1, NotSerialized)
Warning 1086 - ^ Not all control paths return a value (SGFD)

ASL Input: dsdt.dsl - 9430 lines, 289592 bytes, 3962 keywords
AML Output: dsdt.aml - 31289 bytes 1108 named objects 2854 executable opcodes

Compilation complete. 0 Errors, 9 Warnings, 0 Remarks, 1262 Optimizations 

i found nothing about this on the internet (correct me if i am wrong...)

other questions: where is that dsdt located (where on the hardware), does it come with the bios?

---

