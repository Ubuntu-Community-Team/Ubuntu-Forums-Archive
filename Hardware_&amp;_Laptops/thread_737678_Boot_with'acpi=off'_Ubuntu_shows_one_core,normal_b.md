---
title: "Boot with'acpi=off' Ubuntu shows one core,normal boot-kacpid process is eating 70%CPU"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by WebEyeX on 2008-03-27
Hi,
I am facing very strange problem.Ectually its started coming up from first day.At the time of installation i had to use 'acpi=no' boot parameter because without it system just got hang.Now if i boot normally 'kacpid' process is eating 60%-70% CPU and if i use 'acpi=off' boot parameter Ubuntu is showing only one core of my Dual core processer.

I know acpi is creating some problem.Here is the out put of 'dmesg | grep CPU' command

[ 0.000000] Initializing CPU#0
[ 35.402589] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[ 35.482968] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e49d 00000000 00000001
[ 35.483057] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 35.483119] CPU: L2 cache: 2048K
[ 35.483156] CPU: Physical Processor ID: 0
[ 35.483193] CPU: Processor Core ID: 0
[ 35.483230] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e49d 00000000 00000001
[ 35.783531] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[ 35.998415] Brought up 1 CPUs


As you can see it is showing and using only one core of Dual core processor...

How to solve this problem?I searched a lot about this but unable to find any solution.
My system specs are..
Intel Pentium D processor 3.0 Ghz
Intel 945GCNL motherboard
Windows XP + Ubuntu 7.10(Dual boot)

Thanks and Regards

---

