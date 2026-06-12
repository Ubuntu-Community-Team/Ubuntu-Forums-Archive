---
title: "L3 CPU cache"
date: 2014-06-29
forum: Hardware
---

### Post by tm4ig on 2014-06-29
Hello!
On my computer  **lshw** and **dmidecode** shows that the L3 CPU cache is DISABLED.

**dmidecode**
```
[COLOR=#000000][FONT=Ubuntu Beta]Handle 0x0007, DMI type 7, 19 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Cache Information[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Socket Designation: L3-Cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Configuration: [/FONT][/COLOR][COLOR=red][FONT=Ubuntu Beta]Disabled[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta], Not Socketed, Level 3[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Operational Mode: Unknown[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Location: Internal[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Installed Size: 6144 kB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Maximum Size: 6144 kB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Supported SRAM Types:[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]      Other[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Installed SRAM Type: Other[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Speed: Unknown[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Error Correction Type: None[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   System Type: Unified[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Associativity: Other[/FONT][/COLOR]
```

**lshw**
```
[COLOR=#000000][FONT=Ubuntu Beta]*-cpu[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: &#1062;&#1055;&#1059;[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Intel Corp.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 4[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1089;&#1074;&#1077;&#1076;&#1077;&#1085;&#1080;&#1103; &#1086; &#1096;&#1080;&#1085;&#1077;: cpu@0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: To Be Filled By O.E.M.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1089;&#1083;&#1086;&#1090;: LGA1155[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 1600MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          capacity: 3800MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 100MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]          &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: cores=4 enabledcores=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        *-cache:0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: L1 &#1082;&#1101;&#1096;[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1089;&#1083;&#1086;&#1090;: L1-Cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 256KiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             capacity: 256KiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: internal write-back unified[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        *-cache:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: L2 &#1082;&#1101;&#1096;[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 6[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1089;&#1083;&#1086;&#1090;: L2-Cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 1MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             capacity: 1MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: internal varies unified[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        *-cache:2 [/FONT][/COLOR][COLOR=red][FONT=Ubuntu Beta]&#1042;&#1067;&#1050;&#1051;&#1070;&#1063;&#1045;&#1053;&#1054; (DISABLED)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: L3 &#1082;&#1101;&#1096;[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 7[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1089;&#1083;&#1086;&#1090;: L3-Cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1088;&#1072;&#1079;&#1084;&#1077;&#1088;: 6MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             capacity: 6MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]             &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: internal unified[/FONT][/COLOR]
```

**lscpu**
```
[COLOR=#000000][FONT=Ubuntu Beta]CPU op-mode(s):        32-bit, 64-bit
&#1055;&#1086;&#1088;&#1103;&#1076;&#1086;&#1082; &#1073;&#1072;&#1081;&#1090;&#1086;&#1074;:Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
&#1055;&#1086;&#1090;&#1086;&#1082;&#1086;&#1074; &#1085;&#1072; &#1103;&#1076;&#1088;&#1086;:1
&#1071;&#1076;&#1077;&#1088; &#1085;&#1072; &#1089;&#1086;&#1082;&#1077;&#1090;:4
&#1057;&#1086;&#1082;&#1077;&#1090;(&#1099;):        1
NUMA node(s):          1
Vendor ID:             GenuineIntel
&#1057;&#1077;&#1084;&#1077;&#1081;&#1089;&#1090;&#1074;&#1086; CPU:6
&#1052;&#1086;&#1076;&#1077;&#1083;&#1100;:          42
Stepping:              7
CPU &#1052;&#1043;&#1094;:            1600.000
BogoMIPS:              6600.16
&#1042;&#1080;&#1088;&#1090;&#1091;&#1072;&#1083;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;:VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0-3[/FONT][/COLOR]

```

But in Windows 7 aida64 banchmark shows

[http://itmages.ru/image/view/1749865/a8c3c7ce](http://itmages.ru/image/view/1749865/a8c3c7ce)
[http://itmages.ru/image/view/1749876/7e3a85ef](http://itmages.ru/image/view/1749876/7e3a85ef)

What's the problem?

---

### Post by gordintoronto on 2014-06-29
What version of Ubuntu? What kernel?

---

### Post by slooksterpsv on 2014-06-29
You could check your BIOS and see if it has an option to enable or disable it. From what I'm seeing from other people out there on the interwebs they've experienced the same issue and its a matter of waiting for upstream patches for the hardware.

---

### Post by tm4ig on 2014-06-30
> **gordintoronto said:**
> What version of Ubuntu? What kernel?

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
Linux sinx 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

In the BIOS there is no option to disable/enable cache


I think that this screenshot shows that the cache works
[http://itmages.ru/image/view/1749865/a8c3c7ce](http://itmages.ru/image/view/1749865/a8c3c7ce)

---

### Post by slonk on 2014-06-30
This is much more likely to be a problem with reading the hardware description bits than the cache actually being disabled.

---

