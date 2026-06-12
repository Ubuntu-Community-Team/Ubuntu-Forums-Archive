---
title: "How ubuntu decide SMP should be enabled or not?"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by hzpeterchen on 2009-03-22
Hi all,

My CPU is AMD Sempron 2800+:
[http://en.wikipedia.org/wiki/List_of_AMD_Sempron_microprocessors#.22Palermo.22_.28Socket_754.2C_D0.2C_E3_.26_E6.2C_90_nm.29](http://en.wikipedia.org/wiki/List_of_AMD_Sempron_microprocessors#.22Palermo.22_.28Socket_754.2C_D0.2C_E3_.26_E6.2C_90_nm.29)

It sounds a single-core cpu, as I haven't find it at AMD cpu lists which
support SMP:
[http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)

My desktop uses ubuntu8.04, and I find it enable CONFIG_SMP
at /boot/config-2.6.24-24-generic.
My cpuinfo is:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 28
model name      : AMD Sempron(tm) Processor 2800+
stepping        : 0
cpu MHz         : 1607.322
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm
3dnowext 3dnow up lahf_lm ts ttp
bogomips        : 3216.87
clflush size    : 64

ps results:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3   2844  1688 ?        Ss   12:55
0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   12:55   0:00
[kthreadd]
root         3  0.0  0.0      0     0 ?        S<   12:55   0:00
[migration/0]
root         4  0.0  0.0      0     0 ?        S<   12:55   0:00
[ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   12:55   0:00
[watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   12:55   0:00
[events/0]
root         7  0.0  0.0      0     0 ?        S<   12:55   0:00
[khelper]
root        41  0.0  0.0      0     0 ?        S<   12:55   0:00
[kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   12:55   0:00
[kacpid]
root        45  0.0  0.0      0     0 ?        S<   12:55   0:00
[kacpi_notify]
root       150  0.0  0.0      0     0 ?        S<   12:55   0:00
[kseriod]
root       188  0.0  0.0      0     0 ?        S    12:55   0:00
[pdflush]
root       189  0.0  0.0      0     0 ?        S    12:55   0:00
[pdflush]
root       190  0.0  0.0      0     0 ?        S<   12:55   0:00
[kswapd0]
root       231  0.0  0.0      0     0 ?        S<   12:55   0:00 [aio/0]
root      1552  0.0  0.0      0     0 ?        S<   12:55   0:00
[ksuspend_usbd]
root      1558  0.0  0.0      0     0 ?        S<   12:55   0:00 [khubd]
root      1578  0.0  0.0      0     0 ?        S<   12:55   0:01 [ata/0]
root      1581  0.0  0.0      0     0 ?        S<   12:55   0:00
[ata_aux]
root      2318  0.0  0.0      0     0 ?        S<   12:55   0:00
[scsi_eh_0]
root      2319  0.0  0.0      0     0 ?        S<   12:55   0:01
[scsi_eh_1]
root      2349  0.0  0.0      0     0 ?        S<   12:55   0:00
[scsi_eh_2]
root      2351  0.0  0.0      0     0 ?        S<   12:55   0:00
[scsi_eh_3]
root      2638  0.0  0.0      0     0 ?        S<   12:55   0:00
[kjournald]
root      2839  0.0  0.1   2412   956 ?        S<s  12:55
0:00 /sbin/udevd --daemon
root      3320  0.0  0.0      0     0 ?        S<   12:56   0:00
[kpsmoused]
root      4343  0.0  0.0      0     0 ?        S<   12:56   0:00
[kjournald]
root      4344  0.0  0.0      0     0 ?        S<   12:56   0:00
[kjournald]
root      4636  0.0  0.0   1716   512 tty4     Ss+  12:56
0:00 /sbin/getty 38400 tty4
......


I have three questions:

1. How ubuntu decide SMP should be enabled or not?
2. Does SMP technology can be only used at Dual-core processor, or only
Dual-core processor can get benefit from SMP technology?

3. If mine cpu is single-core and I enabled SMP, which will happen?


Thank you
Peter Chen

---

