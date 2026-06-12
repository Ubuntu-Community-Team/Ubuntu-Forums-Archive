---
title: "Problem of cpu balancing"
date: 2014-11-07
forum: Hardware
---

### Post by pantale on 2014-11-07
Hi,

I don't know if it's the right place to post, but I have a problem since I reinstalled ubuntu 14.10.

I have no more load balancing available for my computer. I have Two 4 core CPU on my computer, but only one cpu is used.
Core 0 to 7 are detected but only 0 to 4 are used.

Everything was ok on my prevoius install Kubuntu 14.04.

Olivier

---

### Post by tgalati4 on 2014-11-07
What processor?

```
cat /proc/cpuinfo
```

Look through your log files for errors pertaining to your CPU.  Post only the helpful messages, not the entire log file.

```
more /var/log/syslog
```

---

### Post by pantale on 2014-11-07
Here are the syslog and the cpuinfo files.

Thank's alot for your consideration.

---

### Post by tgalati4 on 2014-11-07
So you have an 8-core Xeon E5620 running at 2.4 GHz.  I presume that this is a single CPU with 8 cores on one die?

You are running a 3.16 kernel.  All of your processors are initially detected by the kernel:

> Nov  7 11:56:58 pcpantale kernel: [    0.259943] x86: Booting SMP configuration:
Nov  7 11:56:58 pcpantale kernel: [    0.259946] .... node  #0, CPUs:        #1
Nov  7 11:56:58 pcpantale kernel: [    0.274060] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Nov  7 11:56:58 pcpantale kernel: [    0.274193]   #2  #3  #4  #5  #6  #7
Nov  7 11:56:58 pcpantale kernel: [    0.448196] x86: Booted up 1 node, 8 CPUs
Nov  7 11:56:58 pcpantale kernel: [    0.448201] smpboot: Total of 8 processors activated (**38304.20** BogoMIPS)


That's a lot of MIPS.

I presume that this is the actual processor in your machine:

> Nov  7 11:56:58 pcpantale kernel: [    0.151133] smpboot: CPU0: Intel(R) Xeon(R) CPU           E5620  @ 2.40GHz (fam: 06, model: 2c, stepping: 02)


I don't know how you would verify, other than either taking the heatsink off (which I don't recommend on a new machine) or checking the server build invoice.

I don't see any problems in your syslog.  It could be a power management scheme.  Shut down 4 cores if they are not being used.  Well, there is a way around that:

```
sudo apt-get install htop
htop
```

In another terminal:

```

sudo apt-get install cpuburn
burnP6 &
burnP6 &
burnP6 &
burnP6 &
burnP6 &
burnP6 &
burnP6 &
burnP6 &
sudo killall burnP6

```

Open a window and have a fire extinguisher ready.

---

### Post by pantale on 2014-11-08
Hi,

No, It's not a 8 core processor, I have 2 CPU, each of them have 4 core and hyperthread is not activated. So, I realy think that one is completely iddle but detected on boot.

I will try your test commands, but, as this is my office computer, I will only be able to do this monday.
I will also test with a live usb of my previous installation using another kernel to check.

Kindly Regards,

Olivier

---

### Post by Doug S on 2014-11-08
The only thing I found a little odd in the files you posted was the "core id" numbering:```
doug@s15:~/temp2$ grep "core id" cpuinfo.txt
core id         : 0
core id         : 1
core id         : 9
core id         : 10
core id         : 0
core id         : 1
core id         : 9
core id         : 10
```We expect them to repeat per physical id, but I find the 0,1,9,10 sequence odd (but also am not familiar with this processor).

In addition to what tgalati4 already mentioned, I would try to manually force the use of each CPU to see if it works. Example (using my own CPU burner and, in another terminal, top instead of htop):```
doug@s15:~/temp2$ [COLOR=#ff0000]taskset -c 7 ~/c/test1[/COLOR]
``````
top - 08:41:13 up 1 day, 17:27,  3 users,  load average: 0.84, 0.36, 0.17
Tasks: 177 total,   2 running, 175 sleeping,   0 stopped,   0 zombie
%Cpu0  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu1  :  0.0 us,  0.3 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu2  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu3  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu4  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu5  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu6  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
[COLOR=#ff0000]%Cpu7  :100.0 us,  0.0 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st[/COLOR]
KiB Mem:  16002000 total,  2529424 used, 13472576 free,   638596 buffers
KiB Swap:  8294396 total,        0 used,  8294396 free.   601336 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 9296 doug      20   0  785452 782188    852 R  [COLOR=#ff0000]99.8  4.9   1:31.24 test1[/COLOR]
    1 root      20   0   33920   4512   2740 S   0.0  0.0   0:01.90 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:01.64 ksoftirqd/0
```

---

### Post by tgalati4 on 2014-11-09
I would boot with a LiveUSB of 14.04 and capture the beginning of /var/log/syslog and compare it to 14.10.  It's possible there is a bug in the new kernel version.  To the kernel, it looks like one Compute Node, with 8 CPU's, but in reality, it is 2 CPU's with 4 cores each.  Try turning on Hytherthreading in BIOS and see what happens.

---

### Post by Doug S on 2014-11-09
> **tgalati4 said:**
> I would boot with a LiveUSB of 14.04 and capture the beginning of /var/log/syslog and compare it to 14.10.  It's possible there is a bug in the new kernel version.That is a good idea.  > **tgalati4 said:**
> To the kernel, it looks like one Compute Node, with 8 CPU's, but in reality, it is 2 CPU's with 4 cores each.I disagree, two are being detected with 4 cores each, as detailed via "physical id" and "cores" and "siblings".```
doug@s15:~/temp2$ grep "physical id" cpuinfo.txt
physical id     : 1
physical id     : 1
physical id     : 1
physical id     : 1
physical id     : 0
physical id     : 0
physical id     : 0
physical id     : 0
```Edit: Oh, I see from syslog and from your earlier post, where it says "Booted up 1 node, 8 CPUs". I believe (but am not sure) 1 node can have more than one processor.

---

### Post by pantale on 2014-11-10
I tried with a 14.04 xubuntu live USB, it was the same... Strange...

I think it's not a hardware problem since I tested the following with success:
core 0-4 are used
core 5-7 are alway 0%

taskset -c 4 burnP6&
taskset -c 5 burnP6&
taskset -c 6 burnP6&
taskset -c 7 burnP6&
gives:
core 4 : 100%
core 5 : 100%
core 6 : 100%
core 7 : 100%

When I switch off those specific tasks : return to 0%

Olivier

---

### Post by Doug S on 2014-11-10
Try loading up the system the way tgalati4 mentioned, where you do not force the CPU, but rather the scheduler will decide. What do you get for that case?

---

### Post by pantale on 2014-11-10
> **Doug S said:**
> Try loading up the system the way tgalati4 mentioned, where you do not force the CPU, but rather the scheduler will decide. What do you get for that case?
Only the core 0 to 4 are used in this case.

---

### Post by pantale on 2014-11-10
Hi,

Hereafter is a comparison of a working configuration using 3.2 kernel and non working one using 3.16 kernel.
The 3.2 is with a 12.04 LTS version
The 3.16 is with the new 14.10 version

Olivier

---

### Post by tgalati4 on 2014-11-10
There are differences between the two.  Perhaps file a bug against the 3.16 kernel and reference this thread.  Does turning on hyperthreading make a difference?

---

### Post by pantale on 2014-11-10
With hyperthreading on:
core 0-3 and 8-11 are ok.
core 4-7 and 12-15 are iddle.

---

### Post by pantale on 2014-11-10
I found the origin of the problem, or maybe a workaround...

In my bios settings on my Dell 7500 Precision workstation I have the choice between SMP and NUMA memory sharing for the processors.

I have 6Gb of ram on the motherboard with the first processor
I have 6Gb of ram on a deported board with the second processor.

With SMP, only half of the first processor is used.
With NUMA, both processors are used.

But, I don't know why and how the performances will be this this new configuration of my RAM.

Olivier

---

### Post by tgalati4 on 2014-11-10
You would have to get into the details on NUMA--I have no idea what that is.  SMP could be symmetric multiprocessing--which means RAM is shared equally between two processors.  The caches are generally 2-way, set associative, so anything in L1 (possibly L2) cache can be pulled by any core on the same die.  Perhaps there is an L3 cache and the performance of that would depend on whether the RAM is split or shared.

There are probably several performance-related tweaks in the BIOS of a Dell Precision workstation.

---

