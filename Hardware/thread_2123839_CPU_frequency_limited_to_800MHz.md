---
title: "CPU frequency limited to 800MHz?"
date: 2013-03-09
forum: Hardware
---

### Post by Freek07 on 2013-03-09
fpufreqd doesn't rise frequency above 800MHz.
I will get physical access to the machine (to check bios) in few hours but it seems weird to me so here's the data:

CPU:
[INDENT]cat /proc/cpuinfo | grep 'model name'
model name      : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
model name      : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz[/INDENT]

Freq:
[INDENT]cat /proc/cpuinfo | grep 'MHz'
cpu MHz         : 800.000
cpu MHz         : 800.000[/INDENT]

governor in cpufreqd is performance but available states are only 600 and 800 MHz:
[INDENT]cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
800000 600000 [/INDENT]

[INDENT]cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq 
800000[/INDENT]

Dmidecode reports correct speed:
[INDENT]Processor Information
        Socket Designation: LGA 775
        Type: Central Processor
        Family: Core 2
        Manufacturer: Intel
        ID: F6 06 00 00 FF FB EB BF
        Signature: Type 0, Family 6, Model 15, Stepping 6
        Flags:
                FPU (Floating-point unit on-chip)
                VME (Virtual mode extension)
                DE (Debugging extension)
                PSE (Page size extension)
                TSC (Time stamp counter)
                MSR (Model specific registers)
                PAE (Physical address extension)
                MCE (Machine check exception)
                CX8 (CMPXCHG8 instruction supported)
                APIC (On-chip APIC hardware supported)
                SEP (Fast system call)
                MTRR (Memory type range registers)
                PGE (Page global enable)
                MCA (Machine check architecture)
                CMOV (Conditional move instruction supported)
                PAT (Page attribute table)
                PSE-36 (36-bit page size extension)
                CLFSH (CLFLUSH instruction supported)
                DS (Debug store)
                ACPI (ACPI supported)
                MMX (MMX technology supported)
                FXSR (FXSAVE and FXSTOR instructions supported)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                SS (Self-snoop)
                HTT (Multi-threading)
                TM (Thermal monitor supported)
                PBE (Pending break enabled)
        Version: Intel(R) Core(TM)2 CPU          6
        Voltage: 1.8 V
        External Clock: 1066 MHz
        Max Speed: 3000 MHz
**        Current Speed: 2130 MHz**
        Status: Populated, Enabled
        Upgrade: Slot 1
        L1 Cache Handle: 0x0005
        L2 Cache Handle: 0x0006[/INDENT]

any ideas why cpufreqd cannot see all the frequencies?

Kernel:
[INDENT]uname -a
Linux Media 3.2.0-3-686-pae #1 SMP Mon Jul 23 03:50:34 UTC 2012 i686 GNU/Linux[/INDENT]

---

### Post by carl4926 on 2013-03-09
Have you checked it under load, such as when rendering a video

---

### Post by Freek07 on 2013-03-09
Oh, sure, I forgot to note that CPU load was 100% when checking this...

---

### Post by carl4926 on 2013-03-09
Look at cpufrequtils
Google might help

---

### Post by Freek07 on 2013-03-09
It was bios setting "only allow 'foo' and 'bar' cpu states" under power saving.... can't remember setting this one... it's working now :-)

---

