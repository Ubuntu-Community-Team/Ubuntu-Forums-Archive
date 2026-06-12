---
title: "Ram upgrade on ubuntu 8.10"
date: 2009-05-01
forum: Hardware
---

### Post by Chetan26 on 2009-05-01
Hi,
    Iam currently  on Ubuntu 8.10  with AMD ATHLON LE-1600 1 Ghz Processror.  with 1 GB(DDR2 800) RAM. I have  recently  tried to upgrade  my RAM to 4GB (2 X 2GB DDR2 800). The RAM is  correctly installed  but my
Ubuntu recognises only  2.7 GB of RAM when I shud have  4 GB. Could  you please  tell me why there is such deviation. Do i need to change any BIOS settings  or Is it related to OS? I guess mine is a 64 bit OS.

Please provide some Help.


Many Thanks
Chetan

---

### Post by Barry Carroll on 2009-05-01
What does ```
uname -m
``` say?  My guess would be that you possibly have a 32 bit Ubuntu install and some shared graphics memory.

---

### Post by Chetan26 on 2009-05-01
It  says  i686 ..I guess its 32  bit  is it so?

---

### Post by Barry Carroll on 2009-05-01
Yes you have 32-bit.  My guess is that you also have integrated graphics that are stealing some of your main RAM.  You would get a lot more usable RAM by going to 64-bit.

---

### Post by Chetan26 on 2009-05-01
How can I make it 64 bit ? Is it due to ATHLON 1600 Processor?

---

### Post by zzHanks on 2009-05-01
Yes, you would have to buy a new processor.

---

### Post by Barry Carroll on 2009-05-01
Are you sure that you have an Athlon LE-1600?  According to the specs on AMD's site it is 64-bit capable so you wouldn't have to buy a new processor but it's supposed to be clocked at 2.2GHz

[http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=81](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=81)

---

### Post by Chetan26 on 2009-05-01
Mine is  a ATHLON LE 1600 1 GHZ processor.  How  can I make it 2.2?
Will  it  work if we make changes  to some bios?
Please suggest  a best way out?

---

### Post by Chetan26 on 2009-05-01
do I need to change my Ubuntu either?

---

### Post by Barry Carroll on 2009-05-01
Run ```
cat /proc/cpuinfo
``` and post the output back here, should give a better indication of your CPU's specs.

---

### Post by Chetan26 on 2009-05-01
i686
chetan@ubuntu:~/Desktop/eclipse$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 95
model name	: AMD Athlon(tm) Processor LE-1600
stepping	: 3
cpu MHz		: 1000.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy
bogomips	: 2009.08
clflush size	: 64
power management: ts fid vid ttp tm stc

---

### Post by Chetan26 on 2009-05-01
i686
chetan@ubuntu:~/Desktop/eclipse$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 95
model name	: AMD Athlon(tm) Processor LE-1600
stepping	: 3
cpu MHz		: 1000.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy
bogomips	: 2009.08
clflush size	: 64
power management: ts fid vid ttp tm stc

---

### Post by Eviljim on 2009-05-01
> **Chetan26 said:**
> i686
chetan@ubuntu:~/Desktop/eclipse$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 95
model name	: AMD Athlon(tm) Processor LE-1600
stepping	: 3
cpu MHz		: 1000.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm svm extapic cr8_legacy
bogomips	: 2009.08
clflush size	: 64
power management: ts fid vid ttp tm stc

If your CPU is the Athlon 64 LE1600 model (AM2 socket), your clock multiplier should be 11x and the hyper-transport should be 1000MHz in your bios.

---

### Post by Chetan26 on 2009-05-01
Thnx has  UBuntu 8.10  anything do with this?

If I make the changes  to BIos would I be able to get the RAM fully?

---

### Post by Eviljim on 2009-05-01
No, Ubuntu is not the issue, nor would Windows (if you had it).

Your motherboard was probably set to a factory default setting when it was made. When the processor is installed, you are meant to change both the multiplier and the HyperTransport according to settings given in the processor manual.

The bios can reset these settings from time to time (i.e. CMOS battery removed, or an overclock was not stable).

Because you are using a 32bit OS (be it ubuntu or Windows) you can really only access the first 3GB minus any memory requirements for an onboard graphics card (i.e. 256MB).

You would need a 64bit OS to be able to fully access the RAM.
Just grab a copy of the Ubuntu 64Bit live cd to try this out for yourself.

---

