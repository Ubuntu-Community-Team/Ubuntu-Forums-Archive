---
title: "Ryzen single core only?"
date: 2017-04-10
forum: Hardware
---

### Post by cpu-pirate on 2017-04-10
Hello all,

New here, and I have seen a lot of threads across the Internet with similar issues, I have tried several steps outlined in older versions and kernels and so far have been unable to solve the single core issue with my new Ryzen system, specs below:

Mobo: MSI Pro Carbon x370
Proc: AMD Ryzen 1700x
Ram: 32 GB Corsair LPX
Drives: 2x NVMe (booting drive) and 1x 1tb ssd

```
 $lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            23
Model:                 1
Model name:            AMD Ryzen 7 1700X Eight-Core Processor
Stepping:              1
CPU MHz:               3393.217
BogoMIPS:              6786.43
Virtualization:        AMD-V
L1d cache:             32K
L1i cache:             64K
L2 cache:              512K
L3 cache:              8192K
NUMA node0 CPU(s):     0


```

So far I have got Ubuntu 16.04.2 to boot and install by appending "acpi=off" during boot (grub.cfg)
After that I was able to update to the latest kernel 4.10 
```
 uname -a
Linux pirate-Ubuntu 4.10.1-041001-generic #201702260735 SMP Sun Feb 26 12:36:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

I then removed acpi=off from /etc/default/grub.cfg and still able to boot but I still return the same single core used.

I have checked bios and manually set the number of downcore to all variants from 2 to 6 with no avail, I can still boot but still only show 1 core available. 
I just remembered one more step I will try after posting this to disable legacy USB in the bios, saw that somewhere. 

Anyone run into this, is this appearing to be a Ryzen specific issue (dont think so as several reviewers have been able to get full support for all cores in linux on Ryzen already, and it appears Gigabyte users are complaining about this issue as well) or is this something with Ubuntu?

---

### Post by cpu-pirate on 2017-04-11
Tired to disable USB legacy support in the bios same issue. I have windows installed on another hard drive now and even in a VM I can still only see 1 core no matter how many I give the VM. Windows sees them all just fine.

---

### Post by cpu-pirate on 2017-04-11
UPDATE:

Dont know what happened exactly I decided to try the new 4.11 rc6 kernel which resulted in a login loop.
I selected advanced options for startup and went back to the old kernel 4.10.1 and when it booted in, all the procs show!! 

```

$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                16
On-line CPU(s) list:   0-15
Thread(s) per core:    2
Core(s) per socket:    8
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            23
Model:                 1
Model name:            AMD Ryzen 7 1700X Eight-Core Processor
Stepping:              1
CPU MHz:               3000.000
CPU max MHz:           3400.0000
CPU min MHz:           2200.0000
BogoMIPS:              6770.68
Virtualization:        AMD-V
L1d cache:             32K
L1i cache:             64K
L2 cache:              512K
L3 cache:              8192K
NUMA node0 CPU(s):     0-15


 
```

---

