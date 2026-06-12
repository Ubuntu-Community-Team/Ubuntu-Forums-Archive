---
title: "AMD Athlon X2 Compatibility Problem"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by adun07 on 2008-03-22
Processor: AMD Athlon X2 4400+
Motherboard: ASUS M2N-MX SE
Chipset: NVIDIA GeForce6100 / nForce430
Memory: 2GB ddr2 800 (dual channel)

Ubuntu 7.10, 7.04, 5.10 (32-bit and 64-bit alike) and openSUSE 10.3 didn't work.

In the versions of 32-bit ubuntu says:
MP-BIOS bug: 8254 timer not connected to 10-APIC
Kernel Panic-not syncing:
IOAPIC +timer doesn't work!
Boot with apic=debug and send report. Then try booting with the 'noapic' option.

Please help. :cry:

---

### Post by mrsteveman1 on 2008-03-22
Have you tried booting with the kernel options that suse uses for safe mode? they are more extensive than what lots of distros use and almost always work.

I dont have a suse system sitting here and i cant find the options they use online for the moment, but if you can boot the suse 10.3 cd you should be able to select their safe mode.

---

### Post by mrsteveman1 on 2008-03-22
I think this is the line modified to use on ubuntu:

```
vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single
```

This will also boot into single user mode so that you can tell easily if it worked without waiting for the livecd to load everything.

---

### Post by adun07 on 2008-03-29
I tried to run gutsy gibbon in virtual pc on my box with the specs written on my first post. It worked. I wonder why.

---

### Post by adun07 on 2008-03-29
> **mrsteveman1 said:**
> I think this is the line modified to use on ubuntu:

```
vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single
```

This will also boot into single user mode so that you can tell easily if it worked without waiting for the livecd to load everything.

Thanks, man! Where do I go from there? Can I install ubuntu from the command line?

---

### Post by mrsteveman1 on 2008-03-30
Well, if that line fixed the problem, what solved it wasn't single user mode, so remove the single part from that line and boot the livecd normally, and you can install like normal.

However it would be a good idea for you to test each of those options individually to see which one keeps the system from locking, you dont want to run all the time with all those things turned off.

---

