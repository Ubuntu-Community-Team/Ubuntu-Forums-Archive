---
title: "lost dual core after edgy update"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by william_nbg on 2007-01-04
I updated to Edgy the other day and I have lost my dual core.

Here is my 'cpuinfo'

william@lord:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4034.43

________________________________________________

cpu 0 is showing up but not 1. I running the i386 kernel and can't even find the K7 kernel for this version in the repos.

Any ideas

---

### Post by xelink on 2007-01-04
download and install the k7 or 686 kernal.

---

### Post by teaker1s on 2007-01-04
[http://ubuntuforums.org/showthread.php?t=85917]("http://ubuntuforums.org/showthread.php?t=85917")

386i is x86 based single core kernel

---

### Post by william_nbg on 2007-01-05
I tried that, but is says I already have it, though it's not showing up in my grub.

william@lord:~$ sudo apt-get install linux-k7-smp
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-k7-smp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by MetalMusicAddict on 2007-01-05
Grab the linux-image-generic package. It should install the -generic kernel with SMP support.

---

### Post by william_nbg on 2007-01-05
I can't boot into the generic kernel - get a tty erro message.

But I realized the K7 kernel is installed, but not showing up in the grub menu - anyone have an idea??

---

### Post by william_nbg on 2007-01-05
Bump!!

This is a stange problem and I still haven't had any luck figuring it out. 

My amd dual core worked fine in Dapper (K7 smp kernel), but after upgrading to Edgy I'm stuck on single core. The K7 kernels don't show up in Grub and the generic kernel won't boot.

Maybe it's time to do a fresh install - I'm on the same install since Hoary. A good chance to clean up a lot of old stuff lying around on the old drives.

---

