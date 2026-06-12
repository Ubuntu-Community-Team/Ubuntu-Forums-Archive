---
title: "Ubuntu ARM Kernel Panic"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by welchsteven on 2009-07-01
I need some help debuging a kernel panic. Here is the situation. First some background. I am working on a Mini2440 ARM board. The Processor is a Samsung S3C2440. I has an ARM920T core. There is a QEMU and kernel port for the Board. I have had no problems building the Ubuntu rootfs and installing it onto an SD card. Also the system works fine with the Mini2440 kernel and Ubuntu rootfs in qemu. When I move the Ubuntu rootfs to the actual hardware then the problems begin. I get up to the point of running INIT and the kernel panics. If I use an Emdebian rootfs and the same kernel the system boots on hardware with no problems. So I am not sure if the problem is with the Ubuntu-ARM rootfs or the Mini2440 Kernel. I have not done much kernel debugging and I am completely stuck at this point. Any help or pointer would be appreciated. Thanks in advance.

 
Kernel panic - not syncing: Attempted to kill init!
[<c002d774>] (unwind_backtrace+0x0/0xdc) from [<c02b8cec>] (panic+0x40/0x118)
[<c02b8cec>] (panic+0x40/0x118) from [<c003d060>] (do_exit+0x64/0x578)
[<c003d060>] (do_exit+0x64/0x578) from [<c003d5fc>] (do_group_exit+0x88/0xbc)
[<c003d5fc>] (do_group_exit+0x88/0xbc) from [<c00464bc>] (get_signal_to_deliver+0x2ec/0x324)
[<c00464bc>] (get_signal_to_deliver+0x2ec/0x324) from [<c002af88>] (do_signal+0x68/0x4d4)
[<c002af88>] (do_signal+0x68/0x4d4) from [<c0028eac>] (work_pending+0x1c/0x20)

---

### Post by AshmanEck on 2009-07-15
I've been thinking about a mini2440/Ubuntu combo myself.  The mini2440 seems to be worlds better (and cheaper) than the beagleboard that everyone seems to be playing with.
 
Anyway, from what I can tell, the patches for the mini2440 were included in the linux kernel version 2.6.31 while Ubuntu 9.04 looks to be currently based upon 2.6.28.
 
It may just be a matter of waiting until Ubuntu catches up with the kernel versions that include the support for the mini2440, but I'm just guessing.
 
It's been years since I've looked at Linux, but I've been contemplating some embedded PC projects so I guess I'll have to bite the bullet and get re-educated...

---

### Post by welchsteven on 2009-07-15
While I was driving home from another city at about 4:30am I realized the problem. There is no problem with the kernel or with Ubuntu ARM port. The problem is that the Mini2440 which is based on the S3C440 has an ARM920T core. This core only supports the ARMv4 Instruction Set. The new Ubuntu ARM port is designed for the ARMv5 Instruction Set. After some digging in ARM's website I was able to verify this and that every ARM core that is still "supported" from the ARM926EJ-S to the Cortex-A9 is compatible with the ARMv5 Instruction set. This is some thing I should have figured out long ago. So if you are thinking about running Ubuntu on a Mini2440 don't it wont work. Unless you want to compile all of the packages from source. 

As far as the Mini2440 vs Beagleboard. In the performance category there is no contest the Beagleboard wins hands down. It has much more flash and RAM. The processing power of the CPU is far greater than that of the Mini2440. Also the beagle board has a GPU with OpenGL support so it has graphics acceleration and there is a DSP core for signal processing. The downside is the BeagleBoard is not really designed for embedded applications. No connections for LCD support and of course no LCD. Bottom line is if you are looking for power and Ubuntu Compatibility go with the BeagleBoard. If you want cheap and an LCD go with the Mini2440.

---

