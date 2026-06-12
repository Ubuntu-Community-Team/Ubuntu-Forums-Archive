---
title: "Ubuntu only detecting 3GB of RAM when 4GB Installed"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by bartman007 on 2005-09-21
I am running the 32-bit version of Hoary on an AMD64 based system.
The hardware is as follows:
Athlon64 3700+ San Diego Core
ASUS A8N-SLI Motherboard - nForce4 SLI chipset
4x 1GB PC3200 ECC Ram Sticks
2x 160GB SATAII Western Digital HD's in a RAID-1 array

I am running the current 686 kernel on the computer and it detected the RAM fine when I had only 2x 1GB sticks installed.  Upon installing the other two sticks, Ubuntu only detects 3GB.  I have found reference across the net to older kernels (2.4 based) that had problems with 4GB of ram, generally the kernel allocated only 3GB to userspace, and left 1GB for itself, but since Ubuntu is based on a 2.6 kernel, this shouldn't be an issue.  The kernel is configured to use 4G (CONFIG_HIGHMEM4G=y) so I don't know what could be wrong.

This server is commonly used for intense simulations that can consume several gigabytes of memory between them so minimal use of swap is highly desirable.

Thank you,
-Bartman007

---

### Post by earobinson on 2005-09-21
have your tried a mem test?

---

### Post by bartman007 on 2005-09-21
Yes I have tried Memtest86+ 1.60, and it correctly detects 4GB of ram.  Though, it does test it in two segments, up to 3072MB (3GB) and then from 4096 to 5120.  This occurs when PAE (Physical Address Extending) is enabled.  This moves the 3072-4096 meg section of ram to 4096-5120.  When PAE (which is executed in via hardware since this chip is higher than E0 revision,) is disabled, both the BIOS and Memtest only see 3072 MB of ram.  In either case, Ubuntu detects 3GB of ram.

I understood that Linux 2.4 kernels could only allocated 3GB of ram to the userspace, but I thought that Linux 2.6 kernels could allocate more (up to 64GB or higher), but were limited to 3GB per thread/process.

In order to access the remapped ram (now in the 4096-5120MB area) am I going to have to recompile the kernel with 64GB support enabled?  Also, would the AMD64 version of Ubuntu support all 4GB natively?

Thank you,
-Bartman007

---

### Post by machaval on 2006-08-11
We try with the live cd of 64 bits and it detect the 4G. Is there a way to use the 4G with the 32 bits version.

---

