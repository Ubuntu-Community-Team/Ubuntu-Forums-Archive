---
title: "CPU performance"
date: 2008-07-07
forum: Hardware
---

### Post by alican timur on 2008-07-07
I'm running hardy heron 64bit with intel q6600 quad core and I'm not quite sure that I'm getting the best of it. I'm a newbie and not really sure if I've managed to install all the appropriate drivers, if that's got anything to do with it.

Is there some way to check this?

---

### Post by sdennie on 2008-07-07
You shouldn't need to install any drivers to make a quad core to work.  Try:

```

lshw -short -C processor

```

You should see your CPU with 4 logical CPUs.

---

### Post by DonnieP on 2008-07-07
> **alican timur said:**
> I'm running hardy heron 64bit with intel q6600 quad core and I'm not quite sure that I'm getting the best of it. I'm a newbie and not really sure if I've managed to install all the appropriate drivers, if that's got anything to do with it.

Is there some way to check this?
You might want to give the CPU Frequency Scaling Monitor Panel Applet a try - you can set up one for each processor.

---

### Post by tamoneya on 2008-07-07
vors command should be preceeded by sudo and it is a little better to remove the "-short" in my opinion:```
sudo lshw -C processor
```

I have  a Q6600 and here is my output:```
tamoneya@ubuntu0:~$ sudo lshw -C processor
  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.15.7
       serial: To Be Filled By O.E.M.
       slot: LGA 775
       size: 2394MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 266MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
  *-cpu:1 UNCLAIMED
       physical id: 1
       bus info: cpu@1
       version: 6.15.7
  *-cpu:2 UNCLAIMED
       physical id: 2
       bus info: cpu@2
       version: 6.15.7

```

---

### Post by alican timur on 2008-07-08
i've got this. is this right? Seems different than yours.

```

  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM)2 Quad CPU
       slot: Socket 775
       size: 2400MHz
       capacity: 4GHz
       width: 64 bits
       clock: 266MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

```

just this. no continuation.no cpu2 part.

and for the -short version, i get

```

H/W path         Device      Class       Description
====================================================
/0/4                         processor   Intel(R) Core(TM)2 Quad CPU    Q6600  @

```

only this.

---

### Post by sdennie on 2008-07-08
What are the outputs of the following two commands:

```

grep processor /proc/cpuinfo

```

And:

```

uname -a

```

---

### Post by alican timur on 2008-07-08
```

alican@Alican-HQ:~$ grep processor /proc/cpuinfo
processor	: 0
processor	: 1
processor	: 2
processor	: 3

```

and
```

Linux Alican-HQ 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

```

is the second one for determining the kernel version? if so, is there any updates/upgrades i should make?

---

### Post by tamoneya on 2008-07-08
looks fine to me.  You should be all set.

---

### Post by alican timur on 2008-07-08
thanks a million. is there a way to test it?

---

### Post by tamoneya on 2008-07-08
run super PI as detailed in this thread and then compare to others with the same processor.
[http://ubuntuforums.org/showthread.php?t=60264](http://ubuntuforums.org/showthread.php?t=60264)

It is best that you start near the end of the thread to look for similar processors since it is a relatively old thread.

---

### Post by stchman on 2008-07-08
> **alican timur said:**
> I'm running hardy heron 64bit with intel q6600 quad core and I'm not quite sure that I'm getting the best of it. I'm a newbie and not really sure if I've managed to install all the appropriate drivers, if that's got anything to do with it.

Is there some way to check this?

Ubuntu and Linux in general support multi core processors OOB.  I believe the -generic kernel can support 32 physical processors if I am not mistaken (please other forum member correct me if I am wrong).  No drivers are needed.  What kind of mobo do you have?

---

### Post by alican timur on 2008-07-10
What do you mean by mobo?

---

### Post by alican timur on 2008-07-10
> **tamoneya said:**
> run super PI as detailed in this thread and then compare to others with the same processor.
[http://ubuntuforums.org/showthread.php?t=60264](http://ubuntuforums.org/showthread.php?t=60264)

It is best that you start near the end of the thread to look for similar processors since it is a relatively old thread.

It's better for the time reported to be shorter right? Because that it's measuring how fast the cpu is processing?

My results are like this.

```
 ------ Started super_pi run : Thu Jul 10 19:52:12 EEST 2008
 Start of PI calculation up to 1048576 decimal digits
 End of initialization. Time=       0.360 Sec.
 I= 1 L=       0        Time=       1.040 Sec.
 I= 2 L=       0        Time=       1.168 Sec.
 I= 3 L=       1        Time=       1.172 Sec.
 I= 4 L=       2        Time=       1.184 Sec.
 I= 5 L=       5        Time=       1.176 Sec.
 I= 6 L=      10        Time=       1.180 Sec.
 I= 7 L=      21        Time=       1.180 Sec.
 I= 8 L=      43        Time=       1.176 Sec.
 I= 9 L=      87        Time=       1.168 Sec.
 I=10 L=     174        Time=       1.176 Sec.
 I=11 L=     349        Time=       1.176 Sec.
 I=12 L=     698        Time=       1.180 Sec.
 I=13 L=    1396        Time=       1.180 Sec.
 I=14 L=    2794        Time=       1.176 Sec.
 I=15 L=    5588        Time=       1.168 Sec.
 I=16 L=   11176        Time=       1.156 Sec.
 I=17 L=   22353        Time=       1.140 Sec.
 I=18 L=   44707        Time=       1.100 Sec.
 I=19 L=   89415        Time=       1.016 Sec.
 End of main loop
 End of calculation.    Time=      23.165 Sec.
 End of data output.    Time=       0.160 Sec.
 Total calculation(I/O) time=      23.325(       0.600) Sec.
 ------ Ended super_pi run : Thu Jul 10 19:52:35 EEST 2008

```

---

### Post by sdennie on 2008-07-10
> **stchman said:**
> I believe the -generic kernel can support 32 physical processors if I am not mistaken (please other forum member correct me if I am wrong).

Suprisingly, the -generic kernel only supports up to 8 cores/threads/cpus:

```

$ grep CONFIG_NR_CPUS /boot/config-2.6.24-19-generic  
CONFIG_NR_CPUS=8

```

More surprisingly the -server kernel only supports up to 8 as well:

```

$ grep CONFIG_NR_CPUS /boot/config-2.6.24-19-server 
CONFIG_NR_CPUS=8

```

---

