---
title: "ASUS M5A97 R2.0, AMD FX-8350 and Ubuntu 12.04 = PROBLEM"
date: 2014-02-08
forum: Hardware
---

### Post by JohnnyS987 on 2014-02-08
I can only boot Ubuntu 12.04 on this system if I use "acpi=off" in the boot string, but then the kernel only seems to see 1 of the 8 cores in the CPU. I can't seem to find any other change that I can make to allow the system to boot with all the 8 cores enabled.

Note: The UEFI boot has been set to "other OS" in BIOS. No other changes have been made in BIOS from the defaults. In particular, SVM is "Enabled".

Does anyone have any ideas? I have put Win7 on this and all 8 cores are working, so it's not a hardware problem. It really is a pain when only 1 of 8 cores is working!

uname -a gives:

Linux js-ubuntu 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

cat /proc/cpuinfo give the following, which clearly shows that only one core is visible to the kernel:

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-8350 Eight-Core Processor           
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 0.000
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 16
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc up rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1
bogomips	: 3307.52
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

---

### Post by JohnnyS987 on 2014-02-09
More info:

If I disable all processor cores in the BIOS except the first one, I can boot without the "acpi=off" flag in my boot string. But if I have any more than one core enabled, I need "acpi=off" in the boot string or it locks up during boot with the message "CPU1:  Not responding".

Either way, "nproc" always reports "1" as the number of processors.

Any ideas?

---

### Post by JohnnyS987 on 2014-02-09
Well, foo. I fixed it, but it's weird.

So I have a USB keyboard, mouse and webcam that are plugged into the rear USB 2.0 ports, and a USB 2.0 hub that is also plugged into a rear USB 2.0 port. The USB 2.0 hub has a Griffin PowerMate, a USB headset and a USB game controller plugged into it. Here's the weird thing: IF the USB hub is unplugged during boot, THEN it will boot normally without the "acpi=off" switch, nproc reports 8 cores and VMWare Workstation will allow images with more than 1 processor configured to run. All of the BIOS settings are set to the defaults except the UEFI boot is set to "Other OS". All is well and the universe is unfolding as it should...

I got the idea from this post: [http://askubuntu.com/questions/261003/ubuntu-thinks-my-laptop-only-has-one-core](http://askubuntu.com/questions/261003/ubuntu-thinks-my-laptop-only-has-one-core) 

So the problem is solved, but the weirdness remains: Why would unplugging a USB 2.0 hub affect the number of CPU cores detected and used by the Linux kernel??

---

### Post by Yellow Pasque on 2014-02-09
Make sure you have latest BIOS. There are a bunch of "improve system stability" updates and one that says "Enhance compatibility with some USB devices."

---

### Post by JohnnyS987 on 2014-02-09
Thanks for your reply!

I did make sure I was on the latest BIOS, which is version 2201. So hopefully there will be another update sometime.

---

### Post by mörgæs on 2014-02-10
If the problem is solved please mark the thread so using 'thread tools'.

---

