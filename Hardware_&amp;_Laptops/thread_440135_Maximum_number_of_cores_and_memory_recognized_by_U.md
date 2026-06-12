---
title: "Maximum number of cores and memory recognized by Ubuntu?"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by ioannis on 2007-05-11
We are looking to get a new workstation which has four quad core processors and 128 GB \\:D/ , I was wondering what are the upper limits (if any) that amd64 Ubuntu has in terms of number of cpu's and memory.
Thanks!

---

### Post by Ken_Lewis81 on 2007-05-11
Congratulations on winning the bragging contest.  Forever. :)

There's the linux-image-server and linux-image-server-bigiron kernels you can install for big machines.  The linux-server-bigiron kernel package ([notes here](https://launchpad.net/ubuntu/gutsy/+package/linux-image-2.6.20-15-server-bigiron)) might be helpful.

Take care.
Ken.

---

### Post by ioannis on 2007-05-11
Thanks for the reply. I was looking at the bigiron kernel, and it seems that it is only available for the i386 architecture option, not available for the amd64. Won't this limit the memory recognized by the system to 4 GB? I thought that the i386 arch option was a 32 bit OS and the amd64 was the only 64 bit option, which pretty much made the max memory some huge number. Am I wrong about this?
Should I assume that if I don't use the bigiron kernel all 16 cores and 128 GB will not be recognized, or is it just optimized for such a powerful computer?

Thanks!

---

### Post by Ken_Lewis81 on 2007-05-16
Looking at the AMD64 linux-image-generic, the MAX_CPU is set to 8; the linux-image-server has MAX_CPU set to 64. My single-core Turion64 could address all of your 128 GiB of RAM -- all AMD64 chips can address 40 bits worth of bytes; that's 8 times your memory load. I guess that means that Ubuntu's AMD64 edition will handle your system.

Two ways to go about it: if you're going to be using it as a server, install the Server flavour.  If you're going to be using it as a workstation, either:
(*) Install the server flavour, then 'sudo aptitude install ubuntu-desktop'; or
(*) Install the desktop flavour, then 'sudo aptitude install linux-image-server' (which would perhaps be best)

Take care.
Ken.

---

### Post by heimo on 2007-05-16
> **ioannis said:**
> We are looking to get a new workstation which has four quad core processors and 128 GB \\:D/ , I was wondering what are the upper limits (if any) that amd64 Ubuntu has in terms of number of cpu's and memory.
Thanks!

And please do send us some benchmarks when you get it set up. :)

---

