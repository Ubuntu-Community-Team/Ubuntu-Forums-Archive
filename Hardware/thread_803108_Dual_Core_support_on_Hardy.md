---
title: "Dual Core support on Hardy"
date: 2008-05-22
forum: Hardware
---

### Post by abreiner on 2008-05-22
I have an AMD Athlon(tm) X2 Dual Core Processor BE-2350, however my system is only using one core.

When I run

mpstat -P ALL

I see that the first processor is being used, but the second processor is all zeros.  The kernel that I have is Linux 2.6.24-16-generic.  Do I really need to install the 64-bit kernel to use both cores?

Thanks for you help.

Andy B.

---

### Post by EXCiD3 on 2008-05-22
> **abreiner said:**
> I have an AMD Athlon(tm) X2 Dual Core Processor BE-2350, however my system is only using one core.

When I run

mpstat -P ALL

I see that the first processor is being used, but the second processor is all zeros.  The kernel that I have is Linux 2.6.24-16-generic.  Do I really need to install the 64-bit kernel to use both cores?

Thanks for you help.

Andy B.

You shouldnt have to install 64 bit for dual core support. My Intel Core 2 Duo uses both and im running 32 bit. I have more repositories enabled so i am running 2.6.24-17 kernel, but it has always used both cores of mine since I started with Feisty. I'm not sure what is going on here, but ill do some searching and see what i can find.

---

### Post by abreiner on 2008-05-23
In case it helps here is the output from "cat /proc/cpuinfo"

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) X2 Dual Core Processor BE-2350
stepping        : 2
cpu MHz         : 2100.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 4335.89
clflush size    : 64

And the output from "mpstat -P ALL"

Linux 2.6.24-16-generic (snares)        05/23/2008

12:54:02 AM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
12:54:02 AM  all   20.27    1.48   10.07   39.22    0.10    0.14    0.00   28.73    241.17
12:54:02 AM    0   20.27    1.48   10.07   39.22    0.10    0.14    0.00   28.73    241.17
12:54:02 AM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00


Thanks for any help that you can give.

Andy B.

---

### Post by sdennie on 2008-05-23
I've not used AMD CPUs before but, one thing you could try would be to run "dmesg | more" in a terminal and scroll through it and look for anything suspicious (it's going to be a bunch of incomprehensible stuff but, the information you are probably going to find useful is likely to be towards the top).

---

### Post by General Specific on 2008-05-23
Ubuntu 8.04 LTS uses both processors on my Gateway Laptop.  AMD Turion 64x2

---

### Post by achi69 on 2008-05-23
I had the same problem last December with a BE- cpu (don't remember the number): only one core seen.

I went to the motherboard manufacturer (GA-M61P-S3, Gigabyte) web site to check the bios version, the BE CPUs support needed a more recent bios. After flashing 2 cores became visible.

Hope this helps,
   Achille

---

### Post by abreiner on 2008-05-23
dmesg had the following:

---------------------------------------------------------------
CPU0: AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 02
SMP alternatives: switching to SMP code
Booting processor 1/1 eip 3000
Not responding.
Inquiring remote APIC #1...
... APIC #1 ID: 1000000
... APIC #1 VERSION: 80050010
... APIC #1 SPIV: ff
CPU #1 not responding - cannot use it.
Total of 1 processors activated (4333.71 BogoMIPS).
---------------------------------------------------------------

So Hi-Ho Hi-Ho it's off to upgrade the BIOS I go.

I really hate upgrading the BIOS.

Thanks for everyone's help and I will let you know how it goes.

Andy B.

---

### Post by bravo331 on 2008-05-24
I have amd athalon 64 x2 processor. Can I run 32bit Ubuntu on an amd 64bit processor? If so, which version of Ubuntu do I install?

---

### Post by sdennie on 2008-05-24
Yes, you can run 32bit Ubuntu with that processor without any problems.

---

### Post by exomondo on 2008-05-24
You shouldnt have to install the 64bit kernel to enable multi-processors. There used to be a specific SMP (symmetric multiprocessing) kernel but I think that has disappeared now.

How many CPUs do you see under the system monitor?

> **bravo331 said:**
> I have amd athalon 64 x2 processor. Can I run 32bit Ubuntu on an amd 64bit processor? If so, which version of Ubuntu do I install?

If you have a 64bit processor you might as well run a 64bit OS.

---

### Post by abreiner on 2008-05-24
I am convinced there is a gremlin living in my computer.  I did the normal update that ubuntu gave me, I think there were 22 security updates today.  That is the only thing  I did and now both cores are working.

I went to "System Monitor" and it said there were two and gave me the usage of both.  I then went to the command line and issued "mpstat -P ALL" and now I get 

Linux 2.6.24-16-generic (snares)        05/24/2008

09:33:35 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
09:33:35 PM  all    8.60    0.69    3.36    3.80    0.02    0.03    0.00   83.49    117.00
09:33:35 PM    0    7.71    0.37    3.05    1.65    0.00    0.00    0.00   87.21      0.36
09:33:35 PM    1    9.46    1.00    3.65    5.87    0.05    0.06    0.00   79.91    116.64
09:33:35 PM    2    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

I have no idea why there is a CPU 2, it is only a dual core.  I then went to dmesg and I see

CPU0: AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 02
SMP alternatives: switching to SMP code
Booting processor 1/1 eip 3000
Initializing CPU#1
Calibrating delay using timer specific routine.. 4189.52 BogoMIPS (lpj=8379058)
CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 1(2) -> Core 1
CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
CPU1: AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 02
Total of 2 processors activated (8523.64 BogoMIPS).

Thanks for everyone's help.

Andy B.

---

### Post by abreiner on 2008-05-24
Also, I don't use the 64-bit version of Ubuntu because back in the day I had problem with firefox and plugins.  I know it has probably gotten better, however I subscribe to the old adage "if it's not broke don't fix it".  The 32-bit works for me.

Andy B.

---

