---
title: "Dual-core support: what's required, how to confirm it?"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by mattengland on 2006-12-31
Dual-core support: what's required, how to confirm it?

I'm running Dapper/6.06.1 and trying to get said system to enable/see/leverage the dual-core processor in my new PC.  Details here:

[http://www.linuxquestions.org/questions/showthread.php?t=515057](http://www.linuxquestions.org/questions/showthread.php?t=515057)

Thanks for any help, and Happy New Year!
-Matt

---

### Post by dshan on 2006-12-31
An SMP kernel comes std with Ubuntu server, for desktop (6.06 anyway) you need to [**install**]("https://wiki.ubuntu.com/auto-smp-support?highlight=%28multi-processor%29%7C%28smp%29") the smp kernel which it appears from your other post you are already doing, so you should be fine.

---

### Post by mattengland on 2006-12-31
> **dshan said:**
> An SMP kernel comes std with Ubuntu server, for desktop (6.06 anyway) you need to [**install**]("https://wiki.ubuntu.com/auto-smp-support?highlight=%28multi-processor%29%7C%28smp%29") the smp kernel which it appears from your other post you are already doing, so you should be fine.

Yeah, thanks for the tip, and I appear to have dual-core support/visibility with my rebuilt 2.6.18.6 kernel.

What I still don't know:  is 2.6.18.x required for this support?  This is still rather unclear to me.  Is 'linux-686-smp' package in pre-2.6.18 kernels supposed to supprot dual core?  Or something else?

Even thought I appear to have the stuff working, I'd like to get further understanding per hte above questions for future sysadmin purposes.

-Matt

---

### Post by dshan on 2006-12-31
Here's the best info on it I can find:

[http://www.ubuntuforums.org/showthread.php?t=300308&highlight=smp+multi-processor](http://www.ubuntuforums.org/showthread.php?t=300308&highlight=smp+multi-processor)

You're right, it seems to be very poorly documented.

---

### Post by mattengland on 2006-12-31
> **dshan said:**
> Here's the best info on it I can find:

[http://www.ubuntuforums.org/showthread.php?t=300308&highlight=smp+multi-processor](http://www.ubuntuforums.org/showthread.php?t=300308&highlight=smp+multi-processor)

You're right, it seems to be very poorly documented.

I've seen several different forum posts, wiki pages, and other references, all with similar ambiguity.

It seems pretty clear to me that the facts on these dual-core matters are rather unclear, across the board.  It would be great if we could eventually document some agreed-upon set of detalis outlining all these issues/configurations/dependencies, etc.

Thanks for any help,
-Matt

---

### Post by wilberfan on 2006-12-31
I've JUST discovered that my AMD Athlon 64x2 4400+ is only running on one processor (!)   And, yes, it's VERY confusing to try and learn what I need to do to get a proper kernel installed!

:-k

[Edit]  Here's what I just learned:   I already HAD the Edgy "generic" kernel installed--but it was the SECOND one listed in my GRUB menu list!   When I boot into that kernel, GKrellM confirms (?) that I have TWO processors detected and running...  :-D    And my system is MUCH faster now!

---

### Post by PseudoRandom on 2006-12-31
To check for SMP support:

Look in /boot: there are a series of files there for each kernel that you can select at boot time. The config-* files contains a record of each kernel's options, so grep it for the string SMP.

My /boot directory looks like this (only one kernel to choose from):

steve@SLM-T60:/boot$ ls -l
total 8088
-rw-r--r-- 1 root root  285721 2006-12-05 17:47 abi-2.6.17-10-generic
-rw-r--r-- 1 root root   74707 2006-12-05 16:20 config-2.6.17-10-generic
drwxr-xr-x 2 root root    4096 2006-12-31 17:19 grub
-rw-r--r-- 1 root root 5411132 2006-12-14 10:27 initrd.img-2.6.17-10-generic
-rw-r--r-- 1 root root   94600 2006-10-20 07:44 memtest86+.bin
-rw-r--r-- 1 root root  728778 2006-12-05 17:47 System.map-2.6.17-10-generic
-rw-r--r-- 1 root root 1636700 2006-12-05 17:47 vmlinuz-2.6.17-10-generic

And I confirm SMP support like this:

steve@SLM-T60:/boot$ grep SMP config-2.6.17-10-generic
CONFIG_SMP=y
# CONFIG_X86_BIGSMP is not set
CONFIG_SUSPEND_SMP=y
CONFIG_X86_FIND_SMP_CONFIG=y
CONFIG_X86_SMP=y

Note that these results are from the 2.6.17-10-generic kernel available via apt-get. **The 2.6.17-10-386 kernel does not have SMP enabled** .

---

### Post by meldroc on 2006-12-31
In Edgy, just make sure the generic kernel's installed, and it should Just Work.

On older versions of Ubuntu, look for a kernel with SMP support.  Once an SMP kernel's installed, it should Just Work.  Any 2.6.x kernel should work (as well as any 2.4.x kernel from an ancient distro - SMP's been in the Linux kernel for a long time now.)

How do you know it's Just Working?  Just go to a shell and type "cat /proc/cpuinfo"  If you have an SMP-enabled kernel, it will show info on two CPUs, for example:

```

meldroc@meldroc-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1995.028
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3995.33
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1995.028
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3990.36
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

meldroc@meldroc-laptop:~$

```

---

### Post by ravennium on 2007-01-08
Ok, I've been using ubuntu for a week and now kubuntu for two days.
Yes I'm a FORMER windows user ](*,) 

Anyway about those dual core processors
Am I now using both cores (I think I am, if I have understood anything):

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 1005.166
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mm
x fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
bogomips        : 2013.04
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 1005.166
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mm                                                            x fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
bogomips        : 2013.04
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc
```

But what about the speed? Shouldn't it be 2GHz? not 1GHz each processor?

---

### Post by art on 2007-01-08
ppp

---

### Post by ravennium on 2007-01-08
Okay little more google.... and it helped, it seems that this 1GHz is due to cpu automatic scaling... I did some loading it and it showed me 2GHz each core. 8)

---

### Post by glabouni on 2007-01-08
what is required for dual core support => a SMP enabled kernel (under edgy a linux-image-generic)

to check if your kernel is SMP enabled in a terminal type:
```
uname -a
```

my simple way to check if dual core support was working in my ubuntu edgy:

1- install [htop]("http://htop.sourceforge.net/") 

```
sudo apt-get install htop
```

2- run htop

- ALT+F2 to call the run application window
- type htop
- ALT+t to check the "run in terminal" box

3- count the number of cpus showing up. for my athlon x2 3800+ that would be 2 :D

another way would be reading /proc/cpuinfo :

```
cat /proc/cpuinfo
```

---

