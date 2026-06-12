---
title: "Missing CPU Cores on Q6600"
date: 2013-10-17
forum: Hardware
---

### Post by mythms on 2013-10-17
Please help.  My Q6600 is only reporting two cores:

* I can't find any settings in BIOS to enable/disable CPUS (board ASUS P5G41T-M LX PLUS)
* I have loaded the BIOS defaults by powering down and jumpering the CLRTC pins (per board manual)
* I do have the latest BIOS

Ideas anyone?

```
@q6600:~$ uname -a
Linux q6600 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 16:50:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

```

@q6600:~$ sudo lshw -class cpu
[sudo] password for joey: 
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.40GHz
       serial: To Be Filled By O.E.M.
       slot: LGA775
       size: 2136MHz
       capacity: 3800MHz
       width: 64 bits
       clock: 266MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
       configuration: cores=4 enabledcores=4 threads=4

```

```
@q6600:~$ dmesg | grep SMP
[    0.000000] Linux version 3.5.0-41-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #64~precise1-Ubuntu SMP Thu Sep 12 16:50:04 UTC 2013 (Ubuntu 3.5.0-41.64~precise1-generic 3.5.7.21)
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs

```

```
user@q6600:~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              11
CPU MHz:               1603.000
BogoMIPS:              4801.57
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              4096K
NUMA node0 CPU(s):     0,1

```

```
@q6600:~$ ls -lia /sys/devices/system/cpu/
total 0
 37 drwxr-xr-x 7 root root    0 Oct 17 20:03 .
  9 drwxr-xr-x 7 root root    0 Oct 17 20:03 ..
977 drwxr-xr-x 8 root root    0 Oct 17 20:03 cpu0
994 drwxr-xr-x 8 root root    0 Oct 17 20:03 cpu1
760 drwxr-xr-x 3 root root    0 Oct 17 20:03 cpufreq
761 drwxr-xr-x 2 root root    0 Oct 17 20:03 cpuidle
 44 -r--r--r-- 1 root root 4096 Oct 17 20:16 kernel_max
 46 -r--r--r-- 1 root root 4096 Oct 17 20:16 modalias
 45 -r--r--r-- 1 root root 4096 Oct 17 20:16 offline
 41 -r--r--r-- 1 root root 4096 Oct 17 20:03 online
 42 -r--r--r-- 1 root root 4096 Oct 17 20:16 possible
 47 drwxr-xr-x 2 root root    0 Oct 17 20:16 power
 43 -r--r--r-- 1 root root 4096 Oct 17 20:16 present
 39 --w------- 1 root root 4096 Oct 17 20:23 probe
 40 --w------- 1 root root 4096 Oct 17 20:16 release
 38 -rw-r--r-- 1 root root 4096 Oct 17 20:03 uevent

```

```

@q6600:~$ cat /sys/devices/system/cpu/offline 
2-3
@q6600:~$ cat /sys/devices/system/cpu/online 
0-1

```

---

### Post by tgalati4 on 2013-10-17
Is it a real Intel CPU chip?  There are some fakes floating around.  (But I really doubt this).

Perhaps the 2 hotplug cores only wake up when the load requires it?  Is there something in the Power Management BIOS that relates to hotplug or on-demand?

Install *htop*, *cpuburn*, then run *htop* on a separate terminal.  Run the following:

```
burnP6 &
burnP6 &
burnP6 &
burnP6 &
```

Watch *htop* and see if the other two cores wake up.  You can kill the *burnP6* processes with:

```
sudo killall burnP6
```

---

### Post by sanderj on 2013-10-18
Did you read [http://ubuntuforums.org/archive/index.php/t-1062918.html](http://ubuntuforums.org/archive/index.php/t-1062918.html) ? Same CPU, same problem. Eventually solved "It's fixed. System monitor now shows all four cores. The problem was that apic wasn't disabled in the kernel line, but it was in the BIOS setup. I'd already checked the BIOS to make sure all cores were enabled, but I guess I didn't notice the apic option."

---

### Post by mythms on 2013-10-19
Just tried burnP6.  100% on two cores in htop but no changes to /sys/devices/system/cpu.  Shouldn't I have /sys/devices/system/cpu/cpu2 and /sys/devices/system/cpu/cpu3 if they were simply 'hot unplugged'?

---

### Post by mythms on 2013-10-19
All of the APIC options were/are enabled in BIOS and I don't see any options for enabling/disabling cores in BIOS.  Admittedly this is kind of low-end motherboard.  I a re-commissioning a q6600 as a server.  The motherboard that served me so well was having stability issues so I purchased this P5G41T-M LX PLUS.  BTW, I am running the latest BIOS firmware. 

Thanks to both of you for thoughtful replies.

---

### Post by tgalati4 on 2013-10-19
Was the Q6600 delivered with the low-end motherboard?  Or did you install it yourself.  Perhaps your board doesn't completely support the Q6600.  The board may be pin-compatible but not feature compatible.

---

### Post by sanderj on 2013-10-19
[http://support.asus.com/Cpusupport/List.aspx?SLanguage=en&m=P5G41T-M%20LX%20PLUS&p=1&s=22](http://support.asus.com/Cpusupport/List.aspx?SLanguage=en&m=P5G41T-M%20LX%20PLUS&p=1&s=22) says

> Core 2 Quad Q6600 (2.40GHz,1066FSB,L2:2X4MB,rev.B3,4 cores)	 ALL	0304	

  
Core 2 Quad Q6600 (2.40GHz,1066FSB,L2:2X4MB,rev.G0,4 cores)	 ALL	0304	

  

So, as long as you've got the latest BIOS, it should work.

Have you already reset the BIOS to default?

---

