---
title: "Uncertain if quad-core processor recognised"
date: 2009-02-07
forum: Hardware
---

### Post by walawa on 2009-02-07
Hi,
I've been using Ubuntu on with an Intel Quad-Core Q6600, but I am currently starting to doubt if all four cores are recognized. I noticed this when I launched Conky and it said that I was trying to monitor more cores than I had. I then went to system monitor and I realized it only shows one core. I checked the BIOS and all four cores are shown and enabled.

I ran "cat /proc/cpuinfo" : ```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping    : 11
cpu MHz        : 2399.950
cache size    : 4096 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips    : 4799.90
clflush size    : 64
power management:
```

I'm not fully sure how to interpret this, but 1 is under cpu cores.

I'm not certain, but I think this may have something to do with updating from 8.04 to 8.10. After the upgrade I noticed the system was slower than before and now I've just noticed what I mentioned above. Another possibility would be that I recently installed Windows on a separate partition. Windows is also pretty slow, but it isn't necessary to me so I don't really mind. Could any of these things be what's causing my problem?

Is there a way to check if Ubuntu recognizes my processor, and if not how can I fix this?

---

### Post by blueridgedog on 2009-02-07
What is the output of

```
sudo lshw -class cpu
```

---

### Post by walawa on 2009-02-07
Here's th ouput:   ```
*-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.15.11
       serial: 0000-06FB-0000-0000-0000-0000
       slot: Socket 775
       size: 600MHz
       width: 64 bits
       clock: 66MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
     *-logicalcpu:2
          description: Logical CPU
          physical id: 0.3
          width: 64 bits
          capabilities: logical
     *-logicalcpu:3
          description: Logical CPU
          physical id: 0.4
          width: 64 bits
          capabilities: logical
```

---

### Post by blueridgedog on 2009-02-07
Well, it sees them there...

You can install sysstat with:

```
sudo apt-get install systat
```

Then run:

```
mpstat -P ALL 
```

Which should give you a list of the load of each core.

---

### Post by igknighted on 2009-02-07
Each "core" is listed as a separate processor.  So each core only has one core, but there should be four CPUs (CPU0-CPU3)

---

### Post by bettlebrox on 2009-02-07
"cat /proc/cpu" should list all of your cores. If if it only shows one core then your kernel is only using one core. 

Which kernel & version are you using? The output of "uname -a" will display that info.

Any recent kernels that Ubuntu should be multi-core/smp aware, so it's possible this is a misconfiguration somewhere.

---

### Post by walawa on 2009-02-07
mpstat -P ALL:
```
Linux 2.6.27-9-generic (tristan-desktop) 	07/02/09 	_i686_

01:07:05 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:07:05 PM  all   19.38    0.11    3.88    1.59    0.31    0.18    0.00   74.55    509.53
01:07:05 PM    0   19.38    0.11    3.88    1.59    0.31    0.18    0.00   74.55    332.08
```

uname -a:
```
Linux tristan-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
```

The output of "cat /proc/cpu" is "no such file or directory". Why is this?

---

### Post by blueridgedog on 2009-02-07
Odd...mpstat is only showing one cpu.  Perhaps another forum member can post a better tool.

---

### Post by anders_c_ on 2009-02-07
its supposed to be:
cat /proc/cpuinfo

---

### Post by walawa on 2009-02-07
cat /proc/cpuinfo: ```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 2399.950
cache size	: 4096 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4799.90
clflush size	: 64
power management:
```

---

### Post by blueridgedog on 2009-02-07
Just a wild idea, but you might try booting into an older kernel (if you system is a few months old, you should have several kernel options when you boot) and run the mpstat command under a different kernel version.

---

### Post by anders_c_ on 2009-02-07
there should be one folder for each core in:
/sys/devices/system/cpu

i have 2 cores so i have the folders:
/sys/devices/system/cpu/cpu0
/sys/devices/system/cpu/cpu1

all cores except "cpu0" should have a file called online in them
if that file contains a zero the core will be offline, so try:
cat /sys/devices/system/cpu/cpu1/online
cat /sys/devices/system/cpu/cpu2/online
cat /sys/devices/system/cpu/cpu3/online

if it says "0" change them to "1" by opening a root terminal and typing:
echo "1" > /sys/devices/system/cpu/cpu1/online

IT HAS TO BE A ROOT TERMINAL, sudo wont work...not really sure why but it
has something to do with the ">"

if this doesnt work or if u dont even have one folder for each core in
/sys/devices/system/cpu/ then i have no clue, perhaps a reinstall??

---

### Post by bettlebrox on 2009-02-07
Your kernel version looks fine:
2.6.27-9-generic #1 SMP

It's possible to disable SMP (and hence multi-core support) at boot time. Did you make any changes to your grub configuration?

Also, start up top from the a shell (command-line). By default it doesn't show all the cores, but if you press "1" it'll show all the CPU/Core's and load on each one. Try and see if you see more than one Core.

---

### Post by ectospasm on 2009-02-07
> **anders_c_ said:**
> there should be one folder for each core in:
/sys/devices/system/cpu

i have 2 cores so i have the folders:
/sys/devices/system/cpu/cpu0
/sys/devices/system/cpu/cpu1

all cores except "cpu0" should have a file called online in them
if that file contains a zero the core will be offline, so try:
cat /sys/devices/system/cpu/cpu1/online
cat /sys/devices/system/cpu/cpu2/online
cat /sys/devices/system/cpu/cpu3/online

if it says "0" change them to "1" by opening a root terminal and typing:
echo "1" > /sys/devices/system/cpu/cpu1/online

IT HAS TO BE A ROOT TERMINAL, sudo wont work...not really sure why but it
has something to do with the ">"

if this doesnt work or if u dont even have one folder for each core in
/sys/devices/system/cpu/ then i have no clue, perhaps a reinstall??

I've only got one cpuN device in /sys/devices/cpu/.  A reinstall is pathetic at this point, since I KNOW it was working with this very kernel previously. I tried downgrading to the 2.6.27-9 kernel, to no avail.  

Here's output of various commands.  lshw apparently shows that I should be seeing all  four cores, but the kernel et al. show nothing:

```
amphetamine:~ # cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9950 Quad-Core Processor
stepping	: 3
cpu MHz		: 2600.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 5199.85
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

amphetamine:~ # lshw -class cpu
  *-cpu:0                 
       description: CPU
       product: AMD Phenom(tm) 9950 Quad-Core Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 3
       bus info: cpu@0
       version: 15.2.3
       slot: Socket AM2
       size: 2600MHz
       capacity: 2600MHz
       width: 64 bits
       clock: 200MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs cpufreq
  *-cpu:1
       physical id: 4
       bus info: cpu@1
       version: 15.2.3
       size: 18EHz
  *-cpu:2
       physical id: 5
       bus info: cpu@2
       version: 15.2.3
       size: 18EHz
  *-cpu:3
       physical id: c
       bus info: cpu@3
       version: 15.2.3
       size: 18EHz
  *-processor UNCLAIMED
       description: Co-processor
       product: MCP78S [GeForce 8200] Co-Processor
       vendor: nVidia Corporation
       physical id: 1.3
       bus info: pci@0000:00:01.3
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master
       configuration: latency=0 maxlatency=1 mingnt=3

```

I KNOW it was working before, and the only thing I really changed was a routine kernel upgrade.  I'm wondering if this is a bug?  Or a failing chip?  I dunno...

---

### Post by walawa on 2009-02-07
I only have a folder named cpu0 and another named cpuidle in /sys/devices/system/cpu. I have made changes to grub. I recently installed Windows over Ubuntu and had to make some changes for it to work.

> Also, start up top from the a shell (command-line). By default it doesn't show all the cores, but if you press "1" it'll show all the CPU/Core's and load on each one. Try and see if you see more than one Core.
I'm not sure how to start up form the shell. Do you mean login without X?

---

### Post by unutbu on 2009-02-07
On a dual core processor, this is the output of "dmesg | grep -i cpu":

```
% dmesg | grep -i cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] ACPI: SSDT 3FEE7CA0, 0380 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.433808] CPU0: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
[    0.004000] Initializing CPU#1
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.520411] CPU1: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
[    0.520428] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.524055] **Brought up 2 CPUs**
[    0.524080] CPU0 attaching sched-domain:
[    0.524093] CPU1 attaching sched-domain:
[    0.576042] Switched to high resolution mode on CPU 0
[    0.576457] Switched to high resolution mode on CPU 1
[    2.148572] cpuidle: using governor ladder
[    2.148575] cpuidle: using governor menu
[    2.275330] ACPI: SSDT 3FEE7680, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    2.275856] ACPI: SSDT 3FEE7B40, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    3.417141]  [<c010288d>] cpu_idle+0x7d/0x140
```

Notice the line that says "Brought up 2 CPUs". 
Sometimes dmesg contains useful error messages. 
Perhaps take a look at and post your "dmesg | grep -i cpu"

Also, post 

```
uname -a
```

This will tell us which kernel you are using.

---

### Post by ectospasm on 2009-02-07
> **unutbu said:**
> On a dual core processor, this is the output of "dmesg | grep -i cpu":...


Yeah, the boot messages say only one CPU has been started.  Unfortunately I have no idea why, since it stopped working afaict on its own.  Reverting back to a previous kernel doesn't fix it, so I doubt the problem lies in the options compiled into (or left out of) my running kernel.

```
amphetamine:~ # dmesg | grep -i cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Kernel command line: root=UUID=5b026cc0-09be-4255-8023-54c95619ca42 ro cpus=4 splash 
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(4) -> Core 0
[    0.333158] CPU0: AMD Phenom(tm) 9950 Quad-Core Processor stepping 03
[   16.512119] Brought up 1 CPUs
[   16.512284] CPU0 attaching NULL sched-domain.
[   16.900044] Switched to high resolution mode on CPU 0
[   17.970274] cpuidle: using governor ladder
[   17.970336] cpuidle: using governor menu
[   51.589855] powernow-k8: Found 1 AMD Phenom(tm) 9950 Quad-Core Processor processors (1 cpu cores) (version 2.20.00)
amphetamine:~ # uname -a
Linux amphetamine 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

```

It seems that WinXP can see all four cores, unless my CPU has failed and Windows just sucks.

---

### Post by walawa on 2009-02-08
Here's the output of dmesg | grep -i cpu: ```
 [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004192] Initializing cgroup subsys cpuacct
[    0.004206] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004208] CPU: L2 cache: 4096K
[    0.004210] CPU: Physical Processor ID: 0
[    0.004211] CPU: Processor Core ID: 0
[    0.300052] weird, boot CPU (#0) not listedby the BIOS.
[    0.304019] Brought up 1 CPUs
[    0.304019] CPU0 attaching sched-domain:
[    0.304019]  domain 0: span 0 level CPU
[    0.928064] Switched to high resolution mode on CPU 0
[    1.396353] cpuidle: using governor ladder
[    1.396355] cpuidle: using governor menu
[    1.884046] ACPI: Processor [CPU0] (supports 8 throttling states)
```
Mine also says only one cpu has been started out of the four.

My kernel is Linux tristan-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux.

I don't know if this has anything to do with it, but I'm using Phoenix BIOS.

---

### Post by walawa on 2009-02-08
I tried booting from an 8.04 LiveCD but system monitor still didn't recognize all 4 cores. Could booting into a more recent LiveCD help?

I've seen posts where booting with acpi off helped. Should I try this?

Would using 64-bit ubuntu help?

---

### Post by unutbu on 2009-02-08
Try booting with kernel option "noapic".

This is where I'm getting this information:
[http://fixunix.com/linux/269544-weird-boot-cpu-0-not-listed-bios.html](http://fixunix.com/linux/269544-weird-boot-cpu-0-not-listed-bios.html)

If that does not work, try "acpi=off".

And here are instructions for booting with kernel options:
[http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4)

---

### Post by blueridgedog on 2009-02-08
My concern is this is not something that is particular to the systems listed, but may be more general for specific CPUs or kernel versions.  Perhaps some other members will chime in with reports of support for their quad core CPUs.

---

### Post by bapoumba on 2009-02-08
Moved to hardware (thanks blueridgedog ;))

---

### Post by walawa on 2009-02-08
I tried booting with noapic and then with acpi=off at the end of the kernel line, but it did not make a difference.

This is the output of dmesg | grep -i cpu: ```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Initializing CPU#0
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004189] Initializing cgroup subsys cpuacct
[    0.004202] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004205] CPU: L2 cache: 4096K
[    0.004207] CPU: Physical Processor ID: 0
[    0.004208] CPU: Processor Core ID: 0
[    0.024039] weird, boot CPU (#0) not listedby the BIOS.
[    0.132067] Brought up 1 CPUs
[    0.132078] CPU0 attaching sched-domain:
[    0.132080]  domain 0: span 0 level CPU
[    1.116669] cpuidle: using governor ladder
[    1.116671] cpuidle: using governor menu
```

Could the line that says "SMP: Allowing 1 CPUs, 0 hotplug CPUs" have anything to do with the problem?

---

### Post by blueridgedog on 2009-02-09
Perhaps it is certain Bios(es) and certain CPU's that the kernal has trouble with?

---

### Post by unutbu on 2009-02-09
I agree with blueridgedog. Please run
```

sudo lshw | bzip2 -c > lshw.bz2
``` and attach lshw.bz2 to a post so we'll know the make/model of your machine, motherboard, bios, and cpus.

Googling any of those keywords along with "SMP Allowing 1 CPUs" or "weird, boot CPU (#0) not listedby the BIOS" might also be useful.

---

### Post by ectospasm on 2009-02-09
> **blueridgedog said:**
> Perhaps it is certain Bios(es) and certain CPU's that the kernal has trouble with?

In that case I'd expect it to be consistent, that it would either recognize or fail to recognize all four of my cores 100% of the time.  For me at least, I'm guessing that it fails to recognize all four cores about 85% of the time.  Right now, I'm in a boot that sees all four cores.  If I reboot, I suspect only one core will come up.

---

### Post by anv on 2009-02-09
Sorry to disturb, but I noticed exactly same behavior on my AMD quad-core processor this was my original question:

[http://ubuntuforums.org/showthread.php?t=1060923](http://ubuntuforums.org/showthread.php?t=1060923)

but as I did some of those first steps in this section, I noticed also that it gives just one cpu. but one thing also as I noticed while doing renderings and following the system from Htop if I stopped and continued it took core 3 instead of the core 4

---

### Post by unutbu on 2009-02-09
For what it's worth, here is a testimonial that the Core 2 Quad Q6600 processor is compatible with Ubuntu 8.10 (both 32- and 64-bit):
[https://lists.ubuntu.com/archives/ubuntu-users/2009-January/170329.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-January/170329.html)

---

### Post by blueridgedog on 2009-02-09
One has to wonder if the author of that post actually verified that all four cores were running rather than the system working.  I am ordering a quad core this week, so soon I will have another statistic to add to the issue.

---

### Post by walawa on 2009-02-09
The output of "sudo lshw | bzip2 -c > lshw.bz2" is attached to this post.

Does ubuntu 8.10 use the 386 or 686 kernel? I've read that 686 is better for Intel processors. Is this true?

---

### Post by walawa on 2009-02-12
Would a fresh install fix the problem? Could installing 64 bit ubuntu or booting into a LiveCD help?

> Perhaps it is certain Bios(es) and certain CPU's that the kernal has trouble with?
Is there a way to reinstall the kernel, or something along those lines?

---

### Post by blueridgedog on 2009-02-13
Well, you might try booting off of the 32 bit and 64 bit live cd and seeing if it sees all four cores.

---

### Post by walawa on 2009-02-14
I'll probably try booting into a 64-bit LiveCD later today. Would compiling a new kernel possibly fix this issue?

---

### Post by blueridgedog on 2009-02-14
I don't think so, but I would verify the kernels you have tried and then submit a bug report:

[https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)

I feel strongly that it is a combination of certain chipsets/bioses/cpus.

---

### Post by walawa on 2009-02-14
It's fixed. System monitor now shows all four cores. The problem was that apic wasn't disabled in the kernel line, but it was in the BIOS setup. I'd already checked the BIOS to make sure all cores were enabled, but I guess I didn't notice the apic option.

Thanks for your help.

---

### Post by unutbu on 2009-02-14
Congratulations, walawa, and thank you for posting your solution!
What did you do differently between now and [post #23 ]("http://ubuntuforums.org/showpost.php?p=6700480&postcount=23") when you tried booting with "noapic" ?

---

### Post by walawa on 2009-02-14
In post #23 I was trying to boot with acpi disabled because I'd read it could help, but this did not make a difference because I didn't know that acpi was already disabled in the BIOS. The problem was that I've been booting with acpi disabled without knowing it. So I enabled it and now everything works fine.

---

### Post by bettlebrox on 2009-02-14
Great! Glad you got the 4 cores enabled. :)

---

### Post by ectospasm on 2009-02-26
It seems to be hit or miss with me.  Earlier this month I posted on launchpad, I'm not sure why I didn't post here.  My original bug post was marked as a duplicate of this:  [Bug#97554]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/97554")

And no, disabling APIC is not a viable solution. The way I understand it, that would disable SMP altogether, which is not what I want.

---

