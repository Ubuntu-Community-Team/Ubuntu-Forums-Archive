---
title: "How can I know if my PC's processor can run 64-bit Linux?"
date: 2011-05-16
forum: Hardware
---

### Post by Uewd on 2011-05-16
I want to know if my PC's processor can run 64-bit Linux. How can I do this?
My PC's processor is Intel Core i3 @ 2.53 GHz
Please help.
Thanks.
Uewd.

---

### Post by arvevans on 2011-05-16
Open a terminal screen.
Enter "sudo lshw", it will ask for password.
Scan the resulting hardware listing to see if your CPU and support system is shown as 32 bit or 64 bit.

---

### Post by slooksterpsv on 2011-05-16
I would imagine the Core i3 would be 64-bit. All of AMD's CPUs besides a few of the Semprons, are 64-bit. If that's not, I would be completely surprised.

EDIT:

Yes that's a 64-bit cpu

---

### Post by walt.smith1960 on 2011-05-16
You don't* have* to run lshw with sudo although it's recommended.  I got this without logging out and back in as a sudo user:

description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 4021MiB
     *-cpu
          product: AMD Athlon(tm) II X2 240 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          version: 15.6.2
          size: 800MHz
          capacity: 800MHz
          **width: 64 bits**

---

### Post by akand074 on 2011-05-16
All i3 processors support 64 bit. This is true for the i5 and i7 as well.

---

### Post by Uewd on 2011-05-20
Thank you all for replying. Which Linux OS is better, 32-bit or 64-bit?

---

### Post by slooksterpsv on 2011-05-21
> **Uewd said:**
> Thank you all for replying. Which Linux OS is better, 32-bit or 64-bit?

Regular normal users will do fine with 32-bit, but if you have 4+ GB of RAM I recommend 64-bit, especially if you do any sort of virtualization or that. 4GB of RAM will be seen as like 3.75 or 3.25 in a 32-bit OS, while in 64-bit it can see more than 4GB of RAM.

---

### Post by cbowman57 on 2011-05-21
> **slooksterpsv said:**
> Regular normal users will do fine with 32-bit, but if you have 4+ GB of RAM I recommend 64-bit, especially if you do any sort of virtualization or that. 4GB of RAM will be seen as like 3.75 or 3.25 in a 32-bit OS, while in 64-bit it can see more than 4GB of RAM.

+1, when I compare them it 'feels' like the 32-bit is faster & has a slightly smaller memory footprint.

YMMV.

---

### Post by Blasphemist on 2011-05-21
The default 32 bit kernel for natty seems to be the pae kernel and it seems to be causing video issues in some configurations. The pae kernel allows 32 bit cpu's to use 4 GB or more memory. That is the case for some 32 bit cpu's at least. 
> Linux
The Linux kernel includes full PAE mode support starting with version 2.3.23,[6] enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE. As of 2009,[7] some common Linux distributions have started to use a PAE-enabled kernel as the distribution-specific default[7] because it adds the NX bit.
The above is from [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

I believe the 64 bit kernel is faster and has smaller memory footprint but you can find people on both sides of that as shown already in this thread. I run the 64 bit on my fairly old Toshiba Sattelite L505-S6946.

---

### Post by cbowman57 on 2011-05-21
> **Blasphemist said:**
> 
I believe the 64 bit kernel is faster and has smaller memory footprint but you can find people on both sides of that as shown already in this thread. I run the 64 bit on my fairly old Toshiba Sattelite L505-S6946.

Might actually be due to slight variations between machines.  All I can do is comment on what I've noticed but I have no doubt that others have had a different experience. :)

---

### Post by Uewd on 2011-06-03
Do you recommend me to install 64-bit Ubuntu if I have 2GB RAM? What are your thoughts?

---

### Post by slooksterpsv on 2011-06-03
Only if any of the following are true:

[LIST]
[*]You need 64-bit apps (Virtualization comes to mind e.g. running 
[*]You are going to upgrade your RAM to 4GB or more.
[*]It works better with your hardware.
[/LIST]

There's probably more but those are the basics I look at.

---

### Post by coffeecat on 2011-06-03
> **walt.smith1960 said:**
> You don't* have* to run lshw with sudo although it's recommended. 

What man lshw says about this is:

> lshw  must be run as super user or it will only report partial information.On my machine:

```
$ sudo lshw -C cpu
  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) II X4 640 Processor
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 4
       bus info: cpu@0
       version: AMD Athlon(tm) II X4 640 Processor
       serial: To Be Filled By O.E.M.
       slot: AM3
       size: 800MHz
       capacity: 3GHz
       width: 64 bits
       clock: 200MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
       configuration: cores=4 enabledcores=4
```And:

```
$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: AMD Athlon(tm) II X4 640 Processor
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: cpu@0
       size: 800MHz
       capacity: 800MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```Which certainly gives enough information for this particular enquiry, except it's got capacity (of this 3GHz CPU) wrong when not run with sudo. So that "output may be incomplete or inaccurate" message may be worth bearing in mind.

Another useful command is lscpu.

```
$ lscpu
Architecture:          x86_64
CPU op-mode(s):        64-bit
CPU(s):                4
Thread(s) per core:    1
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 5
Stepping:              3
CPU MHz:               800.000
Virtualisation:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
```

---

### Post by Uewd on 2011-06-06
> **slooksterpsv said:**
> Only if any of the following are true:

[LIST]
[*]You need 64-bit apps (Virtualization comes to mind e.g. running
[*]You are going to upgrade your RAM to 4GB or more.
[*]It works better with your hardware.
[/LIST]

There's probably more but those are the basics I look at.

You need 64-bit apps (Virtualization comes to mind): Yes I do some Virtualization.
You are going to upgrade your RAM to 4GB or more: Maybe.
It works better with your hardware                        : I have Windows 7 64-bit installed, do you think Ubuntu will work?

---

